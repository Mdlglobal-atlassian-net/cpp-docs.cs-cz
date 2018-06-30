---
title: Mapy událostí | Microsoft Docs
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4522b9ea2f336f5ac88f5444edc0c7df16b5bc6
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122386"
---
# <a name="event-maps"></a>Mapy událostí

Vždy, když ovládacího prvku, které chcete upozornit jeho kontejner, který (například stisknutí klávesy, klikněte na tlačítko myši nebo ke změně stavu ovládacího prvku) některá z akcí (určené vývojář ovládacího prvku) došlo k volání funkce spouštění událostí. Tato funkce upozorní kontejneru ovládacího prvku, který některé důležité akce došlo k chybě ve ohlásí související události.

Knihovny Microsoft Foundation Class nabízí programovací model optimalizované pro aktivaci událostí. V tomto modelu "mapy událostí" slouží k určení, které funkce fire které události pro konkrétní ovládací prvek. Mapy událostí obsahovat jeden makro pro každou jednotlivou událost. Například mapou události, aktivuje se stock klikněte na událost může vypadat například takto:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

`EVENT_STOCK_CLICK` Makro označuje, že ovládací prvek bude platit stock klikněte na událost pokaždé, když zjistí myši klikněte na tlačítko. Podrobnější seznam dalších uložených událostí, najdete v článku [– ovládací prvky ActiveX: události](../../mfc/mfc-activex-controls-events.md). Makra jsou také k dispozici k označení vlastních událostí.

Makra mapy událostí jsou důležité, je obecně nevkládejte je přímo. To je proto okno vlastností automaticky vytvoří položky mapa událostí ve zdrojových souborech, při použití funkce spouštění událostí přidružit události. Kdykoli, kterou chcete upravit, nebo přidejte záznam mapa událostí můžete použít okno vlastností.

Pro podporu mapy událostí, MFC poskytuje následující makra:

## <a name="event-map-macros"></a>Makra mapy událostí

### <a name="event-map-declaration-and-demarcation"></a>Událost mapy deklarace a Rozhraničení

