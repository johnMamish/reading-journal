Alright, broh. This is my first technial book up here.

This book is a guided tour through formal verification techniques applied to RTL chip design. I see RTL chip design as taking an important place in my life in the future, so I'm reading this book to learn about an engineering technology that was considered cutting edge 10 years ago, but is expected among digital designers today.

This book assumes that the reader has access to expensive verification tools and can compile SystemVerilog. I'm just using plain Verilog and am using the open source SymbiYosys tools. SymbiYosys, AFAI can tell, offers SystemVerilog extensions, but some tools that I'll use for compilation and systhesis only support vanilla Verilog, so I'll stick with that.

##### Chapter 1 - Introduction
Formal verification is a technique used in the testing of digital logic circuits. Because of the prohibitively high cost that comes with respinning an IC, testing coverage is very important. There are tons of examples where bugs caught late in the design stage cost a fortune, and some examples of post-fabrication bugs that have threatened to put juggernauts out of business. For instance, this book loves the intel FDIV bug that cost Intel almost $500M in the late 90s; the authors claim that FV methods probably would have caught the FDIV bug, and that it was only caught because making a testbench to land right on the bad cases would have been absurdly unlikely, like dropping a dart from an aeroplane and expecting it to hit a certain piece of grass.

Ideally, formal verification is able to exhaustively test input combinations or write a mathematical proof for a circuit to ensure that it never gets into an illegal state. Oftentimes, FV solvers can't reach this goal - even with heuristics to prune the state space, it remains intractably large - so designers have to 'merely settle' for partial coverage of the state space. The analogy that the authors use is comparing throwing darts at a dart board to covering the dart board with paint. The dart board is the state space, and the darts are individual testbench cases; in the face of such a large state space, the individual testbench cases are basically infinitesimally small. Figure 1.7 is a good example of this.

##### Chapter 2 - Basic formal verifcation algorithms
Exhaustive checking of a model is NP-complete and takes a completely intractable amount of time for models larger than a handful of logic gates. FV tools have a few tricks that they use to shrink the state space or dismiss large parts as unnecessary for testing. A couple examples from early in the chapter: even for some logic tables with billions of entries, all but 10 or 15 of the entries might have zeros as the output; these tables can be drastically simplified; by simplifying a complicated equation to "sum-of-products" form, it can then take linear time to find counterexamples.

BDDs (boolean decision diagrams) are directed acyclic graphs that represent logic circuits. "Model Checking" is a technique that builds up BDDs to explore reachable states of the system (leaves of the BDD).  It tries to reach a 'fixed point', where no new states are added to the state BDD, meaning that all possible states have been explored. As far as I can tell, this process is NP-hard, but there are heuristics for pruning large parts of the BDD that make the problem tractable.

SAT (boolean satisfiablity) is a very well-research problem in computer science where you try to find variables that satisfy a boolean equation. It is NP-hard. It is applied to FV by constructing an equation using the implementations and requirement, and arranging them in the form (implementation -> requirements) (-> is implies). If the equation !(implementation -> requirements) is satisfiable, this produces a counterexample. SAT can be applied step-by-step in models with state, but unlike BDD based methods which have a fixed point, SAT methods can't tell when they're completely done. However, SAT solvers are quicker than BDD solvers and can cover a huge amount of the state space. SAT solvers use heuristics to make the problem size tractable. By dividing and conquering, large "subtrees" of required tests can be pruned.

You could, of course, make a testbench that tries all of the ncycles * 2^n different possible input values, but FV methods prune out functionally identical paths, making this problem tractable. Making a testbench like that would be intractable for all but the smallest cases (and in those smallest cases, it would be the same as doing full FV).

##### Chapter 3
The authors provide the specifics of some SV assertions, including many that aren't relevant to me cause I'm using SymbiYosys (e.g. |->, ##).

The authors make an argument that addition of assertions and assumptions are like "executable comments" in the sense that they simultaneously express author intent AND allow for FV testing.

 - `assert`: <br/>
   This statement is the heart of FV. FV solvers try and prove that none of your asserts are reachable from any starting state.

 - `assume`: <br/>
   Assume can be used to tell the solver what inputs into a module shouldn't be used. If an `opcode` should be one of `{OP_A, OP_B, or NOP}`, you can `assume((opcode == OP_A) || (opcode == OP_B) || (opcode == NOP));` to prevent the solver from dipping into massive numbers of invalid or nonsensical cases. `assume`s in a submodule should be converted to `assert`s when working at a higher level module.

 - `cover`: <br/>
   Ensures that your design is capable of reaching cases with the given states. If your design cannot reach the given states, it will fail. Page 99 in Chapter 4 has a great example of this.

 - `|->` / `|=>`: <br/>

##### Chapter 5
This chapter uses an example of a traffic light state machine to demonstrate strategies for incorporating FV techniques at design time.

Cover points might be the best starting point (as opposed to assertions). It's easy to convert example input waveforms into cover points, and cover points will generate example waveforms that let us sanity check our design. It's also worth remembering that the perfect is the enemy of the good, and that we shouldn't start out expecting 100% coverage of properties implied by the spec.

In more complicated designs that might be extremely computationally strenuous, pieces of logic that are simple or already verified can be blackboxed; this allows the FV engine to give their outputs arbitrary values. These are underconstraints. Likewise you can overconstrain a model to speed up solvers (by, for instance, `assuming` that bits 31 - 8 of a bus will be 0), but this can cut out large and interesting parts of the state space.
