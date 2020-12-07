+++
title =  "Enabling SAP Web GUI"
date =  2020-11-07T19:01:00+01:00
description = ""
author = "Odinei Alexandre"
+++

* Open transaction SICF and Activate the nodes:

```
/default_host/sap/bc/gui/sap/its/webgui 
/default_host/sap/public/bc/ur
/default_host/sap/public/bc/its/mimes
```

* Open SE80 and update WEBGUI adding value 1 to ~WEBGUI

* Open TCOde RZ10
```
login/accept_sso2_ticket = 1
login/create_sso2_ticket = 2
```

* Run transaction code SIAC_PUBLISH_ALL_INTERNAL to activate the services

* Now, just open in the browser: ip_address:port number/sap/bc/gui/sap/its/webgui