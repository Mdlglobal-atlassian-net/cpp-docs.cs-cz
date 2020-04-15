---
title: Mapy událostí
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: c79d2fb1ac73947ddb13adcbd444ff7b5d50bdb4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365739"
---
# <a name="event-maps"></a>Mapy událostí

Kdykoli ovládací prvek chce upozornit svůj kontejner, že došlo k určité akci (určené vývojářem ovládacího prvku) (například stisknutí klávesy, klepnutí myší nebo změna stavu ovládacího prvku) volá funkci spouštění událostí. Tato funkce upozorní kontejner ovládacího prvku, že došlo k některé důležité akce spuštěním související události.

Knihovna tříd Microsoft Foundation nabízí programovací model optimalizovaný pro spouštění událostí. V tomto modelu "mapy událostí" se používají k určení, které funkce oheň, které události pro konkrétní ovládací prvek. Mapy událostí obsahují jedno makro pro každou událost. Například mapa událostí, která spouští akci Ovou událost Click, může vypadat takto:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

Makro `EVENT_STOCK_CLICK` označuje, že ovládací prvek vypálí akci Click při každém zjištění kliknutí myší. Podrobnější seznam dalších akciových událostí naleznete v článku [Ovládací prvky ActiveX: Události](../../mfc/mfc-activex-controls-events.md). Makra jsou také k dispozici k označení vlastních událostí.

Přestože makra mapy událostí jsou důležitá, obvykle je nevkládáte přímo. Důvodem je, že okno **Vlastnosti** (v **zobrazení tříd )** automaticky vytvoří položky mapy událostí ve zdrojových souborech, když je používáte k přidružení funkcí spouštění událostí k událostem. Kdykoli chcete upravit nebo přidat položku mapy událostí, můžete použít okno **Vlastnosti.**

Chcete-li podporovat mapy událostí, knihovna MFC poskytuje následující makra:

## <a name="event-map-macros"></a>Makra mapování událostí

