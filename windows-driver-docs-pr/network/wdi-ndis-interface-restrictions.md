---
title: WDI NDIS interface restrictions
description: The WDI IHV miniport driver has access to all of the functionality provided by NDIS and KMDF.
ms.assetid: 08996045-674B-465D-8880-088320770D2C
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# WDI NDIS interface restrictions


The WDI IHV miniport driver has access to all of the functionality provided by NDIS and KMDF. It is recommended that the IHV driver use the KMDF primitives for talking to the rest of the operating system whenever possible. While the model does not restrict the IHV miniport from calling any of the NDIS APIs, some NDIS APIs are called by the Microsoft WLAN component so the IHV driver should not call them.

The WDI IHV miniport driver needs to be aware of the following restrictions on NDIS interfaces.

Function | Restrictions | Alternative 
---|---|--- 
[**NdisMRegisterMiniportDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/nf-ndis-ndismregisterminiportdriver) | Disallowed |  [**NdisMRegisterWdiMiniportDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/dot11wdi/nf-dot11wdi-ndismregisterwdiminiportdriver) 
[**NdisMDeregisterMiniportDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/nf-ndis-ndismderegisterminiportdriver) | Disallowed |  [**NdisMDeregisterWdiMiniportDriver**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/dot11wdi/nf-dot11wdi-ndismderegisterwdiminiportdriver) 
[**NdisMSetMiniportAttributes**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/nf-ndis-ndismsetminiportattributes) | Disallowed with **MiniportAttributes** types:<br />[**NDIS\_MINIPORT\_ADAPTER\_REGISTRATION\_ATTRIBUTES**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/ns-ndis-_ndis_miniport_adapter_registration_attributes)<br />[**NDIS\_MINIPORT\_ADAPTER\_GENERAL\_ATTRIBUTES**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/ns-ndis-_ndis_miniport_adapter_general_attributes)<br />[**NDIS\_MINIPORT\_ADAPTER\_NATIVE\_802\_11\_ATTRIBUTES**](https://docs.microsoft.com/previous-versions/windows/hardware/wireless/ff565926(v=vs.85)) | None. These are queried using WDI commands. 
[**NdisMIndicateReceiveNetBufferLists**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/nf-ndis-ndismindicatereceivenetbufferlists) | Disallowed | The WDI data path receive handler to indicate received packets. 
[**NdisMSendNetBufferListsComplete**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ndis/nf-ndis-ndismsendnetbufferlistscomplete) | Disallowed | The WDI data path send handler to complete sent packets.

 





