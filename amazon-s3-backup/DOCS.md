# Home Assistant Add-on: Amazon S3 Backup

## Installation

Follow these steps to get the add-on installed on your system:

1. Enable **Advanced Mode** in your Home Assistant user profile.
2. Navigate in your Home Assistant frontend to **Supervisor** -> **Add-on Store**.
3. Find the "Amazon S3 Backup" add-on and click it.
4. Click on the "INSTALL" button.

## How to use

1. Set the `aws_access_key`, `aws_secret_access_key`, `bucket_name`, `bucket_region`, and `storage_class` configuration options.
2. Start the add-on.

## Configuration

Example add-on configuration:

```
log_level: debug
aws_access_key: XXXXXXXXXXXXXXXX
aws_secret_access_key: XXXXXXXXXXXXXXXX
bucket_name: my-bucket
bucket_region: us-east-1
storage_class: STANDARD
upload_missing_files: false
keep_local_snapshots: 2
```

### Option: `log_level`
Log output level for this addon.

### Option: `aws_access_key` (required)
AWS IAM access key used to access the S3 bucket.

### Option: `aws_secret_access_key` (required)
AWS IAM secret access key used to access the S3 bucket.

### Option: `bucket_name` (required)
Amazon S3 bucket used to store backups.

### Option: `bucket_region` (required)
AWS region where the S3 bucket was created. (us-east-1|us-east-2|us-west-1|us-west-2|ca-central-1|eu-west-1|eu-central-1|eu-west-2|eu-west-3|ap-southeast-1|ap-southeast-2|ap-northeast-2|ap-northeast-1|ap-south-1|sa-east-1)

### Option: `storage_class` (required)
Amazon S3 storage class to use when uploading files to S3. (STANDARD|REDUCED_REDUNDANCY|STANDARD_IA|ONEZONE_IA|INTELLIGENT_TIERING|GLACIER|DEEP_ARCHIVE)

### Option: `upload_missing_files`
Upload files to S3 that exist in the Home Assistant backup directory but not in S3. The addon checks for a matching file name and file size. If the file size differs, the addon will assume the file on S3 is corrupt and upload the file again.

### Option: `keep_local_snapshots`
Number of local snapshots to keep. Snapshots are pruned after a successful snapshot upload to S3.

## Support

Usage of the addon requires knowledge of Amazon S3 and AWS IAM.