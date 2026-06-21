# expand.carp

is a simple hygienic macroexpander in and for Carp.

```clojure
(load "expand.carp")

(defdynamic prog
  (Expand.introduce ; adds all the core primitives
    (Expand.from-datum ; builds a syntax object
      '(let-syntax [add (fn [s] (quote-syntax '(+ 1 3)))]
        (add)))))

; expands the syntax object and converts it back to
; regular Carp
(Expand.to-datum (Expand.expand-all prog))
; => '(+ 1 3)
```

<hr/>

Have  fun!