|||
|-|-|
|[DECLARE_EVENT_MAP –](#declare_event_map)|Deklaruje, že mapou události se použije v třídě mapovat události funkce spouštění událostí (musí používat v deklaraci třídy).|
|[BEGIN_EVENT_MAP –](#begin_event_map)|Zahájí definici mapy událostí (musí používat v implementaci třídy).|
|[END_EVENT_MAP –](#end_event_map)|Ukončí definici mapy událostí (musí používat v implementaci třídy).|

### <a name="event-mapping-macros"></a>Makra mapování události

|||
|-|-|
|[EVENT_CUSTOM –](#event_custom)|Určuje, jaké funkce spouštění událostí bude platit zadané události.|
|[EVENT_CUSTOM_ID –](#event_custom_id)|Určuje funkce, jejíž spouštění událostí bude platit zadanou událost s ID určené odesílání.|

### <a name="message-mapping-macros"></a>Makra mapování zpráv

|||
|-|-|
|[ON_OLEVERB –](#on_oleverb)|Určuje vlastní operaci zpracovávaných ovládacího prvku OLE.|
|[ON_STDOLEVERB –](#on_stdoleverb)|Přepíše mapování standardní příkaz ovládacího prvku OLE.|

##  <a name="declare_event_map"></a>  DECLARE_EVENT_MAP –

Každý `COleControl`-odvozené třídy v programu můžete zadat mapování událostí k určení události, které bude platit vlastního ovládacího prvku.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Poznámky

Použijte declare_event_map – makro na konci deklarace třídy. Potom v souboru sada, která definuje členské funkce pro třídu, použijte begin_event_map – makro, makro položky pro všechny události ovládacího prvku a end_event_map – makro deklarovat konce seznamu událostí.

Další informace o mapy událostí najdete v článku [– ovládací prvky ActiveX: události](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Požadavky

**Záhlaví** afxctl.h

## <a name="begin_event_map"></a>  BEGIN_EVENT_MAP –

Zahájí definici mapy událostí.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*  
Určuje, že je název třídy ovládacího prvku, jehož událost mapování těchto.

*baseclass –*  
Určuje název základní třídu *theClass*.

### <a name="remarks"></a>Poznámky

V souboru implementace (sada), který definuje členské funkce pro třídu začínat mapa událostí begin_event_map – Makro potom přidejte makro položky pro všechny události a dokončení mapa událostí s end_event_map – makro.

Další informace o mapy událostí a begin_event_map – makro, najdete v článku [– ovládací prvky ActiveX: události](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Požadavky

**Záhlaví** afxctl.h

##  <a name="end_event_map"></a>  END_EVENT_MAP –

End_event_map – makro Použíjte k ukončení definici mapy událostí.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví** afxctl.h

## <a name="event_custom"></a>  EVENT_CUSTOM –

Definuje položku Mapa událostí pro vlastní události.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName*  
Název události

*pfnFire*  
Název událost, která iniciovala funkce.

*vtsParams*  
Seznam jedné nebo více konstant určující seznam parametrů pro funkci oddělených mezerami.

### <a name="remarks"></a>Poznámky

*VtsParams* parametr je seznam hodnot oddělených mezerami `VTS_` konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne čárkami) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Určuje barvu, která hodnotu následovanou ukazatel na seznam obsahující 32bitové celé číslo představující RGB `IFontDisp` rozhraní OLE písma objektu.

`VTS_` Konstanty a jejich významy jsou následující:

|Symbol|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR –|OLE_COLOR|
|VTS_CY|MĚNA.|
|VTS_DATE|DATUM|
|VTS_BSTR|**Const** __char\*__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT –|`IFontDispatch*`|
|VTS_HANDLE –|POPISOVAČ|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_OPTEXCLUSIVE –|OLE_OPTEXCLUSIVE|
|VTS_PICTURE –|`IPictureDisp*`|
|VTS_TRISTATE –|OLE_TRISTATE|
|VTS_XPOS_PIXELS –|OLE_XPOS_PIXELS|
|VTS_YPOS_PIXELS –|OLE_YPOS_PIXELS|
|VTS_XSIZE_PIXELS –|OLE_XSIZE_PIXELS|
|VTS_YSIZE_PIXELS –|OLE_YSIZE_PIXELS|
|TS_XPOS_HIMETRIC|OLE_XPOS_HIMETRIC|
|VTS_YPOS_HIMETRIC –|OLE_YPOS_HIMETRIC|
|VTS_XSIZE_HIMETRIC –|OLE_XSIZE_HIMETRIC|
|VTS_YSIZE_HIMETRIC –|OLE_YSIZE_HIMETRIC|

> [!NOTE]
> Nebyly definovány další variant konstanty pro všechny variant typy, s výjimkou vts_font – a vts_picture –, které poskytují ukazatel na variant – datové konstanta. Tyto konstanty jsou pojmenované pomocí `VTS_Pconstantname` konvence. Například VTS_PCOLOR je ukazatel na vts_color – konstanta.

### <a name="requirements"></a>Požadavky

**Záhlaví** afxctl.h

## <a name="event_custom_id"></a>  EVENT_CUSTOM_ID –

Definuje událost aktivuje funkce pro vlastní události, které patří k odesílání ID určeného *dispid*.

```cpp
EVENT_CUSTOM_ID(
  pszName,
  dispid,
  pfnFire,
  vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName*  
Název události

*dispID*  
Odesílání ID ovládacího prvku použitou při aktivuje událost.

*pfnFire*  
Název událost, která iniciovala funkce.

*vtsParams*  
Seznam parametrů proměnné předá do kontejneru ovládacího prvku, když událost je aktivována.

### <a name="remarks"></a>Poznámky

*VtsParams* argument je seznam hodnot oddělených mezerami `VTS_` konstanty. Jeden nebo více z těchto hodnot, oddělené mezerami není čárky určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Určuje barvu, která hodnotu následovanou ukazatel na seznam obsahující 32bitové celé číslo představující RGB `IFontDisp` rozhraní OLE písma objektu.

Seznam `VTS_` konstanty, najdete v části [event_custom –](#event_custom).

### <a name="requirements"></a>Požadavky

**Záhlaví** afxctl.h

## <a name="on_oleverb"></a>  ON_OLEVERB –

Toto makro definuje položku mapování zpráva, která se mapuje na konkrétní členské funkce ovládacího prvku vlastní operaci.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*idsVerbName* ID prostředku řetězec názvu daná akce.

*memberFxn*  
Funkce voláno rámcem při vyvolání příkazu.

### <a name="remarks"></a>Poznámky

Editor prostředků lze použít k vytvoření vlastní operaci názvy, které jsou přidány do tabulky řetězec.

Prototyp funkce pro *memberFxn* je:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Hodnoty *lpMsg*, *hWndParent*, a *lprect –* parametry jsou převzaty z odpovídajících parametrů `IOleObject::DoVerb` – členská funkce.

### <a name="requirements"></a>Požadavky

**Záhlaví** afxole.h

## <a name="on_stdoleverb"></a>  ON_STDOLEVERB –

Použití tohoto makra přepsat výchozí chování standardní operaci.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parametry

*iVerb*  
Standardní operace indexu pro příkaz přepsání.

*memberFxn*  
Funkce voláno rámcem při vyvolání příkazu.

### <a name="remarks"></a>Poznámky

Standardní operace indexu je ve formátu `OLEIVERB_`, za nímž následují akce. OLEIVERB_SHOW, OLEIVERB_HIDE a OLEIVERB_UIACTIVATE jsou některé příklady standardní příkazy.

V tématu [on_oleverb –](#on_oleverb) popis prototypu funkce má být použit jako *memberFxn* parametr.


### <a name="requirements"></a>Požadavky

**Záhlaví** afxole.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
