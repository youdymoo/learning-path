# Introduction to the Flux Cluster

- Mac: $ ssh flux-login.art-ts.umich.edu

- Windows: use PuTTy; demo to follow

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

- nodes - num of nodes

- ppn - processor per node

- mem - space of memory

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

============Example with R==============
```
module keyword statistics # description of softwares with keyword
module spider stata # particular package
module available sas # abbr as av, (D) as default
module load R
module list # find what package has been loaded
module swap R/3.4.1 # change the package version
module purge # unload all the packages
module av gromacs # gcc
module load gromacs/5.1.2/openmpi/1.10.2/gcc # have save with modules
```

Never save R workspace

```
> nano iris.R
library(datasets)
data(iris)
summary(iris)
> R CMD BATCH iris.R
> cat iris.Rout
  Sepal.Length    Sepal.Width     Petal.Length    Petal.Width
 Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100
 1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300
 Median :5.800   Median :3.000   Median :4.350   Median :1.300
 Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199
 3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800
 Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500
       Species
 setosa    :50
 versicolor:50
 virginica :50

>
> proc.time()
   user  system elapsed
  0.179   0.038   0.301
  

```
