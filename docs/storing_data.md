# Storing Data

## Cluster storage
There are different storage spaces available on the campus clusters each with
their own purpose.

### Home
Your home directory is where you’re placed upon logging in.
Home directories are not visible to other users and are intended for personal
storage, not for collaborative storage.
Home directories are backed up each night, so we can recover files from your
home if they are deleted accidentally.
The home space for each user on Borah is located at `/bsuhome/(Borah username)`.
**Home directories are limited to 75 GB.** If you hit this limit, you will
receive an email notification letting you know you have 4 weeks to get below
the limit before your home directory is locked and you will no longer be able
to write to it. There is also a hard limit at 100 GB which will immediately
prevent you from writing to your home directory.

### Scratch
Scratch space, conversely, should be the target of all job output or
input/output heavy processes when using the cluster.
While scratch space can accommodate much larger data sets, it is meant for
short-term storage and we ask that you watch utilization.
Scratch space is not backed up and is subject to clean-up if it gets close
to capacity.
There is risk of failure if the filesystem exceeds its useful capacity.
As such, we reserve the right to delete data without notice if /bsuscratch
reaches 90% capacity or higher.

The scratch space for each user on Borah is located at `/bsuscratch/(Borah username)`.
There’s also a symbolic link (a file that represents a “shortcut” to another spot on the file system) to scratch space placed in your home directory, so scratch can be accessed by running `cd scratch` from your home directory.

### Shared project space
Shared project space is available upon request. Like scratch, the shared space
is not backed up and is subject to clean-up if the file system nears its useful
capacity. As such, the shared project space is intended for active
collaboration, not long term storage or archival. To request a shared directory,
please email
[researchcomputing@boisestate.edu](mailto:researchcomputing@boisestate.edu)
with the following information:

- BSU email address of the project PI
- Expected project end date
- Amount of space in GB or TB
- Plan for long term data storage (if needed) once the project is over

## Other storage

### Research share

The Office of Information Technology provides up to 25TB of storage at no cost
for each Boise State faculty and departments.
If you are a faculty or staff member working on a sponsored project and
anticipate that your current allocation will exceed 25TB, please contact
[researchcomputing@boisestate.edu](mailto:researchcomputing@boisestate.edu)
for a quote to include with your proposal.
Staff are charged by the department, researchers are charged by the individual
(or recharge center).

To request a research share, please email
[researchcomputing@boisestate.edu](mailto:researchcomputing@boisestate.edu)
and let us know the following:

- How much space you'll need
- The Boise State emails of any collaborators you'd like to have access
- (optional) If you would like subfolders for project groups, please let us
know.
In the file tree example below, the "myproject" subfolder could have different
access controls than the "common" folder.
```
└── cifs-prd-01
    └── research
        └── johndoe123
            ├── common
            │   └── myproject
            └── home
```


For instructions on how to access this research share from your computer once
it's been created, please see [Mapping a Network Drive](mapping_drive.md).
