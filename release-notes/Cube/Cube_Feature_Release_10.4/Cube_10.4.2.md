---
uid: Cube_Feature_Release_10.4.2
---

# DataMiner Cube Feature Release 10.4.2 – Preview
1
> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For release notes for this release that are not related to DataMiner Cube, see [General Feature Release 10.4.2](xref:General_Feature_Release_10.4.2).

## Highlights

*No highlights have been selected yet.*

## New features

*No new features have been added yet.*

## Changes

### Enhancements

#### Optimization of memory handling when closing cards [ID_37858]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11] - FR 10.4.2 -->

Overall memory handling when closing cards has been optimized.

#### Alarm Console: All alarms tabs listing suggestion events now have the 'Automatically remove cleared alarms' option enabled by default [ID_38034]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11] - FR 10.4.2 -->

From now on, all alarm tabs listing suggestion events will behave like alarm tabs listing active alarms, i.e. the *Automatically remove cleared alarms* option will be enabled by default, except for alarm tabs listing historical alarms or information events.

#### DataMiner Cube - Search: Request to initialize client indexing will only be sent when the user has AdminTools permission [ID_38090]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11]/10.4.0 [CU0] - FR 10.4.2 -->

When, in *System Center > Search & Indexing*, the *Enable search indexing on the client* option was enabled, up to now, DataMiner Cube would send a message to the DataMiner Agent requesting to initialize client indexing, regardless of whether or not the user had *Admin tools* permission (*Modules > System configuration > Tools*). When the user had not been granted this permission, an `Exception occurred while receiving search options` error would be logged.

From now on, before it sends the message in question to the DataMiner Agent, DataMiner Cube will first check whether the user has *Admin tools* permission. If not, it will not send the message.

### Fixes

#### Problem when adding up [Start Time:] placeholders [ID_37661]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11] - FR 10.4.2 -->

When the [Sum:] placeholder was used to add [Start Time:] placeholders, in some cases, the sum would not be correct.

From now on, when configuring [Start Time:] placeholders that will be used in Sum operations, a format will have to be specified.

See also: [Linking a shape to a booking](xref:Linking_a_shape_to_a_booking)

#### Problem when right-clicking after selecting a large number of elements and/or services in a view card [ID_37981]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11] - FR 10.4.2 -->

When, in a view card, you selected a large number of elements and/or services and then right-clicked, in some cases, Cube could become unresponsive.

#### Correlation: Problem with 'Dynamic' option in 'Send email' action [ID_37995]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11] - FR 10.4.2 -->

When configuring a Correlation rule, you can make that rule send an email by adding a *Send email* action to it.

In some cases, when you opened a *Send email* action, it would incorrectly not be possible to select the *Dynamic* option to indicate that the elements that triggered the Correlation rule have to be included.

#### Visual Overview: Problem with user permissions when right-clicking a visual overview linked to a service [ID_38018]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11]/10.4.0 [CU0] - FR 10.4.2 -->

When, in DataMiner Cube, you right-clicked inside a visual overview linked to a service, the context menu would incorrectly allow you to edit the visual overview when you had permission to edit services in general but no permission to edit that specific service.

From now on, when you right-click inside a visual overview linked to a service, the context menu will only allow you to edit the visual overview when you have permission to edit that specific service (on top of the permission to edit services in general and the permission to access and edit visual overviews).

#### DataMiner Cube could leak memory leak when a card in tab layout was closed before it had fully been loaded [ID_38021]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11] - FR 10.4.2 -->

When a card in tab layout was closed before it had fully been loaded, DataMiner Cube could leak memory due to list boxes not being cleared from memory.

#### DataMiner Cube: Memory leaks when opening/closing alarm cards and 'Alarm Console' or 'Cube sides' section of the 'Settings' window [ID_38054]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11]/10.4.0 [CU0] - FR 10.4.2 -->

DataMiner Cube would leak memory each time you opened and closed an alarm card and each time you opened and closed the *Alarm Console* section or the *Cube sides* section in the user settings tab of the *Settings* window.

#### Memory leak in About window [ID_38055]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11]/10.4.0 [CU0] - FR 10.4.2 -->

DataMiner Cube would leak memory each time you opened the About window.

#### Memory leak in Alarm Console [ID_38057]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11]/10.4.0 [CU0] - FR 10.4.2 -->

The Alarm Console would leak memory each time you opened an active alarms tab.

#### System Center: 'Clean up unused' tool would incorrectly consider custom Visio files assigned to elements as unused [ID_38061]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11]/10.4.0 [CU0] - FR 10.4.2 -->

In *System Center*, you can clean up unused Visio files. However, up to now, this *Clean up unused Visio files* tool would incorrectly consider custom Visio files assigned to elements as unused.

#### Visual Overview: Exception values of numeric parameters would be displayed incorrectly when the DynamicUnits soft-launch option was enabled [ID_38083]

<!-- MR 10.2.0 [CU22]/10.3.0 [CU11]/10.4.0 [CU0] - FR 10.4.2 -->

When the *DynamicUnits* soft-launch option was enabled, exception values of numeric parameters would be displayed incorrectly.