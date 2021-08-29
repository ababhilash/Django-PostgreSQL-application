<h1 class="code-line" data-line-start=0 data-line-end=1 ><a id="DjangoPostgreSQLapplication_0"></a>Django-PostgreSQL-application</h1>
<h2 class="code-line" data-line-start=2 data-line-end=3 ><a id="Objective_2"></a>Objective:</h2>
<p class="has-line-data" data-line-start="4" data-line-end="5"><img src="screenshots/Diagram.png" alt=""></p>
<p class="has-line-data" data-line-start="6" data-line-end="7">To set up and run a Django/PostgreSQL application using Docker Compose and Ansible playbook.</p>
<h2 class="code-line" data-line-start=8 data-line-end=9 ><a id="Description_8"></a>Description:</h2>
<p class="has-line-data" data-line-start="10" data-line-end="11">Create a docker-compose file for running a Django application with PostgreSQL 10. The Django app and PostgreSQL should be running as different compose services. Also, the compose app should be deployed using an ansible-playbook. I have used two Amazon Linux EC2 instances, one for the Django/PostgreSQL application and the other one used as an Ansible server.</p>
<h2 class="code-line" data-line-start=12 data-line-end=13 ><a id="Requirements_12"></a>Requirements:</h2>
<ul>
<li class="has-line-data" data-line-start="14" data-line-end="15">Dockerfile</li>
<li class="has-line-data" data-line-start="15" data-line-end="16">Ansible playbook</li>
<li class="has-line-data" data-line-start="16" data-line-end="17">Docker-compose file</li>
<li class="has-line-data" data-line-start="17" data-line-end="19">Requirements.txt file</li>
</ul>
<h2 class="code-line" data-line-start=19 data-line-end=20 ><a id="Steps_19"></a>Steps:</h2>
<h3 class="code-line" data-line-start=20 data-line-end=21 ><a id="Define_the_project_components_20"></a>Define the project components:</h3>
<ol>
<li class="has-line-data" data-line-start="21" data-line-end="22">We need to create an empty project directory.</li>
<li class="has-line-data" data-line-start="22" data-line-end="23">Create a new file called Dockerfile in the project directory.</li>
<li class="has-line-data" data-line-start="23" data-line-end="25">Add the content to the Dockerfile.<br>
The Dockerfile starts with a Python 3 parent image. The parent image is modified by adding a new code directory. The parent image is further modified by installing the Python requirements defined in the requirements.txt file.</li>
<li class="has-line-data" data-line-start="25" data-line-end="27">Create a requirements.txt in the project directory.<br>
This file is used by the RUN “pip install -r requirements.txt” command in the Dockerfile.</li>
<li class="has-line-data" data-line-start="27" data-line-end="28">Add the required software to the file.</li>
</ol>
<pre><code class="has-line-data" data-line-start="29" data-line-end="32" class="language-sh">Django&gt;=<span class="hljs-number">3.0</span>,&lt;<span class="hljs-number">4.0</span>
psycopg2-binary&gt;=<span class="hljs-number">2.8</span>
</code></pre>
<ol start="6">
<li class="has-line-data" data-line-start="32" data-line-end="35">Create a file called docker-compose.yml in the project directory.<br>
The docker-compose.yml file describes the services that make the app. In our case, the “web” and “DB” services are web server and database respectively. The compose file also describes which Docker images these services use, how they link together, any volumes they might need to be mounted inside the containers. Finally, the docker-compose.yml file describes which ports these services expose.</li>
</ol>
<pre><code class="has-line-data" data-line-start="36" data-line-end="46" class="language-sh">[root@ip-<span class="hljs-number">172</span>-<span class="hljs-number">31</span>-<span class="hljs-number">48</span>-<span class="hljs-number">248</span> project]<span class="hljs-comment"># pwd</span>
/root/project
[root@ip-<span class="hljs-number">172</span>-<span class="hljs-number">31</span>-<span class="hljs-number">48</span>-<span class="hljs-number">248</span> project]<span class="hljs-comment"># tree</span>

├── docker-compose.yml
├── Dockerfile
└── requirements.txt

