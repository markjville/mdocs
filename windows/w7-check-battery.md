# How to check your laptop battery health in Windows 7

1. Open cmd.exe as administrator

2. Run: `cd %userprofile%/Desktop `
-This is where the report `.html` file will be generated.

3. Run: `powercfg -energy `
-This will run a test for 60 seconds and generate a report.

4. Open the generated html file on the Desktop and scroll down to "Battery:Battery Infomation". Compare the two numbers of "Design Capacity" and "Last Full Charge". The difference between the two shows by how much the battery has degraded.
