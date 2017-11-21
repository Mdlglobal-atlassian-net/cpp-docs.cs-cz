---
title: "Podpora oznámení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ea98172f1da948ed3839a4d3c07a5924ad952575
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="supporting-notifications"></a>Podpora oznámení
## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Implementace rozhraní bodu připojení na poskytovatele a příjemce  
 Chcete-li implementovat oznámení, třída zprostředkovatele musí dědit z [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) a [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).  
  
 `IRowsetNotifyCP`implementuje poskytovatele lokality pro bod připojení rozhraní [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx). `IRowsetNotifyCP`implementuje vysílání funkce pro navedení naslouchací procesy ve spojovacím bodě **IID_IRowsetNotify** změny obsah sady řádků.  
  
 Všimněte si, že je nutné implementovat a zaregistrovat `IRowsetNotify` pro příjemce (také označované jako jímka) pomocí [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) tak, aby příjemce mohl zpracovávat oznámení. Informace o implementaci rozhraní bodu připojení pro příjemce, najdete v článku [příjem oznámení](../../data/oledb/receiving-notifications.md).  
  
 Kromě toho třída musí také obsahovat mapu, která definuje vstup bodu připojení, například takto:  
  
```  
BEGIN_CONNECTION_POINT_MAP  
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)  
END_CONNECTION_POINT_MAP  
```  
  
## <a name="adding-irowsetnotify"></a>Přidání IRowsetNotify  
 Chcete-li přidat `IRowsetNotify`, je nutné přidat `IConnectionPointContainerImpl<rowset-name>` a `IRowsetNotifyCP<rowset-name>` do vašeho řetězce dědičnosti.  
  
 Zde je řetězec dědičnosti pro například `RUpdateRowset` v [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f):  
  
> [!NOTE]
>  Ukázkový kód se může lišit od co je uveden zde; měli byste považovat ukázkový kód jako aktuální verze.  
  
```  
///////////////////////////////////////////////////////////////////////////  
// class RUpdateRowset (in rowset.h)  
  
class RUpdateRowset :   
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,   
         CAtlArray< CAgentMan, CAtlArray<CAgentMan> >, CSimpleRow,   
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll > >,  
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,  
      public IConnectionPointContainerImpl<RUpdateRowset>,  
      public IRowsetNotifyCP<RUpdateRowset>  
```  
  
### <a name="setting-com-map-entries"></a>Nastavení položek mapy modelu COM  
 Musíte taky přidejte následující COM mapy ve vaší sadě řádků:  
  
```  
COM_INTERFACE_ENTRY(IConnectionPointContainer)  
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)  
```  
  
 Tyto makra kdokoli volání `QueryInterface` pro váš kontejner bodu připojení (základ pro `IRowsetNotify`) k vyhledání požadovaného rozhraní poskytovatele. Příklad použití spojovací body, naleznete v části ukázka MNOHOÚHELNÍKU ATL a kurzu.  
  
### <a name="setting-connection-point-map-entries"></a>Nastavení připojení položek bodu mapy  
 Musíte taky přidat mapu bodů připojení. Měl by vypadat nějak podobně jako:  
  
```  
BEGIN_CONNECTION_POINT_MAP(rowset-name)  
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))  
END_CONNECTION_POINT_MAP()  
```  
  
 Tato mapa bodu připojení umožňuje součást hledá `IRowsetNotify` rozhraní k vyhledání ve zprostředkovateli.  
  
### <a name="setting-properties"></a>Nastavení vlastností  
 Musíte taky přidat následující vlastnosti ke zprostředkovateli. Potřebujete pouze přidat vlastnosti založené na rozhraní, které podporujete.  
  
|Vlastnost|Přidejte, pokud podporujete|  
|--------------|------------------------|  
|**DBPROP_IConnectionPointContainer**|Vždy|  
|**DBPROP_NOTIFICATIONGRANULARITY**|Vždy|  
|**DBPROP_NOTIFICATIONPHASES**|Vždy|  
|**DBPROP_NOTIFYCOLUMNSET**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWDELETE**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWINSERT**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE**|Vždy|  
|**DBPROP_NOTIFYROWFIRSTCHANGE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWSETRELEASE**|Vždy|  
|**DBPROP_NOTIFYROWUNDOCHANGE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUNDODELETE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUNDOINSERT**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUPDATE**|`IRowsetUpdate`|  
  
 Většina implementace pro oznámení je již součástí šablony zprostředkovatele technologie OLE DB. Pokud nepřidáte `IRowsetNotifyCP` do vašeho řetězce dědičnosti kompilátor odebere tento kód z datového proudu kompilace, díky čemuž menší velikost vašeho kódu.  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)