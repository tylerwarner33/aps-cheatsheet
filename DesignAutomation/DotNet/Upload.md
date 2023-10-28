## Upload
How to upload files to OSS bucket (Data Management API) using the SDK.

### Upload Empty Files
```csharp
ObjectsApi objectsApi = new();
objectsApi.Configuration.AccessToken = token;
List<UploadItemDesc> uploadResults = await objectsApi.uploadResources(bucketKey, new List<UploadItemDesc> {
    new UploadItemDesc(objectKey1, " "),
    new UploadItemDesc(objectKey2, " "),
    new UploadItemDesc(objectKey3, " ")
  });

foreach (var result in uploadResults)
{
  if (result.Error)
  {
    throw new Exception(result.completed.ToString());
  }
  
  var json = result.completed.ToJson();
  ObjectDetails objectDetails = json.ToObject<ObjectDetails>();
  string objectId = objectDetails.ObjectId;
}
```
References: [#1](https://aps.autodesk.com/blog/direct-s3-upload-and-download-sdks), [#2](https://github.com/Autodesk-Forge/forge-api-dotnet-client/blob/v1.9.7/src/Autodesk.Forge/Api/ObjectsApi.cs#L4818-L4840), [#3](https://aps.autodesk.com/blog/direct-s3-net-samples), [#4](https://github.com/Autodesk-Forge/design.automation-nodejs-revit.parameters.excel/blob/master/routes/da4revit.js#L99)


### Upload Existing Files
```csharp
ObjectsApi objectsApi = new();
objectsApi.Configuration.AccessToken = token;
List<UploadItemDesc> uploadResults = await objectsApi.uploadResources(bucketKey, new List<UploadItemDesc> {
    new UploadItemDesc(objectKey1, await System.IO.File.ReadAllBytesAsync(filePath1)),
    new UploadItemDesc(objectKey2, await System.IO.File.ReadAllBytesAsync(filePath2)),
    new UploadItemDesc(objectKey3, await System.IO.File.ReadAllBytesAsync(filePath3))
  });

foreach (var result in uploadResults)
{
  if (result.Error)
  {
    throw new Exception(result.completed.ToString());
  }
  
  var json = result.completed.ToJson();
  ObjectDetails objectDetails = json.ToObject<ObjectDetails>();
  string objectId = objectDetails.ObjectId;
}
```
References: [#1](https://aps.autodesk.com/blog/direct-s3-upload-and-download-sdks), [#2](https://github.com/Autodesk-Forge/forge-api-dotnet-client/blob/v1.9.7/src/Autodesk.Forge/Api/ObjectsApi.cs#L4818-L4840), [#3](https://aps.autodesk.com/blog/direct-s3-net-samples), [#4](https://tutorials.autodesk.io/tutorials/design-automation/execute-workitem)
