---
title: Úprava dědičnosti třídy RMyProviderRowset | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RMyProviderRowset
- inheritance [C++]
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 77b26d1d0b67726e1ba2cd66d0e181bc04105a6a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028165"
---
# <a name="modifying-the-inheritance-of-rmyproviderrowset"></a>Úprava dědičnosti třídy RMyProviderRowset

Chcete-li přidat `IRowsetLocate` rozhraní příklad jednoduchého zprostředkovatele pouze pro čtení, změňte dědičnost `RMyProviderRowset`. Na začátku `RMyProviderRowset` dědí z `CRowsetImpl`. Je potřeba upravit tak, aby dědí `CRowsetBaseImpl`.  
  
Chcete-li to provést, vytvořte novou třídu, `CMyRowsetImpl`, v souboru MyProviderRS.h:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>  
{  
...  
};  
```  
  
Nyní upravte mapu rozhraní modelu COM v souboru MyProviderRS.h takto:  
  
```cpp  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
Tím se vytvoří mapu rozhraní modelu COM, která říká `CMyRowsetImpl` volat `QueryInterface` pro obě `IRowset` a `IRowsetLocate` rozhraní. Chcete-li získat všechny ostatní sady řádků implementace třídy, odkazy mapy `CMyRowsetImpl` třídy zpět na `CRowsetBaseImpl` třídy definované šablony technologie OLE DB; na mapě používá makro COM_INTERFACE_ENTRY_CHAIN, který informuje šablony technologie OLE DB kontrolovat mapy modelu COM v `CRowsetBaseImpl` v reakci `QueryInterface` volání.  
  
Nakonec propojit `RAgentRowset` k `CMyRowsetBaseImpl` úpravou `RAgentRowset` dědit z `CMyRowsetImpl`, následujícím způsobem:  
  
```cpp  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CMyProviderCommand>  
```  
  
`RAgentRowset` Teď můžete použít `IRowsetLocate` rozhraní s využitím rest implementace třídy sady řádků.  
  
Když to uděláte, můžete [dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Viz také  

[Rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)