# hosting-your-onw-website
## Hosting Your Own Static Website Without Route 53

Imagine a digital space that serves as a window into your creativity, a platform where your ideas, projects, and passions come to life in a beautifully crafted showcase. Hosting your static website grants you the freedom to design, customize, and curate every aspect of your online presence, without the constraints of dynamic content management systems.

With simplicity at its core, hosting a static website empowers you to focus on what truly matters: your content. Whether it’s a personal portfolio, a professional showcase, or a creative endeavor, your static website provides a stable, fast, and secure platform for sharing your story with the world.

Without using Route 53, we can use alternative DNS services or domain registrars to manage domain configurations. These services often provide DNS management tools that allow you to configure DNS records such as A records, CNAME records, and MX records. Additionally, we’ll rely on a hosting provider that supports static website hosting, such as Amazon S3.

## Diagram:
![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/9fb22006-ffea-4035-864d-480d07ee56ff)

## Create Your Website:
Develop your static website using HTML, CSS, and JavaScript on your favorite IDE and save it to your computer. I used VSCode since it’s my favorite.

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/7675732a-a0ba-4125-ae19-eaaae8648ada)

## Create a Domain Name(Optional)
Navigate to the Route 53 Service from the console home page and select register domain. You can then choose an inexpensive domain, like .click, both your domain and your bucket should have the same name.

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/62200000-c2a2-4730-906b-82d32a0a2ef8)

## Create an AWS S3 Bucket
Navigate to S3 and hit “create bucket“ —( give your bucket the same name as your domain “yourbucketname.click“ if you want your own domain) and select a region near you or leave it at the current region. Next, we need to un-check Block all public access, which is on by default. Leave everything else on this page as default. Example below:

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/063c8e11-b753-466a-b101-2f44dbd22164)

## Enable Hosting + Upload your files
Now you’ve created your bucket we need to enable static website hosting. This can be configured at the bottom of the “properties” tab on your main bucket page. Select “Enable” and type “index.html” in the Index document box — “Specify the home or default page of the website” which is index.html.

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/a24a70e2-1b56-4b1e-9e22-0f70732d0d8c)

This is what mine looks like on VSCode as my code editor.
![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/419ceee2-b33a-4a4f-a435-143cf73ec24e)

## Configure Bucket
We now need to add a bucket policy, under the permissions — select edit and paste this JSON in, replacing the Resource with your bucket ARN:

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/35fddc15-4ca4-4002-a5bc-cf65efab79a6)

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::yourbucketname.yourdomain/*"
        }
    ]
}

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/11587047-eaa9-470a-bef4-be2ee9c57844)

## Upload your files by clicking on your AW S3 bucket name and click on “upload”:

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/2e4619ad-ce22-43ab-9d65-413fd1856e90)

Now is the time to view your files. If you upload a folder, you'll see the folder name. For me, it's a folder with multiple files. Click on the folder of the index.html file. See below:

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/821e818e-dd39-4c78-beca-5cc8ccaa23a7)

You now should be able to see all files. Now you have a lot of options t view the site. DO NOT SELECT ALL FILES! This will open multiple browsers. You need to select only "index.html" and either copy the URL, open URL to your default browser.

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/829cbaab-88cd-4bd1-95e1-14ce396c4e02)

Index.html: You may click on the index file to see the full URL:

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/4c9a6548-4a64-41e1-a654-92c17f985fea)

## Congrats!
Now when we visit the URL in our browser, we should see the website: https://mybucketsclick.s3.amazonaws.com/PORTFOLIO/index.html

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/8d82d30c-9105-494a-a19f-9205932f9c7c)

![image](https://github.com/JohnnyLouisTech/hosting-your-onw-website/assets/29494723/3ce7e5d8-74d9-4059-ac27-f0f2ca553115)

This was the basic route to build a static website,  and deploy it to Amazon using S3 with no Route 53 involved.


































