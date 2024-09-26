
## Read Before Deploying

### 1. Prerequisites

- **cert-manager Operator:** Ensure that the `cert-manager` operator is pre-installed. For more details on setting this up, refer to the [official guide](https://nightlies.apache.org/flink/flink-kubernetes-operator-docs-main/docs/try-flink-kubernetes-operator/quick-start/#deploying-the-operator).

### 2. Operator and Versioning

- This chart is based on **Flink Kubernetes Operator v1.9.0**. You can find the release [here](https://downloads.apache.org/flink/flink-kubernetes-operator-1.9.0/).
- It's crucial to keep track of operator versions, as new releases may upgrade the Flink version or introduce additional CRDs that can help manage deployments more effectively.

## Installation Guide

Off flink CRD usage [example](https://github.com/apache/flink-kubernetes-operator/blob/main/examples/pod-template.yaml)

### Variable Sections Overview

#### `default`
This section defines default values for common properties such as the **Flink version** and the **Kubernetes service account**. These default values are applicable across all Flink deployments, with the flexibility to override them based on your custom requirements.

#### `sessionMode`
Defines the properties for **Session Mode** Flink setup. Only one instance of Flink can be deployed in this mode. This setup does not include job definitions—it's focused solely on the server part.

#### `sessionJobs`
This section depends on the **Session Mode** configuration. It can be expanded to leverage external Flink clusters without needing to deploy a separate cluster for each job.

#### `applicationMode`
[Recommended for production environments](https://nightlies.apache.org/flink/flink-docs-master/docs/deployment/overview/#deployment-modes), the `applicationMode` section is designed as a list of jobs, each with its independent configuration. This mode offers a more scalable approach for managing multiple Flink jobs within the same deployment.