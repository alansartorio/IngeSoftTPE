---
marp: true
<!--theme: uncover-->
class: invert
style: |
  .columns {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    align-items: start;
    gap: 12px;
  }
  section {
    justify-content: center;
    align-items: stretch;
  }
  section p:has(img) {
    align-self: center;
  }
  section h1 {
    font-size: 5em;
    text-align: center;
  }
---

# <!--fit-->Reactive Programming

---

## Introduction

- Reactive programming is a programming paradigm focused on **data streams** and the propagation of changes.
- It provides a declarative and composable way to handle **asynchronous** and **event-based** systems.
- The reactive approach promotes **responsive**, **resilient**, and **scalable** applications.

---

## Main Problem

What's the first thing that comes to mind when you have this dependency tree?

![width:300px](./img/1.png)

---

And this one?

![width:700px](./img/2.png)

---

This is one of the **major issues** we encounter when our components are not self-contained in their functionality and constantly rely on other components.

---

## How can we fix this?

We can transfer the responsibility to each component, but how?

---

#### Let's see an example: Shopping Cart!

![width:700px](./img/3.png)

---

#### Let's simplify it.

![width:700px](./img/4.png)

---

## Imperative Version

![width:900px](./img/4.png)

<div class="columns">
<div>
</div>
<div>

```js
function addProduct(product) {
  Bill.addProduct(product);
}
```

</div>
</div>

---

## More Reactive Version

![width:1100px](./img/4.png)

<div class="columns">
<div>

```js
class Bill {
  let cart;

  function getBill(cart) {
    cart.onAddProduct((product) => {
      // Update bill
    });
  }
}
```

</div>
<div>

```js
function addProduct(product) {
  ...
  // fire event!!
}
```

</div>
</div>

---

## Fully Reactive Version

```javascript
function bill(products: Observable<Products>) Observable<Float> {
    return products.reduce((acc, product) => {
        acc += product.price
    }, 0)
}
```

---

Notice that in this final version, we don't need the Bill class. We have a single function that performs a specific task using observables asynchronously.

---

# Demo

---

## Key Concepts

- **Data Streams**: Sequences of values over time.
- **Observers**: Entities that react to changes in the data streams.
- **Pure Functions**: Functions that produce the same output for the same input, without side effects.

---

## Reactive Principles

1. **Stay Responsive**: Always respond in a timely manner
2. **Accept Uncertainty**: Build reliability despite unreliable foundations
3. **Embrace Failure**: Expect things to go wrong and design for resilience
4. **Assert Autonomy**: Design components that act independently and interact collaboratively

---

5. **Tailor Consistency**: Individualize consistency per component to balance availability and performance
6. **Decouple Time**: Process asynchronously to avoid coordination and waiting
7. **Decouple Space**: Create flexibility by embracing the network
8. **Handle Dynamics**: Continuously adapt to varying demand and resources

---

## Common Operators

**Transforming Operators:**

- `map()`: Transform values.
- `flatMap()`: Flatten nested observables.
- `scan()`: Accumulate values over time.
- `mergeMap()`: Map and merge multiple observables.

---

## Common Operators

**Filtering Operators:**

- `filter()`: Filter values with predicate.
- `distinct()`: Emit unique values.
- `take()`: Emit first _n_ elements.
- `debounceTime()`: Emit item only if a period passed without emitting another item.

---

## Common Operators

**Combining Operators:**

- `combineLatest()`: Combine values from multiple observables using the latest of each.
- `merge()`: Combine multiple observables into one by merging their emissions.
- `concat()`: Concatenate values from multiple observables without interleaving.
- `zip()`: Combine corresponding values from multiple observables.

---

## Common Operators

**Math Operators:**
(for number observables only)

- `sum()`: Calculate the sum of values.
- `min()`: Find the minimum value.
- `max()`: Find the maximum value.
- `average()`: Calculate the average of values.

---

## ReactiveX

- ReactiveX (Rx) is a popular library for reactive programming.
- Provides implementations in various languages (e.g., RxJava, RxJS).
- Offers a rich set of operators and abstractions for working with observables.

---

## ReactiveX Core Operators

`Create` `Defer` `Empty` `From` `Interval` `Just` `Range` `Repeat` `Start` `Timer` `Buffer` `FlatMap` `GroupBy` `Map` `Scan` `Window` `Debounce` `Distinct` `ElementAt` `Filter` `First` `IgnoreElements` `Last` `Sample` `Skip` `SkipLast` `Take` `TakeLast` `And` `Then` `When` `CombineLatest` `Join` `Merge` `StartWith` `Switch` `Zip` `Catch` `Retry` `Delay` `Do` `Materialize` `ObserveOn` `Serialize` `Subscribe` `SubscribeOn` `TimeInterval` `Timeout` `Timestamp` `Using` `All` `Amb` `Contains` `DefaultIfEmpty` `SequenceEqual` `SkipUntil` `SkipWhile` `TakeUntil` `TakeWhile` `Average` `Concat` `Count` `Max` `Min` `Reduce` `Sum` `Connect` `Publish` `RefCount` `Replay` `To`

---

## Libraries for Reactive Programming

- **RxJava**: Java.
- **RxJS**: JavaScript.
- **Rx.NET**: C#.
- **RxPY**: Python.
- **RxSwift**: Swift.

---

## Conclusion

- Reactive programming enables building responsive and scalable applications.
- It leverages the power of data streams, observers, and pure functions.
- ReactiveX and other libraries provide valuable tools for implementing reactive systems.

---

# Questions?

---

# Thank You!
