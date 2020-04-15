---
title: Makra objektů modulu snap-in
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
ms.openlocfilehash: 6a57cdb3c9b6a4448bc954ff754ac9b18fa0b393
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325861"
---
# <a name="snap-in-object-macros"></a>Makra objektů modulu snap-in

Tato makra poskytují podporu pro rozšíření modulu snap-in.

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Označuje začátek mapování datových tříd rozšíření přichycení pro objekt modulu Snap-In.|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Označí začátek mapy panelu nástrojů pro objekt modulu Snap-In.|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Označuje konec mapování datových tříd rozšíření přichycení pro objekt modulu Snap-In.|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Označí konec mapy panelu nástrojů pro objekt modulu Snap-In.|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Vytvoří datový člen pro datovou třídu rozšíření modulu snap-in.|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Zadá třídu dat rozšíření modulu snap-in do mapování datové třídy rozšíření modulu snap-in objektu Snap-In.|
|[SNAPINMENUID](#snapinmenuid)|Deklaruje ID kontextové nabídky používané objektem snap-in.|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Zadá panel nástrojů do mapy panelu nástrojů objektu Modulu snap-In.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsnap.h

## <a name="begin_extension_snapin_nodeinfo_map"></a><a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

Označuje začátek mapování datových tříd rozšíření přichycení.

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
[v] Název datové třídy rozšíření modulu snap-in.

### <a name="remarks"></a>Poznámky

Začněte mapu rozšíření modulu snap-in pomocí BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP makra, přidejte položky pro každý datový typ rozšíření modulu [snap-in](#extension_snapin_nodeinfo_entry) pomocí EXTENSION_SNAPIN_NODEINFO_ENTRY makru a dokončete mapu [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makra.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="begin_snapintoolbarid_map"></a><a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP

Deklaruje začátek mapy ID panelu nástrojů pro objekt modulu Snap-In.

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>Parametry

*_class*<br/>
[v] Určuje třídu objektu Modul snap-in.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

## <a name="end_extension_snapin_nodeinfo_map"></a><a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP

Označuje konec mapování datových tříd rozšíření přichycení.

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Poznámky

Začněte mapu rozšíření modulu snap-in pomocí [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makra, přidejte položky pro každý datový typ modulu snap-in rozšíření pomocí [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) makru a dokončete mapu END_EXTENSION_SNAPIN_NODEINFO_MAP makra.

### <a name="example"></a>Příklad

Viz příklad pro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="end_snapintoolbarid_map"></a><a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP

Deklaruje konec mapy ID panelu nástrojů pro objekt modulu snap-in.

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>Parametry

*_class*<br/>
[v] Určuje třídu objektu Modul snap-in.

### <a name="example"></a>Příklad

Viz příklad pro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="extension_snapin_dataclass"></a><a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS

Přidá datový člen do datové třídy rozšíření modulu snap-in pro odvozenou třídu **ISnapInItemImpl**.

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>Parametry

*třída dataClass*<br/>
[v] Třída dat rozšíření modulu snap-in.

### <a name="remarks"></a>Poznámky

Tato třída by měla být také zadána do mapování datových tříd rozšíření modulu snap-in. Začněte mapování datových tříd rozšíření modulu snap-in s [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makra, přidejte položky pro každý datový typ rozšíření modulu snap-in pomocí [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) makru a doplnovněte mapu [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makra.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="extension_snapin_nodeinfo_entry"></a><a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY

Přidá do mapování datových tříd rozšíření modulu snap-in třídu rozšíření.

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>Parametry

*třída dataClass*<br/>
[v] Třída dat rozšíření modulu snap-in.

### <a name="remarks"></a>Poznámky

Začněte mapování datových tříd rozšíření modulu snap-in s [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map) makra, přidejte položky pro každý datový typ rozšíření modulu snap-in pomocí EXTENSION_SNAPIN_NODEINFO_ENTRY makru a doplnovit mapu [END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map) makra.

### <a name="example"></a>Příklad

Viz příklad pro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="snapinmenuid"></a><a name="snapinmenuid"></a>SNAPINMENUID

Toto makro slouží k deklarování prostředku kontextové nabídky objektu Snap-In.

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikuje místní nabídku objektu Snap-In.

## <a name="snapintoolbarid_entry"></a><a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY

Toto makro slouží k zadání ID panelu nástrojů do mapy ID panelu nástrojů objektu snap-in.

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikuje ovládací prvek panelu nástrojů.

### <a name="remarks"></a>Poznámky

Makro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) označuje začátek mapy ID panelu nástrojů; [makro END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) označuje konec.

### <a name="example"></a>Příklad

Viz příklad pro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
