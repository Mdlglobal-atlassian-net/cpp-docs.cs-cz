---
title: CNoRowset – třída
ms.date: 11/04/2016
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
ms.openlocfilehash: 19a1e01fd29c74cf1c44081c24bf384704cf2acd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211468"
---
# <a name="cnorowset-class"></a>CNoRowset – třída

Dá se použít jako argument šablony (`TRowset`) pro [CCommand](../../data/oledb/ccommand-class.md) nebo [CTable](../../data/oledb/ctable-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Přístupová třída. Výchozí formát je `CAccessorBase`.

## <a name="remarks"></a>Poznámky

Použijte `CNoRowset` jako argument šablony, pokud příkaz nevrátí sadu řádků.

`CNoRowset` implementuje následující zástupné metody, z nichž každý odpovídá jiným přístupovým metodám třídy:

- `BindFinished` – určuje, kdy je vazba dokončena (vrátí `S_OK`).

- `Close` – uvolní řádky a aktuální rozhraní IRowset.

- `GetIID` – načte ID rozhraní bodu připojení.

- `GetInterface` – načte rozhraní.

- `GetInterfacePtr` – načte ukazatel zapouzdřeného rozhraní.

- `SetAccessor` – nastaví ukazatel na přistupující objekt.

- `SetupOptionalRowsetInterfaces` – nastaví volitelná rozhraní pro sadu řádků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atldbcli. h

## <a name="see-also"></a>Viz také

[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
