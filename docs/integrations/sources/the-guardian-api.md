# The Guardian API

## Overview

The Guardian API source can sync data from the [The Guardian](https://open-platform.theguardian.com/)

## Requirements

To access the API, you will need to sign up for an API key, which should be sent with every request. Visit [this](https://open-platform.theguardian.com/access) link to register for an API key.

The following (optional) parameters can be provided to the connector :-

---

##### `q` (query)

The `q` (query) parameter filters the results to only those that include that search term. The `q` parameter supports `AND`, `OR` and `NOT` operators. For example, let's see if the Guardian has any content on political debates: `https://content.guardianapis.com/search?q=debates`

Here the q parameter filters the results to only those that include that search term. In this case, there are many results, so we might want to filter down the response to something more meaningful, specifically looking for political content published in 2014, for example: `https://content.guardianapis.com/search?q=debate&tag=politics/politics&from-date=2014-01-01&api-key=test`

---

##### `tag`

A tag is a piece of data that is used to categorise content. All Guardian content is manually categorised using these tags, of which there are more than 50,000. Use this parameter to filter results by showing only the ones matching the entered tag. See <a href="https://content.guardianapis.com/tags?api-key=test">here</a> for a list of all tags, and <a href="https://open-platform.theguardian.com/documentation/tag">here</a> for the tags endpoint documentation.

---

##### `section`

Use this to filter the results by a particular section. See <a href="https://content.guardianapis.com/sections?api-key=test">here</a> for a list of all sections, and <a href="https://open-platform.theguardian.com/documentation/section">here</a> for the sections endpoint documentation.

---

##### `order-by`

Use this to sort the results. The three available sorting options are - newest, oldest, relevance. For enabling incremental syncs set order-by to oldest.

---

##### `start_date`

Use this to set the minimum date (YYYY-MM-DD) of the results. Results older than the start_date will not be shown.

---

##### `end_date`

Use this to set the maximum date (YYYY-MM-DD) of the results. Results newer than the end_date will not be shown.
Default is set to the current date (today) for incremental syncs.

---

## Output schema

#### Each content item (news article) has the following structure:-

```yaml
{
    "id": "string",
    "type": "string"
    "sectionId": "string"
    "sectionName": "string"
    "webPublicationDate": "string"
    "webTitle": "string"
    "webUrl": "string"
    "apiUrl": "string"
    "isHosted": "boolean"
    "pillarId": "string"
    "pillarName": "string"
}
```

The source is capable of syncing the content stream.

## Setup guide

## Step 1: Set up the The Guardian API connector in Airbyte

### For Airbyte Cloud:

1. [Log into your Airbyte Cloud](https://cloud.airbyte.com/workspaces) account.
2. In the left navigation bar, click **Sources**. In the top-right corner, click **+new source**.
3. On the Set up the source page, select **The Guardian API** from the Source type dropdown.
4. Enter your api_key (mandatory) and any other optional parameters as per your requirements.
5. Click **Set up source**.

### For Airbyte OSS:

1. Navigate to the Airbyte Open Source dashboard.
2. Set the name for your source (The Guardian API).
3. Enter your api_key (mandatory) and any other optional parameters as per your requirements.
4. Click **Set up source**.

## Supported sync modes

The Guardian API source connector supports the following [sync modes](https://docs.airbyte.com/cloud/core-concepts#connection-sync-modes):

| Feature           | Supported? |
| :---------------- | :--------- |
| Full Refresh Sync | Yes        |
| Incremental Sync  | No         |
| Namespaces        | No         |

## Performance considerations

The key that you are assigned is rate-limited and as such any applications that depend on making large numbers of requests on a polling basis are likely to exceed their daily quota and thus be prevented from making further requests until the next period begins.

## Changelog

<details>
  <summary>Expand to review</summary>

| Version | Date       | Pull Request                                             | Subject                                                                                                                                                                |
|:--------|:-----------| :------------------------------------------------------- |:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 0.2.26 | 2025-05-25 | [60501](https://github.com/airbytehq/airbyte/pull/60501) | Update dependencies |
| 0.2.25 | 2025-05-10 | [60109](https://github.com/airbytehq/airbyte/pull/60109) | Update dependencies |
| 0.2.24 | 2025-05-04 | [59627](https://github.com/airbytehq/airbyte/pull/59627) | Update dependencies |
| 0.2.23 | 2025-04-27 | [58436](https://github.com/airbytehq/airbyte/pull/58436) | Update dependencies |
| 0.2.22 | 2025-04-22 | [58596](https://github.com/airbytehq/airbyte/pull/58596) | Manifest cleanup |
| 0.2.21 | 2025-04-12 | [57938](https://github.com/airbytehq/airbyte/pull/57938) | Update dependencies |
| 0.2.20 | 2025-04-05 | [57416](https://github.com/airbytehq/airbyte/pull/57416) | Update dependencies |
| 0.2.19 | 2025-03-29 | [56904](https://github.com/airbytehq/airbyte/pull/56904) | Update dependencies |
| 0.2.18 | 2025-03-22 | [56262](https://github.com/airbytehq/airbyte/pull/56262) | Update dependencies |
| 0.2.17 | 2025-03-08 | [55644](https://github.com/airbytehq/airbyte/pull/55644) | Update dependencies |
| 0.2.16 | 2025-03-01 | [55113](https://github.com/airbytehq/airbyte/pull/55113) | Update dependencies |
| 0.2.15 | 2025-02-22 | [54515](https://github.com/airbytehq/airbyte/pull/54515) | Update dependencies |
| 0.2.14 | 2025-02-15 | [54044](https://github.com/airbytehq/airbyte/pull/54044) | Update dependencies |
| 0.2.13 | 2025-02-08 | [53584](https://github.com/airbytehq/airbyte/pull/53584) | Update dependencies |
| 0.2.12 | 2025-02-01 | [53036](https://github.com/airbytehq/airbyte/pull/53036) | Update dependencies |
| 0.2.11 | 2025-01-25 | [52381](https://github.com/airbytehq/airbyte/pull/52381) | Update dependencies |
| 0.2.10 | 2025-01-18 | [51417](https://github.com/airbytehq/airbyte/pull/51417) | Update dependencies |
| 0.2.9 | 2025-01-13 | [50855](https://github.com/airbytehq/airbyte/pull/50855) | Update to latest CDK and fix custom pagination strategy |
| 0.2.8 | 2024-12-28 | [50818](https://github.com/airbytehq/airbyte/pull/50818) | Update dependencies |
| 0.2.7 | 2024-12-21 | [50341](https://github.com/airbytehq/airbyte/pull/50341) | Update dependencies |
| 0.2.6 | 2024-12-14 | [49797](https://github.com/airbytehq/airbyte/pull/49797) | Update dependencies |
| 0.2.5 | 2024-12-12 | [49378](https://github.com/airbytehq/airbyte/pull/49378) | Update dependencies |
| 0.2.4 | 2024-12-11 | [48790](https://github.com/airbytehq/airbyte/pull/48790) | Add unit tests for custom components |
| 0.2.3 | 2024-12-11 | [48201](https://github.com/airbytehq/airbyte/pull/48201) | Starting with this version, the Docker image is now rootless. Please note that this and future versions will not be compatible with Airbyte versions earlier than 0.64 |
| 0.2.2 | 2024-10-29 | [47779](https://github.com/airbytehq/airbyte/pull/47779) | Update dependencies |
| 0.2.1 | 2024-10-28 | [47456](https://github.com/airbytehq/airbyte/pull/47456) | Update dependencies |
| 0.2.0 | 2024-09-06 | [45195](https://github.com/airbytehq/airbyte/pull/45195) | Refactor connector to manifest-only format |
| 0.1.9 | 2024-08-31 | [44997](https://github.com/airbytehq/airbyte/pull/44997) | Update dependencies |
| 0.1.8 | 2024-08-24 | [44746](https://github.com/airbytehq/airbyte/pull/44746) | Update dependencies |
| 0.1.7 | 2024-08-17 | [44208](https://github.com/airbytehq/airbyte/pull/44208) | Update dependencies |
| 0.1.6 | 2024-08-10 | [43540](https://github.com/airbytehq/airbyte/pull/43540) | Update dependencies |
| 0.1.5 | 2024-08-03 | [42781](https://github.com/airbytehq/airbyte/pull/42781) | Update dependencies |
| 0.1.4 | 2024-07-20 | [42316](https://github.com/airbytehq/airbyte/pull/42316) | Update dependencies |
| 0.1.3 | 2024-07-13 | [41878](https://github.com/airbytehq/airbyte/pull/41878) | Update dependencies |
| 0.1.2 | 2024-07-10 | [41505](https://github.com/airbytehq/airbyte/pull/41505) | Update dependencies |
| 0.1.1 | 2024-07-10 | [41049](https://github.com/airbytehq/airbyte/pull/41049) | Migrate to poetry |
| 0.1.0 | 2022-10-30 | [18654](https://github.com/airbytehq/airbyte/pull/18654) | 🎉 New Source: The Guardian API [low-code CDK] |

</details>
