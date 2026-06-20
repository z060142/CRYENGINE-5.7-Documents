# [Node] Time

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/36869473
- Page ID: 36869473
- Breadcrumb: Editor Tools > Behavior Tree Editor > Behavior Tree Nodes > [Node] Time
- Parent: Behavior Tree Nodes

## Content

## Time Nodes

The execution of**Time** nodes is influenced by the effect of time.

### Timeout

**Description** | Runs for a specified amount of time before failing. |
--- | --- | ---
**Parameters Accepted** | Parameter Name | Description | Value --- | --- | --- **Duration** | Specifies the time, in seconds, for which the node must be processed before yielding Failure as a result. | Accepts a floating point integer that represents the ** Duration**, in seconds. |
Parameter Name | Description | Value
**Duration** | Specifies the time, in seconds, for which the node must be processed before yielding Failure as a result. | Accepts a floating point integer that represents the **Duration**, in seconds.
**Results** | Outcome | Criteria --- | --- **Success** | Never. ** Failure** | When the Timeout node is processed for the entirety of the specified ** Duration**. |
Outcome | Criteria |
**Success** | Never. |
**Failure** | When the Timeout node is processed for the entirety of the specified **Duration**. |
**Additional Information** | None. |

### Timestamp Gate

**Description** | Has exactly one child that is executed when the Timestamp gate is "open". A gate is "open", if a Timestamp associated with it yields a value that either exceeds or fails to reach a specified duration of time as per a defined **Comparator.** |
--- | --- | ---
**Parameters Accepted** | Parameter Name | Description | Value --- | --- | --- **Timestamp** | Specifies the Timestamp to track. | Accepts the name of a Timestamp. The Timestamp must be previously defined in the ** Timestamp** section of the Data Definitions block. ** Comparator** | The logic by which a Timestamp must be compared against a defined ** Duration.** | ** More Than** | Checks if the ** Timestamp** exceeds the specified ** Duration.** --- | --- ** Less Than** | Checks if the ** Timestamp** fails to reach the specified ** Duration**. ** More Than** | Checks if the ** Timestamp** exceeds the specified ** Duration.** | ** Less Than** | Checks if the ** Timestamp** fails to reach the specified ** Duration**. | ** Duration** | The duration of time against which the specified Timestamp must be compared. | Accepts a floating point integer that represents the ** Duration**, in seconds. ** Open If It Was Never Set** | Forces the node to succeed if no Timestamp is specified in the node's Timestamp parameter field. | Boolean; ticking the provided checkbox will "open" the Timestamp gate node whenever no Timestamp has been specified. |
Parameter Name | Description | Value
**Timestamp** | Specifies the Timestamp to track. | Accepts the name of a Timestamp. The Timestamp must be previously defined in the **Timestamp** section of the Data Definitions block.
**Comparator** | The logic by which a Timestamp must be compared against a defined **Duration.** | **More Than** | Checks if the ** Timestamp** exceeds the specified ** Duration.** --- | --- ** Less Than** | Checks if the ** Timestamp** fails to reach the specified ** Duration**.
**More Than** | Checks if the **Timestamp** exceeds the specified ** Duration.** |
**Less Than** | Checks if the **Timestamp** fails to reach the specified ** Duration**. |
**Duration** | The duration of time against which the specified Timestamp must be compared. | Accepts a floating point integer that represents the **Duration**, in seconds.
**Open If It Was Never Set** | Forces the node to succeed if no Timestamp is specified in the node's Timestamp parameter field. | Boolean; ticking the provided checkbox will "open" the Timestamp gate node whenever no Timestamp has been specified.
**Results** | Outcome | Criteria --- | --- **Success** | - If the gate is "open" and its child node succeeds. - If no Timestamp is specified in the node's ** Timestamp** parameter field, and the ** Open If It Was Never** ** Set** checkbox is checked. ** Failure** | - If the gate is "closed", or its child node failed when "open". - If no Timestamp is specified in the node's ** Timestamp** parameter field, and the ** Open If It Was Never Set** checkbox is not checked. |
Outcome | Criteria |
**Success** | - If the gate is "open" and its child node succeeds. - If no Timestamp is specified in the node's **Timestamp** parameter field, and the ** Open If It Was Never** ** Set** checkbox is checked. |
**Failure** | - If the gate is "closed", or its child node failed when "open". - If no Timestamp is specified in the node's **Timestamp** parameter field, and the ** Open If It Was Never Set** checkbox is not checked. |
**Additional Information** | None. |

### Wait

**Description** | Runs for a specified amount of time before returning a successful result. |
--- | --- | ---
**Parameters Accepted** | Parameter Name | Description | Value --- | --- | --- **Duration** | Specifies the time, in seconds, for which the node must be processed before yielding a successful result. | Accepts a floating point integer that represents the ** Duration**, in seconds. ** Variation** | Applies a variation to the ** Duration** value specified above, such that the node is processed for a duration ranging between the values ** Duration** and ** Duration+Variation.** | Accepts a floating point integer that represents the ** Variation**, in seconds. |
Parameter Name | Description | Value
**Duration** | Specifies the time, in seconds, for which the node must be processed before yielding a successful result. | Accepts a floating point integer that represents the **Duration**, in seconds.
**Variation** | Applies a variation to the **Duration** value specified above, such that the node is processed for a duration ranging between the values ** Duration** and ** Duration+Variation.** | Accepts a floating point integer that represents the **Variation**, in seconds.
**Results** | Outcome | Criteria --- | --- **Success** | When the nodes runs for a longer time than the specified ** Duration**, with ** Variation** included. ** Failure** | Never. |
Outcome | Criteria |
**Success** | When the nodes runs for a longer time than the specified **Duration**, with ** Variation** included. |
**Failure** | Never. |
**Additional Information** | None. |

