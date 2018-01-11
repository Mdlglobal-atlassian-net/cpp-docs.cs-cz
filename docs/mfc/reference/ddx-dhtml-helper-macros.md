---
title: "Makra pomocná DDX_DHtml | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
dev_langs: C++
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3d5a69e08d06a53dcb2f3a4be58618e9829e8c8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ddxdhtml-helper-macros"></a>Makra DDX_DHtml pomocné rutiny
Makra pomocná DDX_DHtml umožní snadný přístup k běžně používané vlastností ovládacích prvků na stránce HTML.  
  
### <a name="data-exchange-macros"></a>Makra dat systému Exchange  
  
|||  
|-|-|  
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Nastavuje nebo načítá hodnotu vlastnosti z ovládacího prvku vybrané.|  
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Nastavuje nebo načítá text mezi počáteční a koncové značky aktuálního elementu.|  
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Nastavuje nebo načítá HTML mezi úvodní a koncovou značkou aktuálního elementu.|  
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Nastavuje nebo načítá cílového bodu adresy URL nebo ukotvení.|  
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Nastavuje nebo načítá cílového okna nebo rámce.|  
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Nastavuje nebo načítá název bitové kopie nebo video klip v dokumentu.|  
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Nastavuje nebo načítá adresu URL přidružené rámečku.|  
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Nastavuje nebo načítá adresu URL přidružené rámečku.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdhtml.h  

## <a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href
Nastavuje nebo načítá cílového bodu adresy URL nebo ukotvení.  
  
  
  
```  
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.  
  
 `name`  
 Hodnota, která jste zadali pro parametr ID ovládacího prvku HTML.  
  
 `var`  
 Hodnota během výměny.  
  
## <a name="remarks"></a>Poznámky  
 Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce pomocí DISPID_IHTMLANCHORELEMENT_HREF odesílání ID.

## <a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target
 Nastavuje nebo načítá cílového okna nebo rámce.  
    
```  
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.  
  
 `name`  
 Hodnota, která jste zadali pro parametr ID ovládacího prvku HTML.  
  
 `var`  
 Hodnota během výměny.  
  
## <a name="remarks"></a>Poznámky  
 Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce pomocí DISPID_IHTMLANCHORELEMENT_TARGET odesílání ID.  

## <a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml
 Nastavuje nebo načítá HTML mezi úvodní a koncovou značkou aktuálního elementu.  
  
  
  
```  
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.  
  
 `name`  
 Hodnota, která jste zadali pro parametr ID ovládacího prvku HTML.  
  
 `var`  
 Hodnota během výměny.  
  
## <a name="remarks"></a>Poznámky  
 Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce pomocí DISPID_IHTMLELEMENT_INNERHTML odesílání ID.  
  

## <a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText
Nastavuje nebo načítá text mezi počáteční a koncové značky aktuálního elementu.  
  
  
  
```  
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.  
  
 `name`  
 Hodnota, která jste zadali pro parametr ID ovládacího prvku HTML.  
  
 `var`  
 Hodnota během výměny.  
  
## <a name="remarks"></a>Poznámky  
 Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce pomocí DISPID_IHTMLELEMENT_INNERTEXT odesílání ID. 

## <a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue  
Nastavuje nebo načítá hodnotu vlastnosti z ovládacího prvku vybrané.  
 
```  
DDX_DHtml_ElementValue(
    CDataExchange* dx,  
    LPCTSTR name,
    var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.  
  
 `name`  
 Hodnota, která jste zadali pro parametr ID ovládacího prvku HTML.  
  
 `var`  
 Hodnota během výměny. V tématu *hodnotu* v [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).  
  
## <a name="remarks"></a>Poznámky  
 Toto makro bude úspěšné pouze při spuštění na ovládací prvky, které mají vlastnost Value. Ovládací prvky, které mají hodnotu vlastnosti zahrnují úpravy, seznamy a polí se seznamem.  
  
 Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce pomocí DISPID_A_VALUE odesílání ID.  

## <a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src
Nastavuje nebo načítá adresu URL přidružené rámečku.  
  
```  
DDX_DHtml_Frame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.  
  
 `name`  
 Hodnota, která jste zadali pro parametr ID ovládacího prvku HTML.  
  
 `var`  
 Hodnota během výměny.  
  
## <a name="remarks"></a>Poznámky  
 Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce pomocí DISPID_IHTMLFRAMEBASE_SRC odesílání ID.  

## <a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src
Nastavuje nebo načítá adresu URL přidružené rámečku.  
  
  
  
```  
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.  
  
 `name`  
 Hodnota, která jste zadali pro parametr ID ovládacího prvku HTML.  
  
 `var`  
 Hodnota během výměny.  
  
## <a name="remarks"></a>Poznámky  
 Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce pomocí DISPID_IHTMLFRAMEBASE_SRC odesílání ID. 

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src
Získá nebo načte název bitové kopie nebo video klip v dokumentu.  
  
```  
DDX_DHtml_Img_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Parametry  
 `dx`  
 Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.  
  
 `name`  
 Hodnota, která jste zadali pro parametr ID ovládacího prvku HTML.  
  
 `var`  
 Hodnota během výměny.  
  
## <a name="remarks"></a>Poznámky  
 Při použití `DDX_DHtml_Img_Src` makro načíst vlastnost src pro element OBRÁZKU objekt image aplikace Internet Explorer vrátí plně uvozovacími znaky adresy URL pro zdroj bitové kopie. Například pokud použijete `DDX_DHtml_Img_Src` makro nastavit vlastnost src elementu bitové kopie na řetězec "některé zajímavé formát," Pokud načítáte tuto vlastnost, Internet Explorer vrátí řetězec "res://d:\myapplication\myapp.exe/some% 20interesting % 20picture."  
  
 Toto makro volá [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) funkce pomocí DISPID_IHTMLIMGELEMENT_SRC odesílání ID.  

  
## <a name="see-also"></a>Viz také  
 [CDHtmlDialog – třída](../../mfc/reference/cdhtmldialog-class.md)
