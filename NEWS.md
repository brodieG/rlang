# lazyeval 0.1.10.9000

* A new system for lazy-eval based on formulas, this is described in depth in
  the new `lazyeval` vignette. There are three key components:
  
  * `feval()` evaluates a formula in the environment where it was defined. 
    If supplied, values are first looked for in an optional `data` argument. 
    Pronouns `.data` and `.env` can be used to resolve ambiguity in this case.
    (#43)
    
  * `finterp()` provides a full quasiquoting system using `(( ))` for unquote
    and `({} })` for unquote-splice (#36).
 
  * `explicit_promise()` and `explicit_dots()` make it easy to turn promises
    and `...` into explicit formulas. These should be used sparingly, as
    generally lazy-eval is preferred to non-standard eval.

* This is accompanied by a number of helper functions for working with
  formuals:
  
  * Create a formula from a quoted call and an environment with 
    `make_formula()`.
  
  * "Unwrap" a formula removing one level from the tree of 
    parents with `funwrap()`.
    
  * Identify a formula with `is.formula()`.
  
  * Extract the right-hand side with `rhs()`. This will throw an error 
    if the object isn't a formula or has two sides.

* `lazy_dots()` gains `.ignore_empty` argument to drop extra arguments (#32).

* `interp.formula()` only accepts single-sided formulas (#37).

* `interp()` accepts an environment in `.values` (#35).

* `interp.character()` always produes a single string, regardless of
  input length (#27).

* Fixed an infinite loop in `lazy_dots(.follow_symbols = TRUE)` (#22, #24)

* `lazy()` now fails with an informative error when it is applied on
  an object that has already been evaluated (#23, @lionel-).

* `lazy()` no longer follows the expressions of lazily loaded objects
  (#18, @lionel-).

# lazyeval 0.1.10

* `as.lazy_dots()` gains a method for NULL, returning a zero-length
  list.

* `auto_names()` no longer truncates symbols (#19, #20)