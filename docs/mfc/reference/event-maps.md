---
title: Mapy událostí
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: 34741dc05efe77c0932343739540370f54db6008
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420972"
---
# <a name="event-maps"></a>Mapy událostí

Pokaždé, když si ovládací prvek upozorní svůj kontejner, že došlo k určité akci (určené vývojářem ovládacího prvku) (například stisknutí klávesy, kliknutí myší nebo ke změně stavu ovládacího prvku), volá funkci, která vyvolává událost. Tato funkce upozorní kontejner ovládacího prvku, že při vyvolávání související události došlo k některé důležité akci.

Knihovna Microsoft Foundation Class nabízí programovací model optimalizovaný pro vyvolávání událostí. V tomto modelu se používají "mapy událostí" k určení toho, které funkce budou moci události pro určitý ovládací prvek vyvolávat. Mapy událostí obsahují jedno makro pro každou událost. Například mapa událostí, která aktivuje událost kliknutí na akcie, může vypadat takto:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

Makro `EVENT_STOCK_CLICK` označuje, že se ovládací prvek aktivuje událost po kliknutí pokaždé, když detekuje kliknutí myší. Podrobnější seznam dalších uložených událostí najdete v článku [ovládací prvky ActiveX: události](../../mfc/mfc-activex-controls-events.md). K dispozici jsou také makra, která označují vlastní události.

I když jsou makra mapování událostí důležitá, obecně je nevložíte přímo. Důvodem je, že okno **vlastnosti** (v **zobrazení tříd**) automaticky vytvoří položky mapování událostí ve zdrojových souborech, když ho použijete k přidružení funkcí pro spouštění událostí s událostmi. Kdykoli budete chtít upravit nebo přidat položku mapování událostí, můžete použít okno **vlastnosti** .

Pro podporu map událostí poskytuje MFC následující makra:

## <a name="event-map-macros"></a>Makra map událostí

