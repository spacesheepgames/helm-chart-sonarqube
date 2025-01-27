# SonarQube Chart Changelog
All changes to this chart will be documented in this file.

## [1.0.4+1]
* specific config
* add log4j [vulnerability fix](https://community.sonarsource.com/t/sonarqube-sonarcloud-and-the-log4j-vulnerability/54721)

## [1.0.4]
* fix for missing `serviceAccountName` in STS deployment kind

## [1.0.3]
* fixed prometheus config volume mount if disabled
* switched from wget to curl image per default for downloading agent
* added support for proxy envs

## [1.0.2]
* added option to configure CE java opts separately

## [1.0.1]
* fixed missing conditional that was introduced in 0.9.2.2 to sonarqube-sts.yaml
* updated default application version to 8.9 

## [1.0.0]
* changed default deployment from replica set to statefull set
* added default support for prometheus jmx exporter
* added init filesystem container
* added nginx-ingress as optional dependency
* updated application version to 8.8-community
* improved readiness/startup and liveness probes
* improved documentation

## [0.9.6.2]
* Change order of env variables to better support 7.9-lts

## [0.9.6.1]
* Add support for setting custom annotations in admin hook job.

## [0.9.6.0]
* Add the possibility of definining the secret key name of the postgres password.

## [0.9.5.0]
* Add Ingress default backend for GCE class

## [0.9.2.3]
* Added namespace to port-foward command in notes.

## [0.9.2.2]
* Added a condition to deployment.yaml so that `wait-for-db` initContainer is only created if `postgresql.enabled=true`

## [0.9.2.1]
* Updated the configuration table to include the additional keys added in release 9.2.0.

## [0.9.2.0]
* Added functionality for deployments to OpenShift clusters.
    * .Values.OpenShift flag to signify if deploying to OpenShift.
	* Ability to have chart generate an SCC allowing the init-sysctl container to run as privileged.
	* Setting of a seperate securityContext section for the main SonarQube container to avoid running as root.
	* Exposing additional `postreSQL` keys in values.yaml to support configuring postgres to run under standard "restricted" or "anyuid"/"nonroot" SCCs on OpenShift.
* Added initContainer `wait-for-db` to await postgreSQL successful startup before starting SonarQube, to avoid race conditions.

## [0.9.1.1]
* Update SonarQube to 8.5.1.
* **Fix:** Purge plugins directory before download.

## [0.9.0.0]
* Update SonarQube to 8.5.
* **Breaking change:** Rework init containers.
    * Move global defaults from `plugins` section to `initContainers`.
    * Update container images.
* **Deprecation:** `elasticsearch.configureNode` in favor of `initSysctl.enabled`.
* Rework sysctl with support for custom values.
* Rework plugins installation via `opt/sonarqube/extensions/downloads` folder that is handled by SonarQube itself.
    * **Breaking change:** remove `plugins.deleteDefaultPlugins` as SonarQube stores bundled plugins out of `opt/sonarqube/extensions`.
* Rename deprecated `SONARQUBE_` environment variables to `SONAR_` ones.
* **Breaking change:** Rename `enabledTests` to `tests.enabled`.
* Add `terminationGracePeriodSeconds`.
