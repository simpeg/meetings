# Parallel computation in Python: Directions for SimPEG from Zephyr & Dask

Presented by: [Brendan Smithyman](https://github.com/bsmithyman)

[![2016-11-08](https://img.youtube.com/vi/53dhim3eMGA/0.jpg)](https://youtu.be/53dhim3eMGA)

## Notes

### Zephyr
- Full waveform inversion
- Meant to be competitive in performance with Full Wave
- Works with existing Fortran code
- Improves upon old Fortran solver written by some PhD student from 20 years ago 

### Philosophy
- Python: like a mutual fund
- To get the best performance on codes - look to people who know how to do that already
- Focus your expertise
 
### Parallel
- Built in multi-process in python
- Maps a function to many functions with different input ranges
- Dask 
    - creates a graph of tasks
    - Schedules them
    - High level interface
- Parallel over multiple left hand sides and multiple right hand sides


### How to do parallel in SimPEG?
- Look at Dask
- Mpi in python, can do message passing as numpy array or as python objects (more expensive and uses pickle)
- Concurrent futures, really easy, basic parallelism

## Links
- [demo](https://github.com/uwoseis/zephyr/blob/talk/simpeg/notebooks/Demo%20Links.ipynb)
- [zephyr](https://zephyr.space/)
- [dask](http://dask.pydata.org/en/latest/)