<span class="hljs-number">0</span> directories, <span class="hljs-number">3</span> files
</code></pre>
<ol start="7">
<li class="has-line-data" data-line-start="47" data-line-end="48">Run the ansible-playbook “app.yml”</li>
</ol>
<pre><code class="has-line-data" data-line-start="49" data-line-end="51" class="language-sh">ansible-playbook app.yml
</code></pre>
<ol start="8">
<li class="has-line-data" data-line-start="51" data-line-end="52">After the tasks have been completed, list the contents of the project. You can see that there will be new files created within the project directory.</li>
</ol>
<pre><code class="has-line-data" data-line-start="53" data-line-end="63" class="language-sh">[root@ip-<span class="hljs-number">172</span>-<span class="hljs-number">31</span>-<span class="hljs-number">16</span>-<span class="hljs-number">38</span> project]<span class="hljs-comment"># ll</span>
total <span class="hljs-number">16</span>
drwxr-xr-x <span class="hljs-number">3</span> root root <span class="hljs-number">108</span> Aug <span class="hljs-number">28</span> <span class="hljs-number">10</span>:<span class="hljs-number">19</span> composeexample
drwxr-xr-x <span class="hljs-number">3</span> root root  <span class="hljs-number">16</span> Aug <span class="hljs-number">28</span> <span class="hljs-number">10</span>:<span class="hljs-number">19</span> data
-rw-r--r-- <span class="hljs-number">1</span> root root   <span class="hljs-number">0</span> Aug <span class="hljs-number">28</span> <span class="hljs-number">10</span>:<span class="hljs-number">19</span> db.sqlite3
-rw-r--r-- <span class="hljs-number">1</span> root root <span class="hljs-number">386</span> Aug <span class="hljs-number">28</span> <span class="hljs-number">09</span>:<span class="hljs-number">50</span> docker-compose.yml
-rw-r--r-- <span class="hljs-number">1</span> root root <span class="hljs-number">131</span> Aug <span class="hljs-number">28</span> <span class="hljs-number">09</span>:<span class="hljs-number">49</span> Dockerfile
-rwxr-xr-x <span class="hljs-number">1</span> root root <span class="hljs-number">670</span> Aug <span class="hljs-number">28</span> <span class="hljs-number">10</span>:<span class="hljs-number">19</span> manage.py
-rw-r--r-- <span class="hljs-number">1</span> root root  <span class="hljs-number">38</span> Aug <span class="hljs-number">28</span> <span class="hljs-number">09</span>:<span class="hljs-number">51</span> requirements.txt
</code></pre>
<p class="has-line-data" data-line-start="63" data-line-end="64">If you are running Docker on Linux, the files Django-admin created are owned by root. This happens because the container runs as the root user. Change the ownership of the new files.</p>
<pre><code class="has-line-data" data-line-start="65" data-line-end="67" class="language-sh">sudo chown -R <span class="hljs-variable">$USER</span>:<span class="hljs-variable">$USER</span> .
</code></pre>
<h3 class="code-line" data-line-start=67 data-line-end=68 ><a id="Connect_the_database_67"></a>Connect the database</h3>
<p class="has-line-data" data-line-start="69" data-line-end="70">In this section, you set up the database connection for Django.</p>
<ul>
<li class="has-line-data" data-line-start="70" data-line-end="73">In the project directory, edit the composeexample/settings.py file.<br>
Replace the DATABASES = … with the following:</li>
</ul>
<h3 class="code-line" data-line-start=73 data-line-end=74 ><a id="settingspy_73"></a><a href="http://settings.py">settings.py</a></h3>
<pre><code class="has-line-data" data-line-start="76" data-line-end="87" class="language-sh">DATABASES = {
    <span class="hljs-string">'default'</span>: {
        <span class="hljs-string">'ENGINE'</span>: <span class="hljs-string">'django.db.backends.postgresql'</span>,
        <span class="hljs-string">'NAME'</span>: <span class="hljs-string">'postgres'</span>,
        <span class="hljs-string">'USER'</span>: <span class="hljs-string">'postgres'</span>,
        <span class="hljs-string">'PASSWORD'</span>: <span class="hljs-string">'postgres'</span>,
        <span class="hljs-string">'HOST'</span>: <span class="hljs-string">'db'</span>,
        <span class="hljs-string">'PORT'</span>: <span class="hljs-number">5432</span>,
    }
}
</code></pre>
<p class="has-line-data" data-line-start="87" data-line-end="88">These settings are determined by the Postgres Docker image specified in docker-compose.yml.</p>
<ul>
<li class="has-line-data" data-line-start="89" data-line-end="93">You need to edit ALLOWED_HOSTS inside <a href="http://settings.py">settings.py</a> and add the IP address to the list<br>
ALLOWED_HOSTS = [‘IP’]<br>
<strong>Note:</strong> If you didn’t specify any value to the ALLOWED_HOSTS parameter on the &quot;<a href="http://settings.py">settings.py</a>&quot; file, you will get the below-mentioned error;</li>
</ul>
<p class="has-line-data" data-line-start="93" data-line-end="94"><img src="screenshots/Error.png" alt=""></p>
<ol start="9">
<li class="has-line-data" data-line-start="95" data-line-end="96">Run the docker-compose-up command from the top-level directory for the project.</li>
</ol>
<pre><code class="has-line-data" data-line-start="97" data-line-end="100" class="language-sh">[root@ip-<span class="hljs-number">172</span>-<span class="hljs-number">31</span>-<span class="hljs-number">16</span>-<span class="hljs-number">38</span> ~]<span class="hljs-comment"># cd project/</span>
[root@ip-<span class="hljs-number">172</span>-<span class="hljs-number">31</span>-<span class="hljs-number">16</span>-<span class="hljs-number">38</span> project]<span class="hljs-comment"># docker-compose up</span>
</code></pre>
<p class="has-line-data" data-line-start="101" data-line-end="102"><img src="screenshots/docker-compose.png" alt=""></p>
<p class="has-line-data" data-line-start="103" data-line-end="105">At this point, the Django app should be running at port 8000 and to see the Django welcome page use the below URL.<br>
http://ip_address:8000/</p>
<p class="has-line-data" data-line-start="106" data-line-end="107"><strong>Note:</strong> You need to open the ports 8000 and 5432 in the Security group for the EC2 Instance.</p>
<h2 class="code-line" data-line-start=108 data-line-end=109 ><a id="Versions_108"></a>Versions:</h2>
<ol>
<li class="has-line-data" data-line-start="109" data-line-end="110">Docker</li>
</ol>
<pre><code class="has-line-data" data-line-start="111" data-line-end="114" class="language-sh"> [root@ip-<span class="hljs-number">172</span>-<span class="hljs-number">31</span>-<span class="hljs-number">62</span>-<span class="hljs-number">56</span> project]<span class="hljs-comment"># docker --version</span>
Docker version <span class="hljs-number">20.10</span>.<span class="hljs-number">4</span>, build d3cb89e
</code></pre>
<ol start="2">
<li class="has-line-data" data-line-start="114" data-line-end="115">PostgreSQL</li>
</ol>
<pre><code class="has-line-data" data-line-start="116" data-line-end="119" class="language-sh">root@<span class="hljs-number">1</span>a72ea9bfafe:/<span class="hljs-comment"># postgres -V</span>
postgres (PostgreSQL) <span class="hljs-number">10.17</span> (Debian <span class="hljs-number">10.17</span>-<span class="hljs-number">1</span>.pgdg90+<span class="hljs-number">1</span>)
</code></pre>
<ol start="3">
<li class="has-line-data" data-line-start="119" data-line-end="120">Docker-compose</li>
</ol>
<pre><code class="has-line-data" data-line-start="121" data-line-end="124" class="language-sh">[root@ip-<span class="hljs-number">172</span>-<span class="hljs-number">31</span>-<span class="hljs-number">62</span>-<span class="hljs-number">56</span> project]<span class="hljs-comment"># docker-compose --version</span>
docker-compose version <span class="hljs-number">1.29</span>.<span class="hljs-number">2</span>, build <span class="hljs-number">5</span>becea4c
</code></pre>
<ol start="4">
<li class="has-line-data" data-line-start="124" data-line-end="125">Python</li>
</ol>
<pre><code class="has-line-data" data-line-start="126" data-line-end="129" class="language-sh">[root@ip-<span class="hljs-number">172</span>-<span class="hljs-number">31</span>-<span class="hljs-number">62</span>-<span class="hljs-number">56</span> project]<span class="hljs-comment"># python -V</span>
Python <span class="hljs-number">3.8</span>.<span class="hljs-number">0</span>
</code></pre>
<h2 class="code-line" data-line-start=130 data-line-end=131 ><a id="Outputs_130"></a>Outputs:</h2>
<p class="has-line-data" data-line-start="132" data-line-end="134"><strong><em>Output of Ansible playbook app.yml</em></strong><br>
<img src="screenshots/backend.png" alt=""></p>
<p class="has-line-data" data-line-start="135" data-line-end="137"><strong><em>Output of the Django app running on port 8000</em></strong><br>
<img src="screenshots/frontend.png" alt=""></p>
<p class="has-line-data" data-line-start="138" data-line-end="140"><strong><em>Output of running containers</em></strong><br>
<img src="screenshots/Containers.png" alt=""></p>
<h2 class="code-line" data-line-start=141 data-line-end=142 ><a id="Additional_links_141"></a>Additional links:</h2>
<table class="table table-striped table-bordered">
<thead>
<tr>
<th>Tools</th>
<th>Links</th>
</tr>
</thead>
<tbody>
<tr>
<td>Docker-compose</td>
<td><a href="https://docs.docker.com/compose/">https://docs.docker.com/compose/</a></td>
</tr>
<tr>
<td>Django(framework)</td>
<td><a href="https://www.djangoproject.com/">https://www.djangoproject.com/</a></td>
</tr>
<tr>
<td>Ansible</td>
<td><a href="https://docs.ansible.com/">https://docs.ansible.com/</a></td>
</tr>
<tr>
<td>PostgreSQL</td>
<td><a href="https://www.postgresql.org/docs/">https://www.postgresql.org/docs/</a></td>
</tr>
</tbody>
</table>
<h2 class="code-line" data-line-start=150 data-line-end=151 ><a id="Summary_150"></a>Summary</h2>
<p class="has-line-data" data-line-start="151" data-line-end="152">I hope this will help you in working with Docker, Django, PostgreSQL, and Ansible.</p>
<h2 class="code-line" data-line-start=153 data-line-end=154 ><a id="Thank_You_153"></a><strong>Thank You</strong></h2>
