---
title: WdfRequestSendSyncAtDispatch2 rule (kmdf)
description: The WdfRequestSendSyncAtDispatch2 rule verifies that the WdfRequestSend function is sent at the correct IRQL priority level.
ms.assetid: 0C66BC01-9467-4A04-B1E5-A0EA248F8725
ms.date: 05/21/2018
keywords: ["WdfRequestSendSyncAtDispatch2 rule (kmdf)"]
topic_type:
- apiref
api_name:
- WdfRequestSendSyncAtDispatch2
api_type:
- NA
ms.localizationpriority: medium
---

# WdfRequestSendSyncAtDispatch2 rule (kmdf)


The **WdfRequestSendSyncAtDispatch2** rule verifies that the [**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfrequest/nf-wdfrequest-wdfrequestsend) function is sent at the correct IRQL priority level.

If the driver sets the WDF\_REQUEST\_SEND\_OPTION\_SYNCHRONOUS flag, it must call the [**WdfRequestSend**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfrequest/nf-wdfrequest-wdfrequestsend) function at IRQL = PASSIVE\_LEVEL. If this flag is not set, the driver must call the **WdfRequestSend** function at IRQL = DISPATCH\_LEVEL.

> [!NOTE]
>
> This rule tests the same conditions as the [**WdfRequestSendSyncAtDispatch**](wdfrequestsendsyncatdispatch.md) rule, but it uses a different harness to test different code paths.

 

|              |      |
|--------------|------|
| Driver model | KMDF |

How to test
-----------

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">At compile time</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Run <a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier" data-raw-source="[Static Driver Verifier](https://docs.microsoft.com/windows-hardware/drivers/devtest/static-driver-verifier)">Static Driver Verifier</a> and specify the <strong>WdfRequestSendSyncAtDispatch2</strong> rule.</p>
Use the following steps to run an analysis of your code:
<ol>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code" data-raw-source="[Prepare your code (use role type declarations).](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#preparing-your-source-code)">Prepare your code (use role type declarations).</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier" data-raw-source="[Run Static Driver Verifier.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#running-static-driver-verifier)">Run Static Driver Verifier.</a></li>
<li><a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results" data-raw-source="[View and analyze the results.](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers#viewing-and-analyzing-the-results)">View and analyze the results.</a></li>
</ol>
<p>For more information, see <a href="https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers" data-raw-source="[Using Static Driver Verifier to Find Defects in Drivers](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-static-driver-verifier-to-find-defects-in-drivers)">Using Static Driver Verifier to Find Defects in Drivers</a>.</p></td>
</tr>
</tbody>
</table>

Applies to
----------

[**WdfUsbInterfaceGetConfiguredPipe**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbinterfacegetconfiguredpipe)
[**WdfUsbInterfaceGetConfiguredSettingIndex**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbinterfacegetconfiguredsettingindex)
[**WdfUsbInterfaceGetDescriptor**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbinterfacegetdescriptor)
[**WdfUsbInterfaceGetEndpointInformation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbinterfacegetendpointinformation)
[**WdfUsbInterfaceGetInterfaceNumber**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbinterfacegetinterfacenumber)
[**WdfUsbInterfaceGetNumConfiguredPipes**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbinterfacegetnumconfiguredpipes)
[**WdfUsbInterfaceGetNumEndpoints**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbinterfacegetnumendpoints)
[**WdfUsbInterfaceGetNumSettings**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbinterfacegetnumsettings)
[**WdfUsbInterfaceSelectSetting**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbinterfaceselectsetting)
[**WdfUsbTargetDeviceAllocAndQueryString**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdeviceallocandquerystring)
[**WdfUsbTargetDeviceCreate**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdevicecreate)
[**WdfUsbTargetDeviceCyclePortSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdevicecycleportsynchronously)
[**WdfUsbTargetDeviceFormatRequestForControlTransfer**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdeviceformatrequestforcontroltransfer)
[**WdfUsbTargetDeviceFormatRequestForCyclePort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdeviceformatrequestforcycleport)
[**WdfUsbTargetDeviceFormatRequestForString**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdeviceformatrequestforstring)
[**WdfUsbTargetDeviceFormatRequestForUrb**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdeviceformatrequestforurb)
[**WdfUsbTargetDeviceGetDeviceDescriptor**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdevicegetdevicedescriptor)
[**WdfUsbTargetDeviceGetInterface**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdevicegetinterface)
[**WdfUsbTargetDeviceGetNumInterfaces**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdevicegetnuminterfaces)
[**WdfUsbTargetDeviceIsConnectedSynchronous**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdeviceisconnectedsynchronous)
[**WdfUsbTargetDeviceQueryString**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdevicequerystring)
[**WdfUsbTargetDeviceResetPortSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdeviceresetportsynchronously)
[**WdfUsbTargetDeviceRetrieveConfigDescriptor**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdeviceretrieveconfigdescriptor)
[**WdfUsbTargetDeviceRetrieveCurrentFrameNumber**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdeviceretrievecurrentframenumber)
[**WdfUsbTargetDeviceRetrieveInformation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdeviceretrieveinformation)
[**WdfUsbTargetDeviceSelectConfig**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdeviceselectconfig)
[**WdfUsbTargetDeviceSendControlTransferSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdevicesendcontroltransfersynchronously)
[**WdfUsbTargetDeviceSendUrbSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdevicesendurbsynchronously)
[**WdfUsbTargetDeviceWdmGetConfigurationHandle**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetdevicewdmgetconfigurationhandle)
[**WdfUsbTargetPipeAbortSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipeabortsynchronously)
[**WdfUsbTargetPipeConfigContinuousReader**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipeconfigcontinuousreader)
[**WdfUsbTargetPipeFormatRequestForAbort**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforabort)
[**WdfUsbTargetPipeFormatRequestForRead**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforread)
[**WdfUsbTargetPipeFormatRequestForReset**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforreset)
[**WdfUsbTargetPipeFormatRequestForUrb**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforurb)
[**WdfUsbTargetPipeFormatRequestForWrite**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipeformatrequestforwrite)
[**WdfUsbTargetPipeGetInformation**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipegetinformation)
[**WdfUsbTargetPipeGetType**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipegettype)
[**WdfUsbTargetPipeIsInEndpoint**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipeisinendpoint)
[**WdfUsbTargetPipeIsOutEndpoint**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipeisoutendpoint)
[**WdfUsbTargetPipeReadSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipereadsynchronously)
[**WdfUsbTargetPipeResetSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpiperesetsynchronously)
[**WdfUsbTargetPipeSendUrbSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipesendurbsynchronously)
[**WdfUsbTargetPipeSetNoMaximumPacketSizeCheck**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipesetnomaximumpacketsizecheck)
[**WdfUsbTargetPipeWdmGetPipeHandle**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipewdmgetpipehandle)
[**WdfUsbTargetPipeWriteSynchronously**](https://docs.microsoft.com/windows-hardware/drivers/ddi/content/wdfusb/nf-wdfusb-wdfusbtargetpipewritesynchronously)
 

 





