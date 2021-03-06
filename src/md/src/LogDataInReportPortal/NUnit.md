### NUnit

#### Installation

There are 2 ways to install NUnit add-in's. The first way directs you to
install the add-in for NUnit runner, the second is only for assembly with
tests. This way, the test results will be reported to ReportPortal if the tests 
are executed by NUnit runner with installed add-in, or only if a specific test
assembly is executed and is not depend on what NUnit runner is used.

#### Windows Installer Package

To download the latest [Windows Installer package](https://www.nuget.org/packages/ReportPortal.Client/) package on your machine follow these instructions during installation.

>   **Warning!**

>   First you must install the add-in into the *bin/addins* folder that is located in the
>   folder where NUnit (nunit.exe) runner is.

>   Example: *C:\\Program Files (x86)\\NUnit 2.6.4\\bin\\addins*

When th installation process is completed, please verify that the add-in is installed
successfully. Execute NUnit GUI runner, go to menu *Tools -\> Addins*.

[ ![Image](Images/NUnit_1.png) ](Images/NUnit_1.png)

[ ![Image](Images/NUnit_2.png) ](Images/NUnit_2.png)

If add-in is successfully loaded beginning from now all tests that will be
executed by this NUnit runner (exe) will be represented on ReportPortal.

#### NuGet Package

Install **ReportPortal.NUnit** NuGet package into your project with features
files. Missed dependencies will be installed automatically.

>   Read [here](<http://docs.nuget.org/consume/package-manager-dialog>) how to
>   manage NuGet packages.

NuGet package is compatible only with NUnit runner **v2.6.4**. This limitation is
related to NUnit architecture restrictions. If you use some other version of
NUnit launcher and you are not able to upgrade/downgrade to v2.6.4, please
contact us and we will provide compatible NuGet package with NUnit runner which
you can use.

#### Configuration

You can configure ReportPortal plugin. All settings are stored in
*EPAM.ReportPortal.Addins.NUnit.dll.config* file. You can find this file by path
where you installed add-in: installation path of MSI package or in VS project in
other case.

| **Property**             | **Description**      |
|--------------------------|----------------------|
| enabled                  |Enable/Disable reporting to ReportPortal server. |
| server - url             |The base URI to Report Portal REST web service. |
| server - project         |Name of project |
| server - proxy - server  |Proxy server for all requests to ReportPortal services. This element is optional. |
| authentication - username|Name of user. |
| authentication - password|Password of user. UID can be used instead of opened password. You can find it on user's profile page. |
| launch - debugMode       |Turn on/off debugging of your tests. Only you have access for test results if test execution is proceeded in debug mode. |
| launch - name            |Name of test execution. |
| launch - tags            |Comma separated tags for test execution. |
| logConsoleOutput         |Specify whether console output also should be reported |


See example of valid configuration file below.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ xml
<configuration>
  <configSections>
    <section name="reportPortal" type="EPAM.ReportPortal.Addins.NUnit.ReportPortalSection, EPAM.ReportPortal.Addins.NUnit, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
  </configSections>
  <reportPortal enabled="true" logConsoleOutput="true">
    <server url="https://{HOST}:{PORT}/api/v1/" project="default_project">
      <authentication username="default" password="1q2w3e" />
      <proxy server="yourproxy.com:port"/>
    </server>
    <launch name="NUnit Demo Launch" debugMode="true" tags="t1,t2" />
  </reportPortal>
</configuration>
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
