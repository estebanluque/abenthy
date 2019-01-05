<h1>How to prepare development environment</h1>
<h2>Docker component</h2>
<p>The Dockerfile defines an application’s image content via one or more build commands that configure that image. 
Once built, you can run the image in a container. For more information on <strong>Dockerfile</strong>, see the 
<a href="https://docs.docker.com/engine/tutorials/dockerimages/#building-an-image-from-a-dockerfile">Docker user guide
</a> and the <a href="https://docs.docker.com/engine/reference/builder/">Dockerfile reference</a>.<p>
<p>This file is used by the <code>RUN pip install -r requirements.txt</code> command in your Dockerfile.</p>
<p>The <code>docker-compose.yml</code> file describes the services that make your app. In
this example those services are a web server and database.  The compose file
also describes which Docker images these services use, how they link
together, any volumes they might need mounted inside the containers.
Finally, the <code>docker-compose.yml</code> file describes which ports these services
expose. See the <a href="https://docs.docker.com/compose/compose-file/"><code>docker-compose.yml</code> reference</a> 
for more information on how this file works. This file defines two services: The <strong>db</strong> service and the 
<strong>web</strong> service.</p>
 
<h2>Create a Django project</h2>
<p>Create the Django project by running the docker-compose run command as follows.<br/>
<code>sudo docker-compose run web django-admin.py startproject composeexample .</code></p>

<h2>Connect DataBase</h2>
<p>n your project directory, edit the composeexample/settings.py file.</p>
   <p>Replace the <code>DATABASES = ...</code> with the following:</p>
<pre><code>
DATABASES = {
  'default': {
      'ENGINE': 'django.db.backends.postgresql',
      'NAME': 'postgres',
      'USER': 'postgres',
      'HOST': 'db',
      'PORT': 5432,
  }
}
</code></pre>
<p>These settings are determined by the postgres Docker image specified in docker-compose.yml.</p>

*source: https://docs.docker.com/compose/django/#create-a-django-project