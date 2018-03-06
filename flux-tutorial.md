# Introduction to the Flux Cluster

- Mac: $ ssh flux-login.art-ts.umich.edu

-Windows: use PuTTy; demo to follow

> http://arc-ts.umich.edu/software/torque/
>
> http://arc-ts.umich.edu/software/lmod/

Portable Batch System - PBS

```
####  Request resources here
####    These are typically, number of processors, amount of memory,
####    an the amount of time a job requires.  May include processor
####    type, too.

#PBS -l nodes=1:ppn=1,mem=1gb,walltime=15:00
```

nodes - num of nodes

ppn - processor per node

mem - space of memory

walltime - different from cpu time (per cpu time) 10:00:00:15 - 10 days and 15 seconds, faster for scheduler - 15 minutes

```
####  Flux account and queue specification here
####    These will change if you work on multiple projects, or need
####    special hardware, like large memory nodes or GPUs or,
####    or if you use software that is restricted to campus use.

#PBS -A training_flux
#PBS -q
```

-A - who would pay (engin_flux) big mem - fluxm, gpu- fluxg

-q - queue it goes to

```
#### #### ####  These are the least frequently changing options

####  Your e-mail address and when you want e-mail

#PBS -M youdymoo@umich.edu
#PBS -m -bea

####  Join output and error; pass environment to job

#PBS -j
#PBS -V
```

-M - email address

-m - send email notifications, b - begin, e - end, a - abort

-j - output style, oe - output and error

-V - environment should be give to the job, 

```
##  Change to the directory from which you submit the job, if running
##  from within a job
if [ -d "$PBS_O_WORKDIR" ] ; then
    cd $PBS_O_WORKDIR
fi


####  Commands your job should run follow this line
##
##  Note:  In batch jobs, programs should always run in foreground.  Do
##         not use an & at the end of a command. Bad things will happen.

echo "Running from $(pwd)"

sleep 180
echo "Hello, world"
```

environment variable - if directory changed, echo $PWD, printenv | less

sleep - 3 minutes

## Important commands:
```
bash hello.pbs
qsub hello.pbs # job id and job name
qstat - u $USER 
qpeek # see the progress
showq -w acct=training_flux # show list of process
mdiag -u youdymoo # my account paid by whom
mdiag -a training_flux # my paying account
freealloc training_flux # 
```

S - Q: queue, R: running, C: completed

output file - in the directcat ory

```
Running on
      1 nyx6145
Running from /home/youdymoo/IntroFlux
Hello, flux
```

