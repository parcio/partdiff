# partdiff

partdiff is an application to solve partial differential equations using the Gauß-Seidel and Jacobi methods.

It is mainly used for teaching and research purposes.

partdiff was originally created by Thomas Ludwig, Thomas A. Zochler, and Andreas C. Schmidt in Fortran and has since been ported to C.

## Usage

```shell
$ git clone
$ cd partdiff
$ make
$ ./partdiff
Usage: ./partdiff [num] [method] [lines] [func] [term] [acc/iter]

  - num:       number of threads (1 .. 1024)
  - method:    calculation method (1 .. 2)
                 1: Gauß-Seidel
                 2: Jacobi
  - lines:     number of interlines (0 .. 100000)
                 matrixsize = (interlines * 8) + 9
  - func:      interference function (1 .. 2)
                 1: f(x,y) = 0
                 2: f(x,y) = 2 * pi^2 * sin(pi * x) * sin(pi * y)
  - term:      termination condition ( 1.. 2)
                 1: sufficient accuracy
                 2: number of iterations
  - acc/iter:  depending on term:
                 accuracy:   1e-4 .. 1e-20
                 iterations:    1 .. 200000

Example: ./partdiff 1 2 100 1 2 100

$ ./partdiff 1 2 100 1 2 100
Calculation time:   0.035731 s
Memory usage:       9.986588 MiB
Calculation method: Jacobi
Interlines:         100
Inference function: f(x,y) = 0
Termination:        Number of iterations
Number iterations:  100
Residuum:           3.544251e-03

Matrix:
 1.0000 0.8750 0.7500 0.6250 0.5000 0.3750 0.2500 0.1250 0.0000
 0.8750 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.1250
 0.7500 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.2500
 0.6250 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.3750
 0.5000 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.5000
 0.3750 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.6250
 0.2500 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.7500
 0.1250 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.0000 0.8750
 0.0000 0.1250 0.2500 0.3750 0.5000 0.6250 0.7500 0.8750 1.0000
```

## Regression testing

We use [partdiff_tester](https://github.com/parcio/partdiff_tester) to perform automatic regression tests.
