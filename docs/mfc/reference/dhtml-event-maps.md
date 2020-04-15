---
title: DHTML – mapa událostí
ms.date: 11/04/2016
f1_keywords:
- vc.macros.shared
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
ms.openlocfilehash: 30c755b2901374cffab3ce91d0683811ef6624b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365811"
---
# <a name="dhtml-event-maps"></a>DHTML – mapa událostí

Následující makra lze použít ke zpracování událostí DHTML.

## <a name="dhtml-event-map-macros"></a>Makra mapy událostí DHTML

Následující makra lze použít ke zpracování událostí DHTML v [cdhtmldialog](../../mfc/reference/cdhtmldialog-class.md)-odvozené třídy.

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Označuje začátek mapy událostí DHTML.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Označuje začátek mapy událostí DHTML.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Deklaruje mapu událostí DHTML.|
|[DHTML_EVENT](#dhtml_event)|Slouží ke zpracování události na úrovni dokumentu pro jeden element HTML.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Slouží ke zpracování události vypálené ovládacím prvkem ActiveX.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Slouží ke zpracování události na úrovni dokumentu pro všechny elementy HTML s určitou třídou CSS.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Slouží ke zpracování události na úrovni prvku.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Slouží ke `onafterupdate` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Slouží ke `onbeforeupdate` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Slouží ke `onblur` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Slouží ke `onchange` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Slouží ke `onclick` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Slouží ke `ondataavailable` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Slouží ke `ondatasetchanged` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Slouží ke `ondatasetcomplete` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Slouží ke `ondblclick` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Slouží ke `ondragstart` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Slouží ke `onerrorupdate` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Slouží ke `onfilterchange` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Slouží ke `onfocus` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Slouží ke `onhelp` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Slouží ke `onkeydown` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Slouží ke `onkeypress` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Slouží ke `onkeyup` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Slouží ke `onmousedown` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Slouží ke `onmousemove` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Slouží ke `onmouseout` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Slouží ke `onmouseover` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Slouží ke `onmouseup` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Slouží ke `onresize` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Slouží ke `onrowenter` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Slouží ke `onrowexit` zpracování události z elementu HTML.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Slouží ke `onselectstart` zpracování události z elementu HTML.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Slouží ke zpracování události na úrovni dokumentu pro všechny prvky s určitou značkou HTML.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Označuje konec mapy událostí DHTML.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Označuje konec mapy událostí DHTML. |

## <a name="url-event-map-macros"></a>Makra mapy událostí adresy URL

Následující makra lze použít ke zpracování událostí DHTML v třídách odvozených [z CMultiPageDHtmlDialog.](../../mfc/reference/cmultipagedhtmldialog-class.md)

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Označuje začátek vícestránkové mapy událostí DHTML a URL.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Označuje začátek vložené mapy událostí DHTML.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Označuje začátek mapy pro zadání události adresy URL.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Deklaruje vícestránkovou mapu událostí DHTML a URL.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Označuje konec vícestránkové mapy událostí DHTML a URL.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Označuje konec vložené mapy událostí DHTML.|
|[END_URL_ENTRIES](#end_url_entries)|Označuje konec mapy pro zadání události adresy URL.|
|[URL_EVENT_ENTRY](#url_event_entry)|Mapuje adresu URL nebo prostředek HTML na stránku ve vícestránkovém dialogu.|

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a>BEGIN_DHTML_EVENT_MAP

Označí začátek mapy událostí DHTML při umístění do `className`zdrojového souboru pro třídu identifikovanou aplikací .

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Název třídy obsahující mapu událostí DHTML. Tato třída by měla být odvozena přímo nebo nepřímo z [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) a zahrnout [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) makro do definice třídy.

### <a name="remarks"></a>Poznámky

Přidejte mapu událostí DHTML do třídy, která poskytuje informace, `CDHtmlDialog` které lze použít ke směrování událostí vypalovaných prvky HTML nebo ovládacími prvky ActiveX na webové stránce do funkcí obslužné rutiny ve vaší třídě.

Umístěte BEGIN_DHTML_EVENT_MAP makro do souboru implementace třídy (.cpp) následovaný DHTML_EVENT makra pro události, které má třída zpracovat (například DHTML_EVENT_ONMOUSEOVER pro události mouseoveru). Pomocí [END_DHTML_EVENT_MAP](#end_dhtml_event_map) makra označte konec mapy událostí. Tato makra implementují následující funkci:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a>BEGIN_DHTML_EVENT_MAP_INLINE

Označuje začátek mapy událostí DHTML v rámci definice třídy pro *název_třídy*.

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Název třídy obsahující mapu událostí DHTML. Tato třída by měla být odvozena přímo nebo nepřímo z [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) a zahrnout [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) makro do definice třídy.

### <a name="remarks"></a>Poznámky

Přidejte mapu událostí DHTML do třídy, která poskytuje informace, `CDHtmlDialog` které lze použít ke směrování událostí vypalovaných prvky HTML nebo ovládacími prvky ActiveX na webové stránce do funkcí obslužné rutiny ve vaší třídě.

Umístěte BEGIN_DHTML_EVENT_MAP makro do souboru definice třídy (.h) následovaný makra DHTML_EVENT pro události, které má třída zpracovat (například DHTML_EVENT_ONMOUSEOVER pro události s myší). Pomocí [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) makra označte konec mapy událostí. Tato makra implementují následující funkci:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a>DECLARE_DHTML_EVENT_MAP

Deklaruje mapu událostí DHTML v definici třídy.

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Poznámky

Toto makro má být použito v definici tříd odvozených z [CDHtmlDialog.](../../mfc/reference/cdhtmldialog-class.md)

K implementaci mapy použijte [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) nebo [BEGIN_DHTML_EVENT_MAP_INLINE.](#begin_dhtml_event_map_inline)

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) deklaruje následující funkci:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event"></a><a name="dhtml_event"></a>DHTML_EVENT

Zpracovává (na úrovni dokumentu) událost označená *dispid* vznikl a element HTML identifikovaný *elemName*.

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
DISPID události, která má být zpracována.

*elemName*<br/>
LPCWSTR, který drží ID elementu HTML, který získává událost, nebo NULL pro zpracování událostí dokumentu.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a>DHTML_EVENT_AXCONTROL

Zpracovává událost označenou *dispid* fired ovládacího prvku ActiveX *označeného controlName*.

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
ID odeslání události, která má být zpracována.

*název ovládacího prvku*<br/>
LPCWSTR drží HTML ID ovládacího prvku spouštění události.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a>DHTML_EVENT_CLASS

Zpracovává (na úrovni dokumentu) událost označená *dispid* vznikl a jakýkoli prvek HTML s CSS třídy označené *elemName*.

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
ID odeslání události, která má být zpracována.

*elemName*<br/>
LPCWSTR drží css třídy HTML prvků získávání události.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a>DHTML_EVENT_ELEMENT

Zpracovává (na prvek identifikovaný *elemName*) událost označená *dispid*.

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
ID odeslání události, která má být zpracována.

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

Pokud se toto makro používá ke zpracování událostí bez bublinek, bude zdrojem události prvek identifikovaný *elemName*.

Pokud toto makro slouží ke zpracování probublávání události, prvek identifikovaný *elemName* nemusí být zdrojem události (zdrojem může být libovolný prvek obsažený *elemName*).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a>DHTML_EVENT_ONAFTERUPDATE

Zpracovává (na úrovni dokumentu) `onafterupdate` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a>DHTML_EVENT_ONBEFOREUPDATE

Zpracovává (na úrovni dokumentu) `onbeforeupdate` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a>DHTML_EVENT_ONBLUR

Zpracovává (na úrovni prvku) `onblur` události. Toto je nebublající událost.

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a>DHTML_EVENT_ONCHANGE

Zpracovává (na úrovni prvku) `onchange` události. Toto je nebublající událost.

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a>DHTML_EVENT_ONCLICK

Zpracovává (na úrovni dokumentu) `onclick` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a>DHTML_EVENT_ONDATAAVAILABLE

Zpracovává (na úrovni dokumentu) `ondataavailable` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a>DHTML_EVENT_ONDATASETCHANGED

Zpracovává (na úrovni dokumentu) `ondatasetchanged` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a>DHTML_EVENT_ONDATASETCOMPLETE

Zpracovává (na úrovni dokumentu) `ondatasetcomplete` událost vznikla element HTML `elemName`identifikován .

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a>DHTML_EVENT_ONDBLCLICK

Zpracovává (na úrovni dokumentu) `ondblclick` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a>DHTML_EVENT_ONDRAGSTART

Zpracovává (na úrovni dokumentu) `ondragstart` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a>DHTML_EVENT_ONERRORUPDATE

Zpracovává (na úrovni dokumentu) `onerrorupdate` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a>DHTML_EVENT_ONFILTERCHANGE

Zpracovává (na úrovni dokumentu) `onfilterchange` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a>DHTML_EVENT_ONFOCUS

Zpracovává (na úrovni prvku) `onfocus` události. Toto je nebublající událost.

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a>DHTML_EVENT_ONHELP

Zpracovává (na úrovni dokumentu) `onhelp` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a>DHTML_EVENT_ONKEYDOWN

Zpracovává (na úrovni dokumentu) `onkeydown` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a>DHTML_EVENT_ONKEYPRESS

Zpracovává (na úrovni dokumentu) `onkeypress` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a>DHTML_EVENT_ONKEYUP

Zpracovává (na úrovni dokumentu) `onkeyup` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a>DHTML_EVENT_ONMOUSEDOWN

Zpracovává (na úrovni dokumentu) `onmousedown` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a>DHTML_EVENT_ONMOUSEMOVE

Zpracovává (na úrovni dokumentu) `onmousemove` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a>DHTML_EVENT_ONMOUSEOUT

Zpracovává (na úrovni dokumentu) `onmouseout` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a>DHTML_EVENT_ONMOUSEOVER

Zpracovává (na úrovni dokumentu) `onmouseover` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a>DHTML_EVENT_ONMOUSEUP

Zpracovává (na úrovni dokumentu) `onmouseup` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a>DHTML_EVENT_ONRESIZE

Zpracovává (na úrovni prvku) `onresize` události. Toto je nebublající událost.

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a>DHTML_EVENT_ONROWENTER

Zpracovává (na úrovni dokumentu) `onrowenter` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a>DHTML_EVENT_ONROWEXIT

Zpracovává (na úrovni dokumentu) `onrowexit` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a>DHTML_EVENT_ONSELECTSTART

Zpracovává (na úrovni dokumentu) `onselectstart` událost vznikla element HTML identifikován *elemName*.

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR držící ID elementu HTML, který událost získává.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a>DHTML_EVENT_TAG

Zpracovává (na úrovni dokumentu) událost `dispid` identifikovanou libovolným elementem HTML se značkou HTML označenou *elemName*.

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
ID odeslání události, která má být zpracována.

*elemName*<br/>
Značka HTML prvků HTML, které událost získávají.

*členFxn*<br/>
Funkce obslužné rutiny pro událost.

### <a name="remarks"></a>Poznámky

Toto makro slouží k přidání položky do [mapy událostí DHTML](#begin_dhtml_event_map_inline) ve vaší třídě.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a>END_DHTML_EVENT_MAP

Označuje konec mapy událostí DHTML.

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Poznámky

Musí být použit ve spojení s [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a>BEGIN_DHTML_URL_EVENT_MAP

Spustí definici mapy událostí DHTML a URL ve vícestránkovém dialogu.

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Poznámky

Vložte BEGIN_DHTML_URL_EVENT_MAP do implementačního souboru odvozené třídy [CMultiPageDHtmlDialog.](../../mfc/reference/cmultipagedhtmldialog-class.md) Postupujte podle něj s [vloženými mapami událostí DHTML](#begin_embed_dhtml_event_map) a [položkami adres URL](#begin_url_entries)a zavřete je [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Zahrnout [makro DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) do definice třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a>BEGIN_EMBED_DHTML_EVENT_MAP

Spustí definici vložené mapy událostí DHTML ve vícestránkovém dialogu.

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Název třídy obsahující mapu událostí. Tato třída by měla být odvozena přímo nebo nepřímo z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Vložená mapa událostí DHTML musí být uvnitř [mapy událostí DHTML a URL).](#begin_dhtml_url_event_map)

*název mapy*<br/>
Určuje stránku, jejíž mapa událostí se nachází. To odpovídá *mapName* v [URL_EVENT_ENTRY](#url_event_entry) makru skutečně definování URL nebo HTML prostředku.

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že vícestránkový dialog DHTML se skládá z více stránek HTML, z nichž každá může vyvolat události DHTML, vložená mapování map událostí se používá k mapování událostí na obslužné rutiny na základě jednotlivých stránek.

Vložená mapování událostí v mapách událostí DHTML a URL se skládá z BEGIN_EMBED_DHTML_EVENT_MAP makra následovaného [DHTML_EVENT](#dhtml_event) makry a [END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map) makra.

Každé vložené mapování událostí vyžaduje odpovídající [položku události URL](#url_event_entry) pro *mapName* (zadaný v BEGIN_EMBED_DHTML_EVENT_MAP) na adresu URL nebo prostředek HTML.

### <a name="example"></a>Příklad

Viz příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a>BEGIN_URL_ENTRIES

Spustí definici mapy pro zadávání událostí adresy URL ve vícestránkovém dialogu.

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Název třídy obsahující mapu pro zadání události adresy URL. Tato třída by měla být odvozena přímo nebo nepřímo z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa pro vstup událostí adresy URL musí být uvnitř [mapy událostí DHTML a URL](#begin_dhtml_url_event_map)).

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že dialogové okno Vícestránkového dhtml se skládá z více stránek HTML, používají se položky událostí url k mapování adres URL nebo prostředků HTML na odpovídající [vložené mapy událostí DHTML](#begin_embed_dhtml_event_map). Mezi makra BEGIN_URL_ENTRIES a [END_URL_ENTRIES](#end_url_entries) vložte URL_EVENT_ENTRY makra.

### <a name="example"></a>Příklad

Viz příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a>DECLARE_DHTML_URL_EVENT_MAP

Deklaruje mapu událostí DHTML a URL v definici třídy.

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Poznámky

Toto makro má být použito v definici tříd odvozených z [cMultiPageDHtmlDialog.](../../mfc/reference/cmultipagedhtmldialog-class.md)

Mapa událostí DHTML a URL obsahuje [vložené mapy událostí DHTML](#begin_embed_dhtml_event_map) a [položky událostí URL,](#begin_url_entries) které mapují události DHTML na obslužné rutiny na základě stránky. Pomocí [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) k implementaci mapy.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a>END_DHTML_URL_EVENT_MAP

Označuje konec mapy událostí DHTML a URL.

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Název třídy obsahující mapu událostí. Tato třída by měla být odvozena přímo nebo nepřímo z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). To by mělo odpovídat *className* v odpovídající [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) makro.

### <a name="example"></a>Příklad

Viz příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a>END_EMBED_DHTML_EVENT_MAP

Označuje konec vložené mapy událostí DHTML.

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>Příklad

Viz příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="end_url_entries"></a><a name="end_url_entries"></a>END_URL_ENTRIES

Označuje konec mapy pro zadání události adresy URL.

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>Příklad

Viz příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="url_event_entry"></a><a name="url_event_entry"></a>URL_EVENT_ENTRY

Mapuje adresu URL nebo prostředek HTML na stránku ve vícestránkovém dialogu.

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Název třídy obsahující mapu pro zadání události adresy URL. Tato třída by měla být odvozena přímo nebo nepřímo z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa pro vstup událostí adresy URL musí být uvnitř [mapy událostí DHTML a URL](#begin_dhtml_url_event_map)).

*Adresu url*<br/>
Url nebo HTML prostředek pro stránku.

*název mapy*<br/>
Určuje stránku, jejíž adresa URL je *adresa URL*. To odpovídá *mapName* v [makru BEGIN_EMBED_DHTML_EVENT_MAP,](#begin_embed_dhtml_event_map) který mapuje události z této stránky.

### <a name="remarks"></a>Poznámky

Pokud je stránka prostředkem HTML, musí být *adresa URL* řetězcovou reprezentací id prostředku (tj. "123", nikoli 123 nebo ID_HTMLRES1).

Identifikátor stránky *mapName*je libovolný symbol používaný k propojení vložených map událostí DHTML s mapami událostí URL. Je omezen rozsahem mapy událostí DHTML a URL.

### <a name="example"></a>Příklad

Viz příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdhtml.h

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

Označuje konec mapy událostí DHTML.

### <a name="syntax"></a>Syntaxe

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Poznámky

Musí být použit ve spojení s [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdhtml.h

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)
