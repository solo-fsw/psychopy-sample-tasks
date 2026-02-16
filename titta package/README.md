# 

\# Titta Package

The titta package allows to use tobii eye trackers with python and can be used to integrate Tobii Pro Lab in Psychopy experiments. Note that Tobii does not work in every Python version, see \[SOLO Research Wiki - Tobii and OpenSesame]



\*\*builder\_test\_TPL.psyexp\*\* is an example Psychopy builder task of how to use Titta with Tobii Pro Lab integration. It is an adapted from the the example psychopy coder file which can be accessed here: https://github.com/marcus-nystrom/Titta. This page also contains more information about the titta package. Note that you also need to create an External Presenter project in Tobii  Pro Lab to record the data.



\## Psychopy

\### Initialize Titta 

See the first routine "init\_1". It is important to define which eye tracker you are using, e.g. `et\_name = 'Tobii Pro Spark'`. Additionally, you need to define the name of your external presenter project in Tobii Pro Lab. If you define it as None, then it will simply use the project that is currently opened in Tobii Pro Lab, e.g. `project\_name = None`.



\### Performing the Calibration 

Calibration is performed outside of Tobii Pro Lab via the Tobii module, see the Calibration routine. In this example task, images with calibration results are saved in the output folder. It is also possible to save the validation accuracy results using tracker.calibration\_history() after calibration was performed. 



\### Starting the recording

See the start\_recording routine. The Tobii Pro Lab recording needs to be started before the stimuli are presented. 



\### During the trial

You will need a trial routine and a trial loop. In the loop properties, add a csv file containing the stimulus file names. 

In the code component, the media is uploaded and optionally, AOIs can be added to the stimuli. For each stimulus, the recording id, onset time, media id and offset time are sent to Tobii Pro Lab as stimulus events.



\### Stopping the recording

The recording in Tobii Pro Lab needs to be stopped at the end of the experiment, see the "stop\_recording" routine. 



\## Tobii Pro Lab 

You need to create an external presenter project in Tobii Pro Lab by going to \*\*Create new project - External Presenter - Create\*\*. Make sure to keep the project open and on the `Record` tab before starting the experiment in OpenSesame. The External Presenter box will change the status to "Connected" once the experiment started and OpenSesame successfully connected to Tobii Pro Lab. After the recording is finished, you can view the recording in the Analyze tab. 



