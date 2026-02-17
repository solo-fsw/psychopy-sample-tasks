
# Titta Package

The titta package allows to use tobii eye trackers with python and can be used to integrate Tobii Pro Lab in Psychopy experiments. Note that Tobii does not work in every Python version, see [SOLO Research Wiki - Tobii and OpenSesame](https://researchwiki.solo.universiteitleiden.nl/xwiki/wiki/researchwiki.solo.universiteitleiden.nl/view/Software/OpenSesame/Tobii%20and%20OpenSesame/)



**builder_test_TPL.psyexp** is an example Psychopy builder task of how to use Titta with Tobii Pro Lab integration. It is adapted from the example psychopy coder file which can be accessed here: https://github.com/marcus-nystrom/Titta. This page also contains more information about the titta package. Note that you also need to create an External Presenter project in Tobii  Pro Lab to record the data.



## Psychopy

### Initialize Titta 

See the first routine "init_1". It is important to define which eye tracker you are using, e.g. `et_name = 'Tobii Pro Spark'`. Additionally, you need to define the name of your external presenter project in Tobii Pro Lab. If you define it as None, then it will simply use the project that is currently opened in Tobii Pro Lab, e.g. `project_name = None`.



### Performing the Calibration 

Calibration is performed outside of Tobii Pro Lab via the Tobii module, see the Calibration routine. In this example task, images with calibration results are saved in the output folder. It is also possible to save the validation accuracy results using tracker.calibration_history() after calibration was performed. 



### Starting the recording

See the start_recording routine. The Tobii Pro Lab recording needs to be started before the stimuli are presented. 



### During the trial

You will need a trial routine and a trial loop. In the loop properties, add a csv file containing the stimulus file names. 

In the code component the media is uploaded and optionally AOIs can be added to the stimuli. For each stimulus, the recording id, onset time, media id and offset time are sent to Tobii Pro Lab as stimulus events.



### Stopping the recording

The recording in Tobii Pro Lab needs to be stopped at the end of the experiment, see the "stop_recording" routine. 

>[!IMPORTANT]
If Psychopy crashes or the experiment is exited before you reach the end, the connection to Tobii Pro Lab may not be properly closed. You might receive this error when trying to run the experiment the next time: `OSError: [WinError 10048] Only one usage of each socket address (protocol/network address/port) is normally permitted: ('', 9036)`. To resolve this, you can restart your laptop or manually disable the connection. To do so, go to the Command prompt and identify what is holding the connection: 
```python
netstat -aon | findstr :9036
```
You will see a PID number on the right side, it could look something like this: 

 `UDP    0.0.0.0:9036           *:*                                    10872`

 Stop the offending process by entering the process ID: 
 
 ```python
taskkill /PID <PID> /F
#in our example PID = 10872
taskkill /PID 10872 /F
```

 

## Tobii Pro Lab 

You need to create an external presenter project in Tobii Pro Lab by going to **Create new project - External Presenter - Create**. Make sure to keep the project open and on the `Record` tab before starting the experiment in OpenSesame. The External Presenter box will change the status to "Connected" once the experiment started and OpenSesame successfully connected to Tobii Pro Lab. After the recording is finished, you can view the recording in the `Analyze` tab. 



