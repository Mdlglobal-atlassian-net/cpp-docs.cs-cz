---
title: Podpora oznámení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9fea13ef4a89ee2a1105702db4fe692c12643d2
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337937"
---
# <a name="supporting-notifications"></a>Podpora oznámení

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Implementace rozhraní bod připojení pro zprostředkovatele a spotřebitele  
 Pokud chcete implementovat oznámení, třída zprostředkovatele musí dědit z [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) a [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).  
  
 `IRowsetNotifyCP` implementuje poskytovatele lokality pro bod připojení rozhraní [IRowsetNotify](https://msdn.microsoft.com/library/ms712959.aspx). `IRowsetNotifyCP` implementuje vysílání funkce radit naslouchacích procesů najdete v bodě připojení `IID_IRowsetNotify` změny obsahu v sadě řádků.  
  
 Všimněte si, že musí také implementovat a zaregistrovat `IRowsetNotify` na spotřebitele (označované také jako jímka) pomocí [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) tak, aby příjemce může zpracovat oznámení. Informace o implementaci rozhraní bod připojení pro spotřebitele, naleznete v tématu [příjem oznámení](../../data/oledb/receiving-notifications.md).  
  
 Kromě toho třída musí obsahovat také mapu, která definuje vstupní bod připojení, následujícím způsobem:  
  
```  
BEGIN_CONNECTION_POINT_MAP  
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)  
END_CONNECTION_POINT_MAP  
```  
  
## <a name="adding-irowsetnotify"></a>Přidání IRowsetNotify  
 Chcete-li přidat `IRowsetNotify`, budete muset přidat `IConnectionPointContainerImpl<rowset-name>` a `IRowsetNotifyCP<rowset-name>` do vašeho řetězce dědičnosti.  
  
 Například tady je řetězec dědičnosti pro `RUpdateRowset` v [UpdatePV](http://msdn.microsoft.com/c8bed873-223c-4a7d-af55-f90138c6f38f):  
  
> [!NOTE]
>  Vzorový kód se mohou lišit od zde; uvedeného vzorový kód by měl považovat za aktuálnější verzi.  
  
```cpp
///////////////////////////////////////////////////////////////////////////  
// class RUpdateRowset (in rowset.h)  
  
class RUpdateRowset :   
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,   
         CAtlArray< CAgentMan, CAtlArray<CAgentMan>>, CSimpleRow,   
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll >>,  
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,  
      public IConnectionPointContainerImpl<RUpdateRowset>,  
      public IRowsetNotifyCP<RUpdateRowset>  
```  
  
### <a name="setting-com-map-entries"></a>Nastavení položky mapy modelu COM.  
 Také je potřeba přidat následující do mapy modelu COM ve vaší sadě řádků:  
  
```  
COM_INTERFACE_ENTRY(IConnectionPointContainer)  
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)  
```  
  
 Tato makra může kdokoli volání `QueryInterface` pro váš kontejner bodu připojení (základ `IRowsetNotify`) k vyhledání požadovaného rozhraní poskytovatele. Příklad použití spojovací body naleznete v tématu ukázka MNOHOÚHELNÍKU knihovny ATL a kurzu.  
  
### <a name="setting-connection-point-map-entries"></a>Nastavení připojení položek bodu mapy  
 Také budete muset přidat mapu bodu připojení. By měl vypadat přibližně jako:  
  
```  
BEGIN_CONNECTION_POINT_MAP(rowset-name)  
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))  
END_CONNECTION_POINT_MAP()  
```  
  
 Toto mapování bodu připojení umožňuje komponentu hledá `IRowsetNotify` rozhraní k vyhledání ve zprostředkovateli.  
  
### <a name="setting-properties"></a>Nastavení vlastností  
 Také musíte přidat následující vlastnosti pro daného poskytovatele. Stačí přidat vlastnosti založené na rozhraních, které podporujete.  
  
|Vlastnost|Přidejte, pokud podporujete|  
|--------------|------------------------|  
|`DBPROP_IConnectionPointContainer`|Vždy|  
|`DBPROP_NOTIFICATIONGRANULARITY`|Vždy|  
|`DBPROP_NOTIFICATIONPHASES`|Vždy|  
|`DBPROP_NOTIFYCOLUMNSET`|`IRowsetChange`|  
|`DBPROP_NOTIFYROWDELETE`|`IRowsetChange`|  
|`DBPROP_NOTIFYROWINSERT`|`IRowsetChange`|  
|`DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE`|Vždy|  
|`DBPROP_NOTIFYROWFIRSTCHANGE`|`IRowsetUpdate`|  
|`DBPROP_NOTIFYROWSETRELEASE`|Vždy|  
|`DBPROP_NOTIFYROWUNDOCHANGE`|`IRowsetUpdate`|  
|`DBPROP_NOTIFYROWUNDODELETE`|`IRowsetUpdate`|  
|`DBPROP_NOTIFYROWUNDOINSERT`|`IRowsetUpdate`|  
|`DBPROP_NOTIFYROWUPDATE`|`IRowsetUpdate`|  
  
 Implementaci pro oznámení je již součástí šablony zprostředkovatele technologie OLE DB. Pokud nepřidáte `IRowsetNotifyCP` do vašeho řetězce dědičnosti kompilátor odebere tento kód z datový proud kompilace, díky čemuž menší velikosti kódu.  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)