# Generate hardware condition report, showing battery condition.

1. Open elevated cmd prompt
2. `cd %userprofile%/Desktop`
3. `powercfg -energy`
4. After 60 seconds, an html file will be generated on the current user’s Desktop.

*Note:* Battery condition is near bottom of the report. Compare the designed capacity with the last full charge.
