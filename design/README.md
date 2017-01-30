# Overview

This design yaml files can be used to deploy OneOps like any other application in OneOps.

# Prerequisites

1. Working OneOps.
2. Nexus repository.
3. 

# Setup

1. Load oneops-design.yaml file into design via "Load" button.
2. First validate the yaml design them import.
3. Add below cloud variables:
   1. QUEUE : Location of activemq queues.
   2. nexus: Nexus repo where all component artifacts and depended jar are available,
   3. smtp : SMTP mail server.
4. Edit values for all the global variable with required values mostly database and activemq related user name and passwords.
5. Deploy components from bottom to top as per dependency diagram.
6. 

