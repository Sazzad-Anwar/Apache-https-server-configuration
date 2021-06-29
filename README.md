<p align="center">
  <img src="./apache_logo.svg"
</p>

<h1 align="center">Apache Https Server Configuration</h1>

### To point the `https` of node application in a LAMP stack server add the below code in `.htaccess` file in application's root directory

```php
RewriteOptions inherit
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]

# php -- BEGIN cPanel-generated handler, do not edit
# Set the “ea-php73” package as the default “PHP” programming language.
<IfModule mime_module>
  AddHandler application/x-httpd-ea-php73 .php .php7 .phtml
</IfModule>
# php -- END cPanel-generated handler, do not edit
```

### You can copy the code or download the file of `.htaccess` and include into your application

<p align="center">
  <img src="./deploy.png" height="80" width="auto" style="margin-top: 5rem" />
</p>

<h1 align="center">Auto Deploy in Hosting Server using GIT version control</h1>

### Steps To Do It

- Create a git repository of project.
- Push it to github.
- Go to CPanel Search for git and create a repository directory.
- Clone the github project through input the link.
- Set the repository name.
- Press create.

#### The repository will be clone to the directory that has been mentioned top

- Open the repository folder.
- Enter into `.git` folder and enter into it.
- Find the `hooks` folder and enter into it.
- Find the `post-receive` file and edit it as below and save.

```sh
  #!/bin/sh

  while read oldrev newrev ref
  do
    branch=`echo $ref | cut -d/ -f3`

    if [ "master" == "$branch" ]; then
      git --work-tree=[write the directory path of your project] checkout -f $branch
      echo 'Changes pushed live.'
    fi

    if [ "dev" == "$branch" ]; then
      git --work-tree=[write the directory path of your project] checkout -f $branch
      echo 'Changes pushed to dev.'
    fi
  done

```

#### After that whenever new updates are pushed to github, the CPanels repository can be updated by pulling the repo