### <a name="event-map-declaration-and-demarcation"></a>Deklarace a vymezení mapy událostí

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Deklaruje, že mapa události bude použita ve třídě pro mapování událostí na funkce, které jsou založené na událostech (musí být použity v deklaraci třídy).|
|[BEGIN_EVENT_MAP](#begin_event_map)|Zahájí definici mapy událostí (musí být použita v implementaci třídy).|
|[END_EVENT_MAP](#end_event_map)|Ukončí definici mapy událostí (musí být použita v implementaci třídy).|

### <a name="event-mapping-macros"></a>Makra mapování událostí

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|Určuje, která funkce pálení události spustí zadanou událost.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Určuje, která funkce spuštění události spustí zadanou událost s určeným ID odeslání.|

### <a name="message-mapping-macros"></a>Makra mapování zpráv

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|Označuje vlastní příkaz, který je zpracován ovládacím prvkem OLE.|
|[ON_STDOLEVERB](#on_stdoleverb)|Přepíše mapování standardních příkazů ovládacího prvku OLE.|

##  <a name="declare_event_map"></a>DECLARE_EVENT_MAP

Každá třída odvozená od `COleControl`v programu může poskytnout mapu události, která určuje události, které ovládací prvek bude moci aktivovat.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Poznámky

Použijte makro DECLARE_EVENT_MAP na konci deklarace třídy. Poté v souboru. cpp, který definuje členské funkce pro třídu, použijte makro BEGIN_EVENT_MAP, položky makra pro každou událost ovládacího prvku a makro END_EVENT_MAP k deklaraci konce seznamu událostí.

Další informace o mapách událostí naleznete v článku [ovládací prvky ActiveX: události](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Požadavky

**Header** AFXCTL. h

## <a name="begin_event_map"></a>BEGIN_EVENT_MAP

Zahájí definici mapy událostí.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje název třídy ovládacího prvku, jejíž mapa události je.

*baseClass*<br/>
Určuje název základní třídy *theclass*.

### <a name="remarks"></a>Poznámky

V souboru implementace (. cpp), který definuje členské funkce pro vaši třídu, spusťte mapu události pomocí makra BEGIN_EVENT_MAP, pak přidejte položky makra pro každou z vašich událostí a dokončete mapu událostí pomocí makra END_EVENT_MAP.

Další informace o mapách událostí a makru BEGIN_EVENT_MAP naleznete v článku [ovládací prvky ActiveX: události](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Požadavky

**Header** AFXCTL. h

##  <a name="end_event_map"></a>END_EVENT_MAP

K ukončení definice mapy událostí použijte makro END_EVENT_MAP.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Požadavky

**Header** AFXCTL. h

## <a name="event_custom"></a>EVENT_CUSTOM

Definuje položku mapování událostí pro vlastní událost.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName*<br/>
Název události.

*pfnFire*<br/>
Název funkce pro vyvolávání událostí.

*vtsParams*<br/>
Mezerou oddělený seznam jedné nebo více konstant určujících seznam parametrů funkce.

### <a name="remarks"></a>Poznámky

Parametr *vtsParams* je seznam hodnot oddělených mezerami z `VTS_` konstant. Jedna nebo více z těchto hodnot oddělených mezerami (nejedná se o čárky) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Určuje seznam obsahující 32 celé číslo představující hodnotu barvy RGB následovaný ukazatelem na `IFontDisp` rozhraní objektu písma OLE.

Konstanty `VTS_` a jejich význam jsou následující:

|Písmeno|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|MĚNA|
|VTS_DATE|DATUM|
|VTS_BSTR|\***const** __char__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|POPISOVAČ|
|VTS_SCODE|SCODE|
|VTS_BOOL|LOGICK|
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
> Pro všechny typy variant byly definovány další konstanty variant s výjimkou VTS_FONT a VTS_PICTURE, které poskytují ukazatel na konstantu dat variant. Tyto konstanty jsou pojmenovány pomocí `VTS_Pconstantname` konvence. Například VTS_PCOLOR je ukazatel na konstantu VTS_COLOR.

### <a name="requirements"></a>Požadavky

**Header** AFXCTL. h

## <a name="event_custom_id"></a>EVENT_CUSTOM_ID

Definuje funkci vyvolávání události pro vlastní událost, která patří do ID odeslání určeného identifikátorem *DISPID*.

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

*DISPID*<br/>
ID odeslání používané ovládacím prvkem při vyvolávání události.

*pfnFire*<br/>
Název funkce pro vyvolávání událostí.

*vtsParams*<br/>
Seznam proměnných parametrů předaných kontejneru ovládacího prvku při vyvolání události.

### <a name="remarks"></a>Poznámky

Argument *vtsParams* je seznam hodnot oddělených mezerami z `VTS_` konstant. Jedna nebo více z těchto hodnot oddělených mezerami, ne čárkami, určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Určuje seznam obsahující 32 celé číslo představující hodnotu barvy RGB následovaný ukazatelem na `IFontDisp` rozhraní objektu písma OLE.

Seznam konstant `VTS_` naleznete v tématu [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Požadavky

**Header** AFXCTL. h

## <a name="on_oleverb"></a>ON_OLEVERB

Toto makro definuje položku mapování zpráv, která mapuje vlastní příkaz na konkrétní členskou funkci vašeho ovládacího prvku.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*idsVerbName*<br/>
ID prostředku řetězce názvu příkazu.

*memberFxn*<br/>
Funkce, která je volána rozhraním, když je vyvolána operace.

### <a name="remarks"></a>Poznámky

Editor prostředků lze použít k vytvoření vlastních názvů operací, které jsou přidány do tabulky řetězců.

Prototyp funkce pro *memberFxn* je:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Hodnoty parametrů *lpMsg*, *hwndParent*a *lpRect* jsou odebírány z odpovídajících parametrů členské funkce `IOleObject::DoVerb`.

### <a name="requirements"></a>Požadavky

**Header** AFXOLE. h

## <a name="on_stdoleverb"></a>ON_STDOLEVERB

Pomocí tohoto makra můžete přepsat výchozí chování standardního příkazu.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Standardní index příkazu pro operaci, která je přepsána.

*memberFxn*<br/>
Funkce, která je volána rozhraním, když je vyvolána operace.

### <a name="remarks"></a>Poznámky

Standardní index příkazu je `OLEIVERB_`formuláře, po kterém následuje akce. Příklady standardních sloves jsou OLEIVERB_SHOW, OLEIVERB_HIDE a OLEIVERB_UIACTIVATE.

Popis prototypu funkce, který se má použít jako parametr *memberFxn* , najdete v tématu [ON_OLEVERB](#on_oleverb) .

### <a name="requirements"></a>Požadavky

**Header** AFXOLE. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
