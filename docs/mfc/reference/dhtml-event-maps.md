---
title: DHTML – mapa událostí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.macros.shared
dev_langs:
- C++
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5942a41272671a391cb600ef959d2c69b0bab3e3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419032"
---
# <a name="dhtml-event-maps"></a>DHTML – mapa událostí

Následující makra lze použít ke zpracování událostí v jazyce DHTML.

## <a name="dhtml-event-map-macros"></a>Makra mapy událostí DHTML

Následující makra lze použít ke zpracování událostí v jazyce DHTML v [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-odvozené třídy.

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Označuje začátek DHTML – mapa událostí.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Označuje začátek DHTML – mapa událostí.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Deklaruje DHTML – mapa událostí.|
|[DHTML_EVENT](#dhtml_event)|Umožňuje zpracovat události na úrovni dokumentu pro jeden element HTML.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Umožňuje zpracovat události vyvolané ovládacího prvku ActiveX.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Umožňuje zpracovat události na úrovni dokumentu pro všechny prvky jazyka HTML s konkrétní třídu šablony stylů CSS.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Umožňuje zpracovat události na úrovni prvku.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Používá ke zpracování `onafterupdate` události z elementu HTML.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Používá ke zpracování `onbeforeupdate` události z elementu HTML.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Používá ke zpracování `onblur` události z elementu HTML.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Používá ke zpracování `onchange` události z elementu HTML.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Používá ke zpracování `onclick` události z elementu HTML.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Používá ke zpracování `ondataavailable` události z elementu HTML.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Používá ke zpracování `ondatasetchanged` události z elementu HTML.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Používá ke zpracování `ondatasetcomplete` události z elementu HTML.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Používá ke zpracování `ondblclick` události z elementu HTML.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Používá ke zpracování `ondragstart` události z elementu HTML.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Používá ke zpracování `onerrorupdate` události z elementu HTML.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Používá ke zpracování `onfilterchange` události z elementu HTML.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Používá ke zpracování `onfocus` události z elementu HTML.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Používá ke zpracování `onhelp` události z elementu HTML.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Používá ke zpracování `onkeydown` události z elementu HTML.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Používá ke zpracování `onkeypress` události z elementu HTML.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Používá ke zpracování `onkeyup` události z elementu HTML.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Používá ke zpracování `onmousedown` události z elementu HTML.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Používá ke zpracování `onmousemove` události z elementu HTML.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Používá ke zpracování `onmouseout` události z elementu HTML.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Používá ke zpracování `onmouseover` události z elementu HTML.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Používá ke zpracování `onmouseup` události z elementu HTML.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Používá ke zpracování `onresize` události z elementu HTML.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Používá ke zpracování `onrowenter` události z elementu HTML.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Používá ke zpracování `onrowexit` události z elementu HTML.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Používá ke zpracování `onselectstart` události z elementu HTML.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Umožňuje zpracovat události na úrovni dokumentu pro všechny elementy s konkrétní značkou jazyka HTML.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Označuje konec DHTML – mapa událostí.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Označuje konec DHTML – mapa událostí. |

## <a name="url-event-map-macros"></a>Adresa URL makra mapy událostí

Následující makra lze použít ke zpracování událostí v jazyce DHTML v [cmultipagedhtmldialog –](../../mfc/reference/cmultipagedhtmldialog-class.md)-odvozené třídy.

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Označuje začátek vícestránkové mapa událostí DHTML a adresu URL.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Označuje začátek vložený DHTML – mapa událostí.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Označuje začátek mapování adresy URL události vstupu.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Deklaruje vícestránkové mapa událostí DHTML a adresu URL.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Označuje konec vícestránkové mapa událostí DHTML a adresu URL.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Označuje konec vložený DHTML – mapa událostí.|
|[END_URL_ENTRIES](#end_url_entries)|Označuje konec mapování adresy URL události vstupu.|
|[URL_EVENT_ENTRY](#url_event_entry)|Mapuje adresu URL nebo HTML prostředků na stránku vícestránkové dialogové okno.|

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="begin_dhtml_event_map"></a>  BEGIN_DHTML_EVENT_MAP

Označuje začátek DHTML – mapa událostí při umístění ve zdrojovém souboru pro třídu identifikovaný `className`.

```
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Parametry

*Název třídy*<br/>
Název třídy obsahující DHTML – mapa událostí. Tato třída musí být odvozený přímo nebo nepřímo z: [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) a zahrnout [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) – makro v rámci dané definice třídy.

### <a name="remarks"></a>Poznámky

DHTML – mapa událostí přidat do vaší třídy poskytnout informace o `CDHtmlDialog` , který je možné směrování události vyvolané elementy HTML nebo ovládací prvky ActiveX na webové stránce k funkcím obslužných rutin ve své třídě.

Umístíte BEGIN_DHTML_EVENT_MAP – makro třídy implementace (.cpp) souboru za nímž následuje DHTML_EVENT makra pro události, které je třída pro zpracování (například DHTML_EVENT_ONMOUSEOVER mouseover událostí). Použití [END_DHTML_EVENT_MAP](#end_dhtml_event_map) – makro konec mapa událostí. Tato makra implementovat následující funkce:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="begin_dhtml_event_map_inline"></a>  BEGIN_DHTML_EVENT_MAP_INLINE

Označuje začátek DHTML – mapa událostí v rámci definice třídy pro *className*.

```
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Parametry

*Název třídy*<br/>
Název třídy obsahující DHTML – mapa událostí. Tato třída musí být odvozený přímo nebo nepřímo z: [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) a zahrnout [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) – makro v rámci dané definice třídy.

### <a name="remarks"></a>Poznámky

DHTML – mapa událostí přidat do vaší třídy poskytnout informace o `CDHtmlDialog` , který je možné směrování události vyvolané elementy HTML nebo ovládací prvky ActiveX na webové stránce k funkcím obslužných rutin ve své třídě.

Umístíte BEGIN_DHTML_EVENT_MAP – makro třídy definice (.h) souboru za nímž následuje DHTML_EVENT makra pro události, které je třída pro zpracování (například DHTML_EVENT_ONMOUSEOVER mouseover událostí). Použití [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) – makro konec mapa událostí. Tato makra implementovat následující funkce:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h


##  <a name="declare_dhtml_event_map"></a>  DECLARE_DHTML_EVENT_MAP

Deklaruje DHTML – mapa událostí v definici třídy.

```
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Poznámky

Toto makro se má použít v definici [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-odvozené třídy.

Použití [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) nebo [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) k implementaci na mapě.

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) deklaruje následující funkce:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event"></a>  DHTML_EVENT

Zpracovává (na úrovni dokumentu) událost identifikovaný *dispid* původce prvku HTML, který je identifikován *elemName*.

```
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*identifikátor DISPID*<br/>
Hodnota DISPID událost, která má být zpracována.

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML sourcing události, nebo hodnota NULL pro zpracování událostí v dokumentu.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_axcontrol"></a>  DHTML_EVENT_AXCONTROL

Zpracovává událost identifikovaný *dispid* vyvolané ovládací prvek ActiveX, který je identifikován *název ovládacího prvku*.

```
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*identifikátor DISPID*<br/>
ID odbavení událostí ke zpracování.

*název ovládacího prvku*<br/>
LPCWSTR, která uchovává ID HTML vyvoláním události ovládacího prvku.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_class"></a>  DHTML_EVENT_CLASS

Zpracovává (na úrovni dokumentu) událost identifikovaný *dispid* původce libovolný prvek HTML pomocí třídy šablony stylů CSS identifikovaný *elemName*.

```
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*identifikátor DISPID*<br/>
ID odbavení událostí ke zpracování.

*elemName*<br/>
LPCWSTR obsahující třídu šablony stylů CSS prvků HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_element"></a>  DHTML_EVENT_ELEMENT

Zpracovává (na prvek identifikovaný *elemName*) událost identifikovaný *dispid*.

```
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*identifikátor DISPID*<br/>
ID odbavení událostí ke zpracování.

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

Pokud toto makro se používá ke zpracování nonbubbling události, zdroj události bude prvek identifikovaný *elemName*.

Pokud toto makro se používá ke zpracování šíření událostí, element identifikovaný *elemName* nemusí být zdroj události (zdroj může být libovolný prvek obsažený objektem *elemName*).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onafterupdate"></a>  DHTML_EVENT_ONAFTERUPDATE

Zpracovává (na úrovni dokumentu) `onafterupdate` událost pochází podle prvku HTML, který je identifikován *elemName*.

```
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onbeforeupdate"></a>  DHTML_EVENT_ONBEFOREUPDATE

Zpracovává (na úrovni dokumentu) `onbeforeupdate` událost pochází podle prvku HTML, který je identifikován *elemName*.

```
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onblur"></a>  DHTML_EVENT_ONBLUR

Zpracovává (na úrovni prvku) `onblur` událostí. Toto je nonbubbling událost.

```
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onchange"></a>  DHTML_EVENT_ONCHANGE

Zpracovává (na úrovni prvku) `onchange` událostí. Toto je nonbubbling událost.

```
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onclick"></a>  DHTML_EVENT_ONCLICK

Zpracovává (na úrovni dokumentu) `onclick` událost pochází podle prvku HTML, který je identifikován *elemName*.

```
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_ondataavailable"></a>  DHTML_EVENT_ONDATAAVAILABLE

Zpracovává (na úrovni dokumentu) `ondataavailable` událost pochází podle prvku HTML, který je identifikován *elemName*.

```
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_ondatasetchanged"></a>  DHTML_EVENT_ONDATASETCHANGED

Zpracovává (na úrovni dokumentu) `ondatasetchanged` událost pochází podle prvku HTML, který je identifikován *elemName*.

```
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_ondatasetcomplete"></a>  DHTML_EVENT_ONDATASETCOMPLETE

Zpracovává (na úrovni dokumentu) `ondatasetcomplete` událost pochází podle prvku HTML, který je identifikován `elemName`.

```
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_ondblclick"></a>  DHTML_EVENT_ONDBLCLICK

Zpracovává (na úrovni dokumentu) `ondblclick` událost pochází podle prvku HTML, který je identifikován *elemName*.

```
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_ondragstart"></a>  DHTML_EVENT_ONDRAGSTART

Zpracovává (na úrovni dokumentu) `ondragstart` událost pochází podle prvku HTML, který je identifikován *elemName*.

```
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onerrorupdate"></a>  DHTML_EVENT_ONERRORUPDATE

Zpracovává (na úrovni dokumentu) `onerrorupdate` událost pochází podle prvku HTML, který je identifikován *elemName*.

```
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onfilterchange"></a>  DHTML_EVENT_ONFILTERCHANGE

Zpracovává (na úrovni dokumentu) `onfilterchange` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onfocus"></a>  DHTML_EVENT_ONFOCUS

Zpracovává (na úrovni prvku) `onfocus` událostí. Toto je nonbubbling událost.

```

DHTML_EVENT_ONFOCUS(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onhelp"></a>  DHTML_EVENT_ONHELP

Zpracovává (na úrovni dokumentu) `onhelp` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONHELP(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onkeydown"></a>  DHTML_EVENT_ONKEYDOWN

Zpracovává (na úrovni dokumentu) `onkeydown` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onkeypress"></a>  DHTML_EVENT_ONKEYPRESS

Zpracovává (na úrovni dokumentu) `onkeypress` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onkeyup"></a>  DHTML_EVENT_ONKEYUP

Zpracovává (na úrovni dokumentu) `onkeyup` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONKEYUP(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onmousedown"></a>  DHTML_EVENT_ONMOUSEDOWN

Zpracovává (na úrovni dokumentu) `onmousedown` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onmousemove"></a>  DHTML_EVENT_ONMOUSEMOVE

Zpracovává (na úrovni dokumentu) `onmousemove` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onmouseout"></a>  DHTML_EVENT_ONMOUSEOUT

Zpracovává (na úrovni dokumentu) `onmouseout` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onmouseover"></a>  DHTML_EVENT_ONMOUSEOVER

Zpracovává (na úrovni dokumentu) `onmouseover` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onmouseup"></a>  DHTML_EVENT_ONMOUSEUP

Zpracovává (na úrovni dokumentu) `onmouseup` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onresize"></a>  DHTML_EVENT_ONRESIZE

Zpracovává (na úrovni prvku) `onresize` událostí. Toto je nonbubbling událost.

```

DHTML_EVENT_ONRESIZE(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onrowenter"></a>  DHTML_EVENT_ONROWENTER

Zpracovává (na úrovni dokumentu) `onrowenter` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONROWENTER(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onrowexit"></a>  DHTML_EVENT_ONROWEXIT

Zpracovává (na úrovni dokumentu) `onrowexit` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONROWEXIT(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_onselectstart"></a>  DHTML_EVENT_ONSELECTSTART

Zpracovává (na úrovni dokumentu) `onselectstart` událost pochází podle prvku HTML, který je identifikován *elemName*.

```

DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)

```

### <a name="parameters"></a>Parametry

*elemName*<br/>
LPCWSTR, která uchovává ID elementu HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="dhtml_event_tag"></a>  DHTML_EVENT_TAG

Zpracovává (na úrovni dokumentu) událost identifikovaný `dispid` pochází ze značky HTML, který je identifikován podle libovolný prvek HTML *elemName*.

```
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*identifikátor DISPID*<br/>
ID odbavení událostí ke zpracování.

*elemName*<br/>
Značka HTML prvků HTML event sourcing.

*memberFxn*<br/>
Obslužné rutiny události.

### <a name="remarks"></a>Poznámky

Použijte toto makro přidat položku [DHTML – mapa událostí](#begin_dhtml_event_map_inline) ve své třídě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="end_dhtml_event_map"></a>  END_DHTML_EVENT_MAP

Označuje konec DHTML – mapa událostí.

```
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Poznámky

Je potřeba použít ve spojení s [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="begin_dhtml_url_event_map"></a>  BEGIN_DHTML_URL_EVENT_MAP

Spustí vícestránkové dialogové okno Definice DHTML a adresu URL mapa událostí.

```
BEGIN_DHTML_URL_EVENT_MAP()

```

### <a name="remarks"></a>Poznámky

Vložit BEGIN_DHTML_URL_EVENT_MAP v souboru implementace vaší [cmultipagedhtmldialog –](../../mfc/reference/cmultipagedhtmldialog-class.md)-odvozené třídy. Použijte ho s [vložené DHTML – mapa událostí](#begin_embed_dhtml_event_map) a [adresa URL položky](#begin_url_entries)a pak zavřete ho s [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Zahrnout [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) – makro v rámci definice třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="begin_embed_dhtml_event_map"></a>  BEGIN_EMBED_DHTML_EVENT_MAP

Definice vložené DHTML – mapa událostí se spustí v vícestránkové dialogové okno.

```
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)

```

### <a name="parameters"></a>Parametry

*Název třídy*<br/>
Název třídy obsahující mapa událostí. Tato třída musí být odvozený přímo nebo nepřímo z: [cmultipagedhtmldialog –](../../mfc/reference/cmultipagedhtmldialog-class.md). Vložený DHTML – mapa událostí musí být uvnitř [DHTML a adresu URL mapa událostí](#begin_dhtml_url_event_map)).

*mapName*<br/>
Určuje, že je na stránce namapujte tento parametr jehož událost. To odpovídá *mapName* v [URL_EVENT_ENTRY](#url_event_entry) – makro skutečně definuje prostředek URL nebo HTML.

### <a name="remarks"></a>Poznámky

Protože vícestránkové dialogové okno Dynamic HTML se skládá z více stránek HTML, z nichž každá může vyvolat události DHTML, mapy vložený událostí slouží k mapování události do obslužné rutiny na základě stránky.

Mapy událostí vložený v mapě událostí DHTML a adresa URL obsahovat BEGIN_EMBED_DHTML_EVENT_MAP – makro, za nímž následuje [DHTML_EVENT](#dhtml_event) makra a [END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map) – makro.

Mapa každý vložený událostí vyžaduje odpovídající [adresa URL položky události](#url_event_entry) mapovat *mapName* (zadané v BEGIN_EMBED_DHTML_EVENT_MAP) na prostředek adresy URL nebo HTML.

### <a name="example"></a>Příklad

Podívejte se na příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="begin_url_entries"></a>  BEGIN_URL_ENTRIES

Definice objektu map vstupní události adresy URL se spustí v vícestránkové dialogové okno.

```
BEGIN_URL_ENTRIES(className)

```

### <a name="parameters"></a>Parametry

*Název třídy*<br/>
Název třídy obsahující URL map vstupní události. Tato třída musí být odvozený přímo nebo nepřímo z: [cmultipagedhtmldialog –](../../mfc/reference/cmultipagedhtmldialog-class.md). Adresa URL události položku mapování musí být uvnitř [DHTML a adresu URL mapa událostí](#begin_dhtml_url_event_map)).

### <a name="remarks"></a>Poznámky

Protože vícestránkové dialogové okno Dynamic HTML se skládá z více stránek HTML, URL vstupů události se používají k mapování adresy URL nebo HTML prostředky odpovídající [vložené DHTML – mapa událostí](#begin_embed_dhtml_event_map). Vložit URL_EVENT_ENTRY makra mezi BEGIN_URL_ENTRIES a [END_URL_ENTRIES](#end_url_entries) makra.

### <a name="example"></a>Příklad

Podívejte se na příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="declare_dhtml_url_event_map"></a>  DECLARE_DHTML_URL_EVENT_MAP

Deklaruje DHTML a adresu URL mapa událostí v definici třídy.

```
DECLARE_DHTML_URL_EVENT_MAP()

```

### <a name="remarks"></a>Poznámky

Toto makro se má použít v definici [cmultipagedhtmldialog –](../../mfc/reference/cmultipagedhtmldialog-class.md)-odvozené třídy.

DHTML a adresu URL mapa událostí obsahuje [vložené DHTML – mapa událostí](#begin_embed_dhtml_event_map) a [položek událostí URL](#begin_url_entries) mapování obslužné rutiny na základě na stránku DHTML – události. Použití [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) k implementaci na mapě.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="end_dhtml_url_event_map"></a>  END_DHTML_URL_EVENT_MAP

Označuje konec DHTML a adresu URL mapa událostí.

```
END_DHTML_URL_EVENT_MAP(className)

```

### <a name="parameters"></a>Parametry

*Název třídy*<br/>
Název třídy obsahující mapa událostí. Tato třída musí být odvozený přímo nebo nepřímo z: [cmultipagedhtmldialog –](../../mfc/reference/cmultipagedhtmldialog-class.md). Ten by měl odpovídat *className* z odpovídajících [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) – makro.

### <a name="example"></a>Příklad

Podívejte se na příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="end_embed_dhtml_event_map"></a>  END_EMBED_DHTML_EVENT_MAP

Označuje konec vložený DHTML – mapa událostí.

```
END_EMBED_DHTML_EVENT_MAP()

```

### <a name="example"></a>Příklad

Podívejte se na příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="end_url_entries"></a>  END_URL_ENTRIES

Označuje konec mapování adresy URL události vstupu.

```
END_URL_ENTRIES()

```

### <a name="example"></a>Příklad

Podívejte se na příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="url_event_entry"></a>  URL_EVENT_ENTRY

Mapuje adresu URL nebo HTML prostředků na stránku vícestránkové dialogové okno.

```
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Parametry

*Název třídy*<br/>
Název třídy obsahující URL map vstupní události. Tato třída musí být odvozený přímo nebo nepřímo z: [cmultipagedhtmldialog –](../../mfc/reference/cmultipagedhtmldialog-class.md). Adresa URL události položku mapování musí být uvnitř [DHTML a adresu URL mapa událostí](#begin_dhtml_url_event_map)).

*url*<br/>
Adresa URL nebo HTML prostředek pro stránku.

*mapName*<br/>
Určuje stránku, jehož adresa URL je *url*. To odpovídá *mapName* v [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) makro, které mapuje události z této stránky.

### <a name="remarks"></a>Poznámky

Pokud je prostředek ve formátu HTML stránka *url* musí být řetězcové vyjádření čísla ID prostředku (tedy "123", ne 123 nebo ID_HTMLRES1).

Identifikátor stránky *mapName*, je libovolný symbol slouží k propojení vložené DHTML – mapa událostí do mapy záznam událostí adresy URL. Je omezený rozsah, který mapa událostí DHTML a adresu URL.

### <a name="example"></a>Příklad

Podívejte se na příklad v [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).


### <a name="requirements"></a>Požadavky

  **Hlavička** afxdhtml.h

##  <a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

Označuje konec DHTML – mapa událostí.

### <a name="syntax"></a>Syntaxe

```
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Poznámky

Je potřeba použít ve spojení s [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdhtml.h

### <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)
