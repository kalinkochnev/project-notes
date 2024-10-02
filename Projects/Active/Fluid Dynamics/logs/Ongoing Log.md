re# 9/28/24
- [ ] Plot quadratic norm based on debug data for these points:
	- [ ] Look at center point $m_{0}=k=0$ on ODE45 and 
	- [ ] Look at point that is stable on convex $m_{0}=0.8, k=0.3$ but unstable on ode45
- [x] Push changes to github
- [ ] Submit ode45 job to hpc with second half linear fit 
# 9/24/24
- [ ] Save arbitrary debug data into log files
- [ ] Save integration data for each cell entry

I got it to save a cell into a file. The problem is that the cell can't take nested cells. So there goes the plan of shoving everything into a cell. I'm going to try and array of structures next.
The problem is that the structure must be preallocated. Why is this so annoying.
# 9/21/24
- Almost finished making the debug feature working with matlab `cell`
- Final issue is that `save` cannot be called in parfor unless matlab knows exactly what variable is being saved. A separate function is necessary
https://www.mathworks.com/matlabcentral/answers/135285-how-do-i-use-save-with-a-parfor-loop-using-parallel-computing-toolbox
https://www.mathworks.com/help/parallel-computing/save-variables-in-parfor-loop.html

# 9/20/24
- I began developing the feature to save debug data for each `x, y` in `growthRateHeatmap`. 
	- The callback should return an additional value for debugging purposes
	- Callback should return `[]` if no debug data

![[convexode45_9-20-24.png]]
# 9/11/24
- [ ] Setup HPC on NSF accesss
# 8/30/24
- [x] Try sampling less for convex (~50-100)

- Add a progress bar 
- Sampling less has had very successful results.

- Yalmip gave this error message:
```
Warning: YALMIP has detected that your drive or network is unusually slow.
This causes a severe delay in OPTIMIZE when I try to find available solvers.
To avoid this, use the options CACHESOLVERS in SDPSETTINGS.
```

## TODO
- [ ] Specify the number of samples for ode45
- [ ] Do fitting for steady state, lets say `[15T, 100T]`
- [ ] Maybe try more initial conditions

## Process for running a job
1) Synchronize files from current directory to fluid stability directory 
```
rsync -avz --exclude-from='.gitignore' . kak21001@hpc2.storrs.hpc.uconn.edu:~/fluidstability/
```
# 8/28/24
- [x] Save figures and matrix of results to file
- [x] Submit HPC job for [[Radko 2019 Thermohaline-shear instability.pdf]] figure 1a ode45
- [x] Submit HPC job for [[Radko 2019 Thermohaline-shear instability.pdf]] figure 1a convex optimization
- [ ] Code figure 1b
- [ ] Submit HPC job for figure 1b
- [ ] Convert typst equations 7-11 [[Radko 2019 Thermohaline-shear instability.pdf]] to latex

- Results are stored in `latest_results` directory on HPC
- Copy files from HPC to laptop
```
rsync -avz --exclude-from='.gitignore' kak21001@hpc2.storrs.hpc.uconn.edu:~/fluidstability/latest_results/ ./results/
```
- Synchronize files from current directory to fluid stability directory 
```
rsync -avz --exclude-from='.gitignore' . kak21001@hpc2.storrs.hpc.uconn.edu:~/fluidstability/
```

- Run matlab script in terminal
```
~/Applications/Matlab/bin/matlab -nodisplay -nosplash -nodesktop -r "thermohaline_fig1a"
```
## TODO
- [x] Add enum to select between different paper matrices and solvers