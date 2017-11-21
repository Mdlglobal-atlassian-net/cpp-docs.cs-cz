---
title: "Příjem oznámení | Microsoft Docs"
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
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ed9c82d97a1d96777ae9b7e3c28b8ffa0de4507a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="receiving-notifications"></a>Příjem oznámení
OLE DB poskytuje rozhraní pro příjem oznámení, když dojde k události. Tyto možnosti jsou popsány v [oznámení objektu technologie OLE DB](https://msdn.microsoft.com/en-us/library/ms725406.aspx) v *referenční příručka programátora technologie OLE DB*. Nastavení těchto událostí používá standardní mechanismus COM spojovacího bodu. Například ATL objekt, který chce načíst události prostřednictvím `IRowsetNotify` implementuje `IRowsetNotify` rozhraní přidáním `IRowsetNotify` seznamu odvozených tříd a přes vystavení **COM_INTERFACE_ENTRY** makro.  
  
 `IRowsetNotify`má tři metody, které lze volat v různé časy. Pokud chcete, aby odpovídal na pouze jednu z těchto metod, můžete použít [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) třídy, která vrátí **E_NOTIMPL** pro metody nejste zájem.  
  
 Při vytváření sady řádků se musí zjistit poskytovatele má objekt vrácený řádků pro podporu **IConnectionPointContainer**, který je nutný k nastavení oznámení.  
  
 Následující kód ukazuje, jak otevřít sadu řádků z objektu knihovny ATL a použít `AtlAdvise` funkce, nastavení oznámení jímky. `AtlAdvise`Vrátí souboru cookie, který se používá při volání `AtlUnadvise`.  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
propset.AddProperty(DBPROP_IConnectionPointContainer, true);  
  
product.Open(session, _T("Products"), &propset);  
  
AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití přístupových objektů](../../data/oledb/using-accessors.md)