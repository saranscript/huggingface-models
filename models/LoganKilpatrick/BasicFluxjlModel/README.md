This model is for anyone using using Flux.jl and looking for a test model to make sue of the Hugging Face hub. You can see the source code to generate this model below:

```Julia
julia> using Flux

julia> model = Chain(Dense(10, 5, NNlib.relu), Dense(5, 2), NNlib.softmax)
Chain(Dense(10, 5, NNlib.relu), Dense(5, 2), NNlib.softmax)

julia> using BSON: @save

julia> @save "mymodel.bson" model
```

you can then load the model in Julia as follows:

```Julia
julia> using Flux

julia> using BSON: @load

julia> @load "mymodel.bson" model

julia> model
Chain(Dense(10, 5, NNlib.relu), Dense(5, 2), NNlib.softmax)
```

See here: https://fluxml.ai/Flux.jl/stable/saving/#Saving-and-Loading-Models for more details! 