---
title: Datadog Integration (Third-Party Monitoring Service)
summary: Learn how to monitor your TiDB cluster with the Datadog integration.
---

# Datadog Integration

You can configure TiDB Cloud to send metric data about your TiDB clusters to [Datadog](https://www.datadoghq.com/). After that, you can view these metrics in your Datadog dashboards directly.

## Prerequisites

- To integrate TiDB Cloud with Datadog, you must have a Datadog account and a Datadog API key. Datadog grants you an API key when you first create a Datadog account.

    If you do not have a Datadog account, sign up at [https://app.datadoghq.com/signup](https://app.datadoghq.com/signup).

- To edit third-party integration settings of TiDB Cloud, you must have the `Organization Owner` access to your organization or `Project Member` access to the target project in TiDB Cloud.

## Limitation

You cannot use the Datadog integration in [Developer Tier clusters](/cloud/select-cluster-tier.md#developer-tier).

## Steps

### Step 1. View the datadog integration

1. On the TiDB Cloud console, click the account name in the upper-right corner of the window.
2. Click **Preferences**. The project preferences page is displayed.
3. In the **Integrations** column, click the **Datadog** icon of a project that you want to view or modify. The **Integration** page of the project is displayed.

### Step 2. Integrate with your Datadog API Key

1. On the **Integration** page, enter your **API Key** of **Datadog**, and choose the **Site** of **Datadog**.
2. Click **Test Integration**, and then click **Confirm**.

## Pre-built dashboard

Click the **Dashboard** link in the **Datadog** card of the integrations. You can see the pre-built dashboard of your TiDB clusters.

## Metrics available to Datadog

Datadog tracks the following metric data for your TiDB clusters.

| Metric name  | Metric type | Labels | Description                                   |
| :------------| :---------- | :------| :----------------------------------------------------- |
| tidb_cloud.db_queries_total| count | sql_type: `Select\|Insert\|...`<br/>cluster_name: `<cluster name>`<br/>instance: `tidb-0\|tidb-1…`<br/>component: `tidb` | The total number of statements executed |
| tidb_cloud.db_failed_queries_total | count | type: `planner:xxx\|executor:2345\|...`<br/>cluster_name: `<cluster name>`<br/>instance: `tidb-0\|tidb-1…`<br/>component: `tidb` | The total number of execution errors |
| tidb_cloud.db_connections | gauge | cluster_name: `<cluster name>`<br/>instance: `tidb-0\|tidb-1…`<br/>component: `tidb` | Current number of connections in your TiDB server |
| tidb_cloud.db_query_duration_seconds | histogram | sql_type: `Select\|Insert\|...`<br/>cluster_name: `<cluster name>`<br/>instance: `tidb-0\|tidb-1…`<br/>component: `tidb` | The duration histogram of statements |
| tidb_cloud.node_storage_used_bytes | gauge | cluster_name: `<cluster name>`<br/>instance: `tikv-0\|tikv-1…\|tiflash-0\|tiflash-1…`<br/>component: `tikv\|tiflash` | The disk usage bytes of TiKV/TiFlash<sup>beta</sup> nodes |
| tidb_cloud.node_storage_capacity_bytes | gauge | cluster_name: `<cluster name>`<br/>instance: `tikv-0\|tikv-1…\|tiflash-0\|tiflash-1…`<br/>component: `tikv\|tiflash` | The disk capacity bytes of TiKV/TiFlash<sup>beta</sup> nodes |
| tidb_cloud.node_cpu_seconds_total | count | cluster_name: `<cluster name>`<br/>instance: `tidb-0\|tidb-1…\|tikv-0…\|tiflash-0…`<br/>component: `tidb\|tikv\|tiflash` | The CPU usage of TiDB/TiKV/TiFlash<sup>beta</sup> nodes |
| tidb_cloud.node_cpu_capacity_cores | gauge | cluster_name: `<cluster name>`<br/>instance: `tidb-0\|tidb-1…\|tikv-0…\|tiflash-0…`<br/>component: `tidb\|tikv\|tiflash` | The CPU limit cores of TiDB/TiKV/TiFlash<sup>beta</sup> nodes |
| tidb_cloud.node_memory_used_bytes | gauge | cluster_name: `<cluster name>`<br/>instance: `tidb-0\|tidb-1…\|tikv-0…\|tiflash-0…`<br/>component: `tidb\|tikv\|tiflash` | The used memory bytes of TiDB/TiKV/TiFlash<sup>beta</sup> nodes |
| tidb_cloud.node_memory_capacity_bytes | gauge | cluster_name: `<cluster name>`<br/>instance: `tidb-0\|tidb-1…\|tikv-0…\|tiflash-0…`<br/>component: `tidb\|tikv\|tiflash` | The memory capacity bytes of TiDB/TiKV/TiFlash<sup>beta</sup> nodes |