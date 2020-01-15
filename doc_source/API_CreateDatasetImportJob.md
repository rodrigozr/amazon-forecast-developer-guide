# CreateDatasetImportJob<a name="API_CreateDatasetImportJob"></a>

Imports your training data to an Amazon Forecast dataset\. You provide the location of your training data in an Amazon Simple Storage Service \(Amazon S3\) bucket and the Amazon Resource Name \(ARN\) of the dataset that you want to import the data to\.

You must specify a [DataSource](API_DataSource.md) object that includes an AWS Identity and Access Management \(IAM\) role that Amazon Forecast can assume to access the data\. For more information, see [Set Up Permissions for Amazon Forecast](aws-forecast-iam-roles.md)\.

The training data must be in CSV format\. The delimiter must be a comma \(,\)\.

You can specify the path to a specific CSV file, the S3 bucket, or to a folder in the S3 bucket\. For the latter two cases, Amazon Forecast imports all files up to the limit of 10,000 files\.

To get a list of all your dataset import jobs, filtered by specified criteria, use the [ListDatasetImportJobs](API_ListDatasetImportJobs.md) operation\.

## Request Syntax<a name="API_CreateDatasetImportJob_RequestSyntax"></a>

```
{
   "[DatasetArn](#forecast-CreateDatasetImportJob-request-DatasetArn)": "string",
   "[DatasetImportJobName](#forecast-CreateDatasetImportJob-request-DatasetImportJobName)": "string",
   "[DataSource](#forecast-CreateDatasetImportJob-request-DataSource)": { 
      "[S3Config](API_DataSource.md#forecast-Type-DataSource-S3Config)": { 
         "[KMSKeyArn](API_S3Config.md#forecast-Type-S3Config-KMSKeyArn)": "string",
         "[Path](API_S3Config.md#forecast-Type-S3Config-Path)": "string",
         "[RoleArn](API_S3Config.md#forecast-Type-S3Config-RoleArn)": "string"
      }
   },
   "[TimestampFormat](#forecast-CreateDatasetImportJob-request-TimestampFormat)": "string"
}
```

## Request Parameters<a name="API_CreateDatasetImportJob_RequestParameters"></a>

The request accepts the following data in JSON format\.

 ** [DatasetArn](#API_CreateDatasetImportJob_RequestSyntax) **   <a name="forecast-CreateDatasetImportJob-request-DatasetArn"></a>
The Amazon Resource Name \(ARN\) of the Amazon Forecast dataset that you want to import data to\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `^[a-zA-Z0-9\-\_\.\/\:]+$`   
Required: Yes

 ** [DatasetImportJobName](#API_CreateDatasetImportJob_RequestSyntax) **   <a name="forecast-CreateDatasetImportJob-request-DatasetImportJobName"></a>
The name for the dataset import job\. We recommend including the current timestamp in the name, for example, `20190721DatasetImport`\. This can help you avoid getting a `ResourceAlreadyExistsException` exception\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 63\.  
Pattern: `^[a-zA-Z][a-zA-Z0-9_]*`   
Required: Yes

 ** [DataSource](#API_CreateDatasetImportJob_RequestSyntax) **   <a name="forecast-CreateDatasetImportJob-request-DataSource"></a>
The location of the training data to import and an AWS Identity and Access Management \(IAM\) role that Amazon Forecast can assume to access the data\. The training data must be stored in an Amazon S3 bucket\.  
If encryption is used, `DataSource` must include an AWS Key Management Service \(KMS\) key and the IAM role must allow Amazon Forecast permission to access the key\. The KMS key and IAM role must match those specified in the `EncryptionConfig` parameter of the [CreateDataset](API_CreateDataset.md) operation\.  
Type: [DataSource](API_DataSource.md) object  
Required: Yes

 ** [TimestampFormat](#API_CreateDatasetImportJob_RequestSyntax) **   <a name="forecast-CreateDatasetImportJob-request-TimestampFormat"></a>
The format of timestamps in the dataset\. The format that you specify depends on the `DataFrequency` specified when the dataset was created\. The following formats are supported  
+ "yyyy\-MM\-dd"

  For the following data frequencies: Y, M, W, and D
+ "yyyy\-MM\-dd HH:mm:ss"

  For the following data frequencies: H, 30min, 15min, and 1min; and optionally, for: Y, M, W, and D
If the format isn't specified, Amazon Forecast expects the format to be "yyyy\-MM\-dd HH:mm:ss"\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `^[a-zA-Z0-9\-\:\.\,\'\s]+$`   
Required: No

## Response Syntax<a name="API_CreateDatasetImportJob_ResponseSyntax"></a>

```
{
   "[DatasetImportJobArn](#forecast-CreateDatasetImportJob-response-DatasetImportJobArn)": "string"
}
```

## Response Elements<a name="API_CreateDatasetImportJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [DatasetImportJobArn](#API_CreateDatasetImportJob_ResponseSyntax) **   <a name="forecast-CreateDatasetImportJob-response-DatasetImportJobArn"></a>
The Amazon Resource Name \(ARN\) of the dataset import job\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `^[a-zA-Z0-9\-\_\.\/\:]+$` 

## Errors<a name="API_CreateDatasetImportJob_Errors"></a>

 **InvalidInputException**   
We can't process the request because it includes an invalid value or a value that exceeds the valid range\.  
HTTP Status Code: 400

 **LimitExceededException**   
The limit on the number of resources per account has been exceeded\.  
HTTP Status Code: 400

 **ResourceAlreadyExistsException**   
There is already a resource with this name\. Try again with a different name\.  
HTTP Status Code: 400

 **ResourceInUseException**   
The specified resource is in use\.  
HTTP Status Code: 400

 **ResourceNotFoundException**   
We can't find a resource with that Amazon Resource Name \(ARN\)\. Check the ARN and try again\.  
HTTP Status Code: 400

## See Also<a name="API_CreateDatasetImportJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/forecast-2018-06-26/CreateDatasetImportJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/forecast-2018-06-26/CreateDatasetImportJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/forecast-2018-06-26/CreateDatasetImportJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/forecast-2018-06-26/CreateDatasetImportJob) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/forecast-2018-06-26/CreateDatasetImportJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/forecast-2018-06-26/CreateDatasetImportJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/forecast-2018-06-26/CreateDatasetImportJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/forecast-2018-06-26/CreateDatasetImportJob) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/forecast-2018-06-26/CreateDatasetImportJob) 