## Practical IV

**Q1.** If `validate.js` runs *before* `main.js` and calls a function defined only in `main.js`, the Console shows a `ReferenceError: functionName is not defined` — the function doesn't exist yet because its file hasn't loaded/run.

**Q2.** Running `document.write()` after the page has fully loaded wipes out the entire page — the browser starts a brand-new document stream and everything that was there disappears. `innerHTML` is safer because it only replaces the contents of one existing element, leaving the rest of the page intact.

**Q3.** No, the form does not clear. `confirm("Clear the whole form?")` returns `false` when Cancel is clicked, so `!confirm(...)` is `true`, and `e.preventDefault()` runs — that's the call that stops the browser's default "reset" action.

**Q4.** Calling `console.log(b)` outside the `if { let b = 2; }` block throws `ReferenceError: b is not defined`. This proves `let` is block-scoped — the variable only exists inside the `{ }` it was declared in and is destroyed once that block ends. `typeof null` is `"object"` (a well-known historical JavaScript quirk).

**Q5.** Changing Inter-College Football's `seats` from `0` to `5` and reloading: the card's `sold-out-card` styling (strikethrough title, reduced opacity) disappears, the badge switches from grey "Sold out" to green "5 seats", the message changes to "Filling fast!", and the "No seats left" text is replaced with a working green **Register** button linking to `register.html?event=3`.

**Q6.** `seatsMessage(0)` returns `"Sold out"`. `seatsMessage(12)` returns `"Filling fast!"` (since 12 is greater than 0 but not greater than 20).

**Q7.** Submitting with an empty email: `validateForm(e)` finds `ok` is `false`, so the line `e.preventDefault();` inside the `if (!ok) { ... }` block stops the browser from leaving the page. Without `e.preventDefault()`, the browser would perform its normal form submission/navigation and the red error messages would never be seen — the page would just reload or navigate away.

**Q8.** `document.querySelectorAll("nav a")` returns a **NodeList**, not an HTMLCollection (that's what `getElementsByTagName` etc. return). Yes, `.forEach()` works directly on a NodeList in all modern browsers (it did not work on older HTMLCollections, which is why `Array.from()` was sometimes needed).