### <a name="event-map-declaration-and-demarcation"></a>Deklarace mapy událostí a vymezení

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Deklaruje, že mapa událostí bude použita ve třídě k mapování událostí na funkce spouštění událostí (musí být použita v deklaraci třídy).|
|[BEGIN_EVENT_MAP](#begin_event_map)|Začíná definice mapy událostí (musí být použita v implementaci třídy).|
|[END_EVENT_MAP](#end_event_map)|Ukončí definici mapy událostí (musí být použita v implementaci třídy).|

### <a name="event-mapping-macros"></a>Makra mapování událostí

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|Označuje, která funkce spouštění událostí vypálí zadanou událost.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Označuje, která funkce spouštění událostí vypálí zadanou událost s určeným ID odeslání.|

### <a name="message-mapping-macros"></a>Makra mapování zpráv

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|Označuje vlastní sloveso zpracované ovládacím prvkem OLE.|
|[ON_STDOLEVERB](#on_stdoleverb)|Přepíše standardní mapování slovesa ovládacího prvku OLE.|

## <a name="declare_event_map"></a><a name="declare_event_map"></a>DECLARE_EVENT_MAP

Každá `COleControl`-derived třída ve vašem programu může poskytnout mapu událostí k určení událostí, které bude váš ovládací prvek sfire.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Poznámky

Použijte makro DECLARE_EVENT_MAP na konci deklarace třídy. Potom v souboru CPP, který definuje členské funkce pro třídu, použijte makro BEGIN_EVENT_MAP, položky maker pro každou událost ovládacího prvku a makro END_EVENT_MAP deklarovat konec seznamu událostí.

Další informace o mapách událostí naleznete v článku [Ovládací prvky ActiveX: Události](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Požadavky

**Záhlaví** afxctl.h

## <a name="begin_event_map"></a><a name="begin_event_map"></a>BEGIN_EVENT_MAP

Začíná definici mapy událostí.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy ovládacího prvku, jejíž mapa událostí se jedná.

*Baseclass*<br/>
Určuje název základní třídy *Class*.

### <a name="remarks"></a>Poznámky

V souboru implementace (.cpp), který definuje členské funkce pro vaši třídu, spusťte mapu událostí pomocí BEGIN_EVENT_MAP makra, přidejte položky maker pro každou událost a dokončete mapu událostí pomocí END_EVENT_MAP makra.

Další informace o mapách událostí a BEGIN_EVENT_MAP makru naleznete v článku [Ovládací prvky ActiveX: Události](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Požadavky

**Záhlaví** afxctl.h

## <a name="end_event_map"></a><a name="end_event_map"></a>END_EVENT_MAP

Pomocí END_EVENT_MAP makru ukončite definici mapy událostí.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Požadavky

**Záhlaví** afxctl.h

## <a name="event_custom"></a><a name="event_custom"></a>EVENT_CUSTOM

Definuje položku mapy událostí pro vlastní událost.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName*<br/>
Název události.

*pfnFire řekl:*<br/>
Název funkce spouštění událostí.

*vtsParams*<br/>
Mezerou oddělený seznam jedné nebo více konstant určujících seznam parametrů funkce.

### <a name="remarks"></a>Poznámky

Parametr *vtsParams* je seznam hodnot oddělených `VTS_` mezerami od konstant. Jedna nebo více těchto hodnot oddělených mezerami (nikoli čárkami) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

určuje seznam obsahující 32bitové celé číslo představující hodnotu barvy RGB, následovaný `IFontDisp` ukazatelem na rozhraní objektu písma OLE.

Konstanty `VTS_` a jejich významy jsou následující:

|Symbol|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|MĚNA|
|VTS_DATE|DATE (Datum)|
|VTS_BSTR|**const** __\* char__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|Zpracování|
|VTS_SCODE|SCODE|
|VTS_BOOL|Bool|
|VTS_VARIANT|`const VARIANT*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_OPTEXCLUSIVE|OLE_OPTEXCLUSIVE|
|VTS_PICTURE|`IPictureDisp*`|
|VTS_TRISTATE|OLE_TRISTATE|
|VTS_XPOS_PIXELS|OLE_XPOS_PIXELS|
|VTS_YPOS_PIXELS|OLE_YPOS_PIXELS|
|VTS_XSIZE_PIXELS|OLE_XSIZE_PIXELS|
|VTS_YSIZE_PIXELS|OLE_YSIZE_PIXELS|
|TS_XPOS_HIMETRIC|OLE_XPOS_HIMETRIC|
|VTS_YPOS_HIMETRIC|OLE_YPOS_HIMETRIC|
|VTS_XSIZE_HIMETRIC|OLE_XSIZE_HIMETRIC|
|VTS_YSIZE_HIMETRIC|OLE_YSIZE_HIMETRIC|

> [!NOTE]
> Další konstanty variant byly definovány pro všechny typy variant, s výjimkou VTS_FONT a VTS_PICTURE, které poskytují ukazatel na konstantu dat varianty. Tyto konstanty jsou `VTS_Pconstantname` pojmenovány pomocí konvence. Například VTS_PCOLOR je ukazatel na VTS_COLOR konstantu.

### <a name="requirements"></a>Požadavky

**Záhlaví** afxctl.h

## <a name="event_custom_id"></a><a name="event_custom_id"></a>EVENT_CUSTOM_ID

Definuje funkci zapalování událostí pro vlastní událost patřící k ID odeslání určené *dispid*.

```cpp
EVENT_CUSTOM_ID(
    pszName,
    dispid,
    pfnFire,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName*<br/>
Název události.

*Dispid*<br/>
ID odeslání používané ovládacím prvkem při spouštění události.

*pfnFire řekl:*<br/>
Název funkce spouštění událostí.

*vtsParams*<br/>
Seznam proměnných parametrů předaných kontejneru ovládacího prvku při aktivována událost.

### <a name="remarks"></a>Poznámky

Argument *vtsParams* je mezerou oddělený seznam `VTS_` hodnot od konstant. Jedna nebo více těchto hodnot oddělených mezerami, nikoli čárkami, určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

určuje seznam obsahující 32bitové celé číslo představující hodnotu barvy RGB, následovaný `IFontDisp` ukazatelem na rozhraní objektu písma OLE.

Seznam konstant naleznete `VTS_` v [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Požadavky

**Záhlaví** afxctl.h

## <a name="on_oleverb"></a><a name="on_oleverb"></a>ON_OLEVERB

Toto makro definuje položku mapy zpráv, která mapuje vlastní sloveso na konkrétní členskou funkci ovládacího prvku.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*idsVerbName*<br/>
ID řetězce prostředku názvu slovesa.

*členFxn*<br/>
Funkce volaná frameworkem při vyvolání slovesa.

### <a name="remarks"></a>Poznámky

Editor prostředků lze použít k vytvoření vlastní názvy sloves, které jsou přidány do tabulky řetězců.

Prototyp funkce pro *memberFxn* je:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Hodnoty parametrů *lpMsg*, *hWndParent*a *lpRect* jsou převzaty z `IOleObject::DoVerb` odpovídajících parametrů členské funkce.

### <a name="requirements"></a>Požadavky

**Záhlaví** afxole.h

## <a name="on_stdoleverb"></a><a name="on_stdoleverb"></a>ON_STDOLEVERB

Toto makro slouží k přepsání výchozího chování standardního slovesa.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parametry

*iSponož*<br/>
Standardní index slovesa pro přepsání slovesa.

*členFxn*<br/>
Funkce volaná frameworkem při vyvolání slovesa.

### <a name="remarks"></a>Poznámky

Standardní index slovesa `OLEIVERB_`je formuláře , následovaný akcí. OLEIVERB_SHOW, OLEIVERB_HIDE a OLEIVERB_UIACTIVATE jsou některé příklady standardních sloves.

Viz [ON_OLEVERB](#on_oleverb) popis prototypu funkce, který má být použit jako *parametr memberFxn.*

### <a name="requirements"></a>Požadavky

**Záhlaví** afxole.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
