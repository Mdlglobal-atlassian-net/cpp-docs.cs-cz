---
title: Složená makra ovládacího prvku
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 685bf55910d4746463de30b17b71aa6d246db199
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417787"
---
# <a name="composite-control-macros"></a>Složená makra ovládacího prvku

Tato makra definují mapy a položky jímky událostí.

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Označuje začátek mapy jímky událostí složeného ovládacího prvku.|
|[END_SINK_MAP](#end_sink_map)|Označuje konec mapy jímky událostí pro složený ovládací prvek.|
|[SINK_ENTRY](#sink_entry)|Záznam do mapy jímky událostí.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Záznam do mapy jímky událostí s dalším parametrem.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Podobně jako u SINK_ENTRY_EX s tím rozdílem, že přebírá ukazatel na identifikátor IID.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Záznam do mapy jímky událostí s ručně dodanými informacemi o typu pro použití s [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Podobně jako u SINK_ENTRY_INFO s tím rozdílem, že přebírá ukazatel na identifikátor IID.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="begin_sink_map"></a>BEGIN_SINK_MAP

Deklaruje začátek mapy jímky událostí pro složený ovládací prvek.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Parametry

*_class*<br/>
pro Určuje ovládací prvek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Poznámky

Implementace CE ATL jímka událostí ActiveX podporuje pouze návratové hodnoty typu HRESULT nebo void z metod obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a chování není definováno.

##  <a name="end_sink_map"></a>END_SINK_MAP

Deklaruje konec mapy jímky událostí pro složený ovládací prvek.

```
END_SINK_MAP()
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Poznámky

Implementace CE ATL jímka událostí ActiveX podporuje pouze návratové hodnoty typu HRESULT nebo void z metod obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a chování není definováno.

##  <a name="sink_entry"></a>SINK_ENTRY

Deklaruje funkci obslužné rutiny (*FN*) pro zadanou událost (*DISPID*) ovládacího prvku identifikovaného *ID*.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Identifikuje ovládací prvek.

*DISPID*<br/>
pro Identifikuje zadanou událost.

*VistaScan*<br/>
pro Název funkce obslužné rutiny události Tato funkce musí používat konvenci volání `_stdcall` a musí mít příslušný podpis ve stylu odesílajícího.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Poznámky

Implementace CE ATL jímka událostí ActiveX podporuje pouze návratové hodnoty typu HRESULT nebo void z metod obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a chování není definováno.

##  <a name="sink_entry_ex"></a>SINK_ENTRY_EX a SINK_ENTRY_EX_P

Deklaruje funkci obslužné rutiny (*FN*) pro zadanou událost (*DISPID*) z rozhraní Dispatch (*IID*) pro ovládací prvek identifikovaný *identifikátorem*.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Identifikuje ovládací prvek.

*identifikátor*<br/>
pro Identifikuje rozhraní dispatch.

*piid*<br/>
pro Ukazatel na rozhraní dispatching.

*DISPID*<br/>
pro Identifikuje zadanou událost.

*VistaScan*<br/>
pro Název funkce obslužné rutiny události Tato funkce musí používat konvenci volání `_stdcall` a musí mít příslušný podpis ve stylu odesílajícího.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Poznámky

Implementace CE ATL jímka událostí ActiveX podporuje pouze návratové hodnoty typu HRESULT nebo void z metod obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a chování není definováno.

##  <a name="sink_entry_info"></a>SINK_ENTRY_INFO a SINK_ENTRY_INFO_P

Pomocí makra SINK_ENTRY_INFO v rámci mapy jímky událostí poskytněte informace, které [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) potřebuje ke směrování událostí do příslušné funkce obslužné rutiny.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro Celé číslo bez znaménka identifikující zdroj události. Tato hodnota se musí shodovat s parametrem šablony *NID* použitým v související základní třídě [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) .

*identifikátor*<br/>
pro IID, který identifikuje rozhraní dispatch.

*piid*<br/>
pro Ukazatel na identifikátor IID, který identifikuje rozhraní dispatch.

*DISPID*<br/>
pro Identifikátor DISPID identifikující zadanou událost

*VistaScan*<br/>
pro Název funkce obslužné rutiny události Tato funkce musí používat konvenci volání `_stdcall` a musí mít příslušný podpis ve stylu odesílajícího.

*příjemce*<br/>
pro Informace o typu pro funkci obslužné rutiny událostí. Tyto informace o typu jsou k dispozici ve formě ukazatele na strukturu `_ATL_FUNC_INFO`. CC_CDECL je jediná možnost podporovaná v systém Windows CE pro pole definice struktury `_ATL_FUNC_INFO`. Jakákoli jiná hodnota je Nepodporovaná, takže její chování není definované.

### <a name="remarks"></a>Poznámky

První čtyři parametry makra jsou stejné jako u [SINK_ENTRY_EXho](#sink_entry_ex) makra. Konečný parametr poskytuje informace o typu události. Implementace CE ATL jímka událostí ActiveX podporuje pouze návratové hodnoty typu HRESULT nebo void z metod obslužné rutiny události; jakákoli jiná návratová hodnota není podporována a chování není definováno.

## <a name="see-also"></a>Viz také

[Makr](../../atl/reference/atl-macros.md)<br/>
[Globální funkce složených ovládacích prvků](../../atl/reference/composite-control-global-functions.md)
