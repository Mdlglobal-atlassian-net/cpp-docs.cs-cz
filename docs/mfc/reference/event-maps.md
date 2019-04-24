---
title: Mapy událostí
ms.date: 06/20/2018
f1_keywords:
- vc.mfc.macros.maps
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: 512170d7eaa891b3616ca1ea56c29a8bb5cccda9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322238"
---
# <a name="event-maps"></a>Mapy událostí

Pokaždé, když se ovládací prvek chce informovat svého kontejneru, která byla zaznamenána některá z akcí (určeno vývojářem ovládacího prvku) (například jedním stisknutím tlačítka, kliknutí myší nebo ke změně stavu ovládacího prvku) volá funkci vyvolávající události. Tato funkce upozorní, že některé důležité akce došlo k podle vyvoláním související události kontejnerem ovládacího prvku.

Knihovny Microsoft Foundation Class nabízí programovací model, který je optimalizovaný pro aktivaci událostí. V tomto modelu "mapy událostí" se používají k určení, funkcích, které aktivují události pro konkrétní ovládací prvek. Mapy událostí obsahovat jedno makro pro každou jednotlivou událost. Například mapu událostí, který aktivuje akcie klikněte na událost může vypadat třeba takto:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

`EVENT_STOCK_CLICK` – Makro označuje, že se ovládací prvek aktivuje akcie klikněte na událost pokaždé, když se zjistí myš, klikněte na tlačítko. Další podrobné informace o dalších uložených událostí, najdete v článku [ovládací prvky ActiveX: Události](../../mfc/mfc-activex-controls-events.md). Makra jsou také k dispozici k označení vlastní události.

Makra mapy událostí jsou důležité, obecně není vložen je přímo. Je to proto, že v okně Vlastnosti automaticky vytvoří položky mapa událostí ve zdrojových souborech, když ho použijete pro přidružení k události funkcí vyvolávající události. Pokaždé, když chcete upravit nebo přidat položku mapy událostí můžete použít v okně Vlastnosti.

Pro podporu mapy událostí, knihovna MFC poskytuje následující makra:

## <a name="event-map-macros"></a>Makra mapy událostí

