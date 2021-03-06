---
title: Controlling Targets
description: Controlling Targets
ms.assetid: b329e9a2-7d24-4612-9aa1-9d7955a61473
keywords:
- Windows Device Testing Framework WDK , action interfaces
- WDTF WDK , action interfaces
- Windows Device Testing Framework WDK , manageable tests
- WDTF WDK , manageable tests
- manageable tests WDK WDTF
- action interfaces WDK WDTF
- COM interfaces WDK WDTF
- interfaces WDK WDTF
- code modules WDK WDTF
- scripts WDK WDTF
- synchronous tests WDK WDTF
- asynchronous tests WDK WDTF
- test scripts WDK WDTF
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Controlling Targets


WDTF includes a set of interfaces that perform specific actions on targets. WDTF uses the Windows registry to map target-specific implementations of these interfaces to actual targets. There might be one implementation for all targets, or multiple class-specific implementations. Scenarios can use [**Action Interfaces**](https://docs.microsoft.com/windows-hardware/drivers/wdtf/action-interfaces) to perform common activities without having to know the specifics of each target.

Your scenario can attempt to locate an implementation for one of these interfaces by calling the [**IWDTFTarget2::GetInterface**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdtf/nf-wdtf-iwdtftarget2-getinterface) method. Note that not all target objects support every action interface. The following VBScript code example retrieves an interface that can disable and enable (and more) the device that the target represents.

```cpp
Set Action = Device.GetInterface("PNP")
```

The [**Action Interfaces**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/index) are identified with a WDTF *ProgId*. You must specify the WDTF *ProgId* when you call the [**HasInterface**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdtf/nf-wdtf-iwdtftarget2-hasinterface), [**GetInterface**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdtf/nf-wdtf-iwdtftarget2-getinterface), [**GetInterfaces**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdtf/nf-wdtf-iwdtftargets2-getinterfaces), and [**GetInterfacesIfExist**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdtf/nf-wdtf-iwdtftargets2-getinterfacesifexist) methods. For information about WDTF *ProgId*, see the **Action Interfaces**.

You can add interfaces and implementations of interfaces to WDTF through a plug-in model. For more information about this model, see [Extending the Framework](extending-the-framework.md).

## Related topics
[**Action Interfaces**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/index)  
[Extending the Framework](extending-the-framework.md)  
[**GetInterface**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdtf/nf-wdtf-iwdtftarget2-getinterface)  
[**GetInterfaces**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdtf/nf-wdtf-iwdtftargets2-getinterfaces)  
[**GetInterfacesIfExist**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdtf/nf-wdtf-iwdtftargets2-getinterfacesifexist)  
[**HasInterface**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdtf/nf-wdtf-iwdtftarget2-hasinterface)  



