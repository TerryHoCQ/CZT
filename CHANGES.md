v0.0.8 (unreleased)
===================

- Testing:
	- Add continuous integration via GitHub actions (testing, linting)
- Misc:
	- Remove lint (unnecessary code)
	- Clean up comments

v0.0.7 (Oct 12, 2021)
=====================

- Bugs:
   - Remove `import czt` from `setup.py`. This was causing a circular dependency.
- Testing:
   - Compare this package against a stripped down version of the CZT algorithm.
   - Improve testing coverage.
- Examples:
   - Plot residuals in examples.

v0.0.6 (Mar 22, 2021)
=====================

- `czt`:
	- `freq2time` and `time2freq`:
		- Fix phase correction.
		- Remove scaling factor (hack).
		- Remove `t_orig` and `f_orig` arguments. Not needed anymore.
		- Don't return original frequency/time in `time2freq` and `freq2time`. Instead make a copy of the Numpy array.
	- Always default to FFT settings if output frequency/time array is not specified.
	- Fix `M!=N` error in `czt.czt`. Use proper `k`-range.
	- Optimize `pd` and `skew_circulant_multiply`. `pd` is now a similar speed as `scipy`.
- Profiling:
	- Add benchmarking scripts using `perfplot`.
	- Add simple timing scripts.

v0.0.5 (Mar 2, 2021)
====================

- CZT:
	- Optimize code to run faster (approx. x4)
	- Change default `t_method` to `'ce'` (fastest, see benchmark scripts)
- Benchmark:
	- Use perfplots to iterate over a range of input sizes

v0.0.4 (Feb 27, 2021)
=====================

- CZT:
	- Change default ``t_method`` to ``'scipy'`` (fastest).
	- czt.iczt: add option to use algorithm 2 from Sukhoy & Stoytchev 2019.
	- Fix error in fft and ifft algorithms. Remove warnings now that they work.
	- Rename ``f_method``: ``"std"`` -> ``"numpy"``, ``"fast"`` -> ``"recursive"``
- Benchmark:
	- Add benchmarks for czt.czt and czt.iczt.
- Misc:
	- Remove windowing functions (unnecessary).

v0.0.3 (Feb 26, 2021)
=====================

- CZT:
	- Added new ``t_method`` to ``czt``. This method uses the new ``matmul_toeplitz`` function from Scipy. Requires ``scipy>=1.6.0``.
	- Fixed argument order in ``scipy.linalg.toeplitz``.
	- Use ``np.complex128`` for A and W. Fixes a potential error if A or W is passed as an integer.
- Setup:
	- Add dependencies for examples.
	- Add ``requriements.txt``.
- Testing:
	- Added new ``t_method`` to testing.
- Misc:
	- More comments.

v0.0.2 (Dec 21, 2020)
=====================

- CZT:
	- Add function for inverse CZT (iczt) using complex conjugate.
	- ``czt``: 
		- Fixed default phase of W so that CZT provides FFT by default.
		- Wrapped ``czt_simple`` into ``czt`` (can still accessed via ``simple=True`` argument).
	- ``time2freq``:
		- Changed default frequency range to match FFT
		- Add normalization for arbitrary freq/time sweeps
	- Add functions to generate windows.
- Testing:
	- Add test to compare CZT to analytic expression
	- Added test to compare CZT to FFT
	- Added test for ICZT
	- Added test for time-domain -> frequency-domain -> time-domain conversion
	- Remove redundant tests
- Examples:
	- Add example calculating the time-domain response of a lossy waveguide
	- Automatic package reloading after each cell
- ``setup.py``:
	- Use ``py_modules`` instead of ``packages``

v0.0.1 (Dec 2, 2020)
====================

Initial release.
