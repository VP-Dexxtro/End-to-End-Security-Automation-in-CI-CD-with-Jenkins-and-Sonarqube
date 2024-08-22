<div class="inside-article">
		<div class="featured-image  page-header-image-single ">
				<img width="1280" height="720" src="https://github.com/VP-Dexxtro/End-to-End-Security-Automation-in-CI-CD-with-Jenkins-and-Sonarqube/blob/main/Infrastructure.png" class="attachment-full size-full" alt="" itemprop="image" decoding="async" fetchpriority="high" srcset="https://mrcloudbook.com/wp-content/uploads/2024/01/PYTHON.png 1280w, https://mrcloudbook.com/wp-content/uploads/2024/01/PYTHON-300x169.png 300w, https://mrcloudbook.com/wp-content/uploads/2024/01/PYTHON-1024x576.png 1024w, https://mrcloudbook.com/wp-content/uploads/2024/01/PYTHON-768x432.png 768w" sizes="(max-width: 1280px) 100vw, 1280px">
			</div>			<header class="entry-header">
				<h1 class="entry-title" itemprop="headline">CI-CD DevSecOps project with Jenkins | Python webapp</h1>		<div class="entry-meta">
			<span class="posted-on"><time class="entry-date published" datetime="2024-01-08T15:33:38+05:30" itemprop="datePublished">8 January 2024</time></span> <span class="byline">by <span class="author vcard" itemprop="author" itemtype="https://schema.org/Person" itemscope=""><a class="url fn n" href="https://mrcloudbook.com/author/mrcloudbook-com/" title="View all posts by mrcloudbook.com" rel="author" itemprop="url"><span class="author-name" itemprop="name">mrcloudbook.com</span></a></span></span> 		</div>
					</header>
			
		<p>Hello friends, we will be deploying a python based application. This is an everyday use case scenario used by several organizations. We will be using Jenkins as a CICD tool and deploying our application on a Docker Container. Hope this detailed blog is useful.</p>
<p><code>Github:</code> <a href="https://github.com/Aj7Ay/Python-System-Monitoring.git" target="_blank" rel="noopener"><code>https://github.com/Aj7Ay/Python-System-Monitoring.git</code></a></p>
<h1 id="heading-steps" class="permalink-heading"><strong>Steps:-</strong></h1>
<p><code>Step 1 — Create an Ubuntu T2 Large Instance</code></p>
<p><code>Step 2 — Install Jenkins, Docker and Trivy. Create a Sonarqube Container using Docker.</code></p>
<p><code>Step 3 — Install Plugins like JDK, Sonarqube Scanner, OWASP Dependency Check,</code></p>
<p><code>Step 4 — Create a Pipeline Project in Jenkins using a Declarative Pipeline</code></p>
<p><code>Step 5 — Configure Sonar Server in Manage Jenkins</code></p>
<p><code>Step 6 — we have to install and make the package</code></p>
<p><code>Step 7 — Docker Image Build and Push</code></p>
<p><code>Step 8 — Deploy the image using Docker</code></p>
<p><code>Step 9 — Access the Real World Application</code></p>
<p><code>Step 10 — Terminate the AWS EC2 Instance</code></p>
<h1 id="heading-references" class="permalink-heading"></h1>
<h1 id="heading-references" class="permalink-heading"><strong>References</strong></h1>
<h1 id="heading-now-lets-get-started-and-dig-deeper-into-each-of-these-steps" class="permalink-heading"></h1>
<h1 id="heading-now-lets-get-started-and-dig-deeper-into-each-of-these-steps" class="permalink-heading"><strong>Now, let’s get started and dig deeper into each of these steps:-</strong></h1>
<h2 id="heading-step-1-launch-an-aws-t2-large-instance" class="permalink-heading"></h2>
<h2 id="heading-step-1-launch-an-aws-t2-large-instance" class="permalink-heading"><strong>Step 1</strong> — Launch an AWS T2 Large Instance.</h2>
<p>Use the image as Ubuntu. You can create a new key pair or use an existing one. Enable HTTP and HTTPS settings in the Security Group.</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1695016278924/ad401f49-befa-4fad-973a-a3c1c797cd69.png?auto=compress,format&amp;format=webp" alt=""></p>
<h2 id="heading-step-2-install-jenkins-docker-and-trivy" class="permalink-heading"></h2>
<h2 id="heading-step-2-install-jenkins-docker-and-trivy" class="permalink-heading"><strong>Step 2</strong> — Install Jenkins, Docker and Trivy</h2>
<h3 id="heading-2a-to-install-jenkins" class="permalink-heading"></h3>
<h3 id="heading-2a-to-install-jenkins" class="permalink-heading">2A — To Install Jenkins</h3>
<p>Connect to your console, and enter these commands to Install Jenkins</p>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">sudo vi jenkins.sh
<span class="hljs-comment">#enter the below code</span>
<span class="hljs-comment">#!/bin/bash</span>
sudo apt update -y
<span class="hljs-comment">#sudo apt upgrade -y</span>
wget -O - https://packages.adoptium.net/artifactory/api/gpg/key/public | tee /etc/apt/keyrings/adoptium.asc
<span class="hljs-built_in">echo</span> <span class="hljs-string">"deb [signed-by=/etc/apt/keyrings/adoptium.asc] https://packages.adoptium.net/artifactory/deb <span class="hljs-subst">$(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release)</span> main"</span> | tee /etc/apt/sources.list.d/adoptium.list
sudo apt update -y
sudo apt install temurin-17-jdk -y
/usr/bin/java --version
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
                  /usr/share/keyrings/jenkins-keyring.asc &gt; /dev/null
