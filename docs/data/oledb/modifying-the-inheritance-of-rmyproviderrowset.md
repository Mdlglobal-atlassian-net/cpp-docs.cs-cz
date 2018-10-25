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
ms.openlocfilehash: 1a9b6e238d3824451ab0f820917c34c97826ffab
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060387"
---
# <a name="modifying-the-inheritance-of-rcustomrowset"></a>Úprava dědičnosti třídy RCustomRowset

Chcete-li přidat `IRowsetLocate` rozhraní příklad jednoduchého zprostředkovatele pouze pro čtení, změňte dědičnost `RCustomRowset`. Na začátku `RCustomRowset` dědí z `CRowsetImpl`. Je potřeba upravit tak, aby dědí `CRowsetBaseImpl`.

Chcete-li to provést, vytvořte novou třídu, `CCustomRowsetImpl`, v CustomRS.h:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

template <class T, class Storage, class CreatorClass, class ArrayType = CAtlArray<Storage>>
class CCustomRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, CSimpleRow, IRowsetLocateImpl< T, IRowsetLocate >>
{
...
};
```

Nyní upravte mapu rozhraní modelu COM v CustomRS.h měl vypadat takto:

```cpp
BEGIN_COM_MAP(CCustomRowsetImpl)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

Tím se vytvoří mapu rozhraní modelu COM, která říká `CCustomRowsetImpl` volat `QueryInterface` pro obě `IRowset` a `IRowsetLocate` rozhraní. Chcete-li získat všechny ostatní sady řádků implementace třídy, odkazy mapy `CCustomRowsetImpl` třídy zpět na `CRowsetBaseImpl` třídy definované šablony technologie OLE DB; na mapě používá makro COM_INTERFACE_ENTRY_CHAIN, který informuje šablony technologie OLE DB kontrolovat mapy modelu COM v `CRowsetBaseImpl` v reakci `QueryInterface` volání.

Nakonec propojit `RAgentRowset` k `CCustomRowsetBaseImpl` úpravou `RAgentRowset` dědit z `CCustomRowsetImpl`, následujícím způsobem:

```cpp
class RAgentRowset : public CCustomRowsetImpl<RAgentRowset, CAgentMan, CCustomCommand>
```

`RAgentRowset` Teď můžete použít `IRowsetLocate` rozhraní s využitím rest implementace třídy sady řádků.

Když to uděláte, můžete [dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Viz také

[Rozšíření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md)