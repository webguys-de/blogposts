Title: Türchen 3 : Automated Deployment with deployer.org

----

Date: 2016-12-03

----

Author: Kevin Krieger

----

Author-Text:  Kevin Krieger is a computer scientist, freelancer and volunteer. He is working as Magento freelancer since 2015, previously as web developer frontend/backend in various projects. His first experience with magento was in 2008. He likes to attend and organize barcamps like [SaarCamp](https://saarcamp.org/") and [CoderDojo Saar](http://coderdojo-saar.de/). Find out more about him on his [blog](https://kkrieger.de/), [GitHub page](https://github.com/kkrieger85), [Xing Profile](https://www.xing.com/profile/Kevin_Krieger) or [Twitter](https://twitter.com/kkrieger)

----

Intro: Putting every change to webservers can be an annoying job. To ensure same procedure every time you deploy, you could automate this process. Let me show how to with deployer.org

----

Text: Bringing new version of your code base may be an annoying job for you and your team if you don't have a specialist DevOps in your team. To ensure you process your deployment every time with same procedure, you could use a specific tool for that job. Especially after some Magento-Core updates it is a good way to deploy your code with one of these tools.

## why using a deployment tool?

There are a lot of deployment tools in the wild. Some automate more or less than others, most use different programming languages, some need a root-server to deploy to other machines. Big **benefit** of these tools are **speed**, **consistency**, **rollbacks** and sometime **parallel deployments**. If you are working as team on a projects, you can guarantee that **everyone deploys code the same way**.

# why deployer.org?

I decided to use [deployer](https://deployer.org/) as this tool come in our native programming language **PHP**. It is simple to install, learn and to use. It also brings some out-of-the-box recipes with it. You could also create your own recipes and share them with your team on VCS.

# typical deployment tasks:

Let's think about tasks, that you have/had to do on every deployment:

- choose server, login
- go to webserver directory
- create folder structure for your project
- separate folder/files that will be used in every deployment
- collect and build your new code
- create symlinks for folder and files
- clear caches folder, flush database cache, invalid cache files

# create your magento deployer recipe

As mentioned earlier, deployer.org brings some recipes with it. One of these recipes if for default Magento1 Shop: [View recipe on Github](https://github.com/deployphp/deployer/blob/master/recipe/magento.php)

This gives us a good base to work on.

First we define our [servers](https://deployer.org/docs/servers)

(code lang: php)
server('prod_1', 'domain.com')
    ->user('user')
    ->password('pass')
    ->set('deploy_path', '/home/www')
    ->stage('production');
(code)

or in an external file with YAML:

(code lang: yaml)
prod:
  host: domain.com
  user: www
  identity_file: ~
  stage: production
  deploy_path: /home/www/
 (code)
 
 After that we build our first recipe:
 Most of our desired tasks are covered by [common.php](https://github.com/deployphp/deployer/blob/master/recipe/common.php) recipe and [magento.php](https://github.com/deployphp/deployer/blob/master/recipe/magento.php) recipe. Therefore we extend the existing Magento-Recipe:
 
 (code lang: php)
 <?php
 
 require 'recipes/magento.php';
 
 #import serverlist
 serverList('config/servers.yaml');

# deployer tasks run as root. We'd like to fix rights:
task('fix-rights', function () {
    $httpUser = get('http_user');

    if (null === $httpUser) {
        $httpUser = run("ps axo user,comm | grep -E '[a]pache|[h]ttpd|[_]www|[w]ww-data|[n]ginx' | grep -v root | head -1 | cut -d\  -f1")->toString();
    }
    #runs as root
    run('chown -R ' . $httpUser . ':' . $httpUser . ' {{deploy_path}}');
});

#We'd like to fix rights after deployment/cleanup and after rollback:
after('cleanup', 'fix-rights');
after('rollback', 'fix-rights');


#Now we define deployment of our git-based code:
task('set-shop-repository', function () {
    set('repository', 'https://github.com/firegento/magento.git');
});

task('deploy-flexstores', [
    'set-shop-repository',
    'deploy'
]);
 (code)
 
 
 

# limitations of deployer.org

# alternatives to deployer.org



You can use (code language: javascript|php|html|xml)YOUR CODE(/code) to highlight your source.

To add some images just put it your new blog-post-directory and include it using (image: banner_fb-650x223.png)