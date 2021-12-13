SonarQube Helm Chart (Custom)
=================

Main differences
---------------
* At `charts/sonarqube/static` we have our PVC and PV that always use the same disk to store sonarqube data
* We do not run it in a dedicated namespace as the original chart does

Deploy
---------------
Fill the values in `charts/sonarqube/values.yaml`:

**Be careful to not commit it**
```
monitoringPasscode: <passcode>

sonarProperties:
  sonar.core.serverBaseURL: <serverUrl>

postgresql:
  postgresqlServer: <postgresServer>
```

Make sure you are using the correct cluster.

Deploy it using helm:
```
cd charts/sonarqube
helm upgrade --install -f values.yaml sonarqube ./
``` 

Original Readme
===============

About this Repo
----------------

This is the Git repo of the SonarSource Helm Chart for [SonarQube](https://www.sonarqube.org/).  
The actual chart can be found in the [charts](charts/sonarqube) directory and see the README of the chart for more information. 

Have Question or Feedback?
--------------------------

For support questions ("How do I?", "I got this error, why?", ...), please first read the [documentation](https://docs.sonarqube.org) and then head to the [SonarSource forum](https://community.sonarsource.com/). There's a chance that a question similar to yours has already been answered. 

Be aware that this forum is a community, so the standard pleasantries ("Hi", "Thanks", ...) are expected. And if you don't get an answer to your thread, you should sit on your hands for at least three days before bumping it. Operators are not standing by. :-)

Contributing
------------

If you would like to see a new feature, please create a new thread in the forum ["Suggest new features"](https://community.sonarsource.com/c/suggestions/features).

With that in mind, if you would like to submit a code contribution, please create a pull request for this repository. Please explain your motives to contribute this change: what problem you are trying to fix, what improvement you are trying to make.

Note of Thanks
--------------

This chart was based on the great work done on the [Oteemo chart](https://github.com/Oteemo/charts/tree/master/charts/sonarqube). 
We would like to thank everyone who contributed for their great work on this project.

License
-------

Licensed under the [MIT Licence](LICENSE)
