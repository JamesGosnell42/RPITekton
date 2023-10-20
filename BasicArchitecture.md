CI/CD, short for Continuous Integration and Continuous Delivery, is a streamlined process that automates the building, testing, and release of software. In essence, it's a powerful automation tool that simplifies the journey from code development to its deployment.

**Steps**: In Tekton, steps (a node) are like individual actions, similar to steps in a recipe. Each step is a discrete operation, such as compiling code, running tests, or packaging software. Steps are designed to be simple and focused, making it easier to manage and troubleshoot specific tasks within a larger process.

![task](https://github.com/JamesGosnell42/RPITekton/assets/16072242/92866453-9c92-4cf3-948f-7043ae3ba907)

**Tasks**: Tasks in Tekton are groups of related steps. Think of them as subtasks within a project. A task bundles together a series of steps that need to be performed together to achieve a specific goal. For example, a "Build" task might include steps for compiling code and generating executable files, making it easier to reuse and share common procedures across different pipelines.

![step](https://github.com/JamesGosnell42/RPITekton/assets/16072242/09e3263f-038b-47ad-862d-a19e5967eed8)

**Pipelines**: Pipelines provide the overarching structure for orchestrating tasks in Tekton. You can consider pipelines as the complete recipe for your software development or delivery process. They define the order in which tasks should be executed, creating a clear roadmap for your entire project. A pipeline can include multiple tasks, ensuring that each step is performed in a logical sequence.

![pipeline](https://github.com/JamesGosnell42/RPITekton/assets/16072242/3d5dafca-eca1-4d1e-a822-43e972e48ba0)

**Triggers**: Triggers in Tekton act as the initiation mechanism for pipelines. They are like the "start" button for your plan. Triggers respond to specific events or conditions, such as code changes in a code repository or manual approvals. When a trigger is activated, it sets the pipeline into motion, enabling automated and controlled execution of tasks.

![trigger](https://github.com/JamesGosnell42/RPITekton/assets/16072242/82e4d93b-d03f-46c7-b3a2-229caba32e12)

**Pipeline Catalog**: A pipeline catalog, or pipeline marketplace, is a repository or collection of predefined, reusable pipelines. These pipelines are like well-crafted recipes for common development or deployment processes. Teams can use a pipeline catalog to access and share standardized, battle-tested pipeline templates. It simplifies the process of creating new pipelines by allowing developers to pick and choose from a catalog of pre-built, proven workflows. This enhances efficiency, reduces duplication of effort, and promotes best practices within an organization's software development processes.

Here is a showcase of how CI/CD can be used in the build - test - deploy - rollback process:

![process](https://github.com/JamesGosnell42/RPITekton/assets/16072242/c935f110-8f84-44e4-9c87-81b390d380a7)

In the case of an inner pipeline failure, the 'on-error' section within the inner pipeline is invoked. After the 'on-error' actions are executed, the outer pipeline continues without interruption. Additionally, any actions specified in the 'finally' section within the inner pipeline are executed prior to the corresponding 'finally' section in the outer pipeline, regardless of what transpires within the inner pipeline.

