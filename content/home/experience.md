+++
# Experience widget.
widget = "experience"  # See https://sourcethemes.com/academic/docs/page-builder/
headless = true  # This file represents a page section.
active = true  # Activate this widget? true/false
weight = 30  # Order that this section will appear.

title = "Experience"
subtitle = ""

# Date format for experience
#   Refer to https://sourcethemes.com/academic/docs/customization/#date-format
date_format = "Jan 2006"

# Experiences.
#   Add/remove as many `[[experience]]` blocks below as you like.
#   Required fields are `title`, `company`, and `date_start`.
#   Leave `date_end` empty if it's your current employer.
#   Begin/end multi-line descriptions with 3 quotes `"""`.
[[experience]]
  title = "DevOps Consultant"
  company = "PA Consulting"
  company_url = "https://www.paconsulting.com/"
  location = "London"
  date_start = "2019-12-04"
  date_end = ""
  description = """
  Using the power of ingenuity to build a positive human future in a technology-driven world with a global network of FTSE 100 and Fortune 500 clients.
  * Deployed a three-tier CMS to AWS using Terraform with CodePipeline for CI/CD. I created the continuous deployment pipeline which allowed us to provision infrastructure by pushing files to CodeCommit.
  * Because of Covid-19 there was a lack of project work. I used the extra time to my advantage: I spent off-the-clock time self-learning and studying for cloud certifications (12xAWS, 8xGCP, 2xAzure, 2xCKA*, 2xHashiCorp) and sharing what I learnt with the rest of the company.
  * Created a new internal training scheme to teach AWS skills to PA people and help them pass AWS certifications.
  * Advocated the use of AWS and found participants for an internal AWS GameDay. A simulated day of deploying services and responding to cyber-attacks.
  """

[[experience]]
  title = "Trainee Cloud Engineer"
  company = "Amazon Web Services (AWS)"
  company_url = "https://aws.amazon.com/training/restart/"
  location = "London"
  date_start = "2019-07-01"
  date_end = "2019-10-01"
  description = """
  AWS re/Start is a training and job placement programme to educate young adults on the latest software development and cloud computing technologies.
  * Deployed a serverless website (www.roshbeed.com). I used CloudFront, Route 53 and S3 to serve the static assets. I created a microservice using Lambda, DynamoDB and API Gateway to allow users to post and view comments. I used CodePipeline to build the static site by processing files from CodeCommit and producing artefacts in S3. I reduced the build time from 3 minutes to 30 seconds with a custom build environment with pre-packaged dependencies
  * Technical skills: AWS, Linux, Networking (DNS, IPsec, BGP, VPN, Load Balancing), Security (IAM), Databases (Relational/NoSQL), Programming (Python)
  * Cloud Concepts: Economics (TCO, CapEx/OpEx), Infrastructure as Code (CloudFormation, Terraform), Configuration Management (OpsWorks, Ansible), Serverless, Well-Architected
  * Behavioural skills: Communication, Teamwork, Time Management, Future Orientation
  """

[[experience]]
  title = "DevOps Engineer"
  company = "Zaizi"
  company_url = "https://www.zaizi.com/"
  location = "London"
  date_start = "2017-08-01"
  date_end = "2018-02-01"
  description = """
  Increased performance of services with new technologies. Configured, tested and deployed updates to services for the UK public sector.
  * Reduced the time of a weekly manual task of copying data from a CSV into a GUI from 2 days to 2 hours with a python script.
  * Created a simple yet secure multi-user secrets management system using GPG for encryption-at-rest and Git over SSH for encryption-in-transit. Used CodeCommit to synchronise passwords between users.
  * Reduced the speed of Alfresco deployments from hours to minutes by creating a golden AMI using Ansible.
  * Developed a dashboard to monitor the company’s services using CloudWatch.
  """

[[experience]]
  title = "Software Engineer"
  company = "GoSweat"
  company_url = "https://www.gosweat.com/"
  location = "London"
  date_start = "2017-05-01"
  date_end = "2017-08-01"
  description = """
  Joined the early stages of a startup to develop a marketplace application to find local sports facilities.
  * Created microservices in Java and a website to consume them with AngularJS.
  * Migrated old services from Digital Ocean to GCP.
  * Set up Continuous Deployment with Bitbucket Pipelines to Google App Engine.
  * Presented demos on tools (e.g. Git and Docker) and how they could be used more efficiently to increase productivity.
  * Built trust with C-level executives and discussed strategies for long-term results.
  * Acted as Tech Lead during handover and led a team of 5 to create a knowledge-sharing platform for customers. I developed people into a high performing team and we found ideas for the platform by speaking to customers.
  """

[[experience]]
  title = "Software Developer"
  company = "East City Films"
  company_url = "https://www.gosweat.com/"
  location = "London"
  date_start = "2017-02-01"
  date_end = "2017-04-01"
  description = """
  Joined the early stages of a startup to develop a marketplace application to find local sports facilities.
  * Created microservices in Java and a website to consume them with AngularJS.
  * Migrated old services from Digital Ocean to GCP.
  * Set up Continuous Deployment with Bitbucket Pipelines to Google App Engine.
  * Presented demos on tools (e.g. Git and Docker) and how they could be used more efficiently to increase productivity.
  * Built trust with C-level executives and discussed strategies for long-term results.
  * Acted as Tech Lead during handover and led a team of 5 to create a knowledge-sharing platform for customers. I developed people into a high performing team and we found ideas for the platform by speaking to customers.
  """

+++
