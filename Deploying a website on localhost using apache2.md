# Assignment-on-Networking-and-Servers
# Step 1:
# Check for running status of Apache2
$ sudo systemctl status apache2
# start apache2, if inactive
$ sudo start apache2
# Check for running status of Apache2
$ sudo systemctl status apache2
#Step 2:
# Setting-up of Virtual host and DNS name (awesomeweb)
# Need to edit the /etc/hosts File
$ sudo nano /etc/hosts
# add 127.0.0.1   awesomeweb
# Step 3: 
# Create a html file for awesomeweb
$ sudo mkdir /var/www/awesomeweb
# grant necessary permissions
$ sudo chown -R $USER:$USER /var/www/awesomeweb
$ sudo chmod -R 755 /var/www/awesomeweb
# Step 4:
# Create a simple html file 
$ sudo nano index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AwesomeWeb</title>
</head>
<body>
    <h1>Welcome to AwesomeWeb!</h1>
    <p>This is your website deployed locally.</p>
</body>
</html>
# Cntl+x, Y and then enter (save the file)

# Step 5:
# Configure Apache to Serve Website
$ sudo nano /etc/apache2/sites-available/awesomeweb.conf
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName awesomeweb
    DocumentRoot /var/www/awesomeweb
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
# Cntl+x, Y and then enter (save the file)
Step 6:
# Enabling the new site and disable the default
$ sudo a2ensite awesomeweb.conf
$ sudo a2dissite 000-default.conf
$ sudo systemctl reload apache2

#Accessing Website
Open a browser and type http://awesomeweb




