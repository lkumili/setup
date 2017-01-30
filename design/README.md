# Overview

This design yaml files can be used to deploy OneOps like any other application in OneOps.

# Prerequisites

1. Working OneOps.
2. Nexus repository.


# Setup

1. Load oneops-design.yaml file into design via "Load" button.
2. First validate the yaml design them import.
3. Add below cloud variables:
   3.1. QUEUE : Location of activemq queues.
   3.2. nexus: Nexus repo where all component artifacts and depended jar are available,
   3.3. smtp : SMTP mail server.
4. Edit values for all the global variable with required values mostly database and activemq related user name and passwords.
    4.1  Domain :  Part of fqdn without component name.
    4.2  Distbase: Nexus repository.
    4.3  Display-rail-env: enterprise to use ldap authentication or production for database authentication.
    4.4 Domain-alias : display app url which is intended to be access oneops instance.
5. Generate certificates for all required components especially ESLogs, Wire and DAQdb.
6. Deploy components from bottom to top as per dependency diagram.
7. Once display app deployed successfully without any error in log ssh box and make changes manually in `…/config/environments/production.rb` setting there for `config.action_mailer.smtp_settings`.

#Inductor

Inductor is not installed as part of above setup.

1. Import inductor design into new assembly.
2. Edit the inductor component to copy DAQ cert into perf cert location, Eslog cert into log stash cert and Wire cert into attachment — ssl-certificate.

3. In case you want to stub the inductor:

   3.1. cat /opt/oneops/inductor/clouds-available/shared/conf/vmargs.
   
   3.2.  Append below to above file
             -Dstub.clouds=openstack -DstubResultCode=0 -Dstub.responseTimeInSeconds=1
             
   3.3. restart inductor
             su -l ooadmin -c "cd /opt/oneops/inductor && inductor restart"