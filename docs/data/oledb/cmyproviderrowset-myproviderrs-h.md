---
title: CCustomRowset (CustomRS.H) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderrowset
- myproviderrs.h
- ccustomrowset
- customrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 211c83ec63611c493f03e48b58619caca373ce65
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216354"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

Průvodce vytvoří položku pro objektu sady řádků. V takovém případě se nazývá `CCustomRowset`. `CCustomRowset` Třída dědí ze třídy zprostředkovatele OLE DB volá `CRowsetImpl`, který implementuje všechna potřebná rozhraní objektu sady řádků. Následující kód ukazuje řetězec dědičnosti pro `CRowsetImpl`:

```cpp
template <class T, class Storage, class CreatorClass, 
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType, 
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` také používá `IAccessor` a `IColumnsInfo` rozhraní. Tato rozhraní se používá pro výstupní pole tabulky. Třída rovněž poskytuje implementaci pro `IRowsetIdentity`, která umožňuje příjemci k určení, zda jsou dva řádky stejné. `IRowsetInfo` Rozhraní implementuje vlastnosti objektu sady řádků. `IConvertType` Rozhraní umožňuje poskytovatelem a vyřešit rozdíly mezi datovými typy požadoval uživatel a používaných zprostředkovatelem.

`IRowset` Rozhraní ve skutečnosti zpracovává data načítání. Příjemce nejprve volá metodu s názvem `GetNextRows` se vraťte na řádek, označované jako popisovač `HROW`. Pak zavolá příjemce `IRowset::GetData` s ním `HROW` načíst požadovaná data.

`CRowsetImpl` také přijímá několik parametrů šablony. Tyto parametry umožňují určit, jak `CRowsetImpl` třída zpracovává data. `ArrayType` Argument umožňuje určit, jaký mechanismus úložiště se používá k ukládání dat řádku. *RowClass* parametr určuje, jaké třída obsahuje `HROW`.

*RowsetInterface* parametr umožňuje použít také `IRowsetLocate` nebo `IRowsetScroll` rozhraní. `IRowsetLocate` a `IRowsetScroll` obě dědí z rozhraní `IRowset`. Šablony zprostředkovatele OLE DB proto musíte zadat speciální zpracování pro tato rozhraní. Pokud chcete použít některou z těchto rozhraní, budete muset použít tento parametr.

## <a name="see-also"></a>Viz také

[Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)<br/>
