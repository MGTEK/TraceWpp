# Visual Studio Build Customization Files for WPP Tracing

To make [WPP software tracing](https://docs.microsoft.com/en-us/windows-hardware/drivers/devtest/wpp-software-tracing) available to WIN32 user mode applications, we created a [build customization](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-create-and-remove-project-dependencies) that enables you to use WPP software tracing in a WIN32 C/C++ project.

You will find a user mode and kernel mode example for WPP tracing in the **[TraceView Plus](https://www.mgtek.com/traceview)** examples folder at **C:\Program Files\MGTEK\TraceView\Examples**.

## Set up a Windows Desktop project for WPP

- Right-click a project in **Solution Explorer**.
- From the menu **Build Dependencies**, select **Build Customizations**.
- Click **Find Existing...** and point Visual Studio to **TraceWpp.targets**.
- Ensure that the checkbox on **TraceWpp** is checked and click **OK**.
- Now, you can open the **Property** dialog of your project and customize WPP under **WPP Tracing**. When you build your project, the WPP preprocessor will run and generate the .tmh trace message header files.

Note 1): The *Tracewpp.exe* tool is typically included with the **Windows SDK**. However, the WPP configuration files (from the WppConfig\Rev1 folder) are part of the **Windows WDK**, which must be installed also.

Note 2): If the tracewpp.exe tool cannot find *defaultwpp.ini*, you need to point the tool to these files. To do this, open the Property pages of your project, select the node **WPP Tracing / File Options** and change **Configuration Directories** to **C:\Program Files (x86)\Windows Kits\10\bin\WppConfig\Rev1**. Note that the tracewpp.exe tool must match the version of the WPP configuration files. If tracewpp.exe gives you configuration errors, search for **defaultwpp.ini** in the WDK directory and provide the proper configuration folder.
