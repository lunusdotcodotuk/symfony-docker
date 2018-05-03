# symfony-docker

A project to allow [Symfony 4] apps to run in a [Docker] environment, with [ELK] and [nginx] based on the fabulous work of [maxpou] with some modifcations from [elaman] to get it to run with official nginx images, and of course trial and error.

Should work out of the box, but I can't promise.  For those unfamiliar with Docker, you will not be able to access your website until the final `docker-compose up -d` line completes successfully.

## Setting Up
1. Copy the `.env.dist` file to `.env` and edit it to your preference.
   - You probably need to use the terminal/console to do this, so if you're unsure at this stage I'd advise not proceeding further.
   - Either use defaults, or change the file directory structures, ports and passwords to match what you'd like.
2. Install your application
   - If you have an application, pull/move to a directory e.g. `application` and check the directory name matches that of the `.env` entry.
   - If you do not, and wish to start a fresh web application in a directory 'application':
     - `composer create-project symfony/website-skeleton application`
     - This is assuming you have [composer] installed
     - See [sfinstall] for more options
3. You need to change your `etc/hosts` file to match the expected "localhost" address in `.env`.
   - Assuming you're using the same address as the default in the `.env` you need to add to the end of the file
     - ```127.0.0.1       symfony.docker```
     - See [this][hostshowto] if you're unsure
4. You will need to match-up database config on both the `.env` and the application config, but out of the box there's no need to get the DB working for a fresh install.
   - Your database should last "between" docker sessions on your local machine.  You can use various tools to set up the structure of the database, but essentially if you're starting from scratch, you just need to follow the guide.
5. Install [docker] if you haven't already, and then run from the project root, **not application root**:
   1. `docker-compose build`
      - If you're unfamiliar with docker, a load of *gubbins* will shoot up your screen [Jurassic Park Style][jps] and be mostly of no informative value at this stage.
      - Depending on various things, it might take a long time and probably a lot of downloading.
   2. `docker-compose up -d`
      - This starts the Docker setup systems "disconnected" so you should only see them start and get terminal control back.
      - You should see four services start, and say `done` in large, friendly letters.  
      - If any don't, you can't symfony-docker today and must go on a quest for answers from a nearby person with a beard and well-thumbed copy of any O'Reilly book.



[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [Symfony 4]: <https://symfony.com/>
   [Docker]: <https://www.docker.com/>
   [ELK]: <https://www.elastic.co/elk-stack>
   [nginx]: <https://www.nginx.com/>
   [maxpou]: <https://github.com/maxpou/docker-symfony>
   [elaman]: <https://github.com/maxpou/docker-symfony/pull/91>
   [composer]: <https://getcomposer.org/>
   [sfinstall]: <https://symfony.com/doc/current/setup.html>
   [hostshowto]: <https://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/>
   [jps]: <http://www.jurassicsystems.com/>