---
title: Makra složených ovládacích prvků
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 10965fed5aac2eb037cf9894998688e3e7c2bffa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498971"
---
# <a name="composite-control-macros"></a>Makra složených ovládacích prvků

Tato makra definují mapy jímek událostí a položek.

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Označuje začátek toho, na mapě událostí jímky složeného ovládacího prvku.|
|[END_SINK_MAP](#end_sink_map)|Označuje konec toho, na mapě událostí jímky složeného ovládacího prvku.|
|[SINK_ENTRY](#sink_entry)|Položka k mapě událostí jímky.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Položka mapy jímky událostí s dalším parametrem.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Podobně jako SINK_ENTRY_EX s tím rozdílem, že bere ukazatel na iid.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Položka mapy jímky událostí s informacemi o ručně zadaný typ pro použití s [idispeventsimpleimpl –](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Podobně jako SINK_ENTRY_INFO s tím rozdílem, že bere ukazatel na iid.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="begin_sink_map"></a>  BEGIN_SINK_MAP

Deklaruje začátku na mapě událostí jímky složeného ovládacího prvku.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Parametry

*_třídy*<br/>
[in] Určuje ovládací prvek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Poznámky

Provádění CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a její chování není definováno.

##  <a name="end_sink_map"></a>  END_SINK_MAP

Deklaruje koncové na mapě událostí jímky složeného ovládacího prvku.

```
END_SINK_MAP()
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Poznámky

Provádění CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a její chování není definováno.

##  <a name="sink_entry"></a>  SINK_ENTRY

Deklaruje funkci obslužné rutiny (*fn*) pro zadanou událost (*dispid*), ovládacího prvku identifikovaný *id*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Určuje ovládací prvek.

*identifikátor DISPID*<br/>
[in] Identifikuje zadané události.

*fn*<br/>
[in] Název funkce obslužné rutiny události. Musíte použít tuto funkci `_stdcall` konvence volání a mít podpis stylům dispinterface.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Poznámky

Provádění CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a její chování není definováno.

##  <a name="sink_entry_ex"></a>  SINK_ENTRY_EX a SINK_ENTRY_EX_P

Deklaruje funkci obslužné rutiny (*fn*) pro zadanou událost (*dispid*), rozhraní odbavení (*iid*), ovládacího prvku identifikovaný *id*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Určuje ovládací prvek.

*identifikátor IID*<br/>
[in] Určuje rozhraní odbavení.

*piid*<br/>
[in] Ukazatel na rozhraní odbavení.

*identifikátor DISPID*<br/>
[in] Identifikuje zadané události.

*fn*<br/>
[in] Název funkce obslužné rutiny události. Musíte použít tuto funkci `_stdcall` konvence volání a mít podpis stylům dispinterface.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Poznámky

Provádění CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a její chování není definováno.

##  <a name="sink_entry_info"></a>  SINK_ENTRY_INFO a SINK_ENTRY_INFO_P

Použijte makro SINK_ENTRY_INFO v rámci mapu jímky událostí k poskytování informací potřebných [idispeventsimpleimpl –](../../atl/reference/idispeventsimpleimpl-class.md) pro směrování událostí na relevantní obslužné rutiny.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*id*<br/>
[in] Celé číslo bez znaménka určující zdroj události. Tato hodnota musí odpovídat *nID* šablony parametr použitý v souvisejících článcích [idispeventsimpleimpl –](../../atl/reference/idispeventsimpleimpl-class.md) základní třídy.

*identifikátor IID*<br/>
[in] Identifikátor IID, který identifikuje rozhraní odbavení.

*piid*<br/>
[in] Ukazatel na IID, který identifikuje rozhraní odbavení.

*identifikátor DISPID*<br/>
[in] Identifikátor DISPID identifikace zadané události.

*fn*<br/>
[in] Název funkce obslužné rutiny události. Musíte použít tuto funkci `_stdcall` konvence volání a mít podpis stylům dispinterface.

*Informace o*<br/>
[in] Zadejte informace pro funkce obslužné rutiny události. Informace o tomto typu je k dispozici ve formě ukazatel na `_ATL_FUNC_INFO` struktury. CC_CDECL je jedinou možností, které jsou podporované ve Windows CE pro DEFINICI pole `_ATL_FUNC_INFO` struktury. Jakákoli jiná hodnota není podporován tedy nedefinované chování.

### <a name="remarks"></a>Poznámky

První čtyři – makro parametry jsou stejné jako u [SINK_ENTRY_EX](#sink_entry_ex) – makro. Poslední parametr poskytuje informace o typu události. Provádění CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a její chování není definováno.

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)<br/>
[Globální funkce složených ovládacích prvků](../../atl/reference/composite-control-global-functions.md)
