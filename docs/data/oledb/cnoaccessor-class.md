---
title: CNoAccessor – třída
ms.date: 11/04/2016
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
ms.openlocfilehash: c82d756690c6c2a719cb03f458c471aa44e3d5b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211728"
---
# <a name="cnoaccessor-class"></a>CNoAccessor – třída

Dá se použít jako argument šablony (`TAccessor`) pro třídy šablon, jako je `CCommand` a `CTable`, které vyžadují přistupující argument třídy.

## <a name="syntax"></a>Syntaxe

```cpp
class CNoAccessor
```

## <a name="remarks"></a>Poznámky

Pokud nechcete, aby třída podporovala parametry nebo výstupní sloupce, použijte `CNoAccessor` jako argument šablony.

`CNoAccessor` implementuje následující zástupné metody, z nichž každý odpovídá jiným přístupovým metodám třídy:

- `BindColumns`-váže sloupce pro přistupující objekty.

- `BindParameters` – vytvoří vazby vytvořených parametrů na sloupce.

- `Bind` – vytvoří vazby.

- `Close` – zavře přistupující objekt.

- `ReleaseAccessors` – uvolňuje přistupující objekty vytvořené třídou.

- `FreeRecordMemory` – uvolní všechny sloupce v aktuálním záznamu, které je třeba uvolnit.

- `GetColumnInfo` – načte informace o sloupci z otevřené sady řádků.

- `GetNumAccessors` – načte počet přístupových objektů vytvořených třídou.

- `IsAutoAccessor` – vrátí hodnotu true, pokud jsou data automaticky načtena pro přistupující objekt během operace přesunutí.

- `GetHAccessor` – načte popisovač přistupujícího objektu zadaného přístupového objektu.

- `GetBuffer` – načte ukazatel na vyrovnávací paměť záložky.

- `NoBindOnNullRowset` – zabrání datové vazbě v prázdných sadách řádků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
