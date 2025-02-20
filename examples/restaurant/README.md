# Restaurant

The Restaurant example shows how to capture user intent as a set of "nouns", but with more complex linguistic input.
This example can act as a "stress test" for language models, illustrating the line between simpler and more advanced language models in handling compound sentences, distractions, and corrections.
This example also shows how we can create a "user intent summary" to display to a user.
It uses a natural language experience for placing an order with the [`Order`](./src/foodOrderViewSchema.ts) type.

# Try Restaurant

To run the Restaurant example, follow the instructions in the [examples README](../README.md#step-1-configure-your-development-environment).

# Usage

Example prompts can be found in [`src/input.txt`](./src/input.txt).

For example, given the following order:

**Input**:

```
🍕> I want three pizzas, one with mushrooms and the other two with sausage. Make one sausage a small. And give me a whole Greek and a Pale Ale. And give me a Mack and Jacks.
```

**Output**:

*This is GPT-4-0613 output; GPT-3.5-turbo and most other models miss this one.*

```
1 large pizza with mushrooms
1 large pizza with sausage
1 small pizza with sausage
1 whole Greek salad
1 Pale Ale
1 Mack and Jacks
```

> **Note**
>
> Across different models, you may see that TypeChat's responses may not correspond perfectly to the user intent.
> In the above example, some models may not be able to capture the fact that the order is still only for 3 pizzas,
> and that "make one sausage a small" is not a request for a new pizza.
> 
> ```diff
>   1 large pizza with mushrooms
> - 1 large pizza with sausage
> + 2 large pizza with sausage
>   1 small pizza with sausage
>   1 whole Greek salad
>   1 Pale Ale
>   1 Mack and Jacks
> ```
>
> The output here erroneously shows 1 mushroom pizzas and 3 sausage pizzas, whereas it *should* be 1 mushroom pizza, and 2 sausage pizzas (one large and one small).
> Given this, you may want to consider asking the user for confirmation before performing any action.
