---
title: "IRowsetNotifyCP – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetNotifyCP
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyCP class
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7d20a4eb011b67a743e91f1f8340c80ea146bb7c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP – třída
Implementuje poskytovatele lokality pro bod připojení rozhraní [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx).  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>  
class IRowsetNotifyCP :   
   public IConnectionPointImpl<  
      T,   
      piid = &__uuidof(IRowsetNotify),   
      CComDynamicUnkArray DynamicUnkArray>,  
   public ReentrantEventSync  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída odvozená z `IRowsetNotifyCP`.  
  
 `ReentrantEventSync`  
 Mutex – třída, která podporuje vícenásobný přístup (výchozí hodnota je **CComSharedMutex**). Mutex je na synchronizační objekt, který umožňuje jedno vlákno vzájemně se vylučuje přístupu k prostředku.  
  
 `piid`  
 Ukazatel rozhraní ID (**IID\***) pro **IRowsetNotify** rozhraní bodu připojení. Výchozí hodnota je **& __uuidof(IRowsetNotify)**.  
  
 `DynamicUnkArray`  
 Pole typu [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), což je dynamicky přidělené pole **IUnknown** ukazatele na klienta jímka rozhraní.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Fire_OnFieldChange](../../data/oledb/irowsetnotifycp-fire-onfieldchange.md)|Upozorní příjemce změnu hodnoty sloupce.|  
|[Fire_OnRowChange](../../data/oledb/irowsetnotifycp-fire-onrowchange.md)|Upozorní příjemce změny, které mají vliv na řádky.|  
|[Fire_OnRowsetChange](../../data/oledb/irowsetnotifycp-fire-onrowsetchange.md)|Upozorní příjemce změnu ovlivňující celou sadu řádků.|  
  
## <a name="remarks"></a>Poznámky  
 `IRowsetNotifyCP` implementuje vysílání funkce pro navedení naslouchací procesy ve spojovacím bodě **IID_IRowsetNotify** změny obsah sady řádků.  
  
 Všimněte si, že je nutné implementovat a zaregistrovat `IRowsetNotify` pro příjemce (také označované jako "jímka") pomocí [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) tak, aby příjemce mohl zpracovávat oznámení. V tématu [příjem oznámení](../../data/oledb/receiving-notifications.md) o implementaci rozhraní bodu připojení pro příjemce.  
  
 Podrobné informace o implementaci oznámení najdete v části "Podpora oznámení" v [vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atldb.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Oznámení (COM)](http://msdn.microsoft.com/library/windows/desktop/ms678433)   
 [BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)   
 [END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)   
 [CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)   
 [Vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md)