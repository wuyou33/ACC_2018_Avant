# Dynamics, Hover Configurations, and Rotor Failure Restabilization of a Morphing Quadrotor

![alt text](videos/animation_pt175_2k.gif)

This is the code for the paper

[**Dynamics, Hover Configurations, and Rotor Failure Restabilization of a Morphing Quadrotor**](https://ieeexplore.ieee.org/document/8431628)

Trevor Avant, Unsik Lee, Brian Katona & Kristi Morgansen, *American Control Conference (ACC) 2018*

## code

The code is written in Mathematica (11.0) and Matlab (2018b).

### dynamics (Section II)
* **dynamics derivation**: run `mathematica/dynamics.nb`
  * *Note:* This will output 3 text files: `M.txt`, `h.txt`, and `Q.txt`. The contents of these files are intended to be copied into the Matlab dynamics file `dx.m`. This has already been done, so it is not necessary to run the .nb file again. Additionally, running this file may take a long time.


### hover configurations (Section III)
* **hover recovery simulation**: analysis is contained in `mathematica/equilibrium_math.nb`

### rotor failure restabilization (Section IV)

* **system overview diagrams (Figures 1 & 2)**: run `matlab/plot/plot_overview_diagrams.m`

* **hover recovery simulation (Figures 3 & 4)**: run `matlab/hover_recovery.m`

* **region of attraction (Figure 5)**: run `matlab/region_of_attraction.m`
  * *Note*: This may take awhile. As an alternative, you can go to the bottom of the file and load previous results by running the commented line: `load region_of_attraction_results.mat`. Then, you can generate the plot by manually running the remaining lines of `region_of_attraction.m`.

## extras

* **calculation of the thrust and torque coefficients**: is explained in `matlab/propeller_calculations/propeller_coefficients_calculation.m`

* **arm motion animations**: run `matlab/plot/plot_arm_motions.m`
  * *Note*: Different motions can be generated by changing the `mode` variable in this file.

* **dynamics tests**: to test dynamics of the quadrotor for different initial conditions and/or control laws, run
`matlab/test_dynamics.m`

## notes

* Our system is poorly scaled, which makes computing an LQR gain numerically challenging. In our code, we use Matlab's `lqr` command, which will work for our system in versions of Matlab prior to 2019a. It does not work in later versions because Matlab changed their `lqr` algorithm. So, if this code is run in version 2019a or later, instead of re-running the `lqr` command, our code will automatically load previous LQR results from the `matlab/saved_results/lqr_results.mat` file.

* There is a small error in Fig. 5. Our choice of Euler angles has singularities at theta = +/- pi/2 (not phi = +/- pi/2), so the blue lines should be vertical.
