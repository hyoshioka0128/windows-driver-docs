---
title: OID_SWITCH_PORT_UPDATED
description: The protocol edge of the Hyper-V extensible switch issues an object identifier (OID) set request of OID_SWITCH_PORT_UPDATED to notify extensible switch extensions about the update of an extensible switch port.
ms.assetid: 7FDC963A-92E4-49B2-AB77-FA9C92EEBC25
ms.date: 08/08/2017
keywords: 
 -OID_SWITCH_PORT_UPDATED Network Drivers Starting with Windows Vista
ms.localizationpriority: medium
---

# OID\_SWITCH\_PORT\_UPDATED


The protocol edge of the Hyper-V extensible switch issues an object identifier (OID) set request of OID\_SWITCH\_PORT\_UPDATED to notify extensible switch extensions about the update of an extensible switch port. The OID will only be issued for ports that have already been created, and have not yet begun the teardown/delete process. Currently, only the **PortFriendlyName** field is subject to update after creation.

The **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/ns-ndis-_ndis_oid_request) structure contains a pointer to an [**NDIS\_SWITCH\_NIC\_SAVE\_STATE**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ntddndis/ns-ntddndis-_ndis_switch_nic_save_state) structure.

Remarks
-------

The **PortId** member of the [**NDIS\_SWITCH\_PORT\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ntddndis/ns-ntddndis-_ndis_switch_port_parameters) structure specifies the extensible switch port for which the update notification is being made.

The extension must follow these guidelines for handling OID set requests of OID\_SWITCH\_PORT\_UPDATED:

-   The extension must not modify the [**NDIS\_SWITCH\_PORT\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ntddndis/ns-ntddndis-_ndis_switch_port_parameters) structure that is associated with the OID request.

-   The extension must always forward this OID set request to underlying extensions. The extension must not fail the request.

**Note**  Extensible switch extensions must not issue OID set requests of OID\_SWITCH\_PORT\_UPDATED.

 

For more information about the states of extensible switch ports and network adapter connections, see [Hyper-V Extensible Switch Port and Network Adapter States](https://docs.microsoft.com/windows-hardware/drivers/network/hyper-v-extensible-switch-port-and-network-adapter-states).

### Return Status Codes

The underlying miniport edge of the extensible switch completes the OID set request of OID\_SWITCH\_PORT\_UPDATED and returns the following status code.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Status Code</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NDIS_STATUS_SUCCESS</p></td>
<td><p>The OID request completed successfully.</p></td>
</tr>
</tbody>
</table>

 

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Version</p></td>
<td><p>Supported in NDIS 6.30 and later.</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Ntddndis.h (include Ndis.h)</td>
</tr>
</tbody>
</table>

## See also


****
[*DereferenceSwitchNic*](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/nc-ndis-ndis_switch_dereference_switch_nic)

[**NDIS\_OID\_REQUEST**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/ns-ndis-_ndis_oid_request)

[**NDIS\_SWITCH\_PORT\_PARAMETERS**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ntddndis/ns-ntddndis-_ndis_switch_port_parameters)

[**NdisFOidRequest**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/nf-ndis-ndisfoidrequest)

[OID\_SWITCH\_NIC\_DELETE](oid-switch-nic-delete.md)

[OID\_SWITCH\_PORT\_ARRAY](oid-switch-port-array.md)

[*ReferenceSwitchNic*](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/nc-ndis-ndis_switch_reference_switch_nic)

 

 




