﻿---
title: Managing Agents and Servers
subtitle: Agents and Servers
keywords: otter,servers,agents
show-headings-in-nav: true
---

To provision and configure your servers, Otter needs to be able to communicate with those servers over a fast and secure channel. There are a few options for doing this.

## Windows Servers {#windows data-title="Windows Servers"}

The [Inedo Agent] is generally the best way to communicate with a Windows server. It's light-weight, and uses a highly-optimized and resilient protocol built solely for this purpose, and is [quite easy to install](/docs/various/inedo-agent/installation).

### Agentless Windows Servers

Alternatively, Otter can use PowerShell Remoting to communicate with Windows servers; however, this is generally slower and less resilient than the Inedo Agent protocol. You can connect using integrated authentication (i.e. whatever account the service is running under), or with a username &amp; password [resource credential]. See [Enable-PSRemoting](https://technet.microsoft.com/en-us/library/hh849694.aspx){target="_blank"} to configure a server to receive remote commands.

## Linux Servers {#linux data-title="Linux Servers"}

To communicate with Linux servers, Otter uses the lightweight, highly-optimized, and resilient protocol already enabled on nearly every Linux box: SSH and SFTP. You can connect with a private key or username &amp; password [resource credential].

## Local Agents {#local data-title="Local Agent"}

If you're using Otter to interact with the server it's installed on, you can just set it up using a local agent. This uses the same process/identity that the [service] is hosted as, and doesn't have very many privileges by default.

## Automatic Inedo Agent Updates {#automatic data-title="Inedo Agent Updates"}

Although the Inedo Agent is both backwards- and forwards-compatible, you may wish to update it on the servers to fix bugs and improve performance. This can be done manually (by running a newer installer on a remote server), or by using the agent update process built-in to Otter.

When Otter performs a routine check on the connected agents, the installed Inedo Agent version is captured, and can be viewed on the server overview page. When you visit the server list page, if any servers have a version of the Inedo Agent that can be updated, you will be prompted to upgrade agents.

Clicking on the *Update Agents* button will open a dialog that gives you the option to select which servers to update, as well as where to download the new Inedo Agent files from.

:::attention {.technical}
Self-updating software always has a risk of failing mid-update. If this happens with the Inedo Agent, you will need to log-on to the server to reinstall the agent. Therefore, only update agent versions when you are prepared to also do a manual update if absolutely necessary.
:::

Clicking *Update Agent* will initiate an execution that downloads the installer and updates the specified servers with a new agent.

[Inedo Agent]: /docs/various/inedo-agent/the-agent
[resource credential]: /docs/otter/global-components/resource-credentials
[service]: /docs/otter/installation/architecture/service