<span class="hljs-built_in">echo</span> deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
                  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
                              /etc/apt/sources.list.d/jenkins.list &gt; /dev/null
sudo apt-get update -y
sudo apt-get install jenkins -y
sudo systemctl start jenkins
sudo systemctl status jenkins
</code></pre></span>
</div>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">sudo chmod 777 jenkins.sh
./jenkins.sh    <span class="hljs-comment"># this will installl jenkins</span>
</code></pre></span>
</div>
<p>Once Jenkins is installed, you will need to go to your AWS EC2 Security Group and open Inbound Port 8080, since Jenkins works on Port 8080.</p>
<p><img decoding="async" src="https://miro.medium.com/v2/resize:fit:875/0*eiURqhP5iMw_FdRq.png" alt=""></p>
<p>Now, grab your Public IP Address</p>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">&lt;EC2 Public IP Address:8080&gt;
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
</code></pre></span>
</div>
<p>Unlock Jenkins using an administrative password and install the required plugins.</p>
<p><img decoding="async" src="https://miro.medium.com/v2/resize:fit:875/0*T1i3HsPH5Fjdyyg6.png" alt=""></p>
<p>Jenkins will now get installed and install all the libraries.</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694159444242/ecdd527f-6183-4651-9480-e0c1f89f5f05.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694159480758/a30da1cc-f1e4-45bf-8182-a5f32d6f6a35.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Jenkins Getting Started Screen</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694159545473/ea177d4e-7182-4601-8ec1-4ad6bb7fa1c6.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<h3 id="heading-2b-install-docker" class="permalink-heading"></h3>
<h3 id="heading-2b-install-docker" class="permalink-heading">2B — Install Docker</h3>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">sudo apt-get update
sudo apt-get install docker.io -y
sudo usermod -aG docker <span class="hljs-variable">$USER</span>
sudo chmod 777 /var/run/docker.sock 
sudo docker ps
</code></pre></span>
</div>
<p>After the docker installation, we create a sonarqube container (Remember added 9000 port in the security group)</p>
<p><img decoding="async" src="https://miro.medium.com/v2/resize:fit:875/0*IoIWmM-z_T2jlOpe.png" alt=""></p>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
</code></pre></span>
</div>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694159658559/a607bab7-4ee0-4802-bf77-e9716ac33838.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Now our sonarqube is up and running</p>
<p>Enter username and password, click on login and change password</p>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">username admin
password admin
</code></pre></span>
</div>
<p><img decoding="async" src="https://miro.medium.com/v2/resize:fit:875/0*MKnpJlclh7_5gIxb.png" alt=""></p>
<p><img decoding="async" src="https://miro.medium.com/v2/resize:fit:875/0*PRBtqWn7YuZXVRBv.png" alt=""></p>
<h3 id="heading-2c-install-trivy" class="permalink-heading"></h3>
<h3 id="heading-2c-install-trivy" class="permalink-heading">2C — Install Trivy</h3>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">sudo apt-get install wget apt-transport-https gnupg lsb-release -y

wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg &gt; /dev/null

<span class="hljs-built_in">echo</span> <span class="hljs-string">"deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb <span class="hljs-subst">$(lsb_release -sc)</span> main"</span> | sudo tee -a /etc/apt/sources.list.d/trivy.list

