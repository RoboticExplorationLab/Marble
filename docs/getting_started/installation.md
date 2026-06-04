# Installing and Building

Marble is a C++ project with bindings for Julia and Python. 


## Dependencies

In order to build the C++ library, the following dependencies are needed:

| Dependency | Version | Needed for |
|---|---|---|
| CMake | ≥ 3.28 | everything |
| A C++17 compiler | — | everything |
| Eigen3 | ≥ 3.3 | everything |
| nlohmann-json | — | everything |
| Python + dev headers | ≥ 3.8 | Python bindings |
| Julia + CxxWrap.jl | ≥ 1.10 | Julia bindings |
| pybind11-stubgen | — | optional: `.pyi` autocomplete stubs |

CMake fetches the other dependencies automatically (from source if they aren't already installed), so you don't need to install them yourself:

| Dependency | Version | Needed for |
|---|---|---|
| QDLDL | — | everything |
| pybind11 | ≥ 2.13 | Python bindings |

## Building Marble

Once you have the prerequisites installed, clone the [Marble](https://github.com/MarbleSolver/RCQP) repository.

### Marble with Julia Bindings

!!! warning 
    CMake will compile using your default Julia version and global environment. You can install CxxWrap.jl into the environment using
    ```bash
    julia -e 'using Pkg; Pkg.add("CxxWrap")'
    ```
    We are working on updating this so that it uses the package environment.

In the root of the Marble repository, run the following in the terminal to build the Marble library and Julia `CxxWrap` bindings:

```bash
cmake --preset julia
cmake --build --preset julia
```

Once the build has completed, you can use Marble from your own Julia environment by running the following inside the Julia REPL:
```julia
using Pkg
Pkg.activate("/path/to/your/env")
Pkg.dev("/path/to/Marble/julia")
```

### Marble with Python Bindings

In the root of the Marble repository, run the following in the terminal to build the Marble library and Python `pybind` bindings:

```bash
cmake --preset python
cmake --build --preset python
```

Once the build has completed, you can use Marble from your own Python virtual environment by installing the `Marble/python` package:
```bash
pip install /path/to/Marble/python
```

#### Extra: VSCode Autocomplete and Type Hints

The high-level API in `Marble/python/marble/__init__.py` is type-annotated, and the compiled core ships a `Marble/python/marble/_core.pyi` stub that is regenerated each time you build `marble_python` (requires `pybind11-stubgen`). Pylance reads both from the `marble` package, so a single setting wires everything up.

Add to `.vscode/settings.json`:
```json
{
  "python.analysis.extraPaths": ["${workspaceFolder}/build/python"],
  "python.analysis.useLibraryCodeForTypes": true
}
```
`extraPaths` tells Pylance where the staged `marble` package (with `_core.so` and `_core.pyi`) lives so it can be imported.

Then install the **Pylance** extension (`ms-python.vscode-pylance`); it picks up the setting automatically.

If stubs are stale or missing, rebuild:
```bash
cmake --build --preset python --target marble_python
```
If `pybind11-stubgen` is not installed, CMake warns but the build still succeeds. Install it with:
```bash
pip install pybind11-stubgen
```