---
title: Úprava dědičnosti třídy RCustomRowset | Dokumentace společnosti Microsoft
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
- RCustomRowset
ms.assetid: 33089c90-98a4-43e7-8e67-d4bb137e267e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a6f4827ecf0571878bc0eeaef5dce74326488c61
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990280"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>Úprava dědičnosti třídy RCustomRowset

Chcete-li přidat `IRowsetLocate` rozhraní příklad jednoduchého zprostředkovatele pouze pro čtení, změňte dědičnost `RCustomRowset`. Na začátku `RCustomRowset` dědí z `CRowsetImpl`. Je potřeba upravit tak, aby dědí `CRowsetBaseImpl`.  
  
Chcete-li to provést, vytvořte novou třídu, `CMyRowsetImpl`v *vlastní*RS.h:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// CustomRS.h  
  
template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>  
class CMyRowsetImpl:  
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>  
{  
...  
};  
```  
  
Nyní, upravit mapu rozhraní modelu COM v *vlastní*RS.h měl vypadat takto:  
  
```cpp  
BEGIN_COM_MAP(CMyRowsetImpl)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
Tím se vytvoří mapu rozhraní modelu COM, která říká `CMyRowsetImpl` volat `QueryInterface` pro obě `IRowset` a `IRowsetLocate` rozhraní. Chcete-li získat všechny ostatní sady řádků implementace třídy, odkazy mapy `CMyRowsetImpl` třídy zpět na `CRowsetBaseImpl` třídy definované šablony technologie OLE DB; na mapě používá makro COM_INTERFACE_ENTRY_CHAIN, který informuje šablony technologie OLE DB kontrolovat mapy modelu COM v `CRowsetBaseImpl` v reakci `QueryInterface` volání.  
  
Nakonec propojit `RAgentRowset` k `CMyRowsetBaseImpl` úpravou `RAgentRowset` dědit z `CMyRowsetImpl`, následujícím způsobem:  
  
```cpp  
class RAgentRowset : public CMyRowsetImpl<RAgentRowset, CAgentMan, CCustomCommand>  
```  
  
`RAgentRowset` Teď můžete použít `IRowsetLocate` rozhraní s využitím rest implementace třídy sady řádků.  
  
Když to uděláte, můžete [dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Viz také  

[Rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)