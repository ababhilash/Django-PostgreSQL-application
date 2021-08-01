# Django-PostgreSQL-application
Docker Compose to set up and run Django/PostgreSQL app using Ansible playbook.

<h1 class="code-line" data-line-start=0 data-line-end=1 ><a id="Objective_To_use_Docker_Compose_to_set_up_and_run_a_simple_DjangoPostgreSQL_app_0"></a>Objective: To use Docker Compose to set up and run a Django/PostgreSQL app.</h1>
<p class="has-line-data" data-line-start="2" data-line-end="3"><a href="https://travis-ci.org/joemccann/dillinger"><img src="https://travis-ci.org/joemccann/dillinger.svg?branch=master" alt="Build Status"></a></p>
<h2 class="code-line" data-line-start=3 data-line-end=4 ><a id="Description_3"></a>Description:</h2>
<p class="has-line-data" data-line-start="4" data-line-end="5">Create a docker-compose file for running a django application with postgresql 10. Django app and postgresql should be running as different compose services. Also the compose app should be deployed using ansible playbook</p>
<h1 class="code-line" data-line-start=6 data-line-end=7 ><a id="Details_of_the_Task_6"></a><strong><em>Details of the Task:</em></strong></h1>
<h2 class="code-line" data-line-start=8 data-line-end=9 ><a id="Version_8"></a>Version:</h2>
<p class="has-line-data" data-line-start="9" data-line-end="18"><strong><em>Docker</em></strong><br>
[root@ip-172-31-62-56 project]# docker --version<br>
Docker version 20.10.4, build d3cb89e<br>
<strong><em>postgres</em></strong><br>
root@1a72ea9bfafe:/# postgres -V<br>
postgres (PostgreSQL) 10.17 (Debian 10.17-1.pgdg90+1)<br>
<strong><em>docker-compose</em></strong><br>
[root@ip-172-31-62-56 project]# docker-compose --version<br>
docker-compose version 1.29.2, build 5becea4c</p>
<h2 class="code-line" data-line-start=19 data-line-end=20 ><a id="File_Locations_19"></a>File Locations:</h2>
<p class="has-line-data" data-line-start="21" data-line-end="28">[root@ip-172-31-48-248 project]# pwd<br>
/root/project<br>
[root@ip-172-31-48-248 project]# tree<br>
.<br>
├── docker-compose.yml<br>
├── Dockerfile<br>
└── requirements.txt</p>
<p class="has-line-data" data-line-start="29" data-line-end="30">0 directories, 3 files</p>
<h2 class="code-line" data-line-start=31 data-line-end=32 ><a id="Successfull_Outputs_31"></a>Successfull Outputs:</h2>
<h4 class="code-line" data-line-start=33 data-line-end=34 ><a id="Output_of_the_Django_app_running_on_port_8000_33"></a><strong><em>Output of the Django app running on port 8000</em></strong></h4>
<p class="has-line-data" data-line-start="35" data-line-end="36"><img src="screenshots/backend.png" alt=""></p>
<h4 class="code-line" data-line-start=37 data-line-end=38 ><a id="Output_of_Ansible_playbookappyml_37"></a><strong><em>Output of Ansible playbook-app.yml</em></strong></h4>
<p class="has-line-data" data-line-start="39" data-line-end="40"><img src="screenshots/frontend.png" alt=""></p>
<h4 class="code-line" data-line-start=41 data-line-end=42 ><a id="Output_of_running_containers_41"></a><strong><em>Output of running containers</em></strong></h4>
<p class="has-line-data" data-line-start="43" data-line-end="44"><img src="screenshots/Containers.png" alt=""></p>
<p class="has-line-data" data-line-start="45" data-line-end="46"><strong>Thank you</strong></p>
