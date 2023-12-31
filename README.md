# Sentry Backup To S3

This script uses docker UNIX socket for backing up sentry volumes and uploads them to a S3 Compatible Object Store.   

## How To Use

1. Clone this repo

1. Install dependencies. \
    `pip install -r requirements.txt`

1. Create an .env file, at the root of project, according to example provided

1. Run \
    `./backup_scrpt.py`

## Configuration

Arguments can be given to script or can be put on .env file. Script arguments have more Priority than envs.

Used in Backup | Used in Restore | Env | Argument | Alias | Description
---- | ---- | ----|--------|------| ----------
&check; | &check; | S3_ACCESS_KEY | --access-key | -u | Access key for s3
&check; | &check;  | S3_SECRET_KEY | --secret-key | -p | Secret key for s3
&check; | &check;  | S3_BUCKET | --bucket | -b | Bucket of s3
&check; | &check;  | S3_PATH_PREFIX | --prefix | -a | Prefix to add to upload path
&check; | &check;  | S3_ENDPOINT | --s3-endpoint | -e | Endpoint to use for s3. __*Note*__: if not provided volume backup are only compressed in backup folder and other s3 args are ignored
&check; | &check;  | BACKUP_FOLDER | --backup-folder | Local backup file location
&check; | &cross;  |  _ | --remove-files | -r | Whether to remove local files after upload or not. Ignored if s3 endpoint is not defined. default: `False`
&cross; | &check;  | _ | --datetime | -d | What datetime to restore. format: '%Y-%m-%dT%H:%M:%S'. example: '2023-02-03T10:01:05'
