# Storing Data

There are two storage spaces available on the campus clusters: “home” space and “scratch” space, each with its own purpose.
                                                                                                                           
Home space is a small area that serves as your home directory on the cluster – this is the directory that you’re placed into upon logging in. 
Home directories are not visible to other users and are intended for your own personal storage, not for collaborative storage. 
They have a hard limit of 100 GB, with a warning sent at 75 GB. 
On R2, the home space for each user is located at /home/(R2 username); on Borah, it’s located at /bsuhome/(Borah username).

Scratch space, conversely, should be the target of all job output or other input/output heavy processes when using the cluster. 
While scratch space can accommodate much larger data sets, it is meant for short-term storage and we ask that you watch utilization. 
Scratch space is not backed up and is subject to clean-up if it gets too close to capacity. 
If the scratch space approaches its useful capacity, the automated process will start removing files that have not been accessed for 4 weeks. 
If the system exceeds its useful capacity, there is risk of failure. 
On R2, the scratch space for each user is located at /scratch/(R2 username); on Borah, it’s located at /bsuscratch/(Borah username). 
There’s also a symbolic link (a file that represents a “shortcut” to another spot on the file system) to scratch space placed in your home directory on both R2 and Borah, and thus scratch can be accessed by simply doing cd scratch from your home directory.