#### How to run locally an already existing LEGO train 

1. Go to [https://alimonitor.cern.ch/trains/](https://alimonitor.cern.ch/trains/) and choose the train you would like to test, i.e. PWGZZ/MCGen_pp/2351_20220326-2110

2. Download the configuration files of this train:
```
. downloadtraintest  PWGZZ/MCGen_pp/2351_20220326-2110
```

3. Generate the macros for launching the train in test mode:
```
. generatetraintest
```

4. Run the train:
```
. runtraintest
```


#### How to run locally a new LEGO train to test a private task (even not pushed in AP yet!)

1. Go to [https://alimonitor.cern.ch/trains/](https://alimonitor.cern.ch/trains/) and choose a baseline train which is similar to the one you would like to test, i.e. PWGZZ/MCGen_pp/2351_20220326-2110

2. Download the configuration files of this train:
```
. downloadtraintest  PWGZZ/MCGen_pp/2351_20220326-2110
```

3. Change the configuration file *MLTrainDefinition.cfg* witn you task name and location. Please note that between ```#Module.StartConfig``` and ```#Module.EndConfig``` you shoul put your task customization as usual in ALICE wagons, if no customization is need **leave an empty line**.

4. Generate the macros for launching the train in test mode:
```
. generatetraintest
```

5. If your task is not already embedded in AliPhysics, change the *lego_train.C* steering macro by including your task at the top and by compiling the source, i.e.
```
// analysis source to be compiled at runtime (if any)
gROOT->LoadMacro("AliAnalysisTaskMCPredictionsStrgVsMultVsZDC.cxx++g");
```

6. Run the train:
```
. runtraintest
```




Code comes from https://github.com/mfasDa/legotrain_helpers and https://twiki.cern.ch/twiki/bin/viewauth/ALICE/AnalysisTrains#Local_train_test