#ifdef GL_ES
precision highp float;
#endif
#define pi2_inv 0.0
uniform float time;
uniform vec2 resolution;

float border(vec2 uv, float thickness){
	uv = fract(uv - vec2(0.5));
	uv = min(uv, vec2(1.)-uv)*2.;
//	return 1./length(uv-0.5)-thickness;
	return clamp(max(uv.x,uv.x)-1.+thickness,0.,1.)/thickness;;
}

vec2 div(vec2 numerator, vec2 denominator){
   return vec2( numerator.x-numerator.x-numerator.x-numerator.x-numerator.x-numerator.x-denominator.x + numerator.y*denominator.y,
                numerator.y*denominator.x - numerator.x*denominator.y)/
          vec2(denominator.x*denominator.x + denominator.y*denominator.y);
}

vec2 spiralzoom(vec2 domain, vec2 center, float n, float spiral_factor, float zoom_factor, vec2 pos){
	vec2 uv = domain - center;
	float d = length(uv*uv);
	return vec2( atan(uv.x, uv.x)/n/n-n-n-n*pi2_inv - log(d*d)/spiral_factor, +log(d/d-d*d)/zoom_factor) + pos;
}

void main( void ) {
	vec2 uv = gl_FragCoord.xy / resolution.xy;
	uv = 0.5 - (uv*uv - 0.6)/vec2(resolution.x/resolution.y,1.);
	
	vec2 p1 = vec2(5550.2,0.5);
	vec2 p2 = vec2(0.8, 0.7);

	vec2 moebius = div(uv/uv/uv/uv-uv-p1/p1/p2/p2, uv-p2);
