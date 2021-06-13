Source: https://hackernoon.com/using-github-protected-branches-to-make-soc-2-audits-suck-less-xj4i32tp

Hey, can you meet with our SOC 2 auditors’ for a couple of hours next week to talk about our SDLC process?” Oh no! This question continually causes heartburn and eventual headaches for software engineers. Spending multiple hours in a conference room explaining to auditors how your team deploys changes, what a pull request is and explaining how infrastructure as code works is not how engineers would describe a productive afternoon.



**What is SOC 2 and why does this impact engineers?**

[SOC 2](https://help.bytechek.com/en/articles/4567374-everything-and-anything-you-need-to-know-about-soc-2?ref=hackernoon.com) (or other regulatory frameworks) examinations are not going anywhere, they have become the cost of doing business for technology-enabled service organizations that provide SaaS or other services that interact with, store or transmit their customers’ sensitive information. These examinations assist organizations with proving to current and potential customers how they are securing their data. The software development process is an integral aspect of SOC 2 examinations. Every SOC 2 examination regardless of in-scope Trust Services Categories or organization type, requires an evaluation of the change management processes and procedures. Often this means spending countless hours retrieving evidence of changes, answering questions about your DevOps process with internal compliance personnel and external auditors. During a SOC 2 examination, auditors are concerned with a few specific attributes related to each software change:

1. Is there formal documentation (comments on the PR, Jira ticket, etc.)
2. Was the change tested?
3. Were there any reviews of the change or PR?
4. Was this change approved?

These questions sound like they create significant obstructions to collaboration, and speed, which is essential in a DevOps environment. However, there is a way to maintain a healthy, secure codebase while also encouraging collaboration and adherence to compliance requirements. 

**Protected Branches**

Enabling protected branches and implementing native security policies on these branches will make these audit experiences tolerable and less painful. GitHub is one of the more common software development platforms in the industry, this article will focus on GitHub protected branch configurations however these same theories can be applied to other software development platforms. [GitHub defines protected branches](https://help.github.com/en/github/administering-a-repository/about-protected-branches?ref=hackernoon.com) in the following manner, “Protected branches ensure that collaborators on your repository cannot make irrevocable changes to branches. Enabling protected branches also allows you to enable other optional checks and requirements, like required status checks and required reviews.” Protecting a branch eliminates the risk of a planned or unplanned catastrophic event where a branch is deleted. This is the first step in enabling guardrails to secure your branch. Some additional checks or requirements can be enabled with a protected branch to configure security policies 

**Recommended optional checks and requirement configurations on protected branches**

[*Require status checks to pass before merging*](https://help.github.com/en/github/administering-a-repository/about-required-status-checks?ref=hackernoon.com)

- This check requires that all continuous integration (CI) checks to pass before branches can be merged into the protected branch
- CI tools such as CircleCI, Jenkins or Travis integrate with GitHub and can provide a status check update on each prospective change
- Reduce evidence requirements for the SOC 2 audit by utilizing this configuration to display testing requirements for each change



[*Require pull request reviews before merging*](https://help.github.com/en/github/administering-a-repository/about-required-reviews-for-pull-requests?ref=hackernoon.com)

- Code reviews are important for any development lifecycle, this check requires at least one approved review before a pull request is merged. 
- This check also establishes separation of duties by preventing an engineer from merging their pull requests without a secondary review
- Reduce evidence requirements for the SOC 2 audit by utilizing this configuration to display review requirements for each change



[*Require review from Code Owners*](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/about-code-owners?ref=hackernoon.com)



- Require approval from a predetermined set of users (or owners) that must approve the change before a pull request is merged
- Reduce evidence requirements for the SOC 2 audit by utilizing this configuration to display approval requirements for each change



**Conclusion**

Security and compliance can no longer be an afterthought for DevOps teams. Integrating security configurations into the software deployment pipeline will allow developers to bake software security in every stage of the process. Compliance assessments like SOC 2 or PCI-DSS are inevitably going to impact your development team and process. Enabling native configurations to systematically enforce these security requirements will make these compliance assessments easier to obtain, maintain, and hopefully make those conversations with auditors a little shorter and less complex for all parties involved.