sudo apt-get update

sudo apt-get install trivy -y
</code></pre></span>
</div>
<p>Next, we will log in to Jenkins and start to configure our Pipeline in Jenkins</p>
<h2 id="heading-step-3-install-plugins-like-jdk-sonarqube-scanner-owasp-dependency-check-docker" class="permalink-heading"></h2>
<h2 id="heading-step-3-install-plugins-like-jdk-sonarqube-scanner-owasp-dependency-check-docker" class="permalink-heading"><strong>Step 3</strong> — Install Plugins like JDK, Sonarqube Scanner, OWASP Dependency Check, Docker.</h2>
<h3 id="heading-3a-install-plugin" class="permalink-heading"></h3>
<h3 id="heading-3a-install-plugin" class="permalink-heading"><strong>3A — Install Plugin</strong></h3>
<p>Goto Manage Jenkins →Plugins → Available Plugins →</p>
<p>Install below plugins</p>
<p>1 → Install OWASP ( (Install without restart)</p>
<p>2 → SonarQube Scanner (Install without restart)</p>
<p>3 → 1 → Eclipse Temurin Installer (Install without restart)</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694160106164/d829e70f-9a23-4d03-a427-887d779aa141.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<h3 id="heading-3b-configure-java-and-maven-in-global-tool-configuration" class="permalink-heading"></h3>
<h3 id="heading-3b-configure-java-and-maven-in-global-tool-configuration" class="permalink-heading"><strong>3B — Configure Java and Maven in Global Tool Configuration</strong></h3>
<p>Goto Manage Jenkins → Tools → Install JDK Click on Apply and Save</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694160282666/7565037d-cf4f-4034-b55a-7028e580e3f8.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<h3 id="heading-3c-create-a-job" class="permalink-heading"></h3>
<h3 id="heading-3c-create-a-job" class="permalink-heading"><strong>3C — Create a Job</strong></h3>
<p>Label it as Dotnet CI-CD, click on Pipeline and OK.</p>
<h2 id="heading-step-4-install-owasp-dependency-check-plugins" class="permalink-heading"></h2>
<h2 id="heading-step-4-install-owasp-dependency-check-plugins" class="permalink-heading"><strong>Step 4</strong> — Install OWASP Dependency Check Plugins</h2>
<p>GotoDashboard → Manage Jenkins → Plugins → OWASP Dependency-Check. Click on it and install it without restart.</p>
<p><img decoding="async" src="https://miro.medium.com/v2/resize:fit:875/0*UaLaw2gr-jxm1PGQ.png" alt=""></p>
<p>First, we configured the Plugin and next, we had to configure the Tool</p>
<p>Goto Dashboard → Manage Jenkins → Tools →</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694162653334/158f6b94-7c92-4556-9151-6213a003b431.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Click on Apply and Save here.</p>
<h2 id="heading-step-5-configure-sonar-server-in-manage-jenkins" class="permalink-heading"></h2>
<h2 id="heading-step-5-configure-sonar-server-in-manage-jenkins" class="permalink-heading"><strong>Step 5 — Configure Sonar Server in Manage Jenkins</strong></h2>
<p>Grab the Public IP Address of your EC2 Instance, Sonarqube works on Port 9000, sp &lt;Public IP&gt;:9000. Goto your Sonarqube Server. Click on Administration → Security → Users → Click on Tokens and Update Token → Give it a name → and click on Generate Token</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694160792404/611ddf2a-9c2c-414a-ad3a-2ba84f8942ca.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Click on Update Token</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694160866134/49f34dd2-de41-455c-aee0-f1ffe13d8488.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Create a token with a name and generate</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694160967625/a96320b2-3eda-411e-bb44-20092b8a79ec.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Copy this Token</p>
<p>Goto Dashboard → Manage Jenkins → Credentials → Add Secret Text. It should look like this</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694161147409/35b423f8-e7e4-402e-895b-cd1869b8a170.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>You will this page once you click on create</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694161221410/9a7a6f3f-fd40-4bbb-8857-bf2ffb8e6895.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Now, go to Dashboard → Manage Jenkins → Configure System</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694161318710/738bd6ea-c374-4c76-9234-5ec09cfe754f.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Click on Apply and Save</p>
<p><strong>The Configure System option</strong> is used in Jenkins to configure different server</p>
<p><strong>Global Tool Configuration</strong> is used to configure different tools that we install using Plugins</p>
<p>We will install a sonar scanner in the tools.</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694161414550/efa6ef74-29e5-41c4-a81e-e6c528048c9f.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>In the Sonarqube Dashboard add a quality gate also</p>
<p>Administration–&gt; Configuration–&gt;Webhooks</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694242716931/c913bcc3-07c6-4e68-b73b-5ec04c63d4d6.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Click on Create</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694242794858/85015d2b-1c59-435a-b058-1db98f215b18.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Add details</p>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash"><span class="hljs-comment">#in url section of quality gate</span>
&lt;http://jenkins-public-ip:8080&gt;/sonarqube-webhook/
</code></pre></span>
</div>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694253241413/c6d214b6-86ad-4561-8d49-3739ac5fe66f.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Let’s go to our Pipeline and add the below code Pipeline Script.</p>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">pipeline{
    agent any
    tools{
        jdk <span class="hljs-string">'jdk17'</span>
    }
    environment {
        SCANNER_HOME=tool <span class="hljs-string">'sonar-scanner'</span>
    }
    stages {
        stage(<span class="hljs-string">'clean workspace'</span>){
            steps{
                cleanWs()
            }
        }
        stage(<span class="hljs-string">'Checkout From Git'</span>){
            steps{
                git branch: <span class="hljs-string">'main'</span>, url: <span class="hljs-string">'https://github.com/Aj7Ay/Python-System-Monitoring.git'</span>
            }
        }
        stage(<span class="hljs-string">"Sonarqube Analysis "</span>){
            steps{
                withSonarQubeEnv(<span class="hljs-string">'sonar-server'</span>) {
                    sh <span class="hljs-string">''</span><span class="hljs-string">' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Python-Webapp \
                    -Dsonar.projectKey=Python-Webapp '</span><span class="hljs-string">''</span>
                }
            }
        }
        stage(<span class="hljs-string">"quality gate"</span>){
           steps {
                script {
                    waitForQualityGate abortPipeline: <span class="hljs-literal">false</span>, credentialsId: <span class="hljs-string">'Sonar-token'</span> 
                }
            } 
        }
        stage(<span class="hljs-string">"TRIVY File scan"</span>){
            steps{
                sh <span class="hljs-string">"trivy fs . &gt; trivy-fs_report.txt"</span> 
            }
        }
        stage(<span class="hljs-string">"OWASP Dependency Check"</span>){
            steps{
                dependencyCheck additionalArguments: <span class="hljs-string">'--scan ./ --format XML '</span>, odcInstallation: <span class="hljs-string">'DP-Check'</span>
                dependencyCheckPublisher pattern: <span class="hljs-string">'**/dependency-check-report.xml'</span>
            }
        }
    }
}
</code></pre></span>
</div>
<p>Click on Build now, you will see the stage view like this</p>
<p><img decoding="async" class="image--center mx-auto" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1695017331230/6a973b65-9401-414c-8a2f-cf6bae57024a.png?auto=compress,format&amp;format=webp" alt=""></p>
<p>To see the report, you can go to Sonarqube Server and go to Projects.</p>
<p><img decoding="async" class="image--center mx-auto" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1695027758960/e5e175d8-c1cf-445c-bebf-e757fee041e4.png?auto=compress,format&amp;format=webp" alt=""></p>
<p>You can see the report has been generated and the status shows as passed. You can see that there are 522 lines. To see a detailed report, you can go to issues.</p>
<h2 id="heading-step-6-we-have-to-install-make-package" class="permalink-heading"></h2>
<h2 id="heading-step-6-we-have-to-install-make-package" class="permalink-heading"><strong>Step 6 — we have to install make package</strong></h2>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">sudo apt install make
<span class="hljs-comment"># to check version install or not</span>
make -v
</code></pre></span>
</div>
<p><img decoding="async" src="https://miro.medium.com/v2/resize:fit:875/1*9hvOM34dOaW-pVeLnFGbdw.png" alt=""></p>
<h2 id="heading-step-7-docker-image-build-and-push" class="permalink-heading"></h2>
<h2 id="heading-step-7-docker-image-build-and-push" class="permalink-heading"><strong>Step 7</strong> — <strong>Docker Image Build and Push</strong></h2>
<p>We need to install the Docker tool in our system, Goto Dashboard → Manage Plugins → Available plugins → Search for Docker and install these plugins</p>
<ul>
<li><code>Docker</code></li>
<li><code>Docker Commons</code></li>
<li><code>Docker Pipeline</code></li>
<li><code>Docker API</code></li>
<li><code>docker-build-step</code></li>
</ul>
<p>and click on install without restart</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694162971794/4e289fe1-c3b9-48d0-8efd-2b8b47118e71.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Now, goto Dashboard → Manage Jenkins → Tools →</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694163030620/59df4527-29d4-41df-8dcd-501e04fda7eb.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>Add DockerHub Username and Password under Global Credentials</p>
<p><img decoding="async" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1694163085161/2dfb909a-61a8-4122-9292-87a2742bb8d9.png?auto=compress,format&amp;format=webp&amp;auto=compress,format&amp;format=webp" alt=""></p>
<p>In the makefile, we already defined some conditions to build, tag and push images to dockerhub.</p>
<p><img decoding="async" class="image--center mx-auto" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1695018295249/bc287cd1-5d9f-41b6-9268-fea852835ad5.png?auto=compress,format&amp;format=webp" alt=""></p>
<p>that’s why we are using make image and make a push in the place of docker build -t and docker push</p>
<p>Add this stage to Pipeline Script</p>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">
       stage(<span class="hljs-string">"Docker Build &amp; tag"</span>){
            steps{
                script{
                   withDockerRegistry(credentialsId: <span class="hljs-string">'docker'</span>, toolName: <span class="hljs-string">'docker'</span>){   
                       sh <span class="hljs-string">"make image"</span>
                    }
                }
            }
        }
        stage(<span class="hljs-string">"TRIVY"</span>){
            steps{
                sh <span class="hljs-string">"trivy image sevenajay/python-system-monitoring:latest &gt; trivy.txt"</span> 
            }
        }
        stage(<span class="hljs-string">"Docker Push"</span>){
            steps{
                script{
                   withDockerRegistry(credentialsId: <span class="hljs-string">'docker'</span>, toolName: <span class="hljs-string">'docker'</span>){   
                       sh <span class="hljs-string">"make push"</span>
                    }
                }
            }
        }