### <a name="event-map-declaration-and-demarcation"></a>Událost mapování deklarace a Rozhraničení

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Deklaruje, že mapu událostí se použije ve třídě pro mapování události funkcí vyvolávající události (musí se použít v deklaraci třídy).|
|[BEGIN_EVENT_MAP](#begin_event_map)|Začíná definice mapu událostí (musí být použitý v implementaci třídy).|
|[END_EVENT_MAP](#end_event_map)|Ukončí definici mapy událostí (musí být použitý v implementaci třídy).|

### <a name="event-mapping-macros"></a>Makra mapování události

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|Určuje funkci, která vyvolávající události se zadanou událost aktivuje.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Určuje funkci, která vyvolávající události se aktivuje zadanou událost s ID určené odeslání.|

### <a name="message-mapping-macros"></a>Makra mapování zpráv

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|Určuje vlastní příkaz zpracovat ovládacího prvku OLE.|
|[ON_STDOLEVERB](#on_stdoleverb)|Přepsání standardních operací mapování ovládacího prvku OLE.|

##  <a name="declare_event_map"></a>  DECLARE_EVENT_MAP

Každý `COleControl`-odvozené třídy ve svém programu můžete zadat mapu událostí k určení události ovládacího prvku se aktivuje.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Poznámky

Použití DECLARE_EVENT_MAP – makro na konec deklarace třídy. Potom v souboru .cpp, který definuje členské funkce třídy, použijte BEGIN_EVENT_MAP – makro, makro položky pro každý z události ovládacího prvku a END_EVENT_MAP – makro deklarovat konce seznamu událostí.

Další informace o mapování události, najdete v článku [ovládací prvky ActiveX: Události](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Požadavky

**Header** afxctl.h

## <a name="begin_event_map"></a>  BEGIN_EVENT_MAP

Začíná definici mapy událostí.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Určuje, že je název třídy ovládacího prvku, namapujte tento parametr jehož událost.

*baseClass*<br/>
Určuje název základní třídy *theClass*.

### <a name="remarks"></a>Poznámky

V souboru implementace (.cpp), který definuje členské funkce třídy mapa událostí začínat BEGIN_EVENT_MAP – makro pak přidat makro položky pro každý z událostí a dokončete mapa událostí s END_EVENT_MAP – makro.

Další informace o mapování události a BEGIN_EVENT_MAP – makro, najdete v článku [ovládací prvky ActiveX: Události](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Požadavky

**Header** afxctl.h

##  <a name="end_event_map"></a>  END_EVENT_MAP

Použíjte END_EVENT_MAP – makro do konce definice mapy událostí.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Požadavky

**Header** afxctl.h

## <a name="event_custom"></a>  EVENT_CUSTOM –

Definuje položku Mapa událostí pro vlastní události.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName*<br/>
Název události

*pfnFire*<br/>
Název funkce událost.

*vtsParams*<br/>
Místo oddělený seznam jednoho nebo více konstant určující seznam parametrů funkce.

### <a name="remarks"></a>Poznámky

*VtsParams* parametr je místo oddělený seznam hodnot z `VTS_` konstanty. Jeden nebo více z těchto hodnot oddělených mezerami (ne čárky) určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Určuje hodnotu, za nímž následuje ukazatel na seznam obsahující 32bitové celé číslo představující RGB barvy `IFontDisp` rozhraní písmo objektu OLE.

`VTS_` Konstanty a jejich význam, jsou následující:

|Symbol|Typ parametru|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|MĚNY|
|VTS_DATE|DATE (Datum)|
|VTS_BSTR|**Const** __char\*__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|POPISOVAČ|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
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
> Další varianty konstanty byly definovány pro všechny varianty typy, s výjimkou VTS_FONT a VTS_PICTURE, poskytující ukazatel na konstantu dat variant. Tyto konstanty jsou pojmenované pomocí `VTS_Pconstantname` konvence. Například VTS_PCOLOR je ukazatel na VTS_COLOR – konstanta.

### <a name="requirements"></a>Požadavky

**Header** afxctl.h

## <a name="event_custom_id"></a>  EVENT_CUSTOM_ID

Definuje událost aktivaci funkce pro vlastní událost, které patří k ID odbavení určené *dispid*.

```cpp
EVENT_CUSTOM_ID(
  pszName,
  dispid,
  pfnFire,
  vtsParams)
```

### <a name="parameters"></a>Parametry

*pszName*<br/>
Název události

*dispid*<br/>
Identifikátor odeslání použit v ovládacím prvku při aktivaci události.

*pfnFire*<br/>
Název funkce událost.

*vtsParams*<br/>
Proměnné seznam parametrů předávaných kontejneru ovládacího prvku, když se aktivuje událost.

### <a name="remarks"></a>Poznámky

*VtsParams* argument je místo oddělený seznam hodnot z `VTS_` konstanty. Jeden nebo více z těchto hodnot oddělených mezerami, ne čárky určuje seznam parametrů funkce. Příklad:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

Určuje hodnotu, za nímž následuje ukazatel na seznam obsahující 32bitové celé číslo představující RGB barvy `IFontDisp` rozhraní písmo objektu OLE.

Seznam `VTS_` konstanty, naleznete v tématu [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Požadavky

**Header** afxctl.h

## <a name="on_oleverb"></a>  ON_OLEVERB

Toto makro definuje položku mapování zpráv, který se mapuje vlastní příkaz zvláštní členské funkce ovládacího prvku.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parametry

*idsVerbName*<br/>
ID zdroje řetězce názvu operaci.

*memberFxn*<br/>
Funkce, která volá se rozhraním, když uživatel vyvolá příkaz.

### <a name="remarks"></a>Poznámky

Editor prostředků lze použít k vytvoření vlastní příkaz názvy, které jsou přidány do vaší tabulky řetězců.

Prototyp funkce *memberFxn* je:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Hodnoty *lpMsg*, *hWndParent*, a *lprect –* parametry jsou převzaty z odpovídajících parametrů `IOleObject::DoVerb` členskou funkci.

### <a name="requirements"></a>Požadavky

**Hlavička** afxole.h

## <a name="on_stdoleverb"></a>  ON_STDOLEVERB

Chcete-li přepsat výchozí chování standardní příkaz použijte toto makro.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parametry

*iVerb*<br/>
Index standardní příkaz pro příkaz přepsání.

*memberFxn*<br/>
Funkce, která volá se rozhraním, když uživatel vyvolá příkaz.

### <a name="remarks"></a>Poznámky

Index standardní příkaz má formát `OLEIVERB_`následovaný akci. OLEIVERB_SHOW OLEIVERB_HIDE a OLEIVERB_UIACTIVATE je několik příkladů standardní příkazy.

Zobrazit [ON_OLEVERB](#on_oleverb) popis prototypu funkce se použije jako *memberFxn* parametru.

### <a name="requirements"></a>Požadavky

**Hlavička** afxole.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
