### Hi there. ✨ Welcome to my GitHub!_👋👋👋

<img src="https://github-readme-stats.vercel.app/api?username=NghiaPhamQn&show_icons=true&include_all_commits=true">


#### Build Jenkin BE
```bash
cd "C:\Windows\System32\config\systemprofile\AppData\Local\Jenkins\.jenkins\workspace\HRM_API"
dotnet publish -c=Release
cd C:\Windows\System32\inetsrv
%SYSTEMROOT%\System32\inetsrv\appcmd stop apppool /apppool.name:"HRMAPI"
%SYSTEMROOT%\System32\inetsrv\appcmd stop site /site.name:"HRMAPI"
del /F /Q C:\Deploy\API\HRMAPI
%systemroot%\System32\xcopy /y "C:\Windows\System32\config\systemprofile\AppData\Local\Jenkins\.jenkins\workspace\HRM_API\bin\Release\net5.0\publish" C:\Deploy\API\HRMAPI /e /o /x /c /h /k
%systemroot%\System32\xcopy /y C:\Deploy\API\HRMAPI\appsettings C:\Deploy\API\HRMAPI /e /o /x /c /h /k
%systemroot%\System32\xcopy /y "C:\Windows\System32\config\systemprofile\AppData\Local\Jenkins\.jenkins\workspace\HRM_API\bin\Release\WebAPI.xml" C:\Deploy\API\HRMAPI /o /x /c /h /k
%SYSTEMROOT%\System32\inetsrv\appcmd start apppool /apppool.name:"HRMAPI"
%SYSTEMROOT%\System32\inetsrv\appcmd start site /site.name:"HRMAPI"
```

#### Build Jenkin FE
////////Step 1
```bash
cd "C:\Windows\System32\config\systemprofile\AppData\Local\Jenkins\.jenkins\workspace\HRM_FE"
node --max_old_space_size=8048 ./node_modules/@angular/cli/bin/ng build
```
////////Step 2
```bash
cd C:\Windows\System32\inetsrv
%SYSTEMROOT%\System32\inetsrv\appcmd stop apppool /apppool.name:"HRMFE_DEV"
%SYSTEMROOT%\System32\inetsrv\appcmd stop site /site.name:"HRMFE_DEV"
del /F /Q C:\Deploy\WEB\HRMFE_DEV
%systemroot%\System32\xcopy /y "C:\Windows\System32\config\systemprofile\AppData\Local\Jenkins\.jenkins\workspace\HRMFE_DEV\dist\HRM-FE" C:\Deploy\WEB\HRMFE_DEV /e /o /x /c /h /k
%SYSTEMROOT%\System32\inetsrv\appcmd start apppool /apppool.name:"HRMFE_DEV"
%SYSTEMROOT%\System32\inetsrv\appcmd start site /site.name:"HRMFE_DEV"
```