### Wait for Condition

**Description** | Evaluates a given condition continuously until satisfied. |
--- | --- | ---
**Parameters Accepted** | Parameter Name | Description | Value --- | --- | --- **Condition** | Specifies the condition that needs to be evaluated continuously. | Accepts a logical expression containing Variables (for example, *!a and* * b*, where * a* and * b* are variables), that must return True/False as its result. Any Variables used must be defined in the Data Definitions block of the Behavior Tree Editor. |
Parameter Name | Description | Value
**Condition** | Specifies the condition that needs to be evaluated continuously. | Accepts a logical expression containing Variables (for example, *!a and* * b*, where * a* and * b* are variables), that must return True/False as its result. Any Variables used must be defined in the Data Definitions block of the Behavior Tree Editor.
**Results** | Outcome | Criteria --- | --- **Success** | When the specified ** Condition** is evaluated true. ** Failure** | Never. |
Outcome | Criteria |
**Success** | When the specified **Condition** is evaluated true. |
**Failure** | Never. |
**Additional Information** | None. |

### Wait for Event

**Description** | Waits until a specific Event has been received. |
--- | --- | ---
**Parameters Accepted** | Parameter Name | Description | Value --- | --- | --- **Event** | Specifies the Event the node must wait for. | Accepts any ** Built-in** or ** Game** Event as its value. However, the Event must be previously defined in the Data Definitions block of the Behavior Tree Editor. |
Parameter Name | Description | Value
**Event** | Specifies the Event the node must wait for. | Accepts any **Built-in** or ** Game** Event as its value. However, the Event must be previously defined in the Data Definitions block of the Behavior Tree Editor.
**Results** | Outcome | Criteria --- | --- **Success** | When the specified ** Event** is received. ** Failure** | Never. |
Outcome | Criteria |
**Success** | When the specified **Event** is received. |
**Failure** | Never. |
**Additional Information** | None. |

### Wait for Timestamp

**Description** | Waits until a specified time-based has been satisfied. |
--- | --- | ---
**Parameters Accepted** | Parameter Name | Description | Value --- | --- | --- **Timestamp** | Specifies the ** Timestamp** to track. | Accepts the name of a ** Timestamp**. The Timestamp must be previously defined in the ** Timestamp** section of the Data Definitions block. ** Comparator** | The logic by which a ** Timestamp** must be compared against a defined ** Duration.** | ** More Than** | Checks if the ** Timestamp** exceeds the defined ** Duration**. --- | --- ** Less Than** | Checks if the ** Timestamp** fails to reach the specified Duration. ** More Than** | Checks if the ** Timestamp** exceeds the defined ** Duration**. | ** Less Than** | Checks if the ** Timestamp** fails to reach the specified Duration. | ** Duration** | The duration of time against which the specified ** Timestamp** must be compared. | Accepts a floating point integer that represents the ** Duration**, in seconds. ** Succeed If It Was Never Set** | Forces the node to succeed if no Timestamp is specified in the node's ** Timestamp** parameter field. | Boolean; ticking the provided checkbox will "open" the Timestamp gate node whenever no ** Timestamp** has been specified. |
Parameter Name | Description | Value
**Timestamp** | Specifies the **Timestamp** to track. | Accepts the name of a **Timestamp**. The Timestamp must be previously defined in the ** Timestamp** section of the Data Definitions block.
**Comparator** | The logic by which a **Timestamp** must be compared against a defined ** Duration.** | **More Than** | Checks if the ** Timestamp** exceeds the defined ** Duration**. --- | --- ** Less Than** | Checks if the ** Timestamp** fails to reach the specified Duration.
**More Than** | Checks if the **Timestamp** exceeds the defined ** Duration**. |
**Less Than** | Checks if the **Timestamp** fails to reach the specified Duration. |
**Duration** | The duration of time against which the specified **Timestamp** must be compared. | Accepts a floating point integer that represents the **Duration**, in seconds.
**Succeed If It Was Never Set** | Forces the node to succeed if no Timestamp is specified in the node's **Timestamp** parameter field. | Boolean; ticking the provided checkbox will "open" the Timestamp gate node whenever no **Timestamp** has been specified.
**Results** | Outcome | Criteria --- | --- **Success** | - When the ** Comparator** between the specified ** Timestamp** and ** Duration** yields true. - If no Timestamp is specified in the node's ** Timestamp** parameter field, and the ** Succeed If It Was Never** ** Set** checkbox is checked. ** Failure** | Never. |
Outcome | Criteria |
**Success** | - When the **Comparator** between the specified ** Timestamp** and ** Duration** yields true. - If no Timestamp is specified in the node's **Timestamp** parameter field, and the ** Succeed If It Was Never** ** Set** checkbox is checked. |
**Failure** | Never. |
**Additional Information** | None. |

[Time Nodes](#time-nodes)[Timeout](#timeout)[Timestamp Gate](#timestamp-gate)[Wait](#wait)[Wait for Condition](#wait-for-condition)[Wait for Event](#wait-for-event)[Wait for Timestamp](#wait-for-timestamp)
