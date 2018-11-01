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
ms.openlocfilehash: 513e393bbc782d87b37dab108428f2970fbb92e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644453"
---
# <a name="cnorowset-class"></a>CNoRowset – třída

Můžete použít jako argument šablony (`TRowset`) pro [CCommand](../../data/oledb/ccommand-class.md) nebo [CTable](../../data/oledb/ctable-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Třídu přistupujícího objektu. Výchozí hodnota je `CAccessorBase`.

## <a name="remarks"></a>Poznámky

Použití `CNoRowset` jako argument šablony, pokud příkaz nevrací sadu řádků.

`CNoRowset` implementuje následující metody zástupných procedur, z nichž každý odpovídají jiné přístupové metody pro třídu:

- `BindFinished` -Určuje po dokončení vazby (vrátí `S_OK`).

- `Close` -Uvolní řádků a aktuální IRowset rozhraní.

- `GetIID` -Načte rozhraní ID bodu připojení.

- `GetInterface` -Načte rozhraní.

- `GetInterfacePtr` -Načte zapouzdřený ukazatel rozhraní.

- `SetAccessor` – Nastaví ukazatel na přistupujícím objektu.

- `SetupOptionalRowsetInterfaces` – Nastaví volitelné rozhraní pro sadu řádků.

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="see-also"></a>Viz také

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)