</code></pre></span>
</div>
<p>When all stages in docker are successfully created then you will see the result You log in to Dockerhub, and you will see a new image is created</p>
<p><img decoding="async" class="image--center mx-auto" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1695017699798/26611577-6999-40df-a44a-6bf157104036.png?auto=compress,format&amp;format=webp" alt=""></p>
<p>stage view</p>
<p><img decoding="async" class="image--center mx-auto" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1695017789796/d017583d-ad5b-49e9-9037-6bd5a783b6a4.png?auto=compress,format&amp;format=webp" alt=""></p>
<h2 id="heading-step-8-deploy-the-image-using-docker" class="permalink-heading"></h2>
<h2 id="heading-step-8-deploy-the-image-using-docker" class="permalink-heading"><strong>Step 8</strong> — <strong>Deploy the image using Docker</strong></h2>
<p>Add this stage to your pipeline syntax</p>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash"> stage(<span class="hljs-string">"Deploy to container"</span>){
            steps{
                sh <span class="hljs-string">"docker run -d --name python1 -p 5000:5000 sevenajay/python-system-monitoring:latest"</span>
            } 
        }
</code></pre></span>
</div>
<p>You will see the Stage View like this,</p>
<p><img decoding="async" class="image--center mx-auto" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1695017898628/2d099914-9b10-4912-95af-4adce825ed57.png?auto=compress,format&amp;format=webp" alt=""></p>
<p>(Add port 5000 to Security Group)</p>
<p><img decoding="async" src="https://miro.medium.com/v2/resize:fit:875/0*mDUkFaVQI2A_HVFF.png" alt=""></p>
<p>The final script looks like this,</p>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">pipeline{
    agent any
    tools{
        jdk <span class="hljs-string">'jdk17'</span>
    }
    environment {
        SCANNER_HOME=tool <span class="hljs-string">'sonar-scanner'</span>
    }
    stages {
        stage(<span class="hljs-string">'clean workspace'</span>){
            steps{
                cleanWs()
            }
        }
        stage(<span class="hljs-string">'Checkout From Git'</span>){
            steps{
                git branch: <span class="hljs-string">'main'</span>, url: <span class="hljs-string">'https://github.com/Aj7Ay/Python-System-Monitoring.git'</span>
            }
        }
        stage(<span class="hljs-string">"Sonarqube Analysis "</span>){
            steps{
                withSonarQubeEnv(<span class="hljs-string">'sonar-server'</span>) {
                    sh <span class="hljs-string">''</span><span class="hljs-string">' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Python-Webapp \
                    -Dsonar.projectKey=Python-Webapp '</span><span class="hljs-string">''</span>
                }
            }
        }
        stage(<span class="hljs-string">"quality gate"</span>){
           steps {
                script {
                    waitForQualityGate abortPipeline: <span class="hljs-literal">false</span>, credentialsId: <span class="hljs-string">'Sonar-token'</span> 
                }
            } 
        }
        stage(<span class="hljs-string">"TRIVY File scan"</span>){
            steps{
                sh <span class="hljs-string">"trivy fs . &gt; trivy-fs_report.txt"</span> 
            }
        }
        stage(<span class="hljs-string">"OWASP Dependency Check"</span>){
            steps{
                dependencyCheck additionalArguments: <span class="hljs-string">'--scan ./ --format XML '</span>, odcInstallation: <span class="hljs-string">'DP-Check'</span>
                dependencyCheckPublisher pattern: <span class="hljs-string">'**/dependency-check-report.xml'</span>
            }
        }
        stage(<span class="hljs-string">"Docker Build &amp; tag"</span>){
            steps{
                script{
                   withDockerRegistry(credentialsId: <span class="hljs-string">'docker'</span>, toolName: <span class="hljs-string">'docker'</span>){   
                       sh <span class="hljs-string">"make image"</span>
                    }
                }
            }
        }
        stage(<span class="hljs-string">"TRIVY"</span>){
            steps{
                sh <span class="hljs-string">"trivy image sevenajay/python-system-monitoring:latest &gt; trivy.txt"</span> 
            }
        }
        stage(<span class="hljs-string">"Docker Push"</span>){
            steps{
                script{
                   withDockerRegistry(credentialsId: <span class="hljs-string">'docker'</span>, toolName: <span class="hljs-string">'docker'</span>){   
                       sh <span class="hljs-string">"make push"</span>
                    }
                }
            }
        }
        stage(<span class="hljs-string">"Deploy to container"</span>){
            steps{
                sh <span class="hljs-string">"docker run -d --name python1 -p 5000:5000 sevenajay/python-system-monitoring:latest"</span>
            } 
        }
    }
}
</code></pre></span>
</div>
<p>And you can access your application on Port 5000. This is a Real World Application that has all Functional Tabs.</p>
<div>
<div></div>
</div>
<div>
<span data-copy-format="" data-button-text="Copy" data-button-position="outside" data-button-copy-text="Copy" data-style="svg-icon" data-button-title="Copy" data-selector="pre" class="copy-the-code-wrap copy-the-code-style-svg-icon copy-the-code-outside-wrap"><div class="copy-the-code-outside"><button class="copy-the-code-button" data-style="svg-icon" title="Copy"><svg aria-hidden="true" focusable="false" role="img" class="copy-icon" viewBox="0 0 16 16" width="16" height="16" fill="currentColor"><path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z"></path><path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z"></path></svg></button></div><pre class="copy-the-code-target"><code class="lang-bash">&lt;public-ip of jenkins:5000&gt;
</code></pre></span>
</div>
<h2 id="heading-step-9-access-the-real-world-application" class="permalink-heading"></h2>
<h2 id="heading-step-9-access-the-real-world-application" class="permalink-heading"><strong>Step 9</strong> — <strong>Access the Real World Application</strong></h2>
<p><img decoding="async" class="image--center mx-auto" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1695027972705/b8f864e9-0fa2-445f-be2d-8af6bf126e66.png?auto=compress,format&amp;format=webp" alt=""></p>
<p><img decoding="async" class="image--center mx-auto" src="https://cdn.hashnode.com/res/hashnode/image/upload/v1695027994900/c436ba7a-9705-47f6-9776-a9516100a22f.png?auto=compress,format&amp;format=webp" alt=""></p>
<h2 id="heading-step-10-terminate-the-aws-ec2-instance" class="permalink-heading"></h2>
<h2 id="heading-step-10-terminate-the-aws-ec2-instance" class="permalink-heading"><strong>Step 10</strong> — <strong>Terminate the AWS EC2 Instance</strong></h2>
<p>Lastly, do not forget to terminate the AWS EC2 Instance.</p>

			</div>
