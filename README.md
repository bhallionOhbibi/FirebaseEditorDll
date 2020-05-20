# FirebaseEditorDll
Custom Firebase.Editor.dll without freeze when pressing play

# What was done:

- replace the following lines in GenerateXmlFromGoogleServicesJson.cctor() 
```
RunOnMainThread.Run(delegate
{
	GenerateXmlFromGoogleServicesJson.CheckConfiguration();
}, false);
```
with:
```
if (!EditorApplication.isPlayingOrWillChangePlaymode)
{
	RunOnMainThread.Run(delegate
	{
		GenerateXmlFromGoogleServicesJson.CheckConfiguration();
	}, false);
}
```
