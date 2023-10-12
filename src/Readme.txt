This folder contains files with the results of the experiments for the methods DN95 and DN99 mentioned in [1] (for the edited version: https://link.springer.com/chapter/10.1007/978-3-031-18530-4_9; for the unedited version: https://hal.laas.fr/hal-03629850v2/document).

The .txt files in the folder "rawlogs" contain the result of one instance per line, with separator between information the string '::'.

    DN95.txt and DN99.txt contain the full results.
    DN95_simplified.txt and DN99_simplified.txt contain the essential informations for comparison purposes:
        - the name of the method (DN95 or DN99)
        - the function name (names: L1,L2,N1,...,N7)
        - the function expression (X*X-Y*Y...)
        - the error allowed (Absolute(delta) for absolute error of delta)
        - the domain (in format [A,B,C,D] meaning [A,B]x[C,D])
        - the number of pieces of the solution
        - the execution time in seconds
        - the solution is a Vector{Vector{Vector{Float64}}} in julia language (described below)

A solution is a Vector{Vector{Vector{Float64}}}: a vertex of a piece is a vector of $\mathbb{R}^3, the first two coordinates give the position in the domain, the third one the value of the PWL function in that position. A piece is a set of vertices, and a PWL function is a set of pieces. Thus, a solution is represented as a vector of pieces, which are vectors of vertices, which are vectors of Float64.

The julia language file "parse_and_plot.jl" contains code in julia with a function called "parse_and_plot_instance", that plots and saves the result of an instance.

    Syntax of the "parse_and_plot_instance" function call (see line 257 in 'parse_and_plot.jl' file):
        T_set, domain, delta, n_pieces, cpu_time, str_exprf = parse_and_plot_instance(method_name, function_name, precision)

    Accepted input parameters values:
        - method_name (String): "DN95", "DN99"
        - function_name (String): "L1, "L2", "N1", "N2", "N3", "N4", "N5", "N6", "N7"
        - precision (Float64): should be equal to the requested delta value (please refer to the table of results in appendix 'https://homepages.laas.fr/sungueve/Docs/IJ/Appendix_ISCO_2022.pdf')

    Examples:
        T_set, domain, delta, n_pieces, cpu_time, str_exprf = parse_and_plot_instance("DN99", "N1", 0.05)
        T_set, domain, delta, n_pieces, cpu_time, str_exprf = parse_and_plot_instance("DN99", "N1", 0.1)

    (Figures of the solution domains are displayed but also saved in the folder 'images/' in a 'png' format)


[1]: Duguet, A., Ngueveu, S.U. (2022). Piecewise Linearization of Bivariate Nonlinear Functions: Minimizing the Number of Pieces Under a Bounded Approximation Error. In: Ljubić, I., Barahona, F., Dey, S.S., Mahjoub, A.R. (eds) Combinatorial Optimization. ISCO 2022. Lecture Notes in Computer Science, vol 13526. Springer, Cham. https://doi.org/10.1007/978-3-031-18530-4_9
