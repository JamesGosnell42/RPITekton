<span style="font-size: 40px;">**Setting Up Docker for Tekton Pipelines:**</span>

Docker is an essential component for running Tekton Pipelines efficiently. In this guide, we will walk you through the process of setting up Docker for Tekton Pipelines. We'll also provide detailed instructions for configuring Docker Desktop, including CPU, RAM, and swap space adjustments, and setting an insecure registry for seamless integration.

<span style="font-size: 40px;">**Prerequisites:**</span>

Before you begin, ensure that you have installed all the required tools for your development environment. While Docker Desktop is available for both Windows and macOS, setting up these tools on a Linux system is recommended for a smoother experience.

<span style="font-size: 40px;">**Configuring Docker Desktop's CPU, RAM, and Swap Space (for WSL users):**</span>

If you're using Docker Desktop with Windows Subsystem for Linux (WSL), it's crucial to allocate the appropriate system resources for a seamless experience. Follow these steps to configure CPU, RAM, and swap space:

Open a PowerShell or command prompt.

Navigate to your home directory using the cd ~ command, or use cd .. if necessary to reach your home directory (e.g., C: or D:).

Move to your user profile by running the command cd %UserProfile%.

Create or edit the .wslconfig file by using a text editor. You can open it with Notepad using the command notepad .wslconfig.

This will open a new Notepad window where you can configure your Docker Desktop settings.

Add the following configuration to allocate resources as needed. Save the file:

```
[wsl2]
memory=10GB
processors=6
swap=2GB
```

This configuration sets the memory, processor cores, and swap space to appropriate values for your development environment. Feel free to adjust these values according to your system's capabilities and requirements.

Setting Up an Insecure Registry with Docker for Desktop

If you need to access an insecure registry, you can configure Docker Desktop to allow this. Follow these steps:

Open Docker Desktop and go to "Settings."

In the settings menu, navigate to "Docker Engine."

In the "Docker Engine" section, find the "insecure-registries" configuration and add your registry's URL with the port (e.g., myregistrydomain.com:5000) as shown below:

```
{
  "builder": {
    "gc": {
      "defaultKeepStorage": "20GB",
      "enabled": true
    }
  },
  "experimental": false,
  "insecure-registries": [
    "myregistrydomain.com:5000"
  ]
}
```

Adding your insecure registry to the Docker Engine ensures that Docker can communicate with the specified registry without any security restrictions.

With these configurations in place, your Docker environment is set up to work seamlessly with Tekton Pipelines, and you can confidently proceed with your development and CI/CD processes.
