Update Site URL:
https://github.com/hengsin/headless/raw/master/4.5

Director:
https://github.com/hengsin/headless/raw/master/director_latest.zip

Jenkin Installation:
- Install Buckminster plugin
- Download https://raw.githubusercontent.com/hengsin/headless/master/4.5/buckminster.json to JENKIN_HOME/userContent/buckminster
- Manage Jenkins > Reload Configuration from Disk
- Manage Jenkins > Global Tool Configuration > Buckminster installations. Select Install automatically and Version Buckminster 4.5 ( should be the only version available )

Project Configurations > Build > Run Buckminster > Commands:

importtargetdefinition -A '${WORKSPACE}/org.adempiere.sdk-feature/build-target-platform.target'

import -P '${WORKSPACE}/org.adempiere.sdk-feature/materialize.properties' '${WORKSPACE}/org.adempiere.sdk-feature/adempiere.cquery'

build -t

perform -D qualifier.replacement.*=generator:buildTimestamp -D generator.buildTimestamp.format=\'v\'yyyyMMdd-HHmm -D target.os=*   -D target.ws=*   -D target.arch=* -D product.features=org.idempiere.eclipse.platform.feature.group -D product.profile=DefaultProfile -D product.id=org.adempiere.server.product   'org.adempiere.server:eclipse.feature#site.p2'

