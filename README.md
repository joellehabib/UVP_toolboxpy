# UVP6_time_merge
Merge different acquisition sequences on a constant time step.

## How to use it

Download this repo with git clone.
```
git clone git@github.com:ecotaxa/UVP_toolboxpy.git
```
Launch time_merge/format_time_series_project.py
```
/usr/bin/pyton UVP6_time_merge/time_merge/format_time_series_project.py
```
Look at your terminal to give the input needed (input folder, start date time, time step, output folder)

## What does it do ?

While the time_merge/functions.py can help you formatting your project "by hand" the time_merge/format_time_series_project.py is a workflow easy to use that will do it for you. Here is the few step it goes through.

### Invite the user to specify the project, date range and time step of the split/merge to execute

When you will execute format_time_series_project.py a message will prompt you to provide the path of a UVP project with a time series acquisition. The project should be organised as a standard UVP6 project, with a "raw" folder that includes different data.txt and associated vignettes. 
The user will then chose when he wants to start the split/merge operation.

### Split your raw folder into different raw folders depending on acquisition configuration

One important prerequisite of merging and splitting acquisition is to make sure that we merge data that have been acquired with the same method. The package is thus designed to split your original raw folder in as much raw folders as there is unique acquisition configuration. Each new folder will be name "raw_a", "raw_b" etc... 
The original datatxt will be copied in the new project. 

### Merge and/or split the data

Once we are sure that our raw folders have the same acquisition parameters we can proceed to data manipulation. The user will input a time step on which he want to reshape the new raw folders (one per acq conf). The new datatxt will be name like "'%Y%m%d-%H%M%S_Merged_data.txt". 

### Moving vignette to new raw folder

Finally, the vig will be copied from the old raw folder, based on the different dates of the merged_data.txt dates.
