# 2D-piecewiselinearization-ISCO2022-computational-results

This repository contains the solutions obtained by our algorithms that compute piecewise linear approximations of nonlinear bivariate functions given a predefined absolute error and that minimize the number of pieces used.

The details of the algorithms and the description of the benchmark can be found in [this paper.](https://hal.archives-ouvertes.fr/hal-03629850v2)


## Basic use

The solutions obtained by algorithms DN99 and DN95 are stored in files 'DN99.txt' and 'DN95.txt' in the folder 'rawlogs'.

The file "parse_and_plot.jl" contains code in julia with a function called "parse_and_plot_instance", that plots and saves the result of an instance.

To extract information about the solution obtained by algorithm DN99 on instance N1 (f(x)=xy on [2.0,8.0]x[2.0,4.0]) with absolute error 0.05 simply do
```julia
julia> T_set, domain, delta, n_pieces, cpu_time, str_exprf = parse_and_plot_instance("DN99", "N1", 0.05)
```

Read the README.txt file in folder src for more information about the input and output of this function

## Examples

Solutions obtained on instances N1 (f(x)=xy on [2.0,8.0]x[2.0,4.0]) or N3 (f(x)=xsin(y) on [1.0,4.0]×[0.05,3.1])

![alt text](https://homepages.laas.fr/sungueve/im/solution_DN99_N1_delta0.1.png)

![alt text](https://homepages.laas.fr/sungueve/im/solution_DN99_N1_delta0.05.png)

![alt text](https://homepages.laas.fr/sungueve/im/solution_DN99_N3_delta0.25.png)

![alt text](https://homepages.laas.fr/sungueve/im/solution_DN99_N3_delta0.05.png)

## Citing

[1] Aloïs Duguet and Sandra Ulrich Ngueveu (2022). Piecewise linearization of bivariate nonlinear functions: minimizing the number of pieces under a bounded approximation error. In: Ljubić, I., Barahona, F., Dey, S.S., Mahjoub, A.R. (eds) Combinatorial Optimization. ISCO 2022. Lecture Notes in Computer Science, vol 13526. Springer, Cham. https://doi.org/10.1007/978-3-031-18530-4_9
