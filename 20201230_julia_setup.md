# Julia Setup


- add `JULIA_HOME=/data/dev/.julia` to `~/.profile`

## Julia Community

- Julia chat: [Zulip](https://julialang.zulipchat.com/#narrow/stream/230248-catlab.2Ejl)

### [Algebraic Julia](https://www.algebraicjulia.org/)

- [Catlab.jl](https://www.juliabloggers.com/notes-on-synthesis-and-equation-proving-for-catlab-jl/)
- [Alg. Julia slides](https://www.algebraicjulia.org/assets/slides/mit-seminar-2020/#40)

### Julia IDE

- [JunoLab](https://junolab.org/)

## Cheatsheets

[Quant Econ Julia](https://cheatsheets.quantecon.org/julia-cheatsheet.html)


## Dependencies

See [Julia Setup](github.com/olynch/julia_setup) for an example (but it uses
conda and runs notebooks on host as root)

[Google Colab](https://cloud.google.com/) would require Julia running locally anyways

### Python

- [Fantastic blog on Python environments](https://www.pluralsight.com/tech-blog/managing-python-environments/)
  - or use python in order to not give a fuck

### Docker Images

- Official [Docker for Data
Science](https://www.youtube.com/watch?v=tuYgEv40s7A&list=TLPQMzAxMjIwMjAxLQf7xRSmQQ&index=1)
(video for Julia)
- [felipenoris' math-server-docker](https://github.com/felipenoris/math-server-docker)
- [another option](https://github.com/QuantumObject/docker-ijulia)

after building on the host computer, refer to [jupyter
docs](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/running.html)
because your dumb ass will google that shit again.

- [Jupyter Datascience image](https://hub.docker.com/r/jupyter/datascience-notebook)
- [Jupyter Docker Stacks](https://github.com/jupyter/docker-stacks/tree/master).
- [Docs:
  Jupyter/Docker](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-datascience-notebook)

### Emacs

- [Tools for Julia](https://www.emacswiki.org/emacs/JuliaProgrammingLanguage)
- [Emacs-based Workflow](https://discourse.julialang.org/t/emacs-based-workflow/19400)



### [Binder](https://mybinder.readthedocs.io/en/latest/)

Makes a repo full of notebooks more reproducible by helping manage dependency

complexity (sets up a running node w/ env in the cloud)
- ["The Turing Way"](https://github.com/alan-turing-institute/the-turing-way)
  for reproducible data science
- [Binder setup for
  Julia](https://github.com/alan-turing-institute/the-turing-way/blob/master/workshops/boost-research-reproducibility-binder/workshop-presentations/zero-to-binder-julia.md)


# Misc Resources

- [Docker Example for BI & Data Science](https://towardsdatascience.com/docker-example-for-bi-data-science-development-16e305ab70fa)
- [Data Viz with
  Julia/Jupyter](https://towardsdatascience.com/starting-data-visualization-with-the-julia-langauge-and-jupyter-notebooks-289bc9f0cd09)

# Julia Packages

Julia Interview Questions (in some git repo)


### Interesting Packages on Julia Observer

```julia
# Essential
Pkg.add(["Flux", "JuMP", "Plots"])
Pkg.add(["DifferentialEquations", "Gadfly", "Gen"])

# Charts (+ plots above)
Pkg.add(["Makie"])

# FFI & Lang Tooling
Pkg.add(["Cxx", "Clang", "Cassette", "BinaryBuilder", "PkgTemplates"])

# Performance
Pkg.add(["ProfileView"])

# Nifty (OhMyREPL modifies base code though)
Pkg.add(["Revise", "OhMyREPL"])

# File & I/O
Pkg.add(["JSON", "ProtoBuf", "HDF5", "DrWatson", "Latexify"])

# GUI
Pkg.add(["QML"])

# Macros and Metaprogramming
Pkg.Add(["MacroTools", "Transducers", "DataTools"])

# Data Science
Pkg.add(["ScikitLearn", "DataStructures", "DataFrames", "DataFramesMeta"])

Pkg.add(["QueryVerse"])

# Statistics
Pkg.add(["OnlineStats", "MultivariateStats", "GeoStats"])

# https://github.com/JuliaStats
Pkg.add(["StatsBase", "StatsFuns", "GLM", "FixedEffectModels"])

# Maths
Pkg.add([

  "LightGraphs", "Laplacians", ## Graph Theory
  "AutoGrad", "ForwardDiff", "Zygote" ## Differentiation methods
  "DiffEqFlux", "DSGE", ## Diff EQ
  "Optim", ## Optimization
  "Polynomials", "Combinatorics", "TimeSeries", ## Misc
  "Manifolds",  "Ipopt", "Roots", "NLSolve", "LeastSquaresOptim", # Solver
  
  # Catlab
  "Catlab", "AlgebraicRelations", "AlgebraicPetri",
  
  # Alien maths
  "Grassmann", # [Tensor Fields](https://github.com/chakravala/Grassmann.jl)
   "Eirene" # Homological persistence using Matroid optimization
])

# Physics/Engineering

Pkg.add(["DSP", "ControlSystems", "PowerSystems", "QuantumOptics"])

# Chemistry

Pkg.add(["ChemometricsTools"])

# Astronomy
# "AstroLib", "AstroTime", "Cosmology", "DustExtinction"
# "LombScargle", "UnitfulAstro", "LibHealpix", "SOFA"
# "JuliaHCI", "JPLEphemeris"

# Economics/Finance

# https://github.com/quantecon?q=&type=&language=julia
Pkg.add(["SimpleDifferentialOperators", "BasisMatrices", "QuantEcon", "InstantiateFromURL"])
Pkg.add(["Distributions", "Expectations", "InstantiateFromURL"])


# Couldn't find, but interesting:
# Lint, ParticleAccelerator

# Conflicts
# Strategems (Plots)

```




## Catlab & Math

- [PiSMC.jl](https://github.com/felipenoris/PiSMC.jl)

## Science

- [ChemometricsTools](https://github.com/caseykneale/ChemometricsTools.jl)


## Economics & Finance

- Julia [Finance Packages](https://juliapackages.com/c/finance)
  - Quandl.jl
  - TradingLogic.jl
  - BusinessDays.jl
  - Ito.jl
  - FinMarkets.jl
  - LibTrading.jl
  - InterestRates.jl
  - Currencies.jl
  - EconDatasets.jl
  - YStockData.jl
  - FinancialBlotter.jl
  
### [QuantEcon](https://github.com/QuantEcon/QuantEcon.jl)

- [github](https://github.com/QuantEcon) and [QuantEcon.jl docs](https://quantecon.github.io/QuantEcon.jl/latest/api/QuantEcon.html)
- BasisMatrices.jl: with Chebyshev polynomials, etc
- TSAnalysis (from fipelle): time series analysis with imperfect information
- GameTheory.jl
- [Archmodels.jl](https://dx.doi.org/10.2139/ssrn.3551503): leveraging JIT-based
  benefits of Julia (dispatch?) to do ... something to make complex recursion
  more efficient (from dynamic programming?)



## Other useful packages 

(from [DrWatson](https://juliadynamics.github.io/DrWatson.jl/dev/))

### Running simulations
* <https://github.com/baggepinnen/Hyperopt.jl>

### Efficient code writing
* <https://github.com/mauro3/Parameters.jl>
* <https://github.com/docopt/DocOpt.jl>
* <https://github.com/vtjnash/Glob.jl>

### Documenting your code
* <https://github.com/JuliaDocs/Documenter.jl>
* <https://github.com/fredrikekre/Literate.jl>
* <https://github.com/caseykneale/Sherlock.jl>
* <https://github.com/miguelraz/DoctorDocstrings.jl> 

### Paper-related
* <https://github.com/Azzaare/Bibliography.jl>

### Debugging, writing code
* <https://github.com/timholy/Revise.jl>
* <https://github.com/JuliaDebug/Debugger.jl>

### Performance measures
* <https://github.com/JuliaCI/BenchmarkTools.jl>
* <https://github.com/timholy/ProgressMeter.jl>
* <https://github.com/KristofferC/TimerOutputs.jl>
* <https://github.com/JuliaDebug/Cthulhu.jl>
* ProfileViews.jl (similar available in Juno with `@profiler`)

### Saving Data
* BSON.jl
* JLD2.jl
* CSV.jl

### Data management & data bases
* <https://github.com/helgee/RemoteFiles.jl>
* <https://github.com/JuliaDynamics/CaosDB.jl>
* <https://github.com/SebastianM-C/StorageGraphs.jl>

### Tabular data
* <https://www.queryverse.org/>

### Traversing folders
* Base.Filesystem
* <https://github.com/Keno/AbstractTrees.jl/blob/master/examples/fstree.jl>

### Time management
* <https://github.com/oxinabox/ProjectManagement.jl>




## Finance Data Sources

- VegaDatasets, DataVoyager, VegaLite

#### [11 Sources for Fin/Eco Datasets]()

- Quandl
- BIS, World Bank, Federal Reserve (and other central banks)
- Data.OECD (consumer data)
- Data.gov (us govt open data)
- Oxford Economics


- Yahoo (free)
- Bloomberg (paid)
- "Global Financial Data" (most paid, some free)


  



# Julia Features

### References to `@view` and `@views` macros (with blocks)

- ./ControlSystems/lhpZ5/src/delay_systems.jl\0106:    @views for k=1:length(Tau)
- ./ArrayLayouts/M5SFk/src/triangular.jl\0243:    @views for j in axes(X,2)
- ./IterativeSolvers/TpeDx/src/lobpcg.jl\0558:    @inbounds @views for (activeblock, block) in blockPairs
- ./ExponentialUtilities/0d0Nm/src/phi.jl\079:    @views mul!(w[:, 1], P[1:m, 1:m], v)
- ./ExponentialUtilities/0d0Nm/src/krylov_phiv_adaptive.jl\0196:        @views @inbounds for j = 0:p-1
- ./ArrayLayouts/x9nhz/src/triangular.jl\0155:    @views for j in axes(X,2)
- ./PrettyTables/W16qB/src/backends/html/print.jl\0163:        @inbounds @views for i = 1:header_num_rows
