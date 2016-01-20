Lecture 2016-01-12
==================

* Kemal Ahmed
* SFWR ENG 4F03
* Ned^2

##Unix Commands
 
* `mpirun`: `mpi-basics%mpirun -np 4 ./partrap`, where 4 is the number of cores
* `mpibasics`:

Sets can underflow with numbers that are too small

##C

For long ints, you need to denote them with an `L` at the end, i.e. `long int a = 200000000000L`

##Runtime

Communications

P^-1
O(p)

P
O(log(p))

`MPI_Bcast`: takes data and send it to everyone else

Parts of Communication:

1. Startup phase [t_s]: has startup time
2. Transmission time [t_m]:

t_s + t_m

[t_w]: time to send the message

