Changes in first release version of MCEq from release candidate 1:

Version 1.1.2:

- Hotfix for MKL library handler

Version 1.1.0:

Minor version bump because of an interface change in some convenience functions, for example
dNdxlab in particledata. Those now consistently accept kinetic energy arguments. In the
previous versions some of these functions required laboratory energies others kinetic, that
may have generated some confusion. Other changes include:

- multiple calls to `set_single_particle` can define an initial state by using an the `append` flag
- updated to crflux 1.0.3 (Windows compatibility)
- Flux and result array are re-created when interaction model changes (not resized)
- Fixed ctypes bug in NRLMSISE
- Long description fixed in setup.py
- added license to scikit-hep project's azure-build-helpers by Henryii@github
- build includes Python 3.8 binaries (except for 32bit Linux)
- tests moved into MCEq package
- improved ctypes library finding
- new convenience function MCEqRun.closest_energy to obtain the closest grid point
- new convenience functions mceq_config.set_mkl_threads allows setting thread count in run time
- new CorsikaAtmosphere location "ANTARES/KM3NeT-ORCA"
- tests for atmospheres

Version 1.0.9:
- disable_decays flag in advanced options fixed
- threshold energy not used in n_mu, n_e
- new generic function 'n_particles' for arbitrary particle types
- new config option dedx_material

Version 1.0.8:
- Fixed a Python3 compatibility issue in density profiles
- Cross checked and corrected the functionality of "disabled particles" in config file
- Version tagged for paper submission

Version 1.0.6 and 1.0.7:
- A few typos corrected

Version 1.0.5:
- Check added to make sure depth grids are strictly increasing
- Tutorial updated to reflect this fact
- New advanced variable in config "stability_margin"
- New method in MCEqRun to set the entire spectrum for combinations
    of particles as initial condition

Version 1.0.4:
    First official version distributed over PyPi

Version 1.0.0:

General remark::
    This is a major rewrite of the MCEq core code. Mostly obsolete stuff is removed.
    The interfaces to the various data sources are handled in a different way via the
    container 'ParticleManager'. Each MCEqParticle object knows its properties, for
    instance if it can decay or interact, and if requires to be included in continuous
    losses. The matrix generation could be simplified a lot and the class MCEqRun became
    what it was meant to be - a user interface. Several experimental and less successful
    solver implementations have been removed. The splitting between energy and time solvers
    is not necessary anymore since the only successful energy (derivative) solver is the
    one based on DifferentialOperators that are not part of the "C Matrix". With the new
    structure it became simpler to exchange physical models or track particle decays of
    any kind.

