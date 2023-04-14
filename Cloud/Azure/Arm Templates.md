 #azure #cloud #iaac 
  
 To implement infrastructure as code for Azure Solutions use Azure Resource Manager (ARM) templates.

Arm Templates are JSON file that defines the insfrastructure and configuration for your project.


Official Refrence Link:
https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/overview

# Benefits 

1. Declarative Syntax
2. Repeatable Results
3. Orchestration

![[Pasted image 20230411192508.png]]
4. Modular Files
5. Create any Azure Resource
6. Extensibility
7. Testing
8. Tracked Deployments
9. Preview Changes
10. Built-in Validation
11. Policy as code
12. Deployment Blueprints
13. CI/CD Integration
14. Exportable Code
15. Authoring Tools

# Template File
To write templates:

**Parameters**: Provides values during deployment that allow the same template to be used with different environments.

**Variables**: Define values that are reused in your templates. They can be constructed from parameter values.

**User-defined functions**: Create customized functions that simplify your template.

**Resources:** Specify the resources to deploy.

**Outputs**: Return values from the deployed resources.

# Template Design
How to approach a designing for template:
1. Single Template 
	![[Pasted image 20230411193517.png]]

2. Nested Template
	![[Pasted image 20230411193540.png]]

3. Multiple Template
	![[Pasted image 20230411193641.png]]
---
