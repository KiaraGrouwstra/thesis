# UvA master thesis

type-driven development with hole-type-supervised NSPS / AlphaNPI? AlphaNSPS?

### papers

sent by Emile:
- [DeepProbLog: Neural Probabilistic Logic Programming](https://arxiv.org/pdf/1805.10872.pdf) @ KU Leuven: differentiable [ProbLog](https://dtai.cs.kuleuven.be/problog/). Emile: less relevant cuz untyped? tests on add/sort/algebra on pics/list/text. induction, no ops.
- [Learning Explanatory Rules from Noisy Data](https://arxiv.org/pdf/1711.04574.pdf) ([code](https://github.com/ai-systems/DILP-Core)) @ DeepMind: Differentiable Inductive Logic Programming (∂ILP) = ILP (data efficient) + NNs' ability to handle ambiguity. trained on various symbolic tasks. uses given template so just handles induction. check if this can do types? see pic on p.31. tests on 20 symbolic tasks (arithmetic, lists, family tree, graphs). task-dependent ops. not sure I can add value here if the template is set.
- [DeepCoder](https://www.microsoft.com/en-us/research/publication/deepcoder-learning-write-programs/) (2017, repos [1](https://github.com/HiroakiMikami/deep-coder), [2](https://github.com/dkamm/deepcoder), [3](https://github.com/amitz25/PCCoder)): train a neural network to predict properties of the program that generated the outputs from the inputs to augment search techniques, e.g. enumerative search, SMT-based solver, depth-first search (DFS), 'sort and add' enumeration, sketch, λ^2. tested on functional programs. good alternative to NSPS paper given available implementations?
- [Neural-Guided Deductive Search (NGDS)](https://www.microsoft.com/en-us/research/blog/neural-guided-deductive-search-best-worlds-approach-program-synthesis/) (2018):
    - combines symbolic logic + statistical models by 'branch & bound' from combinatorial optimization.
    - deductive search: decompose synthesis into sub-problems, Markovian so can do supervised learning.
    - NGDS: find which sub-problems are useful, predict program generalization by LSTM scoring DSL production rules on i/o.
    - evaluated on string transformation (PROSE) against RobustFill / DeepCoder.
    - deductive search seems kinda like pruning by type reasoning, though here it's learned. I guess the stronger the types tho, the less needs learning.
    - train separate models for different DSL levels, symbols, or even productions.
    - I *think* this seems iterative top-down, so seems applicable for me, tho no code.
    - this made me realize you may want to factor in existing operations on i/o to simplify the problem for the given sub-node.
- [Recurrent Neural Network Grammars](https://arxiv.org/abs/1602.07776) (2016): probabilistic model of phrase-structure trees that can be trained generatively and used as a language model or a parser. seems aimed at language models, i.e. mimicking existing usage, which for program synthesis might be secondary to finding programs properly mapping input to output.
- [Leveraging Grammar and RL for Neural Program Synthesis](https://arxiv.org/abs/1805.04276) (2018): supervised + RL to generate semantically correct programs. train to generate syntactically correct programs that fulfill the specification. only applies for sequence approach, which doesn't match the trees I want...

mine (brought up):
- [Neural Programmer-Interpreter (NPI)](https://arxiv.org/abs/1511.06279) @ DeepMind. tests on add/sort / canonicalizing 3d models. ops reset/bubble/rshift/lshift/compswap/ptr1l/ptr1r/ptr2l/ptr2r/swap/stop.
- [Learning Compositional Neural Programs with Recursive Tree Search and Planning](https://arxiv.org/pdf/1905.12941.pdf) ([blog](https://www.instadeep.com/research-article/towards-compositionality-in-deep-reinforcement-learning/)): Neural Programmer-Interpreter (NPI) + AlphaZero = AlphaNPI. tests on sorting/hanoi tasks. ops as NPI.
- [Neuro-Symbolic Program Synthesis (NSPS)](https://arxiv.org/pdf/1611.01855.pdf) (2016, no code): (1) cross correlation I/O network embeds in/out examples, (2) Recursive-Reverse-Recursive Neural Network (R3NN) incrementally synthesizes AST. R3NN has node representations, then calculates representations bottom-up then top-down to get representations for the next hole to fill. tests on flashfill. ops Concat/ConstStr/SubStr/Position/Direction/Regex.

mine (more):
- [Typed meta-interpretive learning of logic programs](https://www.researchgate.net/profile/Andrew_Cropper/publication/331100541_Typed_meta-interpretive_learning_of_logic_programs/links/5c65c7bd299bf1d14cc75a39/Typed-meta-interpretive-learning-of-logic-programs.pdf) (2019): typed MIL (~= inductive logic programming (ILP)) reduces space by a cubic factor. tests on list manipulation: droplasts, filtercapslower, filterevendbl, nestdincr, finddups. ops: tail, map, reverse, sumlist, head, succ, last, in_list, pred, max_list; extra ops: filter, flatten, list_to_set, msort, tolower, odd, uppercase, element, double, toupper, length, even, set, lowercase.
- [Predicting Haskell Type Signatures From Names](people.cs.uchicago.edu/~rchugh/static/theses/bowen-wang-thesis.pdf) (2018): encode name/context, recursively select (non-)arrow
- [Synthesizing Data Structure Transformations from Input-Output Examples](https://www.cs.utexas.edu/~isil/pldi15b.pdf) (2015, 145 cites, [code](https://github.com/jfeser/L2)): λ2: OCaml PBE from 7 combinators by inductive generalisation + (limited) deduction + enumerative search. typed, incremental, holes. old functional synthesis paper that got good improvement from types. tests on 40 data structure manipulation tasks (lists, trees, nested). ops: map, maptree, filter, foldl, foldr, foldtree, recl. 41 ops (lists, trees, nested).
- [Type-and-example-directed program synthesis](https://dl.acm.org/citation.cfm?id=2738007) (2015, 100 cites): Myth: Haskell PBE by types + i/o. shows own synthesis/typecheck rules, library.
- [Programming Assistance for Type-Directed Programming](https://www.cs.grinnell.edu/~osera/publications/osera-tyde-2016.pdf) (2016): Scout: bridge auto-completion / program synthesis with interactive programming assistant for type-directed programming.
- [Program Synthesis from Polymorphic Refinement Types](https://dl.acm.org/citation.cfm?id=2908093) (2016, [code](https://bitbucket.org/nadiapolikarpova/synquid)): code from refinement types. synthesize Haskell-like Synquid by SMT-solver from modular refinement type reconstruction to allow type-checking partial programs using liquid types.
- [Top-Down Inductive Synthesis with Higher-Order Functions](https://www.research-collection.ethz.ch/bitstream/handle/20.500.11850/155821/eth-49631-01.pdf) (2016): Tamandu: PBE w/ large library (37 components) based on best-first enumeration combined with type-based pruning.
- [関係的仕様からの関数型プログラム合成](http://jssst.or.jp/files/user/taikai/2017/PPL/ppl3-1.pdf) (2017): relation-based (?) Haskell synthesis using Horn clauses.
- [Suggesting Valid Hole Fits for Typed-Holes in Haskell](https://www.mpg.is/papers/gissurarson2018suggesting-msc.pdf) (2017): integrates hole filler into GHC. mentions synthesizers insynth (JVM), djinn (haskell, non-polymorphic). dependently typed languages: type inference undecidable. mentions hole-filling for agda and idris.
- [Speeding up Type-Driven Program Synthesis with Polymorphic Succinct Types](https://icfp18.sigplan.org/getImage/orig/icfp18src-zheng-guo.pdf) (2018): generalize succint types for polymorphism. to find which types are used under polymorphism, abstract the types into coarse-grained succinct types, unordered param type sets describing function i/o.
- [Automated Synthesis of Functional Programs with Auxiliary Functions](www-kb.is.s.u-tokyo.ac.jp/~koba/papers/aplas18-long.pdf) (2018): extension of Synquid to enable top-down iterative synthesis of programs with auxiliary functions using holes.
- [Constraint-Based Type-Directed Program Synthesis](https://arxiv.org/pdf/1907.03105.pdf) (2019): synthesis from type. “infer while enumerate” approach to polymorphic type instantiation. uses WIP Haskell synthesis tool Scythe.
- [Temporal Stream Logic: Synthesis beyond the Bools](https://arxiv.org/pdf/1712.00246.pdf) (2017): CEGAR-based synthesis (from formal spec) separating control and data. benchmarks: synthesized music player Android app, controller for autonomous vehicle in the Open Race Car Simulator (TORCS).
- [Machine Learning for Combinatorial Optimization: a Methodological Tour d'Horizon](https://arxiv.org/abs/1811.06128) (2018).
    - is it useful to frame program synthesis as a [Combinatorial Optimization](https://paperswithcode.com/task/combinatorial-optimization) problem (not unlike the TSP)?
    - how do they differ? -- CO implies a loss/reward per configuration. for ML I should need a loss anyway tho, so this seems reasonable. the sub-field of linear programming requires linear relationships, which I doubt apply here.
    - what are the differences between their algorithms?
