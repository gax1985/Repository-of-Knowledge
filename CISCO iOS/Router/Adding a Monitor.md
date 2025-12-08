


# Configuring a Flow Monitor for IPv4 or IPv6 Traffic Using the Predefined Record

To configure a flow monitor for IPv4/IPv6 traffic using the Flexible NetFlow "NetFlow IPv4/IPv6 original input" predefined record for the flow monitor, perform the following required task.

Each flow monitor has a separate cache assigned to it. Each flow monitor requires a record to define the
contents and layout of its cache entries. The record format can be one of the predefined record formats, or an advanced user may create his or her own record format using the **collect** and **match**commands in Flexible NetFlow flow record configuration mode.

>[!Note]
>
>You must remove a flow monitor from all of the interfaces to which you have applied it before you can modify the **record** format of the flow monitor.

>[!SUMMARY STEPS]
>
>1. **enable**
>
>2. **configure terminal**
>
>3. **flow monitor** _monitor-name_
>
>4. **description** _description_
>
>5. **record netflow {ipv4 | ipv6} original-input**
>6. **end**
>7. **show flow monitor** [[**name**] _monitor-name_ [**cache** [**format** {**csv** | **record** | **table**}]][**statistics**]]

## Flexible Netflow Overview

Command or Action

Purpose

Step 1

**enable**

Example:• Enter your password if prompted.

Device> enable

Enables privileged EXEC mode.

Step 2

**configure terminal**

Example:

Device# configure terminal

Enters global configuration mode.

Step 3

**flow monitor** _monitor-name_

Example:

Device(config)# flow monitor FLOW-MONITOR-1

Creates a flow monitor and enters Flexible NetFlow flow

monitor configuration mode.

• This command also allows you to modify an existing

flow monitor.

Step 4

**description** _description_

Example:

Device(config-flow-monitor)# description Used for

monitoring IPv4 traffic

(Optional) Creates a description for the flow monitor.

Step 5

**record netflow {ipv4 | ipv6} original-input**

Example:

Device(config-flow-monitor)# record netflow ipv4

original-input

Specifies the record for the flow monitor.

Step 6

**end**

Example:

Device(config-flow-monitor)# end

Exits Flexible NetFlow flow monitor configuration mode

and returns to privileged EXEC mode.

Step 7

**show flow monitor** [[**name**] _monitor-name_ [**cache** [**format**

{**csv** | **record** | **table**}]][**statistics**]]

Example:

Device# show flow monitor FLOW-MONITOR-2 cache

(Optional) Displays the status and statistics for a Flexible

NetFlow flow monitor.

Step 8

**show running-config flow monitor** _monitor-name_

Example:

Device# show flow monitor FLOW_MONITOR-1

(Optional) Displays the configuration of the specified flow

monitor.