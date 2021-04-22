# AWS - Amazon Web Services

It's a cloud service company

[Official Website](https://aws.amazon.com/)

[Academind tutorial](https://www.youtube.com/watch?v=ubCNZRNjhyo)

 - Create a AWS account that will take credit/debit card number
 - After complete all task launch AWS management console

![Management console](img/management_console.png)

 - Read some solution it will make esier to use

![solution](/img/solution.png)

 - go to console -> expand all services -> select anyone -> select region (from where we want to host)
 - to select region take a look at [global infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/?hp=tile&tile=map)
 - Launch Instance (vartual server) -> Select amozon Linux (We can select any linux)
 - Take a look how AWS pricing [works](https://aws.amazon.com/pricing/?nc2=h_ql_pr). See free teir [boundaries](https://aws.amazon.com/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=categories%23featured)
 - Pricing -> Optimize your cost -> Services Pricing -> See price for what service we are using
 - See on-demand pricing

![pricing](img/pricing.png)

 - Select linux -> see the costs
 - now back to the management console
 - click on Next to see all configurations
 - Add storage -> Add new vloume (don't let it be default)
 - Configure security group -> type ssh with my ip setup

![ip](img/ip.png)

 - Review and launch -> Create a new key pair -> give any name ->  download it and store it in a save place
 - Launch instances
 - Go back to EC2 (or any other service we are using) -> Instances (it will take some time to install )
 - Actions -> instate state -> terminate
 - go to the root page -> build a solution -> build a web app -> name -> select platform -> Application  code upload as zip
 - Configure more options -> configure presets
 - Envitonment setting -> name 
 - **Create app** -> It will create all installation for us
 - node command -> command to run our code -> for example `npm start` -> apply
 - There will be a url to show the website
