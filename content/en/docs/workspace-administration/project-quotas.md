---
title: "Project Quotas"
keywords: 'KubeSphere, Kubernetes, projects, quotas, resources, requests, limits'
description: 'Set requests and limits to control resource usage in a project.'
linkTitle: "Project Quotas"
weight: 9600
---

KubeSphere uses [Kubernetes requests and limits](https://kubesphere.io/blogs/understand-requests-and-limits-in-kubernetes/) to control resource (for example, CPU and memory) usage in a project, also known as [ResourceQuotas](https://kubernetes.io/docs/concepts/policy/resource-quotas/) in Kubernetes. Requests make sure a project can get the resources it needs as they are specifically guaranteed and reserved. On the contrary, limits ensure that a project can never use resources above a certain value.

Besides CPU and memory, you can also set resource quotas for other objects separately such as Pods, [Deployments](../../project-user-guide/application-workloads/deployments/), [Jobs](../../project-user-guide/application-workloads/jobs/), [Services](../../project-user-guide/application-workloads/services/) and [ConfigMaps](../../project-user-guide/configuration/configmaps/) in a project.

This tutorial demonstrates how to configure quotas for a project.

## Prerequisites

You have an available workspace, a project and an account (`ws-admin`). The account must have the `admin` role at the workspace level. For more information, see [Create Workspaces, Projects, Accounts and Roles](../../quick-start/create-workspace-and-project/).

{{< notice note >}}

If you use the account `project-admin` (an account of the `admin` role at the project level), you can set project quotas as well for a new project (i.e. its quotas remain unset). However, `project-admin` cannot change project quotas once they are set. Generally, it is the responsibility of `ws-admin` to set limits and requests for a project. `project-admin` is responsible for [setting limit ranges](../../project-administration/container-limit-ranges/) for containers in a project.

{{</ notice >}} 

## Set Project Quotas

1. Log in to the console as `ws-admin` and go to a project. On the **Overview** page, you can see project quotas remain unset if the project is newly created. Click **Set** to configure quotas.

   ![project-quotas](/images/docs/workspace-administration/project-quotas/project-quotas.png)

2. In the dialog that appears, you can see that KubeSphere does not set any requests or limits for a project by default. To set 
limits to control CPU and memory resources, use the slider to move to a desired value or enter numbers directly. Leaving a field blank means you do not set any requests or limits. 

   ![set-project-quotas](/images/docs/workspace-administration/project-quotas/set-project-quotas.png)

   {{< notice note >}}

   The limit can never be lower than the request.

   {{</ notice >}} 

3. To set quotas for other resources, click **Add Quota Item** and select an object from the list.

   ![set-other-resouce-quotas](/images/docs/workspace-administration/project-quotas/set-other-resouce-quotas.png)

4. Click **OK** to finish setting quotas.

5. Go to **Basic Information** in **Project Settings**, and you can see all resource quotas for the project.

6. To change project quotas, click **Manage Project** on the **Basic Information** page and select **Edit Quota**.

   {{< notice note >}}

   For [a multi-cluster project](../../project-administration/project-and-multicluster-project/#multi-cluster-projects), the option **Edit Quota** does not display in the **Manage Project** drop-down menu. To set quotas for a multi-cluster project, go to **Quota Management** under **Project Settings** and click **Edit Quota**. Note that as a multi-cluster project runs across clusters, you can set resource quotas on different clusters separately.

   {{</ notice >}} 

7. Change project quotas in the dialog that appears and click **OK**.

## See Also

[Container Limit Ranges](../../project-administration/container-limit-ranges/)
