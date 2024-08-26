---
layout: default
title: Release 3.0.x
parent: Releases
nav_order: 3
toc: false
summary: "Release notes for most current CREST version"
permalink: /page/releases/release_current.html
---

# CREST Release 3.0.x
{: .no_toc }

<div class="label label-green">CREST 3.0</div>

---

## CREST version 3.0.2 🛡️
### Build updates and fixes 🛠️

## What's Changed
* 🪲 Minor bug fixes for MSREACT mode by @gorges97 in https://github.com/crest-lab/crest/pull/309
* 🪲 Circumvent segfault due to optional arg in gcc build in https://github.com/crest-lab/crest/pull/318
* 🪲 Fix for #320 in https://github.com/crest-lab/crest/pull/322
* 🔒 Safer toml input parsing in https://github.com/crest-lab/crest/pull/325 Unrecognized keywords will now throw a warning and stop the program immediately
* 🛠️ Maintenance of submodules in https://github.com/crest-lab/crest/pull/328
* ⚙️ Update of GitHub workflows in https://github.com/crest-lab/crest/pull/335
* 🛠️ Safer (but unfortunately still not fixed) MKL handling for ifort builds in https://github.com/crest-lab/crest/pull/331
* 🌊 **Fixing implicit solvation in `tblite` submodule** in https://github.com/crest-lab/crest/pull/331 (most important change, should now be consistent with `xtb`)
* 📦 Added a GNU/CMake static build for the continuous release, alongside the Intel build:<br>[![Download (GNU)](https://img.shields.io/badge/download-GNU_build_binary-green)](https://github.com/crest-lab/crest/releases/download/latest/crest-gnu-12-ubuntu-latest.tar.xz)

<br>


---

## CREST 3.0.1 (CREST 3.0 Hotfixes) 
### What's Changed
* Address errors of issues [#281](https://github.com/crest-lab/crest/issues/281) 
* Restore printout of kpush, mentioned in [#284](https://github.com/crest-lab/crest/issues/284) 
* Address thread OpenMP handling issues of [#284](https://github.com/crest-lab/crest/issues/284) and [#285](https://github.com/crest-lab/crest/issues/285), see [#289](https://github.com/crest-lab/crest/pull/289)  
* Fix uninitialized boolean bug in gcc build [#287](https://github.com/crest-lab/crest/pull/287) 
* Fix axis bug causing [#296](https://github.com/crest-lab/crest/issues/296) 
* Address QCG issues [#297](https://github.com/crest-lab/crest/issues/297) and [#294](https://github.com/crest-lab/crest/issues/294)
* Singlepoint and optimization printout cleanup

### Other Additions
* Allow `tblite` parameter file read-in in [#303](https://github.com/crest-lab/crest/pull/303)
* Implement dipole and atomic charges readout for tblite calculators, gfn0 and gfnff
* CMake-based unit tests (run `make test` after building)


---

## CREST 3.0 

CREST 3.0 is a major overhaul of the previous code versions. A large part of the original source code was rewritten to implement calculators, optimization, and molecular dynamics routines *directly*, rather than relying only on the `xtb` program as a subprocess. 
Consequently, there are performance improvements and a significant reduction of I/O operations.
Read all about the new program version in the new open access article [**J. Chem. Phys. 2024, 160, 114110**](https://doi.org/10.1063/5.0197592).

Features include:
- New [**input file reader** {{site.data.icons.book}}](../documentation/inputfiles.html              "Documentation / Input Files")
- Energy- and gradient-based interface for calculations
- Standalone ANCOPT implementation (RF optimizer with BFGS update step in approximate normal         coordinates)
- Standalone MD and metadynamics module
- Standalone implementation of geometrical constraints
- New minimum energy crossing point (MECP) algorithm (see [**Examples/MECP Calaculations**](../      examples/mecp   "Examples / MECP Calculations"))
- Integration of the [**tblite** {{ site.data.icons.github }}](https://github.com/tblite/tblite  "tblite on GitHub") submodule
- Integration of a [**GFN0-xTB** {{ site.data.icons.github }}](https://github.com/pprcht/gfn0) submodule (see [J. Phys. Chem. Lett. 2023, 14, 19, 4440–4448](https://doi.org/10.1021/acs.jpclett.3c00494))
- Integration of the [**TOML-F**  {{ site.data.icons.github }}](https://github.com/toml-f/toml-f)    parser
- Integration of a [**GFN-FF** {{ site.data.icons.github }}](https://github.com/pprcht/gfnff) submodule
- Implementation of a multi-layered multi-center ONIOM calculator (see [J. Phys. Chem. B 2024, 128, 13, 3145–3156](https://doi.org/10.1021/acs.jpcb.4c00104))
- Proper unit tests for the CMake build
