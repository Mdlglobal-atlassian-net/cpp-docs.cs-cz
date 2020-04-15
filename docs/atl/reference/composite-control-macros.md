---
title: Kombinovaná řídicí makra
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 67ad18c07a92cfecca44667908a8488e8c2da234
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331520"
---
# <a name="composite-control-macros"></a>Kombinovaná řídicí makra

Tato makra definují mapy a položky jímky událostí.

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Označuje začátek mapy jímky událostí pro složený ovládací prvek.|
|[END_SINK_MAP](#end_sink_map)|Označuje konec mapy jímky událostí pro složený ovládací prvek.|
|[SINK_ENTRY](#sink_entry)|Vstup do mapy jímky událostí.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Vstup do mapy jímky událostí s dalším parametrem.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Podobné SINK_ENTRY_EX s tím rozdílem, že trvá ukazatel iid.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Položka do mapy jímky událostí s ručně zadanými informacemi o typu pro použití s [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Podobné SINK_ENTRY_INFO s tím rozdílem, že trvá ukazatel iid.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a>BEGIN_SINK_MAP

Deklaruje začátek mapy jímky událostí pro složený ovládací prvek.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Parametry

*_class*<br/>
[v] Určuje ovládací prvek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Poznámky

CE ATL implementace jímky událostí ActiveX podporuje pouze vrácené hodnoty typu HRESULT nebo void z metody obslužné rutiny události; všechny ostatní vrácená hodnota není podporována a její chování není definováno.

## <a name="end_sink_map"></a><a name="end_sink_map"></a>END_SINK_MAP

Deklaruje konec mapy jímky událostí pro složený ovládací prvek.

```
END_SINK_MAP()
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Poznámky

CE ATL implementace jímky událostí ActiveX podporuje pouze vrácené hodnoty typu HRESULT nebo void z metody obslužné rutiny události; všechny ostatní vrácená hodnota není podporována a její chování není definováno.

## <a name="sink_entry"></a><a name="sink_entry"></a>SINK_ENTRY

Deklaruje funkci obslužné rutiny (*fn*) pro zadanou událost (*dispid*) ovládacího prvku identifikovaného *id*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikuje ovládací prvek.

*Dispid*<br/>
[v] Identifikuje zadanou událost.

*Fn*<br/>
[v] Název funkce obslužné rutiny události. Tato funkce musí `_stdcall` používat konvence volání a mít odpovídající podpis ve stylu dispinterface.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Poznámky

CE ATL implementace jímky událostí ActiveX podporuje pouze vrácené hodnoty typu HRESULT nebo void z metody obslužné rutiny události; všechny ostatní vrácená hodnota není podporována a její chování není definováno.

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a>SINK_ENTRY_EX a SINK_ENTRY_EX_P

Deklaruje funkci obslužné rutiny (*fn*) pro zadanou událost (*dispid*) rozhraní pro odeslání (*iid*) pro ovládací prvek identifikovaný *id*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Identifikuje ovládací prvek.

*Iid*<br/>
[v] Identifikuje rozhraní pro odesílání.

*piid*<br/>
[v] Ukazatel na rozhraní odeslání.

*Dispid*<br/>
[v] Identifikuje zadanou událost.

*Fn*<br/>
[v] Název funkce obslužné rutiny události. Tato funkce musí `_stdcall` používat konvence volání a mít odpovídající podpis ve stylu dispinterface.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Poznámky

CE ATL implementace jímky událostí ActiveX podporuje pouze vrácené hodnoty typu HRESULT nebo void z metody obslužné rutiny události; všechny ostatní vrácená hodnota není podporována a její chování není definováno.

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a>SINK_ENTRY_INFO a SINK_ENTRY_INFO_P

Pomocí SINK_ENTRY_INFO makra v mapě jímky událostí můžete poskytnout informace, které [iDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) potřebuje ke směrování událostí do příslušné funkce obslužné rutiny.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] Nepodepsané celé číslo identifikující zdroj události. Tato hodnota se musí shodovat s parametrem šablony *nID* použitým v související základní třídě [IDispEventSimpleImpl.](../../atl/reference/idispeventsimpleimpl-class.md)

*Iid*<br/>
[v] IID, který identifikuje rozhraní odeslání.

*piid*<br/>
[v] Ukazatel na IID, který identifikuje rozhraní odeslání.

*Dispid*<br/>
[v] DISPID identifikující zadanou událost.

*Fn*<br/>
[v] Název funkce obslužné rutiny události. Tato funkce musí `_stdcall` používat konvence volání a mít odpovídající podpis ve stylu dispinterface.

*Info*<br/>
[v] Zadejte informace pro funkci obslužné rutiny události. Tyto informace o typu jsou poskytovány ve `_ATL_FUNC_INFO` formě ukazatele na strukturu. CC_CDECL je jedinou možností podporovanou v systému `_ATL_FUNC_INFO` Windows CE pro pole CALLCONV struktury. Jakákoli jiná hodnota není podporována, takže její chování není definováno.

### <a name="remarks"></a>Poznámky

První čtyři parametry makra jsou stejné jako u [SINK_ENTRY_EX](#sink_entry_ex) makra. Konečný parametr poskytuje informace o typu události. CE ATL implementace jímky událostí ActiveX podporuje pouze vrácené hodnoty typu HRESULT nebo void z metody obslužné rutiny události; všechny ostatní vrácená hodnota není podporována a její chování není definováno.

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)<br/>
[Globální funkce složených řízení](../../atl/reference/composite-control-global-functions.md)
