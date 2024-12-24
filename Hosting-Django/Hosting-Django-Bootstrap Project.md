<h2>How to Point Domain and Deploy Django Project using Github on Gunicorn & Nginx Remote Server or VPS</h2>
<h5>What is Gunicorn</h5>
<p>Gunicorn is a Web Server Gateway Interface (WSGI) which receive requests sent to the Web Server from a Client and forwards them onto the Python applications or Web Frameworks e.g. Flask or Django in order to run the appropriate application code for the request. It basically provides a bridge to communicate between your Web Server and Web Application.</p>
<hr>
<h5>What is Nginx</h5>
<p>Nginx (pronounced "engine-x") is a high-performance web server and reverse proxy server. It is widely used for serving static content, load balancing, reverse proxying, and as a key component in modern web application architectures.</p>
<hr>






<h3>Step 1 : On Loacal Machine do following things</h3>
<ol>
  <li>Open Terminal</li>
  <li>Activate Virtual Environment by using command <strong>Environment-Name/Scripts/activate </strong></li>
  <li>Install Django Extensions Package It will help to clear pyc and cache (Optional)</li>
  <div class="input-container">
    <strong> pip install django-extensions </strong>
  </div>
  <li>Add Django Extensions Package to INSTALLED_APPS in settings.py File</li>
  <strong>'django_extensions',</strong>
  <li>Create requirements.txt File</li>
  <strong> pip freeze > requirements.txt</strong>
</ol>



<h3>Step 2 : On VPS</h3>
<ol>
  <li>Get SSH Access</li>
  <div>
    <strong>ssh root@your_ip_address_of_vps</strong>
    <br>
    <strong>password - input your ssh password</strong>
  </div>
  <li>Verify that all required softwares are installed</li>
  <div>
    <strong>nginx -v</strong> <br>
    <strong>python3 --version</strong> <br>
    <strong>pip --version</strong> <br>
    <strong>--SQLite is Included with Python</strong> <br>
    <strong>--python -c "import sqlite3; print(sqlite3.sqlite_version)"</strong> <br>
    <strong>git --version</strong>
  </div>  

    
  <li>If above software not found then install using bellow commands</li>
  <div>
    <strong> sudo apt install nginx </strong> <br>
    <strong> sudo apt install python or use sudo apt install python3 </strong> <br>
    <strong>sudo apt install python3-pip</strong> <br>
    <strong> sudo apt install git </strong> <br>
  </div>
  
  <li>Install virtualenv</li>
  <p><strong>pip list  ===</strong> Check all requirements of the VPS</p>
  <p><strong>sudo pip install virtualenv OR sudo apt install python3-virtualenv ===</strong> Install Virtual Environment</p>
  
  <li>Update And Upgrade Command used for linux stability, requirements and security reason </li>
  <p><strong> sudo apt update ===</strong> Update all the requirements installed </p>
  <p><strong> sudo apt upgrade -y  ===</strong> Upgrade all the requirements installed </p>

  <li>Verify Nginx is Active and Running </li>
  <p><strong> sudo service nginx status ===</strong> If it show Active then not any issue </p>

  <li>Verify Web Server Ports are Open and Allowed through Firewall </li>
  <p><strong>sudo ufw status verbose  ===</strong> check 22,80 and 443 port are active if any one not fount the <strong>sudo ufw allow 80/tcp
  </strong> use the command to activate and check again status </p>

  <li>Verify Web Server Ports are Open and Allowed through Firewall </li>
  <p><strong>exit  ===</strong> to stop our ssh </p>

 
</ol>


<h3>Step 3 : Point Domain on VPS </h3>
<ol>
  <li> Login to Your Domain Provider Website </li>
  <li> Navigate to Manage DNS </li>
  <li> Add Following Records: </li>
  <table>
        <thead>
            <tr>
                <th>Type</th>
                <th>Host/Name</th>
                <th>Value</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>A</td>
                <td>@</td>
                <td>Your Remote Server IP</td>
            </tr>
            <tr>
                <td>A</td>
                <td>www</td>
                <td>Your Remote Server IP</td>
            </tr>
            <tr>
                <td>AAAA</td>
                <td>@</td>
                <td>Your Remote Server IPv6</td>
            </tr>
            <tr>
                <td>AAAA</td>
                <td>www</td>
                <td>Your Remote Server IPv6</td>
            </tr>
        </tbody>
    </table>
    <p>Note : IPv6 and Server IP are available on hostinger website. just login the hostinger and click on VPS server manage button and directly you see the ip address and click on ssh u will see the IPv6 id.. </p>
    <p>Note: <a href="https://dnschecker.org/"> DNS Checker </a> Click on the link DNS Checker and at the first input we have to type our domain name if domain show our IP address the all ok ..... </p>

  
</ol>


   
