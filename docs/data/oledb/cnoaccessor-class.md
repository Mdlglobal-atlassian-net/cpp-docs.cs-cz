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
ms.openlocfilehash: 0cf1b47cc03d1839ae5c547393c3c193dab439d4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027659"
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

## <a name="see-also"></a>Viz také:

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)