# HelloWorldAWS

Setting up a Hello World page on Amazon AWS

1. Set up AWS instance (time:10 minutes)
  1. prerequisites: amazon account, credit card (nothing will be charged to it), phone
  2. useful tutorials: 
    * http://docs.aws.amazon.com/quickstarts/latest/vmlaunch/step-1-launch-instance.html (main tutorial)
    * http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html (how to change and edit security groups)
  
  * Follow the turorial all the way through to create a new AWS instace.  For this example, when it was time to choose what kind of instance to create, I chose 'Ubuntu'
  * Create new security group. (see security group tutorial).  Note: I set up my security group to allow all traffic from anywhere.
  * Change Security group for the AWS instance to the newly created security group.

  *  Once the instance is created, from the EC2 Manager portal, the 'connect' button at the top of the page has great info on SSHing into your instance.
  *  SSH into instance

2. Set up GOT (time: 15 minutes)
  1. prerequisites: github account
  2. useful tutorials: 
    * all git-hub documentation
    * https://help.github.com/articles/set-up-git/#platform-linux
    * https://help.github.com/articles/create-a-repo/
    * https://help.github.com/articles/caching-your-github-password-in-git/
 
  * Once a successful SSH connection has been opened to the instance, download git (sudo apt-get install git)
  * Create a new GIT repository.  Set up the Git repo on the AWS instance

3. Set up Flask (time: 40 minutes)
  1. useful tutorials: 
    * http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world
 
  * This tutorial is pretty great and straightforward.  However, in order to connect to the hello world app running on the AWS machine, Flask has to be set to listen from anywhere. (this gotcha took me a while to figure out!)
  * The line "app.run(debug=True)" in run.py should be changed to "app.run(debug=True, host='0.0.0.0')"
  * Once that is done, you can connect to your AWS instance on Port 5000 and see the newly created Hello World program.
  
4. Set up S3 Bucket, and render an HTML template in Flask. (time: 40 minutes) (Time sink was mostly red herring research about rendering images with Flask and S3.  In the end I just uploaded an image to a new S3 bucket, and used an HTML template to render it with Flask.)
  1. useful tutorials: 
    * http://docs.aws.amazon.com/AmazonS3/latest/gsg/CreatingABucket.html
    * http://docs.aws.amazon.com/AmazonS3/latest/gsg/PuttingAnObjectInABucket.html
    * http://docs.aws.amazon.com/AmazonS3/latest/gsg/OpeningAnObject.html
    * http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-ii-templates
  
  * Set up an Amazon s3 Bucket and upload an image.  Don't forget to make the image public! (tutorial on creating an image is pretty straightforward.
  * The Flask tutorial does a great job of explaining templates.  Follow the tutorial to create the example template.  From there, add an img tag and point it to the S3 hosted image.  Add a width and height parameter to the image to not have it 'explode' the page.
  
5. Document (time: 20 minutes)
  * To view into the Hello World page
    * SSH into the AWS instance (See Step 1 about setting up AWS instance) and execute ./run.py
    * go to this link: http://ec2-52-32-64-220.us-west-2.compute.amazonaws.com:5000
  * To edit the Hello World page
    * On the instance, Edit the /home/ubuntu/app/templates/index.html file 
