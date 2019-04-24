---
title: Makra Map vlastností
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
ms.openlocfilehash: 1e2e7235dd924467d9d5e0613a704fedf8340ae4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197265"
---
# <a name="property-map-macros"></a>Makra Map vlastností

Tato makra definují mapy vlastností a položek.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Označuje začátek toho mapy vlastností knihovny ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Určuje rozsah nebo rozměry ovládacího prvku ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Popis vlastnosti DISPID a vlastnost stránky vlastností CLSID zadá do mapy vlastností.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Popis vlastnosti, vlastnost DISPID, stránka vlastností CLSID, zadá a `IDispatch` IID do mapy vlastností.|
|[PROP_PAGE](#prop_page)|Zadá identifikátor CLSID stránky vlastností do objektu map vlastností.|
|[END_PROP_MAP](#end_prop_map)|Označuje konec mapování vlastností knihovny ATL.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="begin_prop_map"></a>  BEGIN_PROP_MAP

Označuje začátek toho mapy vlastností objektu.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
[in] Určuje třídu obsahující mapy vlastností.

### <a name="remarks"></a>Poznámky

Mapy vlastností ukládá popisy vlastností, vlastnost dispID, stránka vlastností CLSID, a `IDispatch` IID. Třídy [iperpropertybrowsingimpl –](../../atl/reference/iperpropertybrowsingimpl-class.md), [ipersistpropertybagimpl –](../../atl/reference/ipersistpropertybagimpl-class.md), [ipersiststreaminitimpl –](../../atl/reference/ipersiststreaminitimpl-class.md), a [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)použijte mapu vlastnosti načíst a nastavit tyto informace.

Při vytváření objektu s Průvodce projektem ATL průvodce vytvoří mapu prázdnou vlastností tak, že zadáte BEGIN_PROP_MAP, za nímž následuje [END_PROP_MAP](#end_prop_map).

BEGIN_PROP_MAP nelze uložit mimo rozsah (to znamená, dimenzí) vlastnosti mapy, protože objekt pomocí vlastnosti mapy nemusí mít uživatelské rozhraní, měl by mít žádné míry. Pokud je objekt ovládacího prvku ActiveX s uživatelským rozhraním, má rozsah. V takovém případě je nutné zadat [PROP_DATA_ENTRY](#prop_data_entry) mapě vlastnost slouží k poskytování rozsahu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>  PROP_DATA_ENTRY

Určuje rozsah nebo rozměry ovládacího prvku ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
[in] Vlastnost popis.

*Člen*<br/>
[in] Datový člen obsahující míry; například `m_sizeExtent`.

*vt*<br/>
[in] Určuje typ varianty vlastnosti.

### <a name="remarks"></a>Poznámky

Toto makro způsobí, že zadaný datový člen natrvalo.

Při vytváření ovládacího prvku ActiveX Průvodce vloží toto makro za makra map vlastností [BEGIN_PROP_MAP](#begin_prop_map) a před makra map vlastností [END_PROP_MAP](#end_prop_map).

### <a name="example"></a>Příklad

V následujícím příkladu, rozsah objektu (`m_sizeExtent`) se jako trvalý.

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>  PROP_ENTRY_TYPE

Pomocí tohoto makra zadejte popis, vlastnost DISPID a vlastnost stránky vlastností CLSID do mapy vlastností objektu.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
[in] Vlastnost popis.

*dispid*<br/>
[in] Vlastnosti DISPID.

*clsid*<br/>
[in] Identifikátor CLSID stránky vlastností. Zvláštní hodnota CLSID_NULL použijte pro vlastnost, která nemá stránku přidružené vlastnosti.

*vt*<br/>
[in] Typ vlastnosti.

### <a name="remarks"></a>Poznámky

Makra PROP_ENTRY byl nezabezpečené a zastaralé funkce. To bylo nahrazeno tématem PROP_ENTRY_TYPE.

[BEGIN_PROP_MAP](#begin_prop_map) – makro označuje začátek toho mapy vlastností; [END_PROP_MAP](#end_prop_map) – makro označuje konec.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_PROP_MAP](#begin_prop_map).

##  <a name="prop_entry_type_ex"></a>  PROP_ENTRY_TYPE_EX

Podobně jako [PROP_ENTRY_TYPE](#prop_entry_type), ale můžete určit konkrétní IID, pokud objekt podporuje více duálních rozhraní.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
[in] Vlastnost popis.

*dispid*<br/>
[in] Vlastnosti DISPID.

*clsid*<br/>
[in] Identifikátor CLSID stránky vlastností. Zvláštní hodnota CLSID_NULL použijte pro vlastnost, která nemá stránku přidružené vlastnosti.

*iidDispatch*<br/>
[in] Identifikátor IID definující vlastnost duální rozhraní.

*vt*<br/>
[in] Typ vlastnosti.

### <a name="remarks"></a>Poznámky

Makra PROP_ENTRY_EX byl nezabezpečené a zastaralé funkce. To bylo nahrazeno tématem PROP_ENTRY_TYPE_EX.

[BEGIN_PROP_MAP](#begin_prop_map) – makro označuje začátek toho mapy vlastností; [END_PROP_MAP](#end_prop_map) – makro označuje konec.

### <a name="example"></a>Příklad

Následující příklad skupiny položky pro `IMyDual1` za nímž následuje záznam pro `IMyDual2`. Seskupení podle duální rozhraní pomůže zvýšit výkon.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>  PROP_PAGE

Použijte toto makro zadat identifikátor CLSID stránky vlastností do mapy vlastností objektu.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Parametry

*clsid*<br/>
[in] Identifikátor CLSID stránky vlastností.

### <a name="remarks"></a>Poznámky

Je podobný PROP_PAGE [PROP_ENTRY_TYPE](#prop_entry_type), ale nevyžaduje, aby vlastnost Popis nebo DISPID.

> [!NOTE]
>  Pokud jste už zadali CLSID s PROP_ENTRY_TYPE nebo [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), není potřeba provést další položka se PROP_PAGE.

[BEGIN_PROP_MAP](#begin_prop_map) – makro označuje začátek toho mapy vlastností; [END_PROP_MAP](#end_prop_map) – makro označuje konec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>  END_PROP_MAP

Označuje konec mapy vlastností objektu.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Poznámky

Při vytváření objektu s Průvodce projektem ATL průvodce vytvoří mapu prázdnou vlastností tak, že zadáte [BEGIN_PROP_MAP](#begin_prop_map) za nímž následuje END_PROP_MAP.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Viz také:

[Makra](../../atl/reference/atl-macros.md)
