---
title: CCustomRowset (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyproviderrowset
- ccustomrowset
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
ms.openlocfilehash: 8e90db287bc7ac8994914766045eb210446dfd48
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079783"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

Průvodce vygeneruje položku pro objekt sady řádků. V tomto případě se nazývá `CCustomRowset`. Třída `CCustomRowset` dědí z třídy poskytovatele OLE DB s názvem `CRowsetImpl`, která implementuje všechna potřebná rozhraní pro objekt sady řádků. Následující kód ukazuje řetěz dědičnosti pro `CRowsetImpl`:

```cpp
template <class T, class Storage, class CreatorClass,
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` používá také rozhraní `IAccessor` a `IColumnsInfo`. Tato rozhraní používá pro výstupní pole v tabulkách. Třída také poskytuje implementaci pro `IRowsetIdentity`, která umožňuje příjemci určit, zda jsou dva řádky stejné. Rozhraní `IRowsetInfo` implementuje vlastnosti pro objekt sady řádků. Rozhraní `IConvertType` umožňuje poskytovateli vyřešit rozdíly mezi datovými typy požadovanými příjemcem a uživateli, které použil poskytovatel.

Rozhraní `IRowset` ve skutečnosti zpracovává načítání dat. Uživatel nejprve volá metodu nazvanou `GetNextRows`, která vrátí popisovač řádku, který se označuje jako `HROW`. Příjemce pak zavolá `IRowset::GetData` s tímto `HROW` načte požadovaná data.

`CRowsetImpl` také přebírá několik parametrů šablony. Tyto parametry umožňují určit, jak `CRowsetImpl` třída zpracovává data. Argument `ArrayType` umožňuje určit, který mechanismus úložiště se používá k ukládání dat řádků. Parametr *RowClass* určuje, která třída obsahuje `HROW`.

Parametr *RowsetInterface* umožňuje také použít rozhraní `IRowsetLocate` nebo `IRowsetScroll`. Rozhraní `IRowsetLocate` a `IRowsetScroll` dědí z `IRowset`. Proto šablony poskytovatele OLE DB musí pro tato rozhraní poskytovat speciální zpracování. Pokud chcete použít jedno z těchto rozhraní, je nutné použít tento parametr.

## <a name="see-also"></a>Viz také

[Soubory generované průvodcem zprostředkovatele](../../data/oledb/provider-wizard-generated-files.md)<br/>
