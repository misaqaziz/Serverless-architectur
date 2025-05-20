import boto3
from botocore.exceptions import ClientError

s3 = boto3.client('s3')
BUCKET_NAME = 'misaq'  # Updated bucket name
VIDEO_KEY = 'Mohammed Siraj s 6_21 _ Super11 Asia Cup 2023 _ Final _ India vs Sri lanka.mp4'  # Updated video file name

def lambda_handler(event, context):
    try:
        # Generate a pre-signed URL that expires in 1 hour
        presigned_url = s3.generate_presigned_url(
            'get_object',
            Params={
                'Bucket': BUCKET_NAME,
                'Key': VIDEO_KEY
            },
            ExpiresIn=3600  # 1 hour expiration
        )
        
        # Redirect to the pre-signed URL
        return {
            'statusCode': 302,
            'headers': {
                'Location': presigned_url
            },
            'body': ''
        }
        
    except ClientError as e:
        return {
            'statusCode': 500,
            'body': f"S3 Error: {str(e)}"
        }
    except Exception as e:
        return {
            'statusCode': 500,
            'body': f"Error: {str(e)}"
        }
