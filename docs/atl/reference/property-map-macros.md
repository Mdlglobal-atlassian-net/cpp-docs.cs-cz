---
title: Makra mapy vlastností
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
ms.openlocfilehash: 56fdb02939a99e396b9000705753e2475b80f6dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326095"
---
# <a name="property-map-macros"></a>Makra mapy vlastností

Tato makra definují mapy vlastností a položky.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Označuje začátek mapy vlastností ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Označuje rozsah nebo rozměry ovládacího prvku ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Do mapy vlastností zadá popis vlastnosti, vlastnost DISPID a stránku vlastností CLSID.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Do mapy vlastností zadá popis vlastnosti, vlastnost `IDispatch` DISPID, stránku vlastností CLSID a IID.|
|[PROP_PAGE](#prop_page)|Zadá stránku vlastností CLSID do mapy vlastností.|
|[END_PROP_MAP](#end_prop_map)|Označuje konec mapy vlastností ATL.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="begin_prop_map"></a><a name="begin_prop_map"></a>BEGIN_PROP_MAP

Označuje začátek mapy vlastností objektu.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
[v] Určuje třídu obsahující mapu vlastností.

### <a name="remarks"></a>Poznámky

Mapa vlastností ukládá popisy vlastností, dispidvlastnosti, clsids stránky vlastností a `IDispatch` IIDs. Třídy [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)a [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) používají mapu vlastností k načtení a nastavení těchto informací.

Když vytvoříte objekt pomocí Průvodce projektem knihovny ATL, průvodce vytvoří mapu prázdných vlastností zadáním BEGIN_PROP_MAP následované [END_PROP_MAP](#end_prop_map).

BEGIN_PROP_MAP neuloží rozsah (tj. dimenze) mapy vlastností, protože objekt používající mapu vlastností nemusí mít uživatelské rozhraní, takže by neměl žádný rozsah. Pokud je objekt ovládací prvek ActiveX s uživatelským rozhraním, má rozsah. V takovém případě je nutné zadat [PROP_DATA_ENTRY](#prop_data_entry) v mapě vlastností, abyste dodávali rozsah.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

## <a name="prop_data_entry"></a><a name="prop_data_entry"></a>PROP_DATA_ENTRY

Označuje rozsah nebo rozměry ovládacího prvku ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
[v] Popis vlastnosti.

*Členské*<br/>
[v] Datový člen obsahující rozsah; například `m_sizeExtent`.

*Vt*<br/>
[v] Určuje typ vlastnosti VARIANT.

### <a name="remarks"></a>Poznámky

Toto makro způsobí, že zadaný datový člen bude trvalý.

Při vytváření ovládacího prvku ActiveX vloží průvodce toto makro za [BEGIN_PROP_MAP](#begin_prop_map) makra mapy vlastností a před [END_PROP_MAP](#end_prop_map)makra mapy vlastností .

### <a name="example"></a>Příklad

V následujícím příkladu je zachován`m_sizeExtent`rozsah objektu ( ).

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

## <a name="prop_entry_type"></a><a name="prop_entry_type"></a>PROP_ENTRY_TYPE

Toto makro slouží k zadání popisu vlastnosti, vlastnosti DISPID a stránky vlastností CLSID do mapy vlastností objektu.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
[v] Popis vlastnosti.

*Dispid*<br/>
[v] Vlastnost je DISPID.

*Identifikátor clsid*<br/>
[v] CLSID přidružené stránky vlastností. Použijte speciální hodnotu CLSID_NULL pro vlastnost, která nemá přidruženou stránku vlastností.

*Vt*<br/>
[v] Typ nemovitosti.

### <a name="remarks"></a>Poznámky

Makro PROP_ENTRY bylo nejisté a zastaralé. Byl nahrazen PROP_ENTRY_TYPE.

Makro [BEGIN_PROP_MAP](#begin_prop_map) označuje začátek mapy vlastností; [makro END_PROP_MAP](#end_prop_map) označuje konec.

### <a name="example"></a>Příklad

Viz příklad pro [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="prop_entry_type_ex"></a><a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

Podobně jako [PROP_ENTRY_TYPE](#prop_entry_type), ale umožňuje zadat konkrétní IID, pokud váš objekt podporuje více duální rozhraní.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
[v] Popis vlastnosti.

*Dispid*<br/>
[v] Vlastnost je DISPID.

*Identifikátor clsid*<br/>
[v] CLSID přidružené stránky vlastností. Použijte speciální hodnotu CLSID_NULL pro vlastnost, která nemá přidruženou stránku vlastností.

*iidDispatch*<br/>
[v] IID duální rozhraní definující vlastnost.

*Vt*<br/>
[v] Typ nemovitosti.

### <a name="remarks"></a>Poznámky

Makro PROP_ENTRY_EX bylo nezabezpečené a zastaralé. Byl nahrazen PROP_ENTRY_TYPE_EX.

Makro [BEGIN_PROP_MAP](#begin_prop_map) označuje začátek mapy vlastností; [makro END_PROP_MAP](#end_prop_map) označuje konec.

### <a name="example"></a>Příklad

Následující příklad seskupí položky pro `IMyDual1` následuje položka pro `IMyDual2`. Seskupování podle duálního rozhraní zlepší výkon.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

## <a name="prop_page"></a><a name="prop_page"></a>PROP_PAGE

Toto makro slouží k zadání stránky vlastností CLSID do mapy vlastností objektu.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
[v] CLSID stránky vlastností.

### <a name="remarks"></a>Poznámky

PROP_PAGE je podobná [PROP_ENTRY_TYPE](#prop_entry_type), ale nevyžaduje popis vlastnosti nebo DISPID.

> [!NOTE]
> Pokud jste již zadali CLSID s PROP_ENTRY_TYPE nebo [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), není nutné provádět další položku s PROP_PAGE.

Makro [BEGIN_PROP_MAP](#begin_prop_map) označuje začátek mapy vlastností; [makro END_PROP_MAP](#end_prop_map) označuje konec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

## <a name="end_prop_map"></a><a name="end_prop_map"></a>END_PROP_MAP

Označuje konec mapy vlastností objektu.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Poznámky

Když vytvoříte objekt pomocí Průvodce projektem knihovny ATL, průvodce vytvoří mapu prázdných vlastností zadáním [BEGIN_PROP_MAP](#begin_prop_map) následovaných END_PROP_MAP.

### <a name="example"></a>Příklad

Viz příklad pro [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
