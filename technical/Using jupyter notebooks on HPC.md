# Using jupyter notebooks on HPC
For Seawulf, but process should be the same for any server.

1. Make sure you have jupyter and jupyterlab libraries installed into your python virtual environment
```bash
pip install jupyter jupyterlab
```
2.  Create the shell script to submit the job. It just needs to contain this line after you source the python venv:

```bash
jupyter lab --ip=0.0.0.0 --port=8888 --no-browser
```
3. Submit a job using that shell script
4. In your own terminal (not connected to any server), enter the following commands:

```bash
ssh -t -t eswong@milan.seawulf.stonybrook.edu -L 8888:localhost:8888 ssh nodelist -L 8888:localhost:8888
```
- Replace `eswong` with your username and `nodelist` with the name of the node assigned to the job you submitted (under NODELIST)
	- View jobs you’re currently running using `squeue -u username`

5.  After you have ensured that “Jupyter Server 1.13.1 is running at:” appears in one of your out/err files, connect to `localhost:8888` and you should see your notebook/lab