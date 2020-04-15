---
title: DDX_DHtml pomocná makra
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
ms.openlocfilehash: f78a923a498713867c13ccc88e3e30c1f0a23885
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365874"
---
# <a name="ddx_dhtml-helper-macros"></a>DDX_DHtml pomocná makra

Pomocná makra DDX_DHtml umožňují snadný přístup k běžně používaným vlastnostem ovládacích prvků na stránce HTML.

### <a name="data-exchange-macros"></a>Makra výměny dat

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Nastaví nebo načte vlastnost Value z vybraného ovládacího prvku.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Nastaví nebo načte text mezi počátečními a koncovými značkami aktuálního prvku.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Nastaví nebo načte HTML mezi počáteční a koncovou značkou aktuálního prvku.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Nastaví nebo načte cílovou adresu URL nebo kotevní bod.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Nastaví nebo načte cílové okno nebo rámeček.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Nastaví nebo načte název obrázku nebo videoklipu v dokumentu.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Nastaví nebo načte adresu URL přidruženého rámce.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Nastaví nebo načte adresu URL přidruženého rámce.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdhtml.h

## <a name="ddx_dhtml_anchor_href"></a><a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href

Nastaví nebo načte cílovou adresu URL nebo kotevní bod.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která je vyměňována.

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí id odeslání DISPID_IHTMLANCHORELEMENT_HREF.

## <a name="ddx_dhtml_anchor_target"></a><a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target

Nastaví nebo načte cílové okno nebo rámeček.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která je vyměňována.

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí id DISPID_IHTMLANCHORELEMENT_TARGET odeslání.

## <a name="ddx_dhtml_elementinnerhtml"></a><a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml

Nastaví nebo načte HTML mezi počáteční a koncovou značkou aktuálního prvku.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která je vyměňována.

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí id DISPID_IHTMLELEMENT_INNERHTML odeslání.

## <a name="ddx_dhtml_elementinnertext"></a><a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText

Nastaví nebo načte text mezi počátečními a koncovými značkami aktuálního prvku.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která je vyměňována.

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí id DISPID_IHTMLELEMENT_INNERTEXT odeslání.

## <a name="ddx_dhtml_elementvalue"></a><a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue

Nastaví nebo načte vlastnost Value z vybraného ovládacího prvku.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která je vyměňována. Viz *hodnota* v [cdhtmldialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

## <a name="remarks"></a>Poznámky

Toto makro bude úspěšné pouze při spuštění na ovládací prvky, které mají Value vlastnost. Ovládací prvky, které mají vlastnost Value, zahrnují editační pole, seznamy a pole se seznamem.

Toto makro volá funkci [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí id DISPID_A_VALUE odeslání.

## <a name="ddx_dhtml_frame_src"></a><a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src

Nastaví nebo načte adresu URL přidruženého rámce.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která je vyměňována.

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí id odeslání DISPID_IHTMLFRAMEBASE_SRC.

## <a name="ddx_dhtml_iframe_src"></a><a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src

Nastaví nebo načte adresu URL přidruženého rámce.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která je vyměňována.

## <a name="remarks"></a>Poznámky

Toto makro volá funkci [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí id odeslání DISPID_IHTMLFRAMEBASE_SRC.

## <a name="ddx_dhtml_img_src"></a><a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

Získá nebo načte název obrázku nebo videoklipu v dokumentu.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parametry

*Dx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*Jméno*<br/>
Hodnota, kterou jste zadali pro parametr ID ovládacího prvku HTML.

*var*<br/>
Hodnota, která je vyměňována.

## <a name="remarks"></a>Poznámky

Při použití DDX_DHtml_Img_Src makro k načtení vlastnosti src pro element IMAGE vrátí objekt obrázku aplikace Internet Explorer plně uvozenou adresu URL pro zdroj obrázku. Pokud například použijete makro DDX_DHtml_Img_Src k nastavení vlastnosti src prvku IMAGE na řetězec "nějaký zajímavý obrázek", když tuto vlastnost načtete, aplikace Internet Explorer vrátí řetězec "res://d:\myapplication\myapp.exe/some%20interesting%20picture".

Toto makro volá funkci [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) pomocí id odeslání DISPID_IHTMLIMGELEMENT_SRC.

## <a name="see-also"></a>Viz také

[Třída CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)
