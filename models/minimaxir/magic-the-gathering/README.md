# magic-the-gathering

A small (~1M parameters) GPT-2 model trained on Magic: The Gathering cards from sets up to and including _Strixhaven_ and _Commander 2021_.

The model was trained 8 hours on a V100 on about ~22k unique encoded cards, with 10 permutations of each possible card.

Examples of encoded cards:

```
<|toughness|><|text|>Counter target spell unless its controller pays {X}.<|power|><|type|>Instant<|loyalty|><|manaCost|>{X}{U}<|name|>Clash of Wills
```

```
<|loyalty|><|text|>~ enters the battlefield tapped.
{T}: Add {C}.
{T}: Add {U} or {R}. ~ deals 1 damage to you.<|toughness|><|name|>Caldera Lake<|power|><|manaCost|><|type|>Land
```

```
<|loyalty|>5<|text|>+1: Scry 1, then draw a card.
−2: Return target creature to its owner's hand.
−8: You get an emblem with "Whenever an opponent casts their first spell each turn, counter that spell."<|name|>Jace, Unraveler of Secrets<|toughness|><|type|>Legendary Planeswalker — Jace<|manaCost|>{3}{U}{U}<|power|>
```

The generated cards follow a similar schema, however because the model learns all possible permutations of the schema, the user can prompt the generation with any combination of schema.
