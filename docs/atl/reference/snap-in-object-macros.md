---
title: Makra objektů modulu snap-In
ms.date: 11/04/2016
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
ms.openlocfilehash: e3eec62e2bea92f1f308b149046b83be1b9085b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656934"
---
# <a name="snap-in-object-macros"></a>Makra objektů modulu snap-In

Tato makra poskytovat podporu pro rozšíření modulu snap-in.

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Označuje začátek toho mapování třídy modulu snap-in rozšíření dat pro objekt modulu Snap-In.|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Označuje začátek toho nástrojů mapování pro objekt modulu Snap-In.|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Označuje konec mapování třídy modulu snap-in rozšíření dat pro objekt modulu Snap-In.|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Označuje konec nástrojů mapování pro objekt modulu Snap-In.|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Vytvoří datové členy třídy dat rozšíření modulu snap-in.|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Třída dat rozšíření modulu snap-in zadá do mapování třídy modulu snap-in rozšíření dat objektu modulu Snap-In.|
|[SNAPINMENUID](#snapinmenuid)|Deklaruje ID v místní nabídce používané tímto objektem modul Snap-In.|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Vloží panel nástrojů do panelu nástrojů mapy objektu modulu Snap-In.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsnap.h

##  <a name="begin_extension_snapin_nodeinfo_map"></a>  BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

Označuje začátek toho mapování třídy dat rozšíření modulu snap-in.

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>Parametry

*Název třídy*<br/>
[in] Název třídy datového rozšíření modulu snap-in.

### <a name="remarks"></a>Poznámky

Začínat – makro BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP mapy rozšíření modulu snap-in, přidejte položky pro každý z vašich rozšíření modulu snap-in datové typy s [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) – makro a proveďte mapování [ END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) – makro.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

##  <a name="begin_snapintoolbarid_map"></a>  BEGIN_SNAPINTOOLBARID_MAP

Deklaruje začátku mapování ID nástrojů pro objekt modulu Snap-In.

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>Parametry

*_třídy*<br/>
[in] Určuje třídu objektu modulu Snap-In.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

##  <a name="end_extension_snapin_nodeinfo_map"></a>  END_EXTENSION_SNAPIN_NODEINFO_MAP

Označuje konec mapování třídy dat rozšíření modulu snap-in.

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Poznámky

Spusťte modul snap-in rozšíření mapu s [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) – makro, přidejte položky pro každý z vašich rozšíření modulu snap-in datové typy s [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) makra a dokončit mapy s END_EXTENSION_SNAPIN_NODEINFO_MAP makra.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

##  <a name="end_snapintoolbarid_map"></a>  END_SNAPINTOOLBARID_MAP

Deklaruje konec mapování ID nástrojů pro objekt modulu Snap-In.

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>Parametry

*_třídy*<br/>
[in] Určuje třídu objektu modulu Snap-In.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

##  <a name="extension_snapin_dataclass"></a>  EXTENSION_SNAPIN_DATACLASS

Datový člen přidá do datové třídy pro rozšíření modulu snap-in **ISnapInItemImpl**-odvozené třídy.

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>Parametry

*dataClass*<br/>
[in] Třída dat rozšíření modulu snap-in.

### <a name="remarks"></a>Poznámky

Tato třída by měly být zadány také do mapování modulu snap-in rozšíření dat třídy. Spusťte modul snap-in rozšíření třídy mapování dat s [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) – makro, přidejte položky pro každý z vašich rozšíření modulu snap-in datové typy s [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)– makro a proveďte mapování [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) – makro.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

##  <a name="extension_snapin_nodeinfo_entry"></a>  EXTENSION_SNAPIN_NODEINFO_ENTRY

Přidá třídu dat rozšíření modulu snap-in k mapování třídy dat rozšíření modulu snap-in.

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>Parametry

*dataClass*<br/>
[in] Třída dat rozšíření modulu snap-in.

### <a name="remarks"></a>Poznámky

Spusťte modul snap-in rozšíření třídy mapování dat s [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) – makro, přidejte položky pro každý z vašich rozšíření modulu snap-in datové typy s EXTENSION_SNAPIN_NODEINFO_ENTRY – makro a dokončete mapy s [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) – makro.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

##  <a name="snapinmenuid"></a>  SNAPINMENUID

Chcete-li deklarovat prostředků místní nabídky objektu modulu Snap-In, použijte toto makro.

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Určuje místní nabídky objektu modulu Snap-In.

##  <a name="snapintoolbarid_entry"></a>  SNAPINTOOLBARID_ENTRY

Použijte toto makro odsouhlasit Identifikátor panelu nástrojů Mapa nástrojů ID objektu modulu Snap-In.

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Určuje ovládací prvek panelu nástrojů.

### <a name="remarks"></a>Poznámky

[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) – makro označuje začátek toho mapování ID nástrojů; [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) – makro označuje konec.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
