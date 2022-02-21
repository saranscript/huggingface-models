---
widget:
- text: " htmlOn ||| <h1"
---

# Work In Progress

# How to use?

To generate text with HTML, the sentence must start with ` htmlOn |||` (note the space at the beginning 😉). To generate normal text, you don't need to add anything. 
 
# Training details

We continued the pre-training of [gpt2](https://huggingface.co/gpt2).

Dataset:[Natural_Questions_HTML_reduced_all](https://huggingface.co/datasets/SaulLu/Natural_Questions_HTML_reduced_all)
50% of the examples in the training data contained `h1`, `h2`, ..., `h6` and `p` HTML tags with only their `id` and `class` attributes. 50% of the examples were just plain text.

Training example with metadata: 
```
 htmlOn ||| <h1 id:firstHeading class:firstHeading>Market power</h1>
From Wikipedia, the free encyclopedia
Jump to: navigation, search
Competition law
Basic concepts
History of competition law
Monopoly
Coercive monopoly
Natural monopoly
Barriers to entry
Herfindahl–Hirschman Index
Market concentration
Market power
SSNIP test
Relevant market
Merger control
Anti-competitive practices
Monopolization
Collusion
Formation of cartels
Price fixing
Bid rigging
Product bundling and tying
Refusal to deal
Group boycott
Essential facilities
Exclusive dealing
Dividing territories
Conscious parallelism
Predatory pricing
Misuse of patents and copyrights
Enforcement authorities and organizations
International Competition Network
List of competition regulators
v
t
e
<p>In economics and particularly in industrial organization, market power is the ability of a firm to profitably raise the market price of a good or service over marginal cost. In perfectly competitive markets, market participants have no market power. A firm with total market power can raise prices without losing any customers to competitors. Market participants that have market power are therefore sometimes referred to as "price makers" or "price setters", while those without are sometimes called "price takers". Significant market power occurs when prices exceed marginal cost and long run average cost, so the firm makes profit.</p>
<p>A firm with market power has the ability to individually affect either the total quantity or the prevailing price in the market. Price makers face a downward-sloping demand curve, such that price increases lead to a lower quantity demanded. The decrease in supply as a result of the exercise of market power creates an economic deadweight loss which is often viewed as socially undesirable. As a result, many countries have anti-trust or other legislation intended to limit the ability of firms to accrue market power. Such legislation often regulates mergers and sometimes introduces a judicial power to compel divestiture.</p>
<p>A firm usually has market power by virtue of controlling a large portion of the market. In extreme cases—monopoly and monopsony—the firm controls the entire market. However, market size alone is not the only indicator of market power. Highly concentrated markets may be contestable if there are no barriers to entry or exit, limiting the incumbent firm's ability to raise its price above competitive levels.</p>
<p>Market power gives firms the ability to engage in unilateral anti-competitive behavior.[1] Some of the behaviours that firms with market power are accused of engaging in include predatory pricing, product tying, and creation of overcapacity or other barriers to entry. If no individual participant in the market has significant market power, then anti-competitive behavior can take place only through collusion, or the exercise of a group of participants' collective market power.</p>
<p>The Lerner index and Herfindahl index may be used to measure market power.</p>
<p></p><h2>Contents</h2>
[hide]
1 Oligopoly
2 Monopoly power
3 Source
4 Measurement
5 Elasticity of demand
6 Nobel Memorial Prize
7 See also
8 References
9 Further references
<p></p><h2>Oligopoly[edit]</h2>
<p>When several firms control a significant share of market sales, the resulting market structure is called an oligopoly or oligopsony. An oligopoly may engage in collusion, either tacit or overt, and thereby exercise market power. A group of firms that explicitly agree to affect market price or output is called a cartel.</p>
<h2>Monopoly power[edit]</h2>
<p>Monopoly power is an example of market failure which occurs when one or more of the participants has the ability to influence the price or other outcomes in some general or specialized market. The most commonly discussed form of market power is that of a monopoly, but other forms such as monopsony, and more moderate versions of these two extremes, exist.</p>
<p>A well-known example of monopolistic market power is Microsoft's market share in PC operating systems. The United States v. Microsoft case dealt with an allegation that Microsoft illegally exercised its market power by bundling its web browser with its operating system. In this respect, the notion of dominance and dominant position in EU Antitrust Law is a strictly related aspect.[2]</p>
<h2>Source[edit]</h2>
<p>A monopoly can raise prices and retain customers because the monopoly has no competitors. If a customer has no other place to go to obtain the goods or services, they either pay the increased price or do without.[3] Thus the key to market power is to preclude competition through high barriers of entry. Barriers to entry that are significant sources
```
