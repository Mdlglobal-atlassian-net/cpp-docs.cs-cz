---
title: Makra pomocná DDX_DHtml
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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866654"
---
# <a name="ddx_dhtml-helper-macros"></a>Makra pomocná DDX_DHtml

Pomocná makra DDX_DHtml umožňují snadný přístup k běžně používaným vlastnostem ovládacích prvků na stránce HTML.

### <a name="data-exchange-macros"></a>Makra výměny dat

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Nastaví nebo načte vlastnost Value z vybraného ovládacího prvku.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Nastaví nebo načte text mezi počátečními a koncovými značkami aktuálního prvku.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Nastaví nebo načte kód HTML mezi počátečními a koncovými značkami aktuálního prvku.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Nastaví nebo načte cílovou adresu URL nebo kotvicí bod.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Nastaví nebo načte cílové okno nebo rámec.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Nastaví nebo načte název obrázku nebo videoklipu v dokumentu.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Nastaví nebo načte adresu URL přidruženého rámce.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Nastaví nebo načte adresu URL přidruženého rámce.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdhtml. h

## <a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href

Nastaví nebo načte cílovou adresu URL nebo kotvicí bod.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) .

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se má vyměňovat

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí DISPID_IHTMLANCHORELEMENT_HREFho ID odeslání.

## <a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target

Nastaví nebo načte cílové okno nebo rámec.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) .

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se má vyměňovat

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí DISPID_IHTMLANCHORELEMENT_TARGETho ID odeslání.

## <a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml

Nastaví nebo načte kód HTML mezi počátečními a koncovými značkami aktuálního prvku.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) .

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se má vyměňovat

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí DISPID_IHTMLELEMENT_INNERHTMLho ID odeslání.

## <a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText

Nastaví nebo načte text mezi počátečními a koncovými značkami aktuálního prvku.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) .

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se má vyměňovat

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí DISPID_IHTMLELEMENT_INNERTEXTho ID odeslání.

## <a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue

Nastaví nebo načte vlastnost Value z vybraného ovládacího prvku.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) .

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se má vyměňovat Zobrazit *hodnotu* v [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

## <a name="remarks"></a>Poznámky

Toto makro bude úspěšné pouze při spuštění u ovládacích prvků, které mají vlastnost Value. Ovládací prvky, které mají vlastnost Value, zahrnují pole pro úpravy, seznamy a pole se seznamem.

Toto makro volá funkci [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí DISPID_A_VALUEho ID odeslání.

## <a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src

Nastaví nebo načte adresu URL přidruženého rámce.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) .

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se má vyměňovat

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí DISPID_IHTMLFRAMEBASE_SRCho ID odeslání.

## <a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src

Nastaví nebo načte adresu URL přidruženého rámce.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) .

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se má vyměňovat

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí DISPID_IHTMLFRAMEBASE_SRCho ID odeslání.

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

Získá nebo načte název obrázku nebo videoklipu v dokumentu.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*DX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) .

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která se má vyměňovat

## <a name="remarks"></a>Poznámky

Při použití makra DDX_DHtml_Img_Src k načtení vlastnosti src pro prvek obrázku, objekt obrázku aplikace Internet Explorer vrátí úplnou řídicí adresu URL pro zdroj obrázku. Například pokud použijete makro DDX_DHtml_Img_Src k nastavení vlastnosti src elementu IMAGE na řetězec "zajímavého obrázku", aplikace Internet Explorer vrátí řetězec "Res://d: \ MyApplication \ MyApp. exe/část %2 0 zajímavého %2 0 obrázku."

Toto makro volá funkci [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí DISPID_IHTMLIMGELEMENT_SRCho ID odeslání.

## <a name="see-also"></a>Viz také

[CDHtmlDialog – třída](../../mfc/reference/cdhtmldialog-class.md)
