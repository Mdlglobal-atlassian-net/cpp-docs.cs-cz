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
ms.openlocfilehash: 2c84ff359bdbb39f281928fa0135edd40b1f7d20
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446081"
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
