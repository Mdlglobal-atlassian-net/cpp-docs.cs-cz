---
title: Pomocné rutiny Ddx_dhtml
ms.date: 11/04/2016
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
ms.openlocfilehash: 90c80dbc5c8b6788f3afad3cf77d796139fbd946
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326644"
---
# <a name="ddxdhtml-helper-macros"></a>Pomocné rutiny Ddx_dhtml

Pomocné rutiny ddx_dhtml umožňují snadný přístup k běžně používaných vlastností ovládacích prvků na stránce HTML.

### <a name="data-exchange-macros"></a>Makra výměny dat

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Nastavuje nebo načítá hodnotu vlastnosti z vybraného ovládacího prvku.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Nastavuje nebo načítá text mezi počáteční a koncovou značku aktuálního prvku.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Nastavuje nebo načítá HTML mezi úvodní a koncovou značkou aktuálního prvku.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Nastavuje nebo načítá cílový bod adresy URL nebo ukotvení.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Nastavuje nebo načítá cílového okna nebo rámce.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Nastavuje nebo načítá název obrázkem nebo videoklipem v dokumentu.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Nastavuje nebo načítá adresy URL přidružené rámce.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Nastavuje nebo načítá adresy URL přidružené rámce.|

## <a name="requirements"></a>Požadavky

**Header:** afxdhtml.h

## <a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href

Nastavuje nebo načítá cílový bod adresy URL nebo ukotvení.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*Jméno*<br/>
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se vyměňují.

## <a name="remarks"></a>Poznámky

Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce využívá DISPID_IHTMLANCHORELEMENT_HREF dispatch ID.

## <a name="ddx_dhtml_anchor_target"></a>  DDX_DHtml_Anchor_Target

Nastavuje nebo načítá cílového okna nebo rámce.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*Jméno*<br/>
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se vyměňují.

## <a name="remarks"></a>Poznámky

Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce využívá DISPID_IHTMLANCHORELEMENT_TARGET dispatch ID.

## <a name="ddx_dhtml_elementinnerhtml"></a>  DDX_DHtml_ElementInnerHtml

Nastavuje nebo načítá HTML mezi úvodní a koncovou značkou aktuálního prvku.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*Jméno*<br/>
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se vyměňují.

## <a name="remarks"></a>Poznámky

Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce využívá DISPID_IHTMLELEMENT_INNERHTML dispatch ID.

## <a name="ddx_dhtml_elementinnertext"></a>  DDX_DHtml_ElementInnerText

Nastavuje nebo načítá text mezi počáteční a koncovou značku aktuálního prvku.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*Jméno*<br/>
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se vyměňují.

## <a name="remarks"></a>Poznámky

Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce využívá DISPID_IHTMLELEMENT_INNERTEXT dispatch ID.

## <a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue

Nastavuje nebo načítá hodnotu vlastnosti z vybraného ovládacího prvku.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*Jméno*<br/>
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se vyměňují. See *value* in [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

## <a name="remarks"></a>Poznámky

Toto makro bude úspěšné pouze při spuštění v ovládacích prvcích, které mají vlastnost Value. Ovládací prvky, které mají vlastnost Value zahrnují editační políčka, seznamy a pole se seznamem.

Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce využívá DISPID_A_VALUE dispatch ID.

## <a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src

Nastavuje nebo načítá adresy URL přidružené rámce.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*Jméno*<br/>
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se vyměňují.

## <a name="remarks"></a>Poznámky

Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce využívá DISPID_IHTMLFRAMEBASE_SRC dispatch ID.

## <a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src

Nastavuje nebo načítá adresy URL přidružené rámce.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*Jméno*<br/>
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se vyměňují.

## <a name="remarks"></a>Poznámky

Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce využívá DISPID_IHTMLFRAMEBASE_SRC dispatch ID.

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

Získá nebo načte název obrázkem nebo videoklipem v dokumentu.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*dx*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*Jméno*<br/>
Hodnota zadaná pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se vyměňují.

## <a name="remarks"></a>Poznámky

Při použití makra DDX_DHtml_Img_Src načíst vlastnost src pro IMAGE element, image objektu aplikace Internet Explorer vrátí plně uvozovacími znaky adresy URL pro zdroj obrázku. Například pokud používáte – makro DDX_DHtml_Img_Src nastavit vlastnost src elementu IMAGE na řetězec "některé zajímavé obrázek", pokud načítáte tuto vlastnost, Internet Explorer vrátí řetězec "res://d:\myapplication\myapp.exe/some% 20interesting % 20picture."

Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce využívá DISPID_IHTMLIMGELEMENT_SRC dispatch ID.

## <a name="see-also"></a>Viz také:

[CDHtmlDialog – třída](../../mfc/reference/cdhtmldialog-class.md)
