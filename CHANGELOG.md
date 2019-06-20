# Change Log
All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](http://semver.org/).



## [1.1.0] - 2019-06-20
#### Added
- Update ELK stack: v6.3.0 -> v7.1.1
- Multiple modifications to the ingestor service:
    * Move ingestor to `extensions` folder
    * Modify VulntoES to record MAC addresses, if present
    * Update ingestor container from python2.7 to python3.7
    * Semplify call method: `docker-compose run ingestor`
    * Minor refactoring to `VulntoES.py`
#### Fixed
- Time pattern now available
#### Removed
- Remove extensions/logspout


## [1.0.1] - 2018-10-17
#### Fixed
- Modify VulntoES to only ingest open ports


## [1.0.0] - 2018-07-16
#### Added
- First Public Release