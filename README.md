import boto3
import json

aws_access_key_id = 'AKIAQYLPMN5HIUI65MP3'
aws_secret_access_key = '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'
region = 'us-east-2'

session = boto3.Session(
    aws_access_key_id=aws_access_key_id,
    aws_secret_access_key=aws_secret_access_key,
    region_name=region
)

s3 = session.resource('s3')

try:
    response = []
    for bucket in s3.buckets.all():
        response.append(bucket.name)
    print(json.dumps(response))
except Exception as e:
    print(f"Error: {e}")
