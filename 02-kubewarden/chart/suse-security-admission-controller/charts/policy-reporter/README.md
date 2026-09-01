# policy-reporter

Policy Reporter adds observability and monitoring possibilities to your cluster security based on the PolicyReport CRDs.

![Version: 3.9.1](https://img.shields.io/badge/Version-3.9.1-informational?style=flat-square) ![AppVersion: 3.9.0](https://img.shields.io/badge/AppVersion-3.9.0-informational?style=flat-square)

## Documentation

You can find detailed Information and Screens about Features and Configurations in the [Documentation](https://kyverno.github.io/policy-reporter-docs).

## Installation with Helm v3

### Basic Installation

The basic installation provides an Prometheus Metrics Endpoint and different REST APIs, for more details have a look at the [Documentation](https://kyverno.github.io/policy-reporter/guide/02-getting-started).

```bash
helm install policy-reporter oci://dp.apps.rancher.io/charts/policy-reporter -n policy-reporter --create-namespace
```

## Policy Reporter UI

You can use the Policy Reporter as standalone Application along with the optional UI SubChart.

### Installation with Policy Reporter UI and Kyverno Plugin enabled

```bash
helm install policy-reporter oci://dp.apps.rancher.io/charts/policy-reporter --set plugin.kyverno.enabled=true --set ui.enabled=true -n policy-reporter --create-namespace
kubectl port-forward service/policy-reporter-ui 8082:8080 -n policy-reporter
```
Open `http://localhost:8082/` in your browser.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Anti-affinity to disallow deploying client and master nodes on the same worker node |
| annotations | object | `{}` | Key/value pairs that are attached to all resources. |
| apiVersionOverride | object | `{"podDisruptionBudget":""}` | Overwrite apiVersion for specific resources |
| autoMemoryLimit.enabled | bool | `true` |  |
| autoMemoryLimit.ratio | float | `0.9` |  |
| basicAuth.password | string | `""` | HTTP BasicAuth password |
| basicAuth.secretRef | optional | `""` | Secret reference to get username and/or password from |
| basicAuth.username | string | `""` | HTTP BasicAuth username |
| database.connectionMaxIdleTime | int | `0` | Maximum amount of time in minutes a connection may be idle, supported for mysql and postgres |
| database.connectionMaxLifetime | int | `0` | Maximum amount of time in minutes a connection may be reused, supported for mysql and postgres |
| database.database | string | `""` | Database |
| database.dsn | string | `""` | Instead of configure the individual values you can also provide an DSN string example postgres: postgres://postgres:password@localhost:5432/postgres?sslmode=disable example mysql: root:password@tcp(localhost:3306)/test?tls=false |
| database.enableSSL | bool | `false` | Enables SSL |
| database.host | string | `""` | Host Address |
| database.maxIdleConnections | int | `25` | Maximum number of idle connections, supported for mysql and postgres |
| database.maxOpenConnections | int | `25` | Maximum number of open connections, supported for mysql and postgres |
| database.metrics | bool | `false` | Enables database related metrics, connection status and query histogram |
| database.mountedSecret | string | `""` |  |
| database.password | string | `""` | Password |
| database.secretRef | string | `""` | Read configuration from an existing Secret supported fields: username, password, host, dsn, database |
| database.timeout | int | `10` | Timeout for database operations in seconds, supported for mysql and postgres |
| database.type | string | `""` | Use an external Database, supported: mysql, postgres, mariadb |
| database.username | string | `""` | Username |
| emailReports.clusterName | optional | `""` | - Displayed in the email report if configured |
| emailReports.graphAPI.azureADEndpoint | string | `"https://login.microsoftonline.com"` | Microsoft Graph API Azure AD Endpoint override |
| emailReports.graphAPI.bcc | list | `[]` | Microsoft Graph API BCC Recipients |
| emailReports.graphAPI.cc | list | `[]` | Microsoft Graph API CC Recipients |
| emailReports.graphAPI.clientID | string | `""` | Microsoft Graph API Client ID |
| emailReports.graphAPI.clientSecret | string | `""` | Microsoft Graph API Client Secret |
| emailReports.graphAPI.disableSaveToSentItems | bool | `false` | Disable saving sent messages to the Sent Items folder |
| emailReports.graphAPI.enabled | bool | `false` | Enable Microsoft Graph API for E-Mail reports, takes precedence over SMTP |
| emailReports.graphAPI.graphEndpoint | string | `"https://graph.microsoft.com"` | Microsoft Graph API endpoint override |
| emailReports.graphAPI.secretRef | optional | `""` | Name of an existing Secret with a `clientSecret` key, used instead of `clientSecret` |
| emailReports.graphAPI.tenant | string | `""` | Microsoft Graph API Tenant ID |
| emailReports.graphAPI.userID | string | `""` | Microsoft Graph API User ID (Sender) |
| emailReports.resources | object | `{}` | Resource constraints for the created CronJobs |
| emailReports.smtp.certificate | string | `""` | SMTP Server Certificate file path |
| emailReports.smtp.encryption | string | `""` | SMTP Encryption Default is none, supports ssl/tls and starttls |
| emailReports.smtp.from | string | `""` | Displayed from email address |
| emailReports.smtp.host | string | `""` | SMTP Server Host |
| emailReports.smtp.password | string | `""` | SMTP Password |
| emailReports.smtp.port | int | `465` | SMTP Server Port |
| emailReports.smtp.secret | optional | `""` | Secret reference to provide the complete or partial SMTP configuration |
| emailReports.smtp.skipTLS | bool | `false` | Skip SMTP TLS verification |
| emailReports.smtp.username | string | `""` | SMTP Username |
| emailReports.summary.activeDeadlineSeconds | int | `300` | CronJob activeDeadlineSeconds |
| emailReports.summary.backoffLimit | int | `3` | CronJob backoffLimit |
| emailReports.summary.channels | optional | `[]` | Channels can be used to to send only a subset of namespaces / sources to dedicated email addresses |
| emailReports.summary.enabled | bool | `false` | Enable Summary E-Mail reports |
| emailReports.summary.filter | optional | `{}` | Report filter |
| emailReports.summary.restartPolicy | string | `"Never"` | CronJob restartPolicy |
| emailReports.summary.schedule | string | `"0 8 * * *"` | CronJob schedule |
| emailReports.summary.to | list | `[]` | List of receiver email addresses |
| emailReports.summary.ttlSecondsAfterFinished | int | `0` | CronJob ttlSecondsAfterFinished |
| emailReports.titlePrefix | string | `"Report"` | Title prefix in the email subject |
| emailReports.violations.activeDeadlineSeconds | int | `300` | CronJob activeDeadlineSeconds |
| emailReports.violations.backoffLimit | int | `3` | CronJob backoffLimit |
| emailReports.violations.channels | optional | `[]` | Channels can be used to to send only a subset of namespaces / sources to dedicated email addresses |
| emailReports.violations.enabled | bool | `false` | Enable Violation Summary E-Mail reports |
| emailReports.violations.filter | optional | `{}` | Report filter |
| emailReports.violations.restartPolicy | string | `"Never"` | CronJob restartPolicy |
| emailReports.violations.schedule | string | `"0 8 * * *"` | CronJob schedule |
| emailReports.violations.to | list | `[]` | List of receiver email addresses |
| emailReports.violations.ttlSecondsAfterFinished | int | `0` | CronJob ttlSecondsAfterFinished |
| envVars | list | `[]` | Allow additional env variables to be added |
| existingTargetConfig.enabled | bool | `false` | Use an already existing configuration |
| existingTargetConfig.name | string | `""` | Name of the secret with the config |
| existingTargetConfig.subPath | string | `""` | SubPath within the secret (defaults to config.yaml) |
| extraConfig | object | `{}` | Extra configuration options appended to core policy reporter |
| extraManifests | list | `[]` | list of extra manifests |
| extraVolumes.volumeMounts | list | `[]` | Deployment volumeMounts |
| extraVolumes.volumes | list | `[]` | Deployment values |
| fullnameOverride | string | `"policy-reporter"` | Overwrite the fullname of all resources |
| global.imagePullSecrets | list | `[]` | Global override for container image registry pull secrets |
| global.imageRegistry | string | `""` | Global override for container image registry |
| global.labels | object | `{}` | additional labels added on each resource |
| httproute.annotations | object | `{}` | Additional HTTPRoute annotations |
| httproute.enabled | bool | `false` | Enable HTTPRoute resource (Gateway API alternative to Ingress) Requires Gateway API CRDs (v1) installed in cluster https://gateway-api.sigs.k8s.io/ |
| httproute.hostnames | list | `[]` | List of hostnames for HTTPRoute |
| httproute.labels | object | `{}` | Additional HTTPRoute labels |
| httproute.parentRefs | list | `[]` | Gateway API parentRefs (list of Gateway references) Must reference an existing Gateway resource |
| httproute.rules | list | `[{"matches":[{"path":{"type":"PathPrefix","value":"/"}}]}]` | HTTPRoute rules configuration Allows advanced routing with matches and filters |
| image.pullPolicy | string | `"IfNotPresent"` | Image pullPolicy |
| image.registry | string | `"dp.apps.rancher.io"` | Image registry |
| image.repository | string | `"containers/policy-reporter"` | Image repository |
| image.tag | string | `"3.9.0-11.3"` | Image tag |
| imagePullSecrets | list | `[]` | Image pullSecrets |
| ingress.annotations | object | `{}` | Annotations for the Ingress |
| ingress.className | string | `""` | Ingress className |
| ingress.enabled | bool | `false` | Create Ingress This ingress exposes the policy-reporter core app. |
| ingress.hosts | string | `nil` | Ingress host list |
| ingress.labels | object | `{}` | Labels for the Ingress |
| ingress.tls | list | `[]` | Ingress tls list |
| leaderElection.leaseDuration | int | `15` |  |
| leaderElection.releaseOnCancel | bool | `true` |  |
| leaderElection.renewDeadline | int | `10` |  |
| leaderElection.retryPeriod | int | `2` |  |
| livenessProbe | object | `{"httpGet":{"path":"/ready","port":"http"}}` | Deployment livenessProbe for policy-reporter |
| logging.encoding | string | `"console"` | Log encoding possible encodings are console and json |
| logging.logLevel | int | `0` | Log level default info |
| logging.server | bool | `false` | Enables server access logging |
| metrics.customLabels | list | `[]` | List of used labels in custom mode Supported fields are: ["namespace", "rule", "policy", "report" // Report name, "kind" // resource kind, "name" // resource name, "status", "severity", "category", "source"] |
| metrics.enabled | bool | `false` | Enables Prometheus Metrics |
| metrics.filter | object | `{}` | Filter results to reduce cardinality |
| metrics.mode | string | `"detailed"` | Metric Mode allows to customize labels Allowed values: detailed, simple, custom |
| monitoring.annotations | object | `{}` | Key/value pairs that are attached to all resources. |
| monitoring.clusterPolicyReportDetails.errorTable.enabled | bool | `true` |  |
| monitoring.clusterPolicyReportDetails.errorTable.height | int | `4` |  |
| monitoring.clusterPolicyReportDetails.failTable.enabled | bool | `true` |  |
| monitoring.clusterPolicyReportDetails.failTable.height | int | `8` |  |
| monitoring.clusterPolicyReportDetails.passTable.enabled | bool | `true` |  |
| monitoring.clusterPolicyReportDetails.passTable.height | int | `8` |  |
| monitoring.clusterPolicyReportDetails.statusRow.height | int | `6` |  |
| monitoring.clusterPolicyReportDetails.statusTimeline.enabled | bool | `true` |  |
| monitoring.clusterPolicyReportDetails.statusTimeline.height | int | `8` |  |
| monitoring.clusterPolicyReportDetails.warningTable.enabled | bool | `true` |  |
| monitoring.clusterPolicyReportDetails.warningTable.height | int | `4` |  |
| monitoring.enabled | bool | `false` | Enables the Prometheus Operator integration |
| monitoring.grafana.dashboards.enable.clusterPolicyReportDetails | bool | `true` | Enable the ClusterPolicyReport Dashboard |
| monitoring.grafana.dashboards.enable.overview | bool | `true` | Enable the Overview Dashboard |
| monitoring.grafana.dashboards.enable.policyReportDetails | bool | `true` | Enable the PolicyReport Dashboard |
| monitoring.grafana.dashboards.enabled | bool | `true` | Enable the deployment of grafana dashboards |
| monitoring.grafana.dashboards.label | string | `"grafana_dashboard"` | Label to find dashboards using the k8s sidecar |
| monitoring.grafana.dashboards.labelFilter | list | `[]` | List of custom label filter Used to add filter for report label based metric labels defined in custom mode |
| monitoring.grafana.dashboards.multicluster.enabled | bool | `false` | Enable cluster filter in all dashboards |
| monitoring.grafana.dashboards.multicluster.label | string | `"cluster"` | Metric Label which is used to filter clusters |
| monitoring.grafana.dashboards.value | string | `"1"` | Label value to find dashboards using the k8s sidecar |
| monitoring.grafana.datasource.label | string | `"Prometheus"` | Grafana Datasource Label |
| monitoring.grafana.datasource.pluginId | string | `"prometheus"` | Grafana Datasource PluginId |
| monitoring.grafana.datasource.pluginName | string | `"Prometheus"` | Grafana Datasource PluginName |
| monitoring.grafana.folder.annotation | string | `"grafana_folder"` | Annotation to enable folder storage using the k8s sidecar |
| monitoring.grafana.folder.name | string | `"Policy Reporter"` | Grafana folder in which to store the dashboards |
| monitoring.grafana.grafanaDashboard.allowCrossNamespaceImport | bool | `true` | Allow cross Namespace import |
| monitoring.grafana.grafanaDashboard.enabled | bool | `false` | Create GrafanaDashboard custom resource referencing to the configMap. according to https://grafana-operator.github.io/grafana-operator/docs/examples/dashboard_from_configmap/readme/ |
| monitoring.grafana.grafanaDashboard.folder | string | `"kyverno"` | Dashboard folder |
| monitoring.grafana.grafanaDashboard.matchLabels | object | `{"dashboards":"grafana"}` | Label match selector |
| monitoring.grafana.namespace | string | `nil` | Naamespace for configMap of grafana dashboards |
| monitoring.policyReportDetails.errorTable.enabled | bool | `true` |  |
| monitoring.policyReportDetails.errorTable.height | int | `4` |  |
| monitoring.policyReportDetails.failTable.enabled | bool | `true` |  |
| monitoring.policyReportDetails.failTable.height | int | `8` |  |
| monitoring.policyReportDetails.firstStatusRow.height | int | `8` |  |
| monitoring.policyReportDetails.passTable.enabled | bool | `true` |  |
| monitoring.policyReportDetails.passTable.height | int | `8` |  |
| monitoring.policyReportDetails.secondStatusRow.enabled | bool | `true` |  |
| monitoring.policyReportDetails.secondStatusRow.height | int | `2` |  |
| monitoring.policyReportDetails.statusTimeline.enabled | bool | `true` |  |
| monitoring.policyReportDetails.statusTimeline.height | int | `8` |  |
| monitoring.policyReportDetails.warningTable.enabled | bool | `true` |  |
| monitoring.policyReportDetails.warningTable.height | int | `4` |  |
| monitoring.policyReportOverview.failingClusterPolicyRuleTable.height | int | `10` |  |
| monitoring.policyReportOverview.failingPolicyRuleTable.height | int | `10` |  |
| monitoring.policyReportOverview.failingSummaryRow.height | int | `8` |  |
| monitoring.policyReportOverview.failingTimeline.height | int | `10` |  |
| monitoring.serviceMonitor.enabled | bool | `true` |  |
| monitoring.serviceMonitor.honorLabels | bool | `false` | HonorLabels chooses the metrics labels on collisions with target labels |
| monitoring.serviceMonitor.interval | optional | `nil` | Scrape interval |
| monitoring.serviceMonitor.labels | object | `{}` | Labels to match the serviceMonitorSelector of the Prometheus Resource |
| monitoring.serviceMonitor.metricRelabelings | list | `[]` | See serviceMonitor.relabelings |
| monitoring.serviceMonitor.namespace | string | `nil` | Allow to override the namespace for serviceMonitor |
| monitoring.serviceMonitor.namespaceSelector | optional | `{}` | NamespaceSelector |
| monitoring.serviceMonitor.relabelings | list | `[]` | ServiceMonitor Relabelings https://github.com/prometheus-operator/prometheus-operator/blob/main/Documentation/api.md#relabelconfig |
| monitoring.serviceMonitor.scrapeTimeout | optional | `nil` | ScrapeTimeout |
| monitoring.serviceMonitor.secure | bool | `false` | Is TLS required for endpoint |
| monitoring.serviceMonitor.tlsConfig | object | `{}` | TLS Configuration for endpoint |
| nameOverride | string | `""` | Override the chart name used for all resources |
| namespaceOverride | string | `""` | Overwrite the namespace of all resources |
| networkPolicy.egress | list | `[{"ports":[{"port":6443,"protocol":"TCP"}],"to":null}]` | Egress rule to allow Kubernetes API Server access |
| networkPolicy.enabled | bool | `false` | Create NetworkPolicy |
| networkPolicy.ingress | list | `[]` |  |
| nodeSelector | object | `{}` | Node labels for pod assignment ref: https://kubernetes.io/docs/user-guide/node-selection/ |
| periodicSync.enabled | bool | `false` |  |
| periodicSync.interval | int | `30` |  |
| plugin.kyverno.affinity | object | `{}` | Affinity constraints. |
| plugin.kyverno.blockReports.enabled | bool | `false` | Enables he BlockReport feature |
| plugin.kyverno.blockReports.eventNamespace | string | `"default"` | Watches for Kyverno Events in the configured namespace leave blank to watch in all namespaces |
| plugin.kyverno.blockReports.policyReport.annotations | list | `[]` | Annotations for all created (Cluster)PolicyReports |
| plugin.kyverno.blockReports.policyReport.labels | list | `[]` | Labels for all created (Cluster)PolicyReports |
| plugin.kyverno.blockReports.results.keepOnlyLatest | bool | `false` | Keep only the latest of duplicated events |
| plugin.kyverno.blockReports.results.maxPerReport | int | `200` | Max items per PolicyReport resource |
| plugin.kyverno.blockReports.source | string | `"Kyverno Event"` | Used value for the source field in the created (Cluster)PolicyReports |
| plugin.kyverno.enabled | bool | `false` | Enable Kyverno Plugin |
| plugin.kyverno.envVars | list | `[]` | Allow additional env variables to be added |
| plugin.kyverno.extraConfig | object | `{}` | Extra configuration options appended to kyverno plugin settings |
| plugin.kyverno.extraVolumes.volumeMounts | list | `[]` | Deployment volumeMounts |
| plugin.kyverno.extraVolumes.volumes | list | `[]` | Deployment values |
| plugin.kyverno.httproute.annotations | object | `{}` | Additional HTTPRoute annotations |
| plugin.kyverno.httproute.enabled | bool | `false` | Enable HTTPRoute resource (Gateway API alternative to Ingress) Requires Gateway API CRDs (v1) installed in cluster https://gateway-api.sigs.k8s.io/ |
| plugin.kyverno.httproute.hostnames | list | `[]` | List of hostnames for HTTPRoute |
| plugin.kyverno.httproute.labels | object | `{}` | Additional HTTPRoute labels |
| plugin.kyverno.httproute.parentRefs | list | `[]` | Gateway API parentRefs (list of Gateway references) Must reference an existing Gateway resource |
| plugin.kyverno.httproute.rules | list | `[{"matches":[{"path":{"type":"PathPrefix","value":"/"}}]}]` | HTTPRoute rules configuration Allows advanced routing with matches and filters |
| plugin.kyverno.image.pullPolicy | string | `"IfNotPresent"` | Image PullPolicy |
| plugin.kyverno.image.registry | string | `"dp.apps.rancher.io"` | Image registry |
| plugin.kyverno.image.repository | string | `"containers/policy-reporter-kyverno-plugin"` | Image repository |
| plugin.kyverno.image.tag | string | `"0.7.0-11.3"` | Image tag |
| plugin.kyverno.imagePullSecrets | list | `[]` | Image pull secrets for image verification policies, this will define the `--imagePullSecrets` argument |
| plugin.kyverno.ingress.annotations | object | `{}` | Ingress annotations. |
| plugin.kyverno.ingress.className | string | `""` | Ingress class name. |
| plugin.kyverno.ingress.enabled | bool | `false` | Create ingress resource. |
| plugin.kyverno.ingress.hosts | list | `[]` | List of ingress host configurations. |
| plugin.kyverno.ingress.labels | object | `{}` | Ingress labels. |
| plugin.kyverno.ingress.tls | list | `[]` | List of ingress TLS configurations. |
| plugin.kyverno.leaderElection.leaseDuration | int | `15` | LeaseDuration is the duration that non-leader candidates will wait to force acquire leadership. |
| plugin.kyverno.leaderElection.lockName | string | `"kyverno-plugin"` | Lock Name |
| plugin.kyverno.leaderElection.releaseOnCancel | bool | `true` | Released lock when the run context is cancelled. |
| plugin.kyverno.leaderElection.renewDeadline | int | `10` | RenewDeadline is the duration that the acting master will retry refreshing leadership before giving up. |
| plugin.kyverno.leaderElection.retryPeriod | int | `2` | RetryPeriod is the duration the LeaderElector clients should wait between tries of actions. |
| plugin.kyverno.logging.api | bool | `false` | Enables external API request logging |
| plugin.kyverno.logging.encoding | string | `"console"` | log encoding possible encodings are console and json |
| plugin.kyverno.logging.logLevel | int | `0` | log level default info |
| plugin.kyverno.logging.server | bool | `false` | Enables Server access logging |
| plugin.kyverno.networkPolicy.egress | list | `[{"ports":[{"port":6443,"protocol":"TCP"}]}]` | A list of valid from selectors according to https://kubernetes.io/docs/concepts/services-networking/network-policies. Enables Kubernetes API Server by default |
| plugin.kyverno.networkPolicy.enabled | bool | `false` | When true, use a NetworkPolicy to allow ingress to the webhook This is useful on clusters using Calico and/or native k8s network policies in a default-deny setup. |
| plugin.kyverno.networkPolicy.ingress | list | `[]` | A list of valid from selectors according to https://kubernetes.io/docs/concepts/services-networking/network-policies. |
| plugin.kyverno.nodeSelector | object | `{}` | Node labels for pod assignment |
| plugin.kyverno.podAnnotations | object | `{}` | Additional annotations to add to each pod |
| plugin.kyverno.podDisruptionBudget.maxUnavailable | string | `nil` | Configures the maximum unavailable pods for kyvernoPlugin disruptions. Cannot be used if `minAvailable` is set. |
| plugin.kyverno.podDisruptionBudget.minAvailable | int | `1` | Configures the minimum available pods for kyvernoPlugin disruptions. Cannot be used if `maxUnavailable` is set. |
| plugin.kyverno.podLabels | object | `{}` | Additional labels to add to each pod |
| plugin.kyverno.podSecurityContext | object | `{"runAsGroup":1234,"runAsUser":1234}` | Security context for the pod |
| plugin.kyverno.priorityClassName | string | `""` | Deployment priorityClassName |
| plugin.kyverno.rbac.enabled | bool | `true` | Create RBAC resources |
| plugin.kyverno.replicaCount | int | `1` | Deployment replica count |
| plugin.kyverno.resources | object | `{}` | Resource constraints |
| plugin.kyverno.revisionHistoryLimit | int | `10` | The number of revisions to keep |
| plugin.kyverno.securityContext.allowPrivilegeEscalation | bool | `false` |  |
| plugin.kyverno.securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| plugin.kyverno.securityContext.privileged | bool | `false` |  |
| plugin.kyverno.securityContext.readOnlyRootFilesystem | bool | `true` |  |
| plugin.kyverno.securityContext.runAsNonRoot | bool | `true` |  |
| plugin.kyverno.securityContext.runAsUser | int | `1234` |  |
| plugin.kyverno.securityContext.seccompProfile.type | string | `"RuntimeDefault"` |  |
| plugin.kyverno.selectorLabels | object | `{}` | Custom selector labels, overwrites the default set |
| plugin.kyverno.server.port | int | `8080` | Application port |
| plugin.kyverno.service.annotations | object | `{}` | Service annotations. |
| plugin.kyverno.service.labels | object | `{}` | Service labels. |
| plugin.kyverno.service.port | int | `8080` | Service port. |
| plugin.kyverno.service.type | string | `"ClusterIP"` | Service type. |
| plugin.kyverno.serviceAccount.annotations | object | `{}` | Annotations for the ServiceAccount |
| plugin.kyverno.serviceAccount.automount | bool | `true` | Enable ServiceAccount automount |
| plugin.kyverno.serviceAccount.create | bool | `true` | Create ServiceAccount |
| plugin.kyverno.serviceAccount.name | string | `""` | The ServiceAccount name |
| plugin.kyverno.tolerations | list | `[]` | List of node taints to tolerate |
| plugin.kyverno.topologySpreadConstraints | object | `{}` | Pod Topology Spread Constraints for the kyverno plugin. |
| plugin.kyverno.updateStrategy | object | `{}` | Deployment update strategy. Ref: https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#strategy |
| plugin.trivy.affinity | object | `{}` | Affinity constraints. |
| plugin.trivy.cli.image.pullPolicy | string | `"IfNotPresent"` | Image PullPolicy |
| plugin.trivy.cli.image.registry | string | `"dp.apps.rancher.io"` | Image registry |
| plugin.trivy.cli.image.repository | string | `"containers/trivy"` | Image repository |
| plugin.trivy.cli.image.tag | string | `"0.74.0-16.4"` | Image tag Defaults to `Chart.AppVersion` if omitted |
| plugin.trivy.cveawg.disable | bool | `false` | disable external CVEAWG API calls. |
| plugin.trivy.dbVolume | object | `{}` | If set the volume for dbVolume is freely configurable below "- name: dbVolume". If no value is set an emptyDir is used. |
| plugin.trivy.enabled | bool | `false` | Enable Trivy Operator Plugin |
| plugin.trivy.envVars | list | `[]` | Allow additional env variables to be added |
| plugin.trivy.extraArgs | object | `{}` | Additional container args. |
| plugin.trivy.extraConfig | object | `{}` | Extra configuration options appended to trivy plugin settings |
| plugin.trivy.extraVolumes.volumeMounts | list | `[]` | Deployment volumeMounts |
| plugin.trivy.extraVolumes.volumes | list | `[]` | Deployment values |
| plugin.trivy.github.disable | bool | `false` | disable GitHub API calls. |
| plugin.trivy.github.token | string | `""` | optional github token for authenticated GitHub API calls. |
| plugin.trivy.image.pullPolicy | string | `"IfNotPresent"` | Image PullPolicy |
| plugin.trivy.image.registry | string | `"dp.apps.rancher.io"` | Image registry |
| plugin.trivy.image.repository | string | `"containers/policy-reporter-trivy-plugin"` | Image repository |
| plugin.trivy.image.tag | string | `"0.5.0-11.3"` | Image tag Defaults to `Chart.AppVersion` if omitted |
| plugin.trivy.imagePullSecrets | list | `[]` | Image pull secrets for image verification policies, this will define the `--imagePullSecrets` argument |
| plugin.trivy.ingress.annotations | object | `{}` | Ingress annotations. |
| plugin.trivy.ingress.className | string | `""` | Ingress class name. |
| plugin.trivy.ingress.enabled | bool | `false` | Create ingress resource. |
| plugin.trivy.ingress.hosts | list | `[]` | List of ingress host configurations. |
| plugin.trivy.ingress.labels | object | `{}` | Ingress labels. |
| plugin.trivy.ingress.tls | list | `[]` | List of ingress TLS configurations. |
| plugin.trivy.livenessProbe | object | `{"httpGet":{"path":"/vulnr/v1/policies","port":"http"},"timeoutSeconds":3}` | Deployment livenessProbe for policy-reporter-trivy-plugin |
| plugin.trivy.logging.api | bool | `false` | Enables external API request logging |
| plugin.trivy.logging.encoding | string | `"console"` | log encoding possible encodings are console and json |
| plugin.trivy.logging.logLevel | int | `0` | log level default info |
| plugin.trivy.logging.server | bool | `false` | Enables Server access logging |
| plugin.trivy.networkPolicy.egress | list | `[{"ports":[{"port":6443,"protocol":"TCP"}]}]` | A list of valid from selectors according to https://kubernetes.io/docs/concepts/services-networking/network-policies. Enables Kubernetes API Server by default |
| plugin.trivy.networkPolicy.enabled | bool | `false` | When true, use a NetworkPolicy to allow ingress to the webhook This is useful on clusters using Calico and/or native k8s network policies in a default-deny setup. |
| plugin.trivy.networkPolicy.ingress | list | `[]` | A list of valid from selectors according to https://kubernetes.io/docs/concepts/services-networking/network-policies. |
| plugin.trivy.nodeSelector | object | `{}` | Node labels for pod assignment |
| plugin.trivy.podAnnotations | object | `{}` | Additional annotations to add to each pod |
| plugin.trivy.podDisruptionBudget.maxUnavailable | string | `nil` | Configures the maximum unavailable pods for kyvernoPlugin disruptions. Cannot be used if `minAvailable` is set. |
| plugin.trivy.podDisruptionBudget.minAvailable | int | `1` | Configures the minimum available pods for kyvernoPlugin disruptions. Cannot be used if `maxUnavailable` is set. |
| plugin.trivy.podLabels | object | `{}` | Additional labels to add to each pod |
| plugin.trivy.podSecurityContext | object | `{"runAsGroup":1234,"runAsUser":1234}` | Security context for the pod |
| plugin.trivy.policyReporter.certificate | string | `""` | TLS Certificate file path |
| plugin.trivy.policyReporter.secretRef | string | `""` | Secret to read the API configuration from supports `host`, `certificate`, `skipTLS`, `username`, `password` key |
| plugin.trivy.policyReporter.skipTLS | bool | `false` | Skip TLS Verification |
| plugin.trivy.priorityClassName | string | `""` | Deployment priorityClassName |
| plugin.trivy.rbac.enabled | bool | `true` | Create RBAC resources |
| plugin.trivy.readinessProbe | object | `{"httpGet":{"path":"/vulnr/v1/policies","port":"http"},"timeoutSeconds":3}` | Deployment readinessProbe for policy-reporter-trivy-plugin |
| plugin.trivy.replicaCount | int | `1` | Deployment replica count |
| plugin.trivy.resources | object | `{}` | Resource constraints |
| plugin.trivy.revisionHistoryLimit | int | `10` | The number of revisions to keep |
| plugin.trivy.securityContext.allowPrivilegeEscalation | bool | `false` |  |
| plugin.trivy.securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| plugin.trivy.securityContext.privileged | bool | `false` |  |
| plugin.trivy.securityContext.readOnlyRootFilesystem | bool | `true` |  |
| plugin.trivy.securityContext.runAsNonRoot | bool | `true` |  |
| plugin.trivy.securityContext.runAsUser | int | `1234` |  |
| plugin.trivy.securityContext.seccompProfile.type | string | `"RuntimeDefault"` |  |
| plugin.trivy.selectorLabels | object | `{}` | Custom selector labels, overwrites the default set |
| plugin.trivy.server.port | int | `8080` | Application port |
| plugin.trivy.service.annotations | object | `{}` | Service annotations. |
| plugin.trivy.service.labels | object | `{}` | Service labels. |
| plugin.trivy.service.port | int | `8080` | Service port. |
| plugin.trivy.service.type | string | `"ClusterIP"` | Service type. |
| plugin.trivy.serviceAccount.annotations | object | `{}` | Annotations for the ServiceAccount |
| plugin.trivy.serviceAccount.automount | bool | `true` | Enable ServiceAccount automount |
| plugin.trivy.serviceAccount.create | bool | `true` | Create ServiceAccount |
| plugin.trivy.serviceAccount.name | string | `""` | The ServiceAccount name |
| plugin.trivy.tmpVolume | object | `{}` | If set the volume for tmpVolume is freely configurable below "- name: tmpVolume". If no value is set an emptyDir is used. |
| plugin.trivy.tolerations | list | `[]` | List of node taints to tolerate |
| plugin.trivy.topologySpreadConstraints | object | `{}` | Pod Topology Spread Constraints for the trivy plugin. |
| plugin.trivy.updateStrategy | object | `{}` | Deployment update strategy. Ref: https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#strategy |
| podAnnotations | object | `{}` | Additional annotations to add to each pod |
| podDisruptionBudget.maxUnavailable | string | `nil` | Configures the maximum unavailable pods for policy-reporter disruptions. Cannot be used if `minAvailable` is set. |
| podDisruptionBudget.minAvailable | int | `1` | Configures the minimum available pods for policy-reporter disruptions. Cannot be used if `maxUnavailable` is set. |
| podLabels | object | `{}` | Additional labels to add to each pod |
| podSecurityContext | object | `{"fsGroup":1234}` | Security context for the pod |
| port | object | `{"name":"http","number":8080}` | Container port |
| priorityClassName | string | `""` | Deployment priorityClassName |
| profiling.enabled | bool | `false` | Enable profiling with pprof |
| rbac.enabled | bool | `true` | Create RBAC resources |
| readinessProbe | object | `{"httpGet":{"path":"/healthz","port":"http"}}` | Deployment readinessProbe for policy-reporter |
| redis.address | string | `""` | Redis host |
| redis.certificate | optional | `""` | Path to a server CA certificate |
| redis.clientCert | optional | `""` | Path to client certificate for mutual TLS authentication |
| redis.clientKey | optional | `""` | Path to client key for mutual TLS authentication |
| redis.database | int | `0` | Redis database |
| redis.enabled | bool | `false` | Enables Redis as external result cache, uses in memory cache by default |
| redis.password | optional | `""` | Password |
| redis.prefix | string | `"policy-reporter"` | Redis key prefix |
| redis.secretRef | optional | `""` | Secret name to pull username and password from |
| redis.skipTLS | bool | `false` | Skip TLS verification |
| redis.username | optional | `""` | Username |
| replicaCount | int | `1` | Deployment replica count |
| reportFilter | object | `{}` | Filter Report resources to process |
| resources | object | `{}` | Resource constraints |
| rest.enabled | bool | `false` | Enables the REST API |
| revisionHistoryLimit | int | `10` | The number of revisions to keep |
| securityContext.allowPrivilegeEscalation | bool | `false` |  |
| securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| securityContext.privileged | bool | `false` |  |
| securityContext.readOnlyRootFilesystem | bool | `true` |  |
| securityContext.runAsNonRoot | bool | `true` |  |
| securityContext.runAsUser | int | `1234` |  |
| securityContext.seccompProfile.type | string | `"RuntimeDefault"` |  |
| selectorLabels | object | `{}` | Custom selector labels, overwrites the default set |
| service.annotations | object | `{}` | Service annotations |
| service.enabled | bool | `true` | Create Service |
| service.labels | object | `{}` | Service labels |
| service.port | int | `8080` | Service port |
| service.type | string | `"ClusterIP"` | Service type |
| serviceAccount.annotations | object | `{}` | Annotations for the ServiceAccount |
| serviceAccount.automount | bool | `true` | Enable ServiceAccount automount |
| serviceAccount.create | bool | `true` | Create ServiceAccount |
| serviceAccount.name | string | `""` | The ServiceAccount name |
| sourceConfig | list | `[]` | Customize source specific logic like result ID generation |
| sourceFilters[0].disableClusterReports | bool | `false` | Filter out cluster scoped Reports |
| sourceFilters[0].kinds | object | `{"exclude":[]}` | Filter out Reports based on the scope resource kind |
| sourceFilters[0].selector.sources | list | `["kyverno","KyvernoValidatingPolicy","KyvernoImageValidatingPolicy"]` | select Report by source |
| sourceFilters[0].uncontrolledOnly | bool | `true` | Filter out Reports of controlled Pods and Jobs, only works for Reports with scope resource |
| sqliteVolume | object | `{}` | If set the volume for sqlite is freely configurable below "- name: sqlite". If no value is set an emptyDir is used. |
| target.alertManager.certificate | string | `""` | Server Certificate file path Can be added under extraVolumes |
| target.alertManager.channels | list | `[]` | List of channels to route results to different configurations |
| target.alertManager.customFields | object | `{}` | Added as additional labels |
| target.alertManager.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.alertManager.headers | object | `{}` | Additional HTTP Headers |
| target.alertManager.host | string | `""` | host address |
| target.alertManager.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.alertManager.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.alertManager.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.alertManager.skipExistingOnStartup | bool | `true` | Skip already existing PolicyReportResults on startup |
| target.alertManager.skipTLS | bool | `false` | Skip TLS verification |
| target.alertManager.sources | list | `[]` | List of sources which should send |
| target.crd | bool | `false` | enable and install TargetConfig CRD |
| target.discord.certificate | string | `""` | Server Certificate file path Can be added under extraVolumes |
| target.discord.channels | list | `[]` | List of channels to route results to different configurations |
| target.discord.customFields | object | `{}` | Added as additional labels |
| target.discord.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.discord.headers | object | `{}` | Additional HTTP Headers |
| target.discord.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.discord.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.discord.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.discord.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.discord.skipTLS | bool | `false` | Skip TLS verification |
| target.discord.sources | list | `[]` | List of sources which should send |
| target.discord.webhook | string | `""` | Webhook Address |
| target.elasticsearch.apiKey | string | `""` | Elasticsearch API Key for api key authentication |
| target.elasticsearch.certificate | string | `""` | Server Certificate file path Can be added under extraVolumes |
| target.elasticsearch.channels | list | `[]` | List of channels to route results to different configurations |
| target.elasticsearch.customFields | object | `{}` | Added as additional labels |
| target.elasticsearch.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.elasticsearch.headers | object | `{}` | Additional HTTP Headers |
| target.elasticsearch.host | string | `""` | Host address |
| target.elasticsearch.index | string | `"policy-reporter"` | Elasticsearch index (default: policy-reporter) |
| target.elasticsearch.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.elasticsearch.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.elasticsearch.password | string | `""` | HTTP BasicAuth password |
| target.elasticsearch.rotation | string | `"daily"` | Elasticsearch index rotation and index suffix Possible values: daily, monthly, annually, none (default: daily) |
| target.elasticsearch.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.elasticsearch.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.elasticsearch.skipTLS | bool | `false` | Skip TLS verification |
| target.elasticsearch.sources | list | `[]` | List of sources which should send |
| target.elasticsearch.typelessApi | bool | `false` | Enables Elasticsearch typless API https://www.elastic.co/blog/moving-from-types-to-typeless-apis-in-elasticsearch-7-0 keeping as false for retrocompatibility. |
| target.elasticsearch.username | string | `""` | HTTP BasicAuth username |
| target.gcs.bucket | required | `""` | GCS Bucket |
| target.gcs.channels | list | `[]` | List of channels to route results to different configurations |
| target.gcs.credentials | optional | `""` | GCS (Google Cloud Storage) Service Account Credentials |
| target.gcs.customFields | object | `{}` | Added as additional labels |
| target.gcs.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.gcs.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.gcs.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.gcs.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.gcs.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.gcs.sources | list | `[]` | List of sources which should send |
| target.googleChat.certificate | string | `""` | Server Certificate file path Can be added under extraVolumes |
| target.googleChat.channels | list | `[]` | List of channels to route results to different configurations |
| target.googleChat.customFields | object | `{}` | Added as additional labels |
| target.googleChat.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.googleChat.headers | object | `{}` | Additional HTTP Headers |
| target.googleChat.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.googleChat.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.googleChat.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.googleChat.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.googleChat.skipTLS | bool | `false` | Skip TLS verification |
| target.googleChat.sources | list | `[]` | List of sources which should send |
| target.googleChat.webhook | string | `""` | Webhook Address |
| target.jira.apiToken | string | `""` | JIRA API token (use password or apiToken, not both) |
| target.jira.apiVersion | string | `"v3"` | JIRA static labels |
| target.jira.certificate | string | `""` | Server Certificate file path Can be added under extraVolumes |
| target.jira.channels | list | `[]` | List of channels to route results to different configurations |
| target.jira.components | list | `[]` | JIRA component names list |
| target.jira.customFields | object | `{}` | Added as additional labels |
| target.jira.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.jira.host | string | `""` | JIRA server URL |
| target.jira.issueType | string | `""` | JIRA issue type (default: "Bug") |
| target.jira.labels | list | `[]` | JIRA static labels |
| target.jira.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.jira.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.jira.password | string | `""` | JIRA password (use password or apiToken, not both) |
| target.jira.projectKey | string | `""` | JIRA project key |
| target.jira.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.jira.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.jira.skipTLS | bool | `false` | Skip TLS verification |
| target.jira.sources | list | `[]` | List of sources which should send |
| target.jira.summaryTemplate | string | `""` | JIRA summary go template, available values: result, customfield default: "{{ if result.ResourceString }}{{ result.ResourceString }}: {{ end }}Policy Violation: {{ result.Policy }}" |
| target.jira.username | string | `""` | JIRA username |
| target.kinesis.accessKeyId | optional | `""` | Access key |
| target.kinesis.channels | list | `[]` | List of channels to route results to different configurations |
| target.kinesis.customFields | object | `{}` | Added as additional labels |
| target.kinesis.endpoint | optional | `""` | Endpoint |
| target.kinesis.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.kinesis.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.kinesis.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.kinesis.region | optional | `""` | Region |
| target.kinesis.secretAccessKey | optional | `""` | SecretAccess key |
| target.kinesis.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.kinesis.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.kinesis.sources | list | `[]` | List of sources which should send |
| target.kinesis.streamName | required | `""` | StreamName |
| target.loki.certificate | string | `""` | Server Certificate file path Can be added under extraVolumes |
| target.loki.channels | list | `[]` | List of channels to route results to different configurations |
| target.loki.customFields | object | `{}` | Added as additional labels |
| target.loki.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.loki.headers | object | `{}` | Additional HTTP Headers |
| target.loki.host | string | `""` | Host Address |
| target.loki.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.loki.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.loki.password | string | `""` | HTTP BasicAuth password |
| target.loki.path | string | `""` | Loki API, defaults to "/loki/api/v1/push" |
| target.loki.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.loki.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.loki.skipTLS | bool | `false` | Skip TLS verification |
| target.loki.sources | list | `[]` | List of sources which should send |
| target.loki.username | string | `""` | HTTP BasicAuth username |
| target.s3.accessKeyId | optional | `""` | S3 Access key |
| target.s3.bucket | required | `""` | S3 Storage bucket name |
| target.s3.bucketKeyEnabled | bool | `false` | S3 Storage to use an S3 Bucket Key for object encryption with SSE-KMS |
| target.s3.channels | list | `[]` | List of channels to route results to different configurations |
| target.s3.customFields | object | `{}` | Added as additional labels |
| target.s3.endpoint | optional | `""` | S3 Storage endpoint |
| target.s3.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.s3.kmsKeyId | string | `""` | S3 Storage KMS Key ID for object encryption with SSE-KMS |
| target.s3.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.s3.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.s3.pathStyle | bool | `false` | S3 Storage, force path style configuration |
| target.s3.prefix | string | `""` | Used prefix, keys will have format: s3://<bucket>/<prefix>/YYYY-MM-DD/YYYY-MM-DDTHH:mm:ss.s+01:00.json |
| target.s3.region | optional | `""` | S3 Storage region |
| target.s3.secretAccessKey | optional | `""` | S3 SecretAccess key |
| target.s3.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.s3.serverSideEncryption | string | `""` | S3 Storage server-side encryption algorithm used when storing this object in Amazon S3, AES256, aws:kms |
| target.s3.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.s3.sources | list | `[]` | List of sources which should send |
| target.securityHub.accessKeyId | optional | `""` | Access key |
| target.securityHub.accountId | required | `""` | AccountId |
| target.securityHub.channels | list | `[]` | List of channels to route results to different configurations |
| target.securityHub.companyName | optional | `""` | Used company name, defaults to "Kyverno" |
| target.securityHub.customFields | object | `{}` | Added as additional labels |
| target.securityHub.delayInSeconds | int | `2` | Delay between AWS GetFindings API calls, to avoid hitting the API RequestLimit |
| target.securityHub.endpoint | optional | `""` | Endpoint |
| target.securityHub.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.securityHub.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.securityHub.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.securityHub.productName | optional | `""` | Used product name, defaults to "Polilcy Reporter" |
| target.securityHub.region | optional | `""` | Region |
| target.securityHub.secretAccessKey | optional | `""` | SecretAccess key |
| target.securityHub.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.securityHub.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.securityHub.sources | list | `[]` | List of sources which should send |
| target.securityHub.synchronize | bool | `true` | Enable cleanup listener for SecurityHub |
| target.slack.channel | string | `""` | Slack Channel |
| target.slack.channels | list | `[]` | List of channels to route results to different configurations |
| target.slack.customFields | object | `{}` | Added as additional labels |
| target.slack.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.slack.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.slack.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.slack.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.slack.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.slack.sources | list | `[]` | List of sources which should send |
| target.slack.webhook | string | `""` | Webhook Address |
| target.teams.certificate | string | `""` | Server Certificate file path Can be added under extraVolumes |
| target.teams.channels | list | `[]` | List of channels to route results to different configurations |
| target.teams.customFields | object | `{}` | Added as additional labels |
| target.teams.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.teams.headers | object | `{}` | Additional HTTP Headers |
| target.teams.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.teams.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.teams.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.teams.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.teams.skipTLS | bool | `false` | Skip TLS verification |
| target.teams.sources | list | `[]` | List of sources which should send |
| target.teams.webhook | string | `""` | Webhook Address |
| target.telegram.certificate | string | `""` | Server Certificate file path Can be added under extraVolumes |
| target.telegram.channels | list | `[]` | List of channels to route results to different configurations |
| target.telegram.chatId | string | `""` | Telegram chat id |
| target.telegram.customFields | object | `{}` | Added as additional labels |
| target.telegram.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.telegram.headers | object | `{}` | Additional HTTP Headers |
| target.telegram.host | optional | `""` | Telegram proxy host |
| target.telegram.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.telegram.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.telegram.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.telegram.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.telegram.skipTLS | bool | `false` | Skip TLS verification |
| target.telegram.sources | list | `[]` | List of sources which should send |
| target.telegram.token | string | `""` | Telegram bot token |
| target.webhook.certificate | string | `""` | Server Certificate file path Can be added under extraVolumes |
| target.webhook.channels | list | `[]` | List of channels to route results to different configurations |
| target.webhook.customFields | object | `{}` | Added as additional labels |
| target.webhook.filter | object | `{}` | Filter Results which should send to this target Wildcars for namespaces and policies are supported, you can either define exclude or include values Filters are available for all targets except the UI |
| target.webhook.headers | object | `{}` | Additional HTTP Headers |
| target.webhook.keepalive | object | `{"interval":"0","params":{}}` | Keepalive configuration |
| target.webhook.keepalive.interval | string | `"0"` | Duration string like "30s" for heartbeat interval, '0' - disabled |
| target.webhook.keepalive.params | object | `{}` | Additional parameters to include in heartbeat payload |
| target.webhook.minimumSeverity | string | `""` | Minimum severity: "" < info < low < medium < high < critical |
| target.webhook.mountedSecret | string | `""` | Mounted secret path by Secrets Controller, secret should be in json format |
| target.webhook.secretRef | string | `""` | Read configuration from an already existing Secret |
| target.webhook.skipExistingOnStartup | bool | `true` | Skip already existing report results on startup |
| target.webhook.skipTLS | bool | `false` | Skip TLS verification |
| target.webhook.sources | list | `[]` | List of sources which should send |
| target.webhook.webhook | string | `""` | Webhook Address |
| tmpVolume | object | `{}` | Allow custom configuration of the /tmp volume |
| tolerations | list | `[]` | Tolerations for pod assignment ref: https://kubernetes.io/docs/concepts/configuration/taint-and-toleration/ |
| topologySpreadConstraints | list | `[]` | Topology Spread Constraints to better spread pods |
| ui.affinity | object | `{}` | Affinity constraints. |
| ui.banner | string | `""` | optional banner text |
| ui.boards | object | `{}` | Configure access control for all default boards. |
| ui.clusters | list | `[]` | Connected Policy Reporter APIs |
| ui.crds.customBoard | bool | `false` | Install UI CustomBoard CRDs |
| ui.customBoards | list | `[]` | Additional customizable dashboards |
| ui.displayMode | string | `""` | DisplayMode dark/light/colorblind/colorblinddark uses the OS configured preferred color scheme as default |
| ui.enabled | bool | `false` | Enable Policy Reporter UI |
| ui.envVars | list | `[]` | Allow additional env variables to be added |
| ui.extraConfig | object | `{}` | Extra configuration options appended to UI settings |
| ui.extraVolumes.volumeMounts | list | `[]` | Deployment volumeMounts |
| ui.extraVolumes.volumes | list | `[]` | Deployment values |
| ui.httproute.annotations | object | `{}` | Additional HTTPRoute annotations |
| ui.httproute.enabled | bool | `false` | Enable HTTPRoute resource (Gateway API alternative to Ingress) Requires Gateway API CRDs (v1) installed in cluster https://gateway-api.sigs.k8s.io/ |
| ui.httproute.hostnames | list | `[]` | List of hostnames for HTTPRoute |
| ui.httproute.labels | object | `{}` | Additional HTTPRoute labels |
| ui.httproute.parentRefs | list | `[]` | Gateway API parentRefs (list of Gateway references) Must reference an existing Gateway resource |
| ui.httproute.rules | list | `[{"matches":[{"path":{"type":"PathPrefix","value":"/"}}]}]` | HTTPRoute rules configuration Allows advanced routing with matches and filters |
| ui.image.pullPolicy | string | `"IfNotPresent"` | Image PullPolicy |
| ui.image.registry | string | `"dp.apps.rancher.io"` | Image registry |
| ui.image.repository | string | `"containers/policy-reporter-ui"` | Image repository |
| ui.image.tag | string | `"2.7.1-11.11"` | Image tag |
| ui.imagePullSecrets | list | `[]` | Image pull secrets for image verification policies, this will define the `--imagePullSecrets` argument |
| ui.ingress.annotations | object | `{}` | Ingress annotations. |
| ui.ingress.className | string | `""` | Ingress class name. |
| ui.ingress.enabled | bool | `false` | Create ingress resource. |
| ui.ingress.hosts | list | `[]` | List of ingress host configurations. |
| ui.ingress.labels | object | `{}` | Ingress labels. |
| ui.ingress.port | string | `nil` | Redirect ingress to an additional defined port on the service |
| ui.ingress.tls | list | `[]` | List of ingress TLS configurations. |
| ui.livenessProbe | object | `{"httpGet":{"path":"/healthz","port":"http"}}` | Deployment livenessProbe for policy-reporter-ui |
| ui.logging.api | bool | `false` | Enables external api request logging |
| ui.logging.encoding | string | `"console"` | Log encoding possible encodings are console and json |
| ui.logging.logLevel | int | `0` | Log level default info |
| ui.logging.server | bool | `false` | Enables server access logging |
| ui.logo.disabled | bool | `false` | disable logo entirely |
| ui.logo.path | string | `""` | custom logo path |
| ui.name | string | `"Default"` |  |
| ui.networkPolicy.egress | list | `[{"ports":[{"port":6443,"protocol":"TCP"}]}]` | A list of valid from selectors according to https://kubernetes.io/docs/concepts/services-networking/network-policies. Enables Kubernetes API Server by default |
| ui.networkPolicy.enabled | bool | `false` | When true, use a NetworkPolicy to allow ingress to the webhook This is useful on clusters using Calico and/or native k8s network policies in a default-deny setup. |
| ui.networkPolicy.ingress | list | `[]` | A list of valid from selectors according to https://kubernetes.io/docs/concepts/services-networking/network-policies. |
| ui.nodeSelector | object | `{}` | Node labels for pod assignment |
| ui.oauth.callbackUrl | string | `""` | OpenID Connect Callback URL |
| ui.oauth.clientId | string | `""` | OpenID Connect ClientID |
| ui.oauth.clientSecret | string | `""` | OpenID Connect ClientSecret |
| ui.oauth.enabled | bool | `false` | Enable openID Connect authentication |
| ui.oauth.provider | string | `""` | OAuth2 Provider supported: amazon, gitlab, github, apple, google, yandex, azuread |
| ui.oauth.scopes | list | `[]` | OpenID Connect allowed Scopes |
| ui.oauth.secretRef | string | `""` | Provide OpenID Connect configuration via Secret supported keys: `provider`, `clientId`, `clientSecret` |
| ui.openIDConnect.callbackUrl | string | `""` | OpenID Connect Callback URL |
| ui.openIDConnect.certificate | string | `""` | TLS Certificate file path |
| ui.openIDConnect.clientId | string | `""` | OpenID Connect ClientID |
| ui.openIDConnect.clientSecret | string | `""` | OpenID Connect ClientSecret |
| ui.openIDConnect.discoveryUrl | string | `""` | OpenID Connect Discovery URL |
| ui.openIDConnect.enabled | bool | `false` | Enable openID Connect authentication |
| ui.openIDConnect.groupClaim | string | `""` | Optional Group Claim to map user groups to the profile groups can be used to define access control for clusters, boards and custom boards. |
| ui.openIDConnect.scopes | list | `[]` | OpenID Connect allowed Scopes |
| ui.openIDConnect.secretRef | string | `""` | Provide OpenID Connect configuration via Secret supported keys: `discoveryUrl`, `clientId`, `clientSecret`, `certificate`, `skipTLS` |
| ui.openIDConnect.skipTLS | bool | `false` | Skip TLS Verification |
| ui.podAnnotations | object | `{}` | Additional annotations to add to each pod |
| ui.podDisruptionBudget.maxUnavailable | string | `nil` | Configures the maximum unavailable pods for kyvernoPlugin disruptions. Cannot be used if `minAvailable` is set. |
| ui.podDisruptionBudget.minAvailable | int | `1` | Configures the minimum available pods for kyvernoPlugin disruptions. Cannot be used if `maxUnavailable` is set. |
| ui.podLabels | object | `{}` | Additional labels to add to each pod |
| ui.podSecurityContext | object | `{"runAsGroup":1234,"runAsUser":1234}` | Security context for the pod |
| ui.priorityClassName | string | `""` | Deployment priorityClassName |
| ui.rbac.enabled | bool | `true` | Create RBAC resources |
| ui.readinessProbe | object | `{"httpGet":{"path":"/healthz","port":"http"}}` | Deployment readinessProbe for policy-reporter-ui |
| ui.replicaCount | int | `1` | Deployment replica count |
| ui.resources | object | `{}` | Resource constraints |
| ui.revisionHistoryLimit | int | `10` | The number of revisions to keep |
| ui.securityContext.allowPrivilegeEscalation | bool | `false` |  |
| ui.securityContext.capabilities.drop[0] | string | `"ALL"` |  |
| ui.securityContext.privileged | bool | `false` |  |
| ui.securityContext.readOnlyRootFilesystem | bool | `true` |  |
| ui.securityContext.runAsNonRoot | bool | `true` |  |
| ui.securityContext.runAsUser | int | `1234` |  |
| ui.securityContext.seccompProfile.type | string | `"RuntimeDefault"` |  |
| ui.selectorLabels | object | `{}` | Custom selector labels, overwrites the default set |
| ui.server.cors | bool | `true` | Enabled CORS header |
| ui.server.overwriteHost | bool | `true` | Overwrites Request Host with Proxy Host and adds `X-Forwarded-Host` and `X-Origin-Host` headers |
| ui.server.port | int | `8080` | Application port |
| ui.server.sessions | object | `{"storage":"filesystem","tempDir":"/tmp"}` | session configuration |
| ui.service.additionalPorts | list | `[]` | Additional service ports for e.g. Sidecars |
| ui.service.annotations | object | `{}` | Service annotations. |
| ui.service.labels | object | `{}` | Service labels. |
| ui.service.port | int | `8080` | Service port. |
| ui.service.type | string | `"ClusterIP"` | Service type. |
| ui.serviceAccount.annotations | object | `{}` | Annotations for the ServiceAccount |
| ui.serviceAccount.automount | bool | `true` | Enable ServiceAccount automount |
| ui.serviceAccount.create | bool | `true` | Create ServiceAccount |
| ui.serviceAccount.name | string | `""` | The ServiceAccount name |
| ui.sidecarContainers | object | `{}` | Add sidecar containers to the UI deployment  sidecarContainers:    oauth-proxy:      image: dp.apps.rancher.io/containers/oauth2-proxy:7.6.0      args:      - --upstream=http://127.0.0.1:8080      - --http-address=0.0.0.0:8081      - ...      ports:      - containerPort: 8081        name: oauth-proxy        protocol: TCP      resources: {} |
| ui.sources | list | `[]` | source specific configurations |
| ui.tolerations | list | `[]` | List of node taints to tolerate |
| ui.topologySpreadConstraints | object | `{}` | Pod Topology Spread Constraints for the policy-reporter-ui. |
| ui.updateStrategy | object | `{}` | Deployment update strategy. Ref: https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#strategy |
| updateStrategy | object | `{}` | Deployment strategy |
| worker | int | `5` | Amount of queue workers for Report resource processing |

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| SUSE LLC |  | <https://www.suse.com/> |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
