---
title: CColumnAccessor – třída
ms.date: 11/04/2016
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
ms.openlocfilehash: 2a3b1dac51a8300a915a7177c36f15512b583fa0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212107"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor – třída

Generuje vložený kód příjemce.

## <a name="syntax"></a>Syntaxe

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>Poznámky

Ve vloženém kódu je každý sloupec svázán jako samostatný přistupující objekt. Měli byste si uvědomit, že tato třída se používá ve vloženém kódu (například při ladění může být k dispozici), ale obvykle ji nemusíte používat nebo přímo na své metody.

`CColumnAccessor` implementuje následující zástupné metody, z nichž každý odpovídá funkčnosti jiným přístupovým metodám třídy:

- `CColumnAccessor` konstruktoru; Vytvoří instanci a inicializuje objekt `CColumnAccessor`.

- `CreateAccessor` přiděluje paměť pro struktury vazeb sloupců a inicializuje datové členy sloupce.

- `BindColumns` váže sloupce k přistupujícím objektů.

- `SetParameterBuffer` přiděluje vyrovnávací paměti pro parametry.

- `AddParameter` přidá do struktur vstupních parametrů položku parametru.

- `HasOutputColumns` určuje, zda má přistupující objekt výstupní sloupce.

- `HasParameters` určuje, zda přistupující objekt obsahuje parametry.

- `BindParameters` váže vytvořené parametry na sloupce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
