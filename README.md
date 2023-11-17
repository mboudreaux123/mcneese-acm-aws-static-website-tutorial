# AWS static website tutorial
A tutorial on how to host a static website on Amazon Simple Storage Service (S3) on Amazon Web Servies (AWS).

This was made as a presentation for the McNeese ACM student chapter on 9/8/2023.

Live example: http://acm-static-website.s3-website-us-east-1.amazonaws.com/

Edit the code on CodePen: https://codepen.io/mboudreaux/pen/jOXBERL

## 0. Preparation
You can upload your own HTML and CSS files, just be sure to have at the minimum a HTML file to follow along.

This repository includes "index.html" and "style.css" if you would rather use a premade example.

Download the files of you choosing, either your own or both the HTML and CSS files included in this repository to your computer.

## 1. Create an Amazon Web Services (AWS) account

## 2. Create an Amazon Simple Storage Service (S3) bucket
Navigate to the Amazon S3 dashboard, or follow the link: https://s3.console.aws.amazon.com/s3/buckets.

When creating a bucket, keep all setting default except for the following:

For the "**Bucket Name**", enter a name that you would like to assign to our bucket. Note: Names are globaly unique, such as a username.

Under "**Block Public Access settings for this bucket**", uncheck the "**Block _all_ public access**" checkbox.

Underneath "**Block Public Access settings for this bucket**", there is a message box to acknowledge that the bucket is public and all files can be access by a URL on the internet.

Check the box that states "**I acknowledge that the current settings might result in this bucket and the objects within becoming public.**".

Optional: Enable "**Bucket Versioning**" to keep the previous versions of files as a backup. Note: This will cost extra money.

To finalize the creation of the bucket, click the organge "**Create Bucket**" button at the bottom right of the page.

## 3. Upload HTML and CSS files to the S3 bucket

Select the bucket that you just created. You will be redirected to the dashboard for your S3 bucket.

To upload files, drag the HTML and CSS files from your computer to the S3 bucket dashbaord, or select "**Upload**" to pick a file on your computer.

You should now be able to see the names of the files in the S3 bucket, but will not be able to access them.

## 4. Enable public access to all files in the S3 bucket

Go back the the S3 dashboard for your particular bucket.

Click on the "**Permissions**" tab to edit the bucket permissions.

Go to the "**Bucket policy**" section and click the "**Edit**" button located to the right.

In the textbox, put the following bucket policy to allow all object to be accessible through the internet.
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "StaticWebsitePublicRead",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::your-s3-bucket-name/*"
        }
    ]
}
```

Note: Change "your-s3-bucket-name" under Resource to the name of the bucket you created.

Once saved, you should now be able to access the files through the URL.

## 5. Redirect default URL to index page

Go back the the S3 dashboard for your particular bucket.

Click on the "**Properties**" tab to edit the bucket permissions.

Go to the "**Static website hosting**" section and click the "**Edit**" button to the right.

When prompted, Enable Static website hosting. Additonal settings will appear.

Navigate to "**Index document**" and in the text box underneath it, type "index.html" or whatevery your html file is named.

Click on the orange "**Save Changes**" button at the bottom right of the webpage.

You are now able to access the website using the Amazon S3 URL

# References

Hosting a static website using Amazon S3:

https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html

# Resources

Generate gradients:

https://cssgradient.io/

Generate glass effect:

https://css.glass/

Generate text for troubleshooting:

https://loremipsum.io/generator/


