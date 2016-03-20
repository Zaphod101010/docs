### `++stun`

Parse several times

Parse bounded number of times.

Accepts
-------

`[les=@ mos=@]` is a cell of atoms indicating the bounds.

`fel` is a [`++rule`]().

Produces
--------

A [`++rule`]().

Source
------

    ++  stun                                                ::  parse several times
      |*  [[les=@ mos=@] fel=_rule]
      |=  tub=nail
      ^-  (like (list ,_(wonk (fel))))
      ?:  =(0 mos)
        [p.tub [~ ~ tub]]
      =+  vex=(fel tub)
      ?~  q.vex
        ?:  =(0 les)
          [p.vex [~ ~ tub]]
        vex
      =+  ^=  wag  %=  $
                     les  ?:(=(0 les) 0 (dec les))
                     mos  ?:(=(0 mos) 0 (dec mos))
                     tub  q.u.q.vex
                   ==
      ?~  q.wag
        wag
      [p.wag [~ [p.u.q.vex p.u.q.wag] q.u.q.wag]]

Examples
--------

    ~zod/try=> ((stun [5 10] prn) [1 1] "aquickbrownfoxran")
    [p=[p=1 q=11] q=[~ [p="aquickbrow" q=[p=[p=1 q=11] q="nfoxran"]]]]
    ~zod/try=> ((stun [5 10] prn) [1 1] "aquickbro")
    [p=[p=1 q=10] q=[~ [p="aquickbro" q=[p=[p=1 q=10] q=""]]]]
    ~zod/try=> ((stun [5 10] prn) [1 1] "aqui")
    [p=[p=1 q=5] q=~]

***