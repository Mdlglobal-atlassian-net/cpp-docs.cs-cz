---
title: DHTML – mapa událostí | Microsoft Docs
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
ms.openlocfilehash: d8a888cfdf8d83f3628bf4ad80b26db6ac51ad72
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123094"
---
# <a name="dhtml-event-maps"></a>DHTML – mapa událostí
Následující makra lze použít pro zpracování DHTML – události.  
  
## <a name="dhtml-event-map-macros"></a>Makra mapy událostí jazyka DHTML  
 Následující makra lze použít pro zpracování DHTML – události v [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-odvozených třídách.  
  
|||  
|-|-|  
|[BEGIN_DHTML_EVENT_MAP –](#begin_dhtml_event_map)|Označuje začátek DHTML – mapa událostí.|  
|[BEGIN_DHTML_EVENT_MAP_INLINE –](#begin_dhtml_event_map_inline)|Označuje začátek DHTML – mapa událostí.|  
|[DECLARE_DHTML_EVENT_MAP –](#declare_dhtml_event_map)|Deklaruje DHTML – mapa událostí.|  
|[DHTML_EVENT –](#dhtml_event)|Použít ke zpracování události na úrovni dokumentu pro jeden element HTML.|  
|[DHTML_EVENT_AXCONTROL –](#dhtml_event_axcontrol)|Použít ke zpracování pomocí ovládacího prvku ActiveX je aktivována událost.|  
|[DHTML_EVENT_CLASS –](#dhtml_event_class)|Použít ke zpracování události na úrovni dokumentu pro všechny elementy HTML s určitou třídu CSS.|  
|[DHTML_EVENT_ELEMENT –](#dhtml_event_element)|Použít ke zpracování události na úrovni elementu.|  
|[DHTML_EVENT_ONAFTERUPDATE –](#dhtml_event_onafterupdate)|Použitý pro zpracování `onafterupdate` událost z elementu HTML.|  
|[DHTML_EVENT_ONBEFOREUPDATE –](#dhtml_event_onbeforeupdate)|Použitý pro zpracování `onbeforeupdate` událost z elementu HTML.|  
|[DHTML_EVENT_ONBLUR –](#dhtml_event_onblur)|Použitý pro zpracování `onblur` událost z elementu HTML.|  
|[DHTML_EVENT_ONCHANGE –](#dhtml_event_onchange)|Použitý pro zpracování `onchange` událost z elementu HTML.|  
|[DHTML_EVENT_ONCLICK –](#dhtml_event_onclick)|Použitý pro zpracování `onclick` událost z elementu HTML.|  
|[DHTML_EVENT_ONDATAAVAILABLE –](#dhtml_event_ondataavailable)|Použitý pro zpracování `ondataavailable` událost z elementu HTML.|  
|[DHTML_EVENT_ONDATASETCHANGED –](#dhtml_event_ondatasetchanged)|Použitý pro zpracování `ondatasetchanged` událost z elementu HTML.|  
|[DHTML_EVENT_ONDATASETCOMPLETE –](#dhtml_event_ondatasetcomplete)|Použitý pro zpracování `ondatasetcomplete` událost z elementu HTML.|  
|[DHTML_EVENT_ONDBLCLICK –](#dhtml_event_ondblclick)|Použitý pro zpracování `ondblclick` událost z elementu HTML.|  
|[DHTML_EVENT_ONDRAGSTART –](#dhtml_event_ondragstart)|Použitý pro zpracování `ondragstart` událost z elementu HTML.|  
|[DHTML_EVENT_ONERRORUPDATE –](#dhtml_event_onerrorupdate)|Použitý pro zpracování `onerrorupdate` událost z elementu HTML.|  
|[DHTML_EVENT_ONFILTERCHANGE –](#dhtml_event_onfilterchange)|Použitý pro zpracování `onfilterchange` událost z elementu HTML.|  
|[DHTML_EVENT_ONFOCUS –](#dhtml_event_onfocus)|Použitý pro zpracování `onfocus` událost z elementu HTML.|  
|[DHTML_EVENT_ONHELP –](#dhtml_event_onhelp)|Použitý pro zpracování `onhelp` událost z elementu HTML.|  
|[DHTML_EVENT_ONKEYDOWN –](#dhtml_event_onkeydown)|Použitý pro zpracování `onkeydown` událost z elementu HTML.|  
|[DHTML_EVENT_ONKEYPRESS –](#dhtml_event_onkeypress)|Použitý pro zpracování `onkeypress` událost z elementu HTML.|  
|[DHTML_EVENT_ONKEYUP –](#dhtml_event_onkeyup)|Použitý pro zpracování `onkeyup` událost z elementu HTML.|  
|[DHTML_EVENT_ONMOUSEDOWN –](#dhtml_event_onmousedown)|Použitý pro zpracování `onmousedown` událost z elementu HTML.|  
|[DHTML_EVENT_ONMOUSEMOVE –](#dhtml_event_onmousemove)|Použitý pro zpracování `onmousemove` událost z elementu HTML.|  
|[DHTML_EVENT_ONMOUSEOUT –](#dhtml_event_onmouseout)|Použitý pro zpracování `onmouseout` událost z elementu HTML.|  
|[DHTML_EVENT_ONMOUSEOVER –](#dhtml_event_onmouseover)|Použitý pro zpracování `onmouseover` událost z elementu HTML.|  
|[DHTML_EVENT_ONMOUSEUP –](#dhtml_event_onmouseup)|Použitý pro zpracování `onmouseup` událost z elementu HTML.|  
|[DHTML_EVENT_ONRESIZE –](#dhtml_event_onresize)|Použitý pro zpracování `onresize` událost z elementu HTML.|  
|[DHTML_EVENT_ONROWENTER –](#dhtml_event_onrowenter)|Použitý pro zpracování `onrowenter` událost z elementu HTML.|  
|[DHTML_EVENT_ONROWEXIT –](#dhtml_event_onrowexit)|Použitý pro zpracování `onrowexit` událost z elementu HTML.|  
|[DHTML_EVENT_ONSELECTSTART –](#dhtml_event_onselectstart)|Použitý pro zpracování `onselectstart` událost z elementu HTML.|  
|[DHTML_EVENT_TAG –](#dhtml_event_tag)|Použít ke zpracování události na úrovni dokumentu pro všechny elementy s konkrétní značkou HTML.|  
|[END_DHTML_EVENT_MAP –](#end_dhtml_event_map)|Označuje konec DHTML – mapa událostí.|  
|[END_DHTML_EVENT_MAP_INLINE –](#end_dhtml_event_map_inline)|Označuje konec DHTML – mapa událostí. |
  
## <a name="url-event-map-macros"></a>Adresa URL makra mapy událostí  
 Následující makra lze použít pro zpracování DHTML – události v [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-odvozených třídách.  
  
|||  
|-|-|  
|[BEGIN_DHTML_URL_EVENT_MAP –](#begin_dhtml_url_event_map)|Označuje začátek vícestránkové mapa událostí DHTML a adresy URL.|  
|[BEGIN_EMBED_DHTML_EVENT_MAP –](#begin_embed_dhtml_event_map)|Označuje začátek embedded DHTML – mapa událostí.|  
|[BEGIN_URL_ENTRIES –](#begin_url_entries)|Označuje začátek mapu položka událostí adresy URL.|  
|[DECLARE_DHTML_URL_EVENT_MAP –](#declare_dhtml_url_event_map)|Deklaruje vícestránkové mapa událostí DHTML a adresy URL.|  
|[END_DHTML_URL_EVENT_MAP –](#end_dhtml_url_event_map)|Označuje konec vícestránkové mapa událostí DHTML a adresy URL.|  
|[END_EMBED_DHTML_EVENT_MAP –](#end_embed_dhtml_event_map)|Označuje konec embedded DHTML – mapa událostí.|  
|[END_URL_ENTRIES –](#end_url_entries)|Označuje konec mapu položka událostí adresy URL.|  
|[URL_EVENT_ENTRY –](#url_event_entry)|Mapuje prostředku adresy URL nebo HTML na stránce v vícestránkové dialogu.|  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="begin_dhtml_event_map"></a>  BEGIN_DHTML_EVENT_MAP –  
 Označuje začátek DHTML – mapa událostí umístěné do zdrojového souboru pro třídu identifikovaný `className`.  
  
```   
BEGIN_DHTML_EVENT_MAP(className)   
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 Název třídy obsahující DHTML – mapa událostí. Tato třída by měl být odvozen přímo nebo nepřímo z [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) a zahrnout [declare_dhtml_event_map –](#declare_dhtml_event_map) makro v rámci dané definice třídy.  
  
### <a name="remarks"></a>Poznámky  
 Přidání DHTML – mapa událostí do vaší třídy poskytují informace, které `CDHtmlDialog` který slouží k události trasy aktivováno elementů HTML nebo ovládací prvky ActiveX na webové stránce k funkcím obslužných rutin v třídě.  
  
 Umístěte begin_dhtml_event_map – makro třídy (sada) soubor implementace následuje dhtml_event – makra pro události, které třídy je zpracování (například dhtml_event_onmouseover – pro myš nad události). Použití [end_dhtml_event_map –](#end_dhtml_event_map) makro konec mapa událostí. Tyto makra implementovat následující funkce:  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="begin_dhtml_event_map_inline"></a>  BEGIN_DHTML_EVENT_MAP_INLINE –  
 Označuje začátek DHTML – mapa událostí v definici třídy *className*.  
  
```   
BEGIN_DHTML_EVENT_MAP_INLINE(className)   
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 Název třídy obsahující DHTML – mapa událostí. Tato třída by měl být odvozen přímo nebo nepřímo z [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) a zahrnout [declare_dhtml_event_map –](#declare_dhtml_event_map) makro v rámci dané definice třídy.  
  
### <a name="remarks"></a>Poznámky  
 Přidání DHTML – mapa událostí do vaší třídy poskytují informace, které `CDHtmlDialog` který slouží k události trasy aktivováno elementů HTML nebo ovládací prvky ActiveX na webové stránce k funkcím obslužných rutin v třídě.  
  
 Umístěte begin_dhtml_event_map – makro třídy (.h) soubor definice následuje dhtml_event – makra pro události, které třídy je zpracování (například dhtml_event_onmouseover – pro myš nad události). Použití [end_dhtml_event_map_inline –](#end_dhtml_event_map_inline) makro konec mapa událostí. Tyto makra implementovat následující funkce:  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  

  
##  <a name="declare_dhtml_event_map"></a>  DECLARE_DHTML_EVENT_MAP –  
 Deklaruje DHTML – mapa událostí v definici třídy.  
  
```   
DECLARE_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se má použít v definici [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-odvozených třídách.  
  
 Použití [begin_dhtml_event_map –](#begin_dhtml_event_map) nebo [begin_dhtml_event_map_inline –](#begin_dhtml_event_map_inline) implementovat mapy.  
  
 [Declare_dhtml_event_map –](#declare_dhtml_event_map) deklaruje následující funkce:  
  
 `virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event"></a>  DHTML_EVENT –  
 Zpracovává (na úrovni dokumentu) událost identifikovaný *dispid* pochází elementu HTML identifikovaný *elemName*.  
  
```   
DHTML_EVENT(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *dispID*  
 DISPID událostí ke zpracování.  
  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události, nebo hodnota NULL pro zpracování události dokumentu.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_axcontrol"></a>  DHTML_EVENT_AXCONTROL –  
 Zpracovává událost identifikovaný *dispid* aktivováno ovládací prvek ActiveX identifikovaný *název ovládacího prvku*.  
  
```   
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)  
```  
  
### <a name="parameters"></a>Parametry  
 *dispID*  
 Odesílání ID události ke zpracování.  
  
 *název ovládacího prvku*  
 LPCWSTR, která uchovává ID HTML prvku aktivuje událost.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_class"></a>  DHTML_EVENT_CLASS –  
 Zpracovává (na úrovni dokumentu) událost identifikovaný *dispid* původce libovolný prvek HTML pomocí třídy CSS identifikovaný *elemName*.  
  
```   
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *dispID*  
 Odesílání ID události ke zpracování.  
  
 *elemName*  
 LPCWSTR, která uchovává třídu CSS prvků HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_element"></a>  DHTML_EVENT_ELEMENT –  
 Zpracovává (na element identifikovaný *elemName*) událost identifikovaný *dispid*.  
  
```   
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn) 
```  
  
### <a name="parameters"></a>Parametry  
 *dispID*  
 Odesílání ID události ke zpracování.  
  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
 Pokud toto makro se používá ke zpracování nonbubbling událostí, bude zdroj události element identifikovaný *elemName*.  
  
 Pokud toto makro se používá ke zpracování probublávání událostí, element identifikovaný *elemName* nemusí být zdroj události (zdroj může být libovolný prvek obsažený v *elemName*).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onafterupdate"></a>  DHTML_EVENT_ONAFTERUPDATE –  
 Zpracovává (na úrovni dokumentu) `onafterupdate` událost pochází elementu HTML identifikovaný *elemName*.  
  
```   
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onbeforeupdate"></a>  DHTML_EVENT_ONBEFOREUPDATE –  
 Zpracovává (na úrovni dokumentu) `onbeforeupdate` událost pochází elementu HTML identifikovaný *elemName*.  
  
```   
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onblur"></a>  DHTML_EVENT_ONBLUR –  
 Zpracovává (na úrovni element) `onblur` událostí. Toto je nonbubbling událost.  
  
```   
DHTML_EVENT_ONBLUR(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onchange"></a>  DHTML_EVENT_ONCHANGE –  
 Zpracovává (na úrovni element) `onchange` událostí. Toto je nonbubbling událost.  
  
```   
DHTML_EVENT_ONCHANGE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onclick"></a>  DHTML_EVENT_ONCLICK –  
 Zpracovává (na úrovni dokumentu) `onclick` událost pochází elementu HTML identifikovaný *elemName*.  
  
```   
DHTML_EVENT_ONCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_ondataavailable"></a>  DHTML_EVENT_ONDATAAVAILABLE –  
 Zpracovává (na úrovni dokumentu) `ondataavailable` událost pochází elementu HTML identifikovaný *elemName*.  
  
```   
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_ondatasetchanged"></a>  DHTML_EVENT_ONDATASETCHANGED –  
 Zpracovává (na úrovni dokumentu) `ondatasetchanged` událost pochází elementu HTML identifikovaný *elemName*.  
  
```   
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_ondatasetcomplete"></a>  DHTML_EVENT_ONDATASETCOMPLETE –  
 Zpracovává (na úrovni dokumentu) `ondatasetcomplete` událost pochází elementu HTML identifikovaný `elemName`.  
  
```   
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn) 
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_ondblclick"></a>  DHTML_EVENT_ONDBLCLICK –  
 Zpracovává (na úrovni dokumentu) `ondblclick` událost pochází elementu HTML identifikovaný *elemName*.  
  
```   
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_ondragstart"></a>  DHTML_EVENT_ONDRAGSTART –  
 Zpracovává (na úrovni dokumentu) `ondragstart` událost pochází elementu HTML identifikovaný *elemName*.  
  
```   
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onerrorupdate"></a>  DHTML_EVENT_ONERRORUPDATE –  
 Zpracovává (na úrovni dokumentu) `onerrorupdate` událost pochází elementu HTML identifikovaný *elemName*.  
  
```   
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onfilterchange"></a>  DHTML_EVENT_ONFILTERCHANGE –  
 Zpracovává (na úrovni dokumentu) `onfilterchange` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onfocus"></a>  DHTML_EVENT_ONFOCUS –  
 Zpracovává (na úrovni element) `onfocus` událostí. Toto je nonbubbling událost.  
  
```  
 
DHTML_EVENT_ONFOCUS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onhelp"></a>  DHTML_EVENT_ONHELP –  
 Zpracovává (na úrovni dokumentu) `onhelp` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONHELP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onkeydown"></a>  DHTML_EVENT_ONKEYDOWN –  
 Zpracovává (na úrovni dokumentu) `onkeydown` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onkeypress"></a>  DHTML_EVENT_ONKEYPRESS –  
 Zpracovává (na úrovni dokumentu) `onkeypress` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onkeyup"></a>  DHTML_EVENT_ONKEYUP –  
 Zpracovává (na úrovni dokumentu) `onkeyup` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONKEYUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onmousedown"></a>  DHTML_EVENT_ONMOUSEDOWN –  
 Zpracovává (na úrovni dokumentu) `onmousedown` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onmousemove"></a>  DHTML_EVENT_ONMOUSEMOVE –  
 Zpracovává (na úrovni dokumentu) `onmousemove` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onmouseout"></a>  DHTML_EVENT_ONMOUSEOUT –  
 Zpracovává (na úrovni dokumentu) `onmouseout` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onmouseover"></a>  DHTML_EVENT_ONMOUSEOVER –  
 Zpracovává (na úrovni dokumentu) `onmouseover` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onmouseup"></a>  DHTML_EVENT_ONMOUSEUP –  
 Zpracovává (na úrovni dokumentu) `onmouseup` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onresize"></a>  DHTML_EVENT_ONRESIZE –  
 Zpracovává (na úrovni element) `onresize` událostí. Toto je nonbubbling událost.  
  
```  
 
DHTML_EVENT_ONRESIZE(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onrowenter"></a>  DHTML_EVENT_ONROWENTER –  
 Zpracovává (na úrovni dokumentu) `onrowenter` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONROWENTER(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onrowexit"></a>  DHTML_EVENT_ONROWEXIT –  
 Zpracovává (na úrovni dokumentu) `onrowexit` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_onselectstart"></a>  DHTML_EVENT_ONSELECTSTART –  
 Zpracovává (na úrovni dokumentu) `onselectstart` událost pochází elementu HTML identifikovaný *elemName*.  
  
```  
 
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *elemName*  
 LPCWSTR, která uchovává ID elementu HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="dhtml_event_tag"></a>  DHTML_EVENT_TAG –  
 Zpracovává (na úrovni dokumentu) událost identifikovaný `dispid` původce libovolný prvek HTML se identifikovanou pomocí značky HTML *elemName*.  
  
```   
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)   
```  
  
### <a name="parameters"></a>Parametry  
 *dispID*  
 Odesílání ID události ke zpracování.  
  
 *elemName*  
 Značka HTML prvků HTML sourcing události.  
  
 *memberFxn*  
 Obslužné rutiny události.  
  
### <a name="remarks"></a>Poznámky  
 Použití tohoto makra přidat položku s [DHTML – mapa událostí](#begin_dhtml_event_map_inline) v třídě.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="end_dhtml_event_map"></a>  END_DHTML_EVENT_MAP –  
 Označuje konec DHTML – mapa událostí.  
  
```   
END_DHTML_EVENT_MAP()   
```  
  
### <a name="remarks"></a>Poznámky  
 Musí použít ve spojení s [begin_dhtml_event_map –](#begin_dhtml_event_map).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="begin_dhtml_url_event_map"></a>  BEGIN_DHTML_URL_EVENT_MAP –  
 Spustí definici mapy událostí DHTML a adresy URL v vícestránkové dialogu.  
  
```  
BEGIN_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>Poznámky  
 V souboru implementace PUT begin_dhtml_url_event_map – vaše [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-odvozené třídy. Postupujte podle její [vložených DHTML – mapa událostí](#begin_embed_dhtml_event_map) a [položek URL](#begin_url_entries)a pak zavřete ho s [end_dhtml_url_event_map –](#end_dhtml_url_event_map). Zahrnout [declare_dhtml_url_event_map –](#declare_dhtml_url_event_map) makra v definici třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="begin_embed_dhtml_event_map"></a>  BEGIN_EMBED_DHTML_EVENT_MAP –  
 Spustí definici embedded DHTML – mapa událostí v vícestránkové dialogu.  
  
```  
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 Název třídy obsahující mapa událostí. Tato třída by měl být odvozen přímo nebo nepřímo z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Vložené DHTML – mapa událostí musí být uvnitř [DHTML a adresy URL mapa událostí](#begin_dhtml_url_event_map)).  
  
 *mapName*  
 Určuje, že je stránka, jehož událost mapování těchto. To odpovídá *mapName* v [url_event_entry –](#url_event_entry) makro ve skutečnosti definice prostředku adresy URL nebo HTML.  
  
### <a name="remarks"></a>Poznámky  
 Protože vícestránkové DHTML dialogové okno se skládá z několika stránky HTML, z nichž každá může být spojeno DHTML – události, vložená událost maps se používají pro mapování události na obslužné rutiny na základě stránky.  
  
 Mapy událostí vložené v rámci mapy událostí DHTML a adresy URL obsahovat begin_embed_dhtml_event_map – makro následuje [dhtml_event –](#dhtml_event) makra a [end_embed_dhtml_event_map –](#end_embed_dhtml_event_map) makro.  
  
 Každý mapa embedded událostí vyžaduje odpovídající [vstupní adresa URL událostí](#url_event_entry) mapovat *mapName* (zadané v begin_embed_dhtml_event_map –) k prostředku adresy URL nebo HTML.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [begin_dhtml_url_event_map –](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="begin_url_entries"></a>  BEGIN_URL_ENTRIES –  
 Spustí definici mapy událostí vstupní adresy URL v vícestránkové dialogové okno.  
  
```  
BEGIN_URL_ENTRIES(className)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 Název třídy obsahující položku mapy událostí adresy URL. Tato třída by měl být odvozen přímo nebo nepřímo z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa položka událostí adresa URL musí být uvnitř [DHTML a adresy URL mapa událostí](#begin_dhtml_url_event_map)).  
  
### <a name="remarks"></a>Poznámky  
 Protože vícestránkové DHTML dialogové okno se skládá z několika stránky HTML, položek událostí URL se používají pro mapování adresy URL nebo HTML prostředky pro odpovídající [vložených DHTML – mapa událostí](#begin_embed_dhtml_event_map). Url_event_entry – makra mezi begin_url_entries – PUT a [end_url_entries –](#end_url_entries) makra.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [begin_dhtml_url_event_map –](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="declare_dhtml_url_event_map"></a>  DECLARE_DHTML_URL_EVENT_MAP –  
 Deklaruje DHTML a adresy URL mapa událostí v definici třídy.  
  
```  
DECLARE_DHTML_URL_EVENT_MAP()  
 
```  
  
### <a name="remarks"></a>Poznámky  
 Toto makro se má použít v definici [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-odvozených třídách.  
  
 Mapy událostí DHTML a adresa URL obsahuje [vložených DHTML – mapa událostí](#begin_embed_dhtml_event_map) a [položek událostí URL](#begin_url_entries) mapovat DHTML – události obslužné rutiny na základě stránky. Použití [begin_dhtml_url_event_map –](#begin_dhtml_url_event_map) implementovat mapy.  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="end_dhtml_url_event_map"></a>  END_DHTML_URL_EVENT_MAP –  
 Označuje konec mapy událostí DHTML a adresy URL.  
  
```  
END_DHTML_URL_EVENT_MAP(className)  
 
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 Název třídy obsahující mapa událostí. Tato třída by měl být odvozen přímo nebo nepřímo z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mělo by to odpovídat *className* do odpovídajícího [begin_dhtml_url_event_map –](#begin_dhtml_url_event_map) makro.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [begin_dhtml_url_event_map –](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="end_embed_dhtml_event_map"></a>  END_EMBED_DHTML_EVENT_MAP –  
 Označuje konec embedded DHTML – mapa událostí.  
  
```  
END_EMBED_DHTML_EVENT_MAP()  
 
```  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [begin_dhtml_url_event_map –](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="end_url_entries"></a>  END_URL_ENTRIES –  
 Označuje konec mapu položka událostí adresy URL.  
  
```  
END_URL_ENTRIES()  
 
```  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [begin_dhtml_url_event_map –](#begin_dhtml_url_event_map).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  
  
##  <a name="url_event_entry"></a>  URL_EVENT_ENTRY –  
 Mapuje prostředku adresy URL nebo HTML na stránce v vícestránkové dialogu.  
  
```  
URL_EVENT_ENTRY(className, url,  mapName)   
```  
  
### <a name="parameters"></a>Parametry  
 *Název třídy*  
 Název třídy obsahující položku mapy událostí adresy URL. Tato třída by měl být odvozen přímo nebo nepřímo z [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md). Mapa položka událostí adresa URL musí být uvnitř [DHTML a adresy URL mapa událostí](#begin_dhtml_url_event_map)).  
  
 *url*  
 Adresa URL nebo HTML prostředek pro stránku.  
  
 *mapName*  
 Určuje stránku, jejichž adresa URL je *url*. To odpovídá *mapName* v [begin_embed_dhtml_event_map –](#begin_embed_dhtml_event_map) makro, která mapuje události z této stránky.  
  
### <a name="remarks"></a>Poznámky  
 Pokud stránka je prostředek HTML *url* musí být řetězcová reprezentace číslo ID prostředku (tedy "123", není 123 nebo ID_HTMLRES1).  
  
 Identifikátor stránky *mapName*, je libovolné symbolu používanou k propojení vložených DHTML – mapa událostí do mapy položka událostí adresu URL. Je omezená obor mapa událostí DHTML a adresy URL.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad v [begin_dhtml_url_event_map –](#begin_dhtml_url_event_map).  

  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdhtml.h  

##  <a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE –
Označuje konec DHTML – mapa událostí.  
   
### <a name="syntax"></a>Syntaxe    
```
END_DHTML_EVENT_MAP_INLINE( )    
```  
   
### <a name="remarks"></a>Poznámky  
 Musí použít ve spojení s [begin_dhtml_event_map_inline –](#begin_dhtml_event_map_inline).  
   
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdhtml.h  
   
### <a name="see-also"></a>Viz také  
 [Makra a globální prvky](mfc-macros-and-globals.md)   
