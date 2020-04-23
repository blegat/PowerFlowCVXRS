# Optimal Power Flow with Convex Restriction

This code provides a implementation for Convex Restriction of AC Optimal Power Flow problem.

You can find more details of convex restrictions and other applications in the [project page](https://dclee131.github.io/research/2019/10/07/CVXRS.html).

### Installation Requirements

The script has written in Julia v1.1, and can be run without installation. 

Follwing packages are necessary to run the code.

```julia
using JuMP, PowerModels, Ipopt, MosekTools, SparseArrays, LinearAlgebra, Plots
```
The project uses [JuMP](https://github.com/JuliaOpt/JuMP.jl) for modeling the QCQP problem and uses MOSEK as the solver.
Power flow data and equations are stored and solved based on [PowerModels](https://github.com/lanl-ansi/PowerModels.jl). 
Figures in Julia are created with [Plots](https://github.com/JuliaPlots/Plots.jl). Color-coded figures were drawn in MATLAB, and you can find relavant code in `plots/draw_boundary.m`.

## Quick Start


```julia
## Import CVXRS_OPF functions
include("src/CVXRS_OPF.jl")

## Read network data using PowerModels.jl
network_data = PowerModels.parse_file("../../pglib-opf-master/pglib_opf_case118_ieee.m");

## Initiailize the network data by solving OPF problem
network_data=opf_initialization(network_data)

```

You can check the folder `tutorials` to find more examples.

## Citing CVXRS_OPF

If you find this content useful for your research, please consider citing: 

[1] Convex Restriction of Power Flow Feasibility Set: proposed convex restriction of OPF constraints.

    @article{lee2019convex,
      author={Lee, Dongchan and Nguyen, Hung D. and Dvijotham, K. and Turitsyn, Konstantin},
      journal={IEEE Transactions on Control of Network Systems},
      title={Convex Restriction of Power Flow Feasibility Sets},
      year={2019}, volume={6}, number={3}, pages={1235-1245}, month={Sep.}
    }

[2] Feasible Path Identification in Optimal Power Flow with Sequential Convex Restriction: proposed to use convex restriction sequentially to identify a feasible path.

    @article{lee2019feasible,
      title={Feasible Path Identification in Optimal Power Flow with Sequential Convex Restriction},
      author={Lee, Dongchan and Turitsyn, Konstantin and Molzahn, Daniel K and Roald, Line A},
      journal={arXiv preprint arXiv:1906.09483},
      year={2019}
    }

[3] Robust Optimal Power Flow with Convex Restriction: The optimal solution for OPF problems almost always occur at the boundary of the operational constraints and is very sensitive to uncertainty in power injections. Convex Restriction provides a computationally tractable way to robustify the solution with a provable robustness guarantee.

