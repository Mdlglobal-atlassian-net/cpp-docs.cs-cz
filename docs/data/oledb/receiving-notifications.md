---
title: "Příjem oznámení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 50911440acbc7514b091a439d42bf73ee60353f9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="receiving-notifications"></a>Příjem oznámení
OLE DB poskytuje rozhraní pro příjem oznámení, když dojde k události. Tyto možnosti jsou popsány v [oznámení objektu technologie OLE DB](https://msdn.microsoft.com/en-us/library/ms725406.aspx) v *referenční příručka programátora technologie OLE DB*. Nastavení těchto událostí používá standardní mechanismus COM spojovacího bodu. Například ATL objekt, který chce načíst události prostřednictvím `IRowsetNotify` implementuje `IRowsetNotify` rozhraní přidáním `IRowsetNotify` seznamu odvozených tříd a přes vystavení **COM_INTERFACE_ENTRY** makro.  
  
 `IRowsetNotify` má tři metody, které lze volat v různé časy. Pokud chcete, aby odpovídal na pouze jednu z těchto metod, můžete použít [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) třídy, která vrátí **E_NOTIMPL** pro metody nejste zájem.  
  
 Při vytváření sady řádků se musí zjistit poskytovatele má objekt vrácený řádků pro podporu **IConnectionPointContainer**, který je nutný k nastavení oznámení.  
  
 Následující kód ukazuje, jak otevřít sadu řádků z objektu knihovny ATL a použít `AtlAdvise` funkce, nastavení oznámení jímky. `AtlAdvise` Vrátí souboru cookie, který se používá při volání `AtlUnadvise`.  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IConnectionPointContainer, true);  
  

product.Open(session, _T("Products"), &propset);  
  

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)