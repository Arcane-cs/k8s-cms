# k8s-cms Changelog

## Version 0.4.0
### Added
- k8s-cms master component
    - added JWT token authentication for k8s-cms master
    - added contest api to import/update/delete contests
    - added dockerfile and k8s service & deployment for k8s-cms master
- kcmscli - k8s-cms CLI
    - import, export users from CSV files
    - import contests into k8s-cms
    - get,update,delete contests from k8s-cms

### Changed
- migrate from helm v2 to helm v3

## Version 0.3.0
### Added
- checksum configmaps and secrets to restart pods on updates
- Quality of Service
    - profiling resource usage for simulated workload (48 particpants/1 submission per 60s)
    - limit worker resources to ensure quality of service.
    - set limits and requests for pods in kubernetes
- securing k8s-cms:
    - HTTPs for RankingWebServer,AdminWebServer,ContestWebServer.
        - setup cert manager chart to use lets encrypt to obtain certificates 
- autoscaling for contest web servers and workers to handle the load
- node taints & selector to to control pod scheduling 

### Changed
- migrate kubernetes yaml to helm v2
    - config maps:
        - cms-config-env
        - cms-config
    - secrets
        - cms-secrets
    - Database service and depolyment
    - LogService service and deployment
    - ResourceService service and deployment
    - ScoringService service and deployment
    - EvaluationService service and deployment
    - ProxyService service and deployment
    - AdminWebServer service and deployment
    - PrintingService service and deployment
    - RankingWebServer service and deployment
    - Checker service and deployment
    - ContestWebServer service and deployment
    - Worker service and deployment

### Removed
- remove support for kustomize under k8s/

## Version 0.2.3 beta 
### Changed
- fixed issue where cms entrypoint did not drop permssions correctly

## Version 0.2.2 beta - 2019-10-07
### Changed
- fixed images deployed using kustomize tagged 'latest' instead of 'v0.2.1b'
- fixed missing cms secret key required for contest web server
- fixed missing ranking server credentials required for proxy server to access 
    ranking server

## Version 0.2.1 beta - 2019-10-04
### Changed
- securing k8s-cms:
	- expose only required secrets instead of using envfrom exposing everything
    - run cms pods with cms-services service account, with automount token disable.

## Version 0.2.0 alpha - 2019-09-30
### Added
- database dependency - wait for database before starting CMS services
- kubernetes support - write k8s deployment for YAMLs all these:
    - Database :heavy_check_mark:
    - ResourceService :heavy_check_mark:
    - LogService :heavy_check_mark:
    - ScoringService :heavy_check_mark:
    - EvaluationService :heavy_check_mark:
    - ProxyService :heavy_check_mark:
    - AdminWebServer :heavy_check_mark:
    - PrintingService :heavy_check_mark:
    - RankingWebServer :heavy_check_mark:
    - Checker :heavy_check_mark:
    - ContestWebServer :heavy_check_mark:
    - Worker  :heavy_check_mark:
    - Ingress service to combine ranking, contest and admin web servers.

### Changed
- make cms docker images source cms configuration from /etc/
- split singular env file to config.env for config, .env for secrets

- securing k8s-cms:
    - run all (except db) services as non root user.

## Version 0.1.0 alpha - 2019-09-21
### Added
- docker containers for CMS services :heavy_check_mark:
    - Database  :heavy_check_mark:
    - ResourceService :heavy_check_mark:
    - LogService :heavy_check_mark:
    - ScoringService :heavy_check_mark:
    - ProxyService - with single contest support limitation :heavy_check_mark:
    - EvaluationService :heavy_check_mark:
    - PrintingService :heavy_check_mark:
    - AdminWebServer :heavy_check_mark:
    - RankingWebServer :heavy_check_mark:
    - Checker :heavy_check_mark:
    - ContestWebServer - with single contest limitation :heavy_check_mark:
    - Worker - requires language support :heavy_check_mark:
        - C C++ Java Pascal Python with zip executable PHP Rust C# 
- docker-compose single machine support :heavy_check_mark:
