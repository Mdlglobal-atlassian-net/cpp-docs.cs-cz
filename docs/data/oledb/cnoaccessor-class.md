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
ms.openlocfilehash: d6eb5aaa9a66f46335b0a364e6c6e79abc297d64
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647889"
---
# <a name="cnoaccessor-class"></a>CNoAccessor – třída

Můžete použít jako argument šablony (`TAccessor`) pro šablony třídy, jako například `CCommand` a `CTable`, přístupového objektu argumentu třídy, které vyžadují.

## <a name="syntax"></a>Syntaxe

```cpp
class CNoAccessor
```

## <a name="remarks"></a>Poznámky

Použití `CNoAccessor` jako argument šablony, když nechcete, aby třídu tak, aby podporovala parametry nebo výstupní sloupce.

`CNoAccessor` implementuje následující metody zástupných procedur, z nichž každý odpovídají jiné přístupové metody pro třídu:

- `BindColumns` -Váže sloupce pro přistupující objekty.

- `BindParameters` -Vytvoří vazbu vytvořené parametry sloupce.

- `Bind` -Vytváří vazby.

- `Close` -Zavře přistupujícího objektu.

- `ReleaseAccessors` -Uvolní přistupující objekty vytvořené třídy.

- `FreeRecordMemory` -Uvolní všechny sloupce v aktuální záznam, který musí být uvolněna.

- `GetColumnInfo` -Získá informace o sloupci z otevřené sady řádků.

- `GetNumAccessors` -Načte počet přistupující objekty vytvořené třídy.

- `IsAutoAccessor` -Vrátí true, pokud je během operace přesunu automaticky načíst data pro přistupující objekt.

- `GetHAccessor` -Načte popisovač přistupujícího objektu zadaného přístupového objektu.

- `GetBuffer` -Načte ukazatel na záložku vyrovnávací paměti.

- `NoBindOnNullRowset` -Brání vytváření datových vazeb na prázdné sady řádků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="see-also"></a>Viz také

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)