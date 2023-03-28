# DevOps Portal

The Choreo Console allows you to observe the basic deployment process of a Dockerfile-based component. The Choreo DevOps Portal provides a low-level Kubernetes view of the underlying data plane resources for advanced developers who want to carry out a detailed diagnosis of Choreo components. Most advanced features on the DevOps Portal are only available for private data planes.

## Access the DevOps Portal

To access the DevOps Portal, you can either:

 - Navigate to [https://devops.choreo.dev/](https://devops.choreo.dev/) 
 
     or
 
 - Select **DevOps** from the **Profile** list in the top menu of the Choreo Console.

      ![Top menu link](../assets/img/byoc/access-devops-portal.png){.cInlineImage-xsmall}

When you open the DevOps Portal, it displays the deployment insights and the recently created components of the currently selected project as shown below:

![DevOps Portal landing page](../assets/img/devops-portal/devops-portal-landing-page.png){.cInlineImage-threeQuarter}

If you hold the pointer over the **Deployment Insights** graph, it displays the number of components you have deployed to each environment up to the date you are pointing. This count applies to the currently selected organization and project.

You can select the required organization and the project for which you need to view this data by selecting the required values in the **Organization** and **Project** lists.

## View component specific information

In the **Recently Created** section, click on a component to open it on a separate page.

![View Component On Separate Page](../assets/img/devops-portal/devops-portal-component-overview.png){.cInlineImage-threeQuarter}

On this page, you can view the information described in the following subtopics.

### Overview

The **Overview** tab displays the following information:

![Component overview in the private data plane](../assets/img/devops-portal/devops-component-overview-in-private-data-plane.png){.cInlineImage-threeQuarter}

!!! Tip
    The internal routing URL is an internal endpoint for the component. Other components in the same organization can use this URL to communicate with this component without using the public internet or an internal gateway.

In this tab, you can perform the following activities:

- Deploy or redeploy a component

    You can click **Deploy** or **Redeploy** as relevant.

- Promote the component to another environment 

    When you have multiple environments, the **Overview** tab of the DevOps Portal allows you to select the environment to which you want to promote the component as shown below: 

    ![Advance promotion](../assets/img/devops-portal/advanced-component-promotion.gif){.cInlineImage-threeQuarter}

    In doing so, you might bypass one or more environments. For example, when you promote a component to the production environment, you can bypass one or more development environments.

- Manage replicas

    If you are on a private data plane, you can click the **+** and **-** icons on this bar to change the minimum and the maximum number of replicas that you want to allow the component to have at any given time.

    ![Control no of replicas](../assets/img/devops-portal/control-no-of-replicas.png){.cInlineImage-half}

    Each row displays basic information (such as the CPU and memory usage) about an individual replica. If you move the pointer over a row, three icons will appear. These enable you to view the replica events, status, and logs.

### Containers

This tab displays information related to a selected Docker container such as the URL to the Docker image from which Choreo pulls the component, the image pull policy, resource limits and requests, exposed ports, etc.

If you are on a private plane, you can edit this information. You can also add commands and arguments to the Docker image.

### Configurations and secrets

This tab displays configurations and/or secrets that you have configured for your component.

You can also add new configurations and/or secrets.

![Create a configuration mount](../assets/img/devops-portal/create-a-configuration-mount.png){.cInlineImage-full}

### Storages

Choreo provides Kubernetes storage support for components to persist state or share volumes between containers.  
Choreo allocates a default storage volume for each component. Choreo also allows you to create and manage additional volume for components in an organization where you have set up private data plane support.

#### Create a volume mount for a component

**Prerequisite**

- Ensure the project is in an organization where you have set up the private data plane capability.

Follow these below to create a volume mount:

1. Sign in to the Choreo DevOps Portal at [https://devops.choreo.dev](https://devops.choreo.dev), select a project, and click a component to create a volume.

2. Click the **Storage** tab and then click **Let’s Get Started**. This opens the **Create Volume Mounts** pane, where you can specify volume information depending on your requirement.

3. Enter a **Volume Name**, add the required labels, and select an appropriate **Volume Type**.

    !!! Tip
        You must specify values for the fields depending on the **Volume Type** you select. For example, if the **Volume Type** is **NFS Server**, you must specify the **Server IP Address** and **Path**.

4. Click **Continue** and proceed to add container mount information.

5. For the selected container, specify a **Mount Path** and click **Finish**.

    ![Container mount information](../assets/img/devops-portal/container-mount-information.png){.cInlineImage-threeQuarter}

    This creates the volume and displays details of it in the **Volume Mounts** pane.

    ![Volume mounts](../assets/img/devops-portal/volume-mounts.png){.cInlineImage-threeQuarter}

    You can perform the following actions in the **Volume Mounts** pane:

    - Create new volumes and mounts.
    - Delete existing volumes and mounts.
    - Search for volumes you have created.

### Health Checks

This tab allows you to define health checks for a selected container. 

![Create health check](../assets/img/devops-portal/create-a-health-check.png){.cInlineImage-xsmall}

### Scaling

In this tab, you can define the thresholds based on which the component can scale horizontally.

![Scaling](../assets/img/devops-portal/scaling.png){.cInlineImage-half}

The threshold limits for memory and CPU consumption are available by default, and you can edit them if required. To add a new threshold criterion, click **Create**. The **Create a Scaling Threshold** pane opens. In this pane, you can select more threshold criteria. You can also create custom thresholds.

When the component reaches the threshold for any resource, the system automatically creates a new replica for it. In this tab, you can specify the minimum and the maximum number of replicas that you want to allow the component to have at any given time.









