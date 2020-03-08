---
title: Makra mapování vlastností
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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857181"
---
# <a name="property-map-macros"></a>Makra mapování vlastností

Tato makra definují mapování a položky vlastností.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Označí začátek mapy vlastností ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Určuje rozsah, nebo rozměry ovládacího prvku ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Do mapy vlastností vloží popis vlastnosti, identifikátor DISPID vlastnosti a stránku vlastností.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Zadá popis vlastnosti, identifikátor DISPID vlastnosti, CLSID stránky vlastností a `IDispatch` IID do mapování vlastností.|
|[PROP_PAGE](#prop_page)|Vloží do mapy vlastností identifikátor CLSID stránky vlastností.|
|[END_PROP_MAP](#end_prop_map)|Označuje konec mapy vlastností ATL.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="begin_prop_map"></a>BEGIN_PROP_MAP

Označuje začátek mapování vlastností objektu.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
pro Určuje třídu obsahující mapu vlastností.

### <a name="remarks"></a>Poznámky

V mapě vlastností jsou uloženy popisy vlastností, identifikátory SPID vlastností, CLSID stránky vlastností a `IDispatch` IID. Třídy [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)a [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) používají mapu vlastností k načtení a nastavení těchto informací.

Při vytváření objektu pomocí Průvodce projekt ATL vytvoří průvodce prázdnou mapu vlastnosti zadáním BEGIN_PROP_MAP následovaných [END_PROP_MAP](#end_prop_map).

BEGIN_PROP_MAP neukládá rozsah (tj. dimenze) mapování vlastností, protože objekt, který používá mapu vlastností, nemusí mít uživatelské rozhraní, takže by neměl mít žádný rozsah. Pokud je objekt ovládacím prvkem ActiveX s uživatelským rozhraním, má rozsah. V takovém případě je nutné zadat [PROP_DATA_ENTRY](#prop_data_entry) v mapě vlastností, aby bylo možné zadat rozsah.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>PROP_DATA_ENTRY

Určuje rozsah, nebo rozměry ovládacího prvku ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
pro Popis vlastnosti

*člen*<br/>
pro Datový člen, který obsahuje rozsah; například `m_sizeExtent`.

*terminálu*<br/>
pro Určuje typ VARIANT vlastnosti.

### <a name="remarks"></a>Poznámky

Toto makro způsobí, že zadaný datový člen bude zachován.

Když vytvoříte ovládací prvek ActiveX, Průvodce vloží toto makro po [BEGIN_PROP_MAP](#begin_prop_map) makro mapování vlastností a předtím, než [END_PROP_MAP](#end_prop_map)makro mapování vlastností.

### <a name="example"></a>Příklad

V následujícím příkladu je trvalý rozsah objektu (`m_sizeExtent`).

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>PROP_ENTRY_TYPE

Pomocí tohoto makra můžete zadat popis vlastnosti, identifikátor DISPID vlastnosti a stránky vlastností CLSID do mapování vlastností objektu.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
pro Popis vlastnosti

*DISPID*<br/>
pro Identifikátor DISPID vlastnosti

*CLSID*<br/>
pro Identifikátor CLSID přidružené stránky vlastností Použijte CLSID_NULL speciální hodnoty pro vlastnost, která nemá přidruženou stránku vlastností.

*terminálu*<br/>
pro Typ vlastnosti.

### <a name="remarks"></a>Poznámky

Makro PROP_ENTRY bylo nezabezpečené a zastaralé. Byl nahrazen PROP_ENTRY_TYPE.

Makro [BEGIN_PROP_MAP](#begin_prop_map) označuje začátek mapy vlastností; [END_PROP_MAP](#end_prop_map) makro označí konec.

### <a name="example"></a>Příklad

Podívejte se na příklad [BEGIN_PROP_MAP](#begin_prop_map).

##  <a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

Podobně jako [PROP_ENTRY_TYPE](#prop_entry_type), ale umožňuje zadat konkrétní IID, pokud váš objekt podporuje více duálních rozhraní.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Parametry

*szDesc*<br/>
pro Popis vlastnosti

*DISPID*<br/>
pro Identifikátor DISPID vlastnosti

*CLSID*<br/>
pro Identifikátor CLSID přidružené stránky vlastností Použijte CLSID_NULL speciální hodnoty pro vlastnost, která nemá přidruženou stránku vlastností.

*iidDispatch*<br/>
pro IID duálního rozhraní, které definuje vlastnost.

*terminálu*<br/>
pro Typ vlastnosti.

### <a name="remarks"></a>Poznámky

Makro PROP_ENTRY_EX bylo nezabezpečené a zastaralé. Byl nahrazen PROP_ENTRY_TYPE_EX.

Makro [BEGIN_PROP_MAP](#begin_prop_map) označuje začátek mapy vlastností; [END_PROP_MAP](#end_prop_map) makro označí konec.

### <a name="example"></a>Příklad

Následující příklad seskupuje položky `IMyDual1` následovaný záznamem pro `IMyDual2`. Seskupení podle duálního rozhraní zvýší výkon.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>PROP_PAGE

Pomocí tohoto makra můžete zadat identifikátor CLSID stránky vlastností do mapování vlastností objektu.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Parametry

*CLSID*<br/>
pro Identifikátor CLSID stránky vlastností

### <a name="remarks"></a>Poznámky

PROP_PAGE je podobná [PROP_ENTRY_TYPE](#prop_entry_type), ale nevyžaduje popis vlastnosti nebo DISPID.

> [!NOTE]
>  Pokud jste již zadali CLSID s PROP_ENTRY_TYPE nebo [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), není nutné vytvořit další položku s PROP_PAGE.

Makro [BEGIN_PROP_MAP](#begin_prop_map) označuje začátek mapy vlastností; [END_PROP_MAP](#end_prop_map) makro označí konec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>END_PROP_MAP

Označuje konec mapování vlastností objektu.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Poznámky

Při vytváření objektu pomocí Průvodce projekt ATL vytvoří průvodce prázdnou mapu vlastnosti zadáním [BEGIN_PROP_MAP](#begin_prop_map) následovaných END_PROP_MAP.

### <a name="example"></a>Příklad

Podívejte se na příklad [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Viz také

[Makr](../../atl/reference/atl-macros.md)
