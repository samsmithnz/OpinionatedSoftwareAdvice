## DevOps steps to success

1. [ ] **DevOps foundation** Ensure that everyone understands what, why, how, when, and where we are using DevOps. 
    1. [ ] **Why DevOps?** Explain the benefits, get everyone on the same page.
    1. [ ] **What is DevOps** Get everyone on the same page about what DevOps is. No assumptions. 
    1. [ ] **Executive support** - get budgets/ time/ buyin from top to bottom.
    1. [ ] **Team POC** - identify the right team/project to test these ideas. A smaller project/single team is easier than a large project/many teams.
    1. [ ] **Construct the Team** - ensure we have the right people. Do we have a security person? a developer? ops? product manager/owner? a DBA? QA? Who else needs to be involved? 
    1. [ ] **Value Stream Mapping** - understand the pain points in our current process. How long does it take to change a line of code and release it to our end users? Where are the bottlenecks? What processes are manual (and can be automated)? Who is needs to approve pieces? Regulations? We need ball park metrics to track success/failure
1. [ ] **Dev/ Repository setup**
    1. [ ] **Source Control** - Create a repository in GitHub. Create a backlog of issues and prioritize them. Setup security.
    1. [ ] **Branching strategy** - decide on a branching strategy. Hint: Simplier is better, you can always add complexity later. Ideally a main branch with feature branches is best. Warning: This could be a holy war, keep this timeboxed and scoped. Have someone pull rank if needed. This is not a good place to experiment, it just leads to pain. KEEP IT SIMPLE. 
    1. Stretch goals:
        1. [ ] **Coding Standards** - What standards should the code be following? Ideally automation is best here (e.g. an editorconfig file). Move the opinion from the code reviewer to an automated system to reduce team conflict 
        1. [ ] **Code Analysis** - what code analysis tools will we use to ensure quality? CodeQL? SonarCloud? Using this earlier will keep a handle on technical debt. Warning: Running this on existing projects will uncover hundreds, if not thousands of issues and overwhelm the team. Consider ignoring the first batch of issues on an existing project, or everything non-critical. 
1. [ ] **CI**
    1. [ ] **Branch Policies** - When we create a PR, what do we need to merge the feature branch back to main? A successful build? Tests? Code review? manager approver? Try to minimize the number of people involved. If you need a DBA, senior director, security guy, and architect to approve every change, your process benefits will be reduced. 
    1. [ ] **Pull Requests** - A good time to remind the team that pull requests and feature branches should be short lived, hanging around for days, not months. Have the team use PR's for work in progress and use draft PR's to help them develop the feature
    1. [ ] **Testing Strategy** - Unit tests are critical. If you can't get feedback on a change in seconds or minutes - then your application is in trouble. Have a good balance of unit, integration and functional tests. Define what each of these tests mean (don't be surprised that everyone thinks a unit test is something else). Include performance and load tests too!
1. [ ] **CD**
    1. [ ] **Continuous Delivery**: Setup a deployment to production on every merge to main. Make sure the build deploys to dev and qa ok too. Approvals to production are ok - perhaps you push to dev/qa every merge, but only prod every couple of weeks.
    1. [ ] **Make sure that a secrets manager is used to manage secrets. No secrets should be stored in source code. **
    1. [ ] Stretch goals:
        1. [ ] **GitOps**: Or Infrastructure as code. Everytime you deploy your application, also deploy the configuration/infrastructure. Over time this will evolve to checking if infrastructure changed and then correcting - but be careful you don't create a lot of optional steps that run infrequently- make sure you deploy a completely new environment periocally to ensure everything works - this is easy with the cloud and dynamic environments
        1. [ ] **The cloud**: The cloud exists for us to elastic scale as needed. Use it for short-lived dynamic dev/qa environments. Ideally when starting a new branch, you can (relatively) quickly create a new environment to test that change before merging. Make use of services like Redis and CDN that were previously really expensive, and are now, not. 
        1. [ ] **Feature Flags**: Continuous deployment, in my opinion, is not possible without feature flags/toggles. Feature flags allow you to wrap changes up into a branches - removing the change from the deployment, instead giving power to the business to enable the feature when they need to. Advanced feature flag systems can target specific users, groups, ip ranges/areas, to help test that the change is safe. If you deploy a bug to production, how quickly can you disable it - without cheating the DevOps process? 10 mins? 2 hours? With a feature flag, it's seconds.
        1. [ ] **Continuous Deployment**: Deploy to production on every merge. Use feature flags to make this safe    
1. [ ] **CM**: All stretch goals
    1. [ ] **DevSecOps**: Do you have security checking dependencys? Do you have dependabot updating them? Does GitHub advanced security make sense here?
    2. [ ] **Monitoring**: Do you have monitoring with an understanding of what 'normal' levels are? Can you detect with CPU spikes? When a cert is about to expire? When storage is running low. You won't capture everything, but continue to evolve this
    3. [ ] **Alerting**: Don't over alert. Every alert should be actionable - otherwise it's a log. If you receive an alert and do nothing - why did you get that alert?  Review the log regularly to make sure there is nothing you are missing.  
    4. [ ] **Continuous learning**: It's ok to make a mistake. It's not ok to make the same mistake twice. If something breaks, ask "Could an automated test have prevented this?" It could be as simple as a validation task to check a json configuration file is valid. Or it could be as complicated as a situation under a load test that causes some issue to arise.
    5. [ ] **DevOps Metrics/DORA**: Use DevOps metrics to measure the progress of your team. These are order of magnitude metrics. You shouldn't compare 12 minutes to 10 minutes, more hours/days/weeks - at least initially!  
