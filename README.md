prereq:

https://community.vtiger.com/help/vtigercrm/administrators/installation.html

### Run the stack locally

    sh runme

### Connect to tiger container

    docker exec -it containerid  bash

    rm -rf /var/www/localhost/htdocs/
    cd /var/www/localhost
    wget https://phoenixnap.dl.sourceforge.net/project/vtigercrm/vtiger%20CRM%207.1.0/Core%20Product/vtigercrm7.1.0.tar.gz
    tar xzf vtigercrm7.1.0.tar.gz --directory /var/www/localhost/
    chown -R apache:apache /var/www/localhost/vtigercrm
    mv /var/www/localhost/vtigercrm /var/www/localhost/htdocs
    rm vtigercrm7.1.0.tar.gz

### Tiger complains

MySQL Server should be configured with:
sql_mode = ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION

set global sql_mode="ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION";
use tiger;
ALTER DATABASE tiger CHARACTER SET utf8 COLLATE utf8_general_ci;

Fatal error: Uncaught Error: Call to undefined function simplexml_load_file() in /var/www/localhost/htdocs/vtlib/Vtiger/PackageImport.php:54 Stack trace: #0 /var/www/localhost/htdocs/vtlib/Vtiger/PackageImport.php(195): Vtiger_PackageImport->\_\_parseManifestFile(Object(Vtiger_Unzip)) #1 /var/www/localhost/htdocs/vtlib/Vtiger/PackageImport.php(281): Vtiger_PackageImport->checkZip('packages/vtiger...') #2 /var/www/localhost/htdocs/modules/Install/models/Utils.php(473): Vtiger_PackageImport->getModuleNameFromZip('packages/vtiger...') #3 /var/www/localhost/htdocs/modules/Install/views/Index.php(204): Install_Utils_Model::installModules() #4 /var/www/localhost/htdocs/modules/Install/views/Index.php(70): Install_Index_view->Step7(Object(Vtiger_Request)) #5 /var/www/localhost/htdocs/includes/main/WebUI.php(215): Install_Index_view->process(Object(Vtiger_Request)) #6 /var/www/localhost/htdocs/index.php(20): Vtiger_WebUI->process(Object(Vtiger_Request)) #7 {main} thrown in /var/www/localhost/htdocs/vtlib/Vtiger/PackageImport.php on line 54
