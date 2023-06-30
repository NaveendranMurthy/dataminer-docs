---
uid: General_Main_Release_10.3.0_CU6
---

# General Main Release 10.3.0 CU6 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For information on how to upgrade DataMiner, see [Upgrading a DataMiner Agent](xref:Upgrading_a_DataMiner_Agent).

### Enhancements

#### DataMiner upgrade: New upgrade action added that will clean up default ListView column configuration data [ID_36475]

<!-- MR 10.2.0 [CU18]/10.3.0 [CU6] - FR 10.3.9 -->

During a DataMiner upgrade, from now on, all default ListView column configuration data left on the server will automatically be cleaned up if no more than one Cube client has taken a copy of that data.

#### DataMiner upgrade: Presence of Visual C++ 2010 redistributable will no longer be checked [ID_36745]

<!-- MR 10.2.0 [CU18]/10.3.0 [CU6] - FR 10.3.9 -->

During a DataMiner upgrade, from now on, the presence of the Visual C++ 2010 redistributable will no longer be checked.

### Fixes

#### Cassandra Cluster: Table data that should not expire incorrectly had a TTL value set [ID_35263]

<!-- MR 10.3.0 [CU6] - FR 10.3.9 -->

Up to now, in a Cassandra Cluster database, certain table data that should not expire incorrectly had a TTL value set when inserted. As a result, that data would automatically get deleted when the TTL value reached 0.

The following mechanisms have now been implemented:

- Table data will no longer have any TTL value configured when inserted. Moreover, as a safety measure, all Cassandra tables will now also have a `default_time_to_live` setting. This value will provide the default TTL value in case it is not possible to pass a value when inserting data.

- When existing data with a TTL value set is retrieved from the database, its TTL value will automatically be removed to prevent it from being deleted.

#### SNMPv3 credentials would not get deleted when an SNMPv3 element was deleted [ID_36573]

<!-- MR 10.2.0 [CU18]/10.3.0 [CU6] - FR 10.3.9 -->

When an SNMPv3 element was deleted, its SNMPv3 credentials would incorrectly not get deleted. Also, when users were deleted, their DCP credentials would not get deleted.

#### NT Notify type NT_ADD_VIEW could be executed with an invalid parent view ID [ID_36739]

<!-- MR 10.2.0 [CU18]/10.3.0 [CU6] - FR 10.3.9 -->

Up to now, when an `NT_ADD_VIEW` call was executed with `parentViewID` set to a non-existing view ID, the newly added view would not be visible in the Surveyor. Hence, there was no way of correcting the situation using the UI. Cube logging would include a warning that a `parentViewID` cannot be resolved.

Validation has now been added to `NT_ADD_VIEW`. When a request enters to create a view with an invalid parent view ID, the view will not be created. Also, views with an invalid parent view ID will now be placed directly under the root view. This will allow you to drag the view to its correct location, updating its parent view ID to a valid ID in the process. An error will also be logged and the *View Recursion* BPA test will report the view in question.

#### SLAnalytics - Behavioral anomaly detection: Problem when processing a behavioral change point [ID_36755]

<!-- MR 10.3.0 [CU6] - FR 10.3.9 -->

In some cases, an `index out of bounds` error could occur when processing a behavioral change point.