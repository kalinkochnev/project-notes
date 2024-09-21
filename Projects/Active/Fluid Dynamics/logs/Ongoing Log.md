# 8/28/24
- [ ] Reduce noise for ODE 45 image

- Results are stored in `latest_results` directory on HPC
Copy files from HPC to laptop
`rsync -avz --exclude-from='.gitignore' kak21001@hpc2.storrs.hpc.uconn.edu:~/fluidstability/latest_results/ ./results/`