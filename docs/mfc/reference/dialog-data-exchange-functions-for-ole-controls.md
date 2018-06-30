---
title: Funkce výměny dat dialogových oken pro ovládací prvky OLE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDISP/DDX_OCBool
- AFXDISP/DDX_OCBoolRO
- AFXDISP/DDX_OCColor
- AFXDISP/DDX_OCColorRO
- AFXDISP/DDX_OCFloat
- AFXDISP/DDX_OCFloatRO
- AFXDISP/DDX_OCInt
- AFXDISP/DDX_OCIntRO
- AFXDISP/DDX_OCShort
- AFXDISP/DDX_OCShortRO
- AFXDISP/DDX_OCText
- AFXDISP/DDX_OCTextRO
dev_langs:
- C++
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 542afe8ba67e1d9c6138998320483a964a08724a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121822"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Funkce výměny dat dialogových oken pro ovládací prvky OLE
Toto téma uvádí DDX_OC funkce, které slouží pro výměnu dat mezi vlastností ovládacího prvku OLE ve dialogového okna, formátu zobrazení nebo objekt zobrazení ovládacího prvku a datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
### <a name="ddxoc-functions"></a>Funkce DDX_OC  
  
|||  
|-|-|  
|[Ddx_ocbool –](#ddx_ocbool)|Spravuje přenos **BOOL** dat mezi vlastností ovládacího prvku OLE a **BOOL** – datový člen.|  
|[Ddx_ocboolro –](#ddx_ocboolro)|Spravuje přenos **BOOL** dat mezi jen pro čtení vlastnost ovládacího prvku OLE a **BOOL** – datový člen.|  
|[Ddx_occolor –](#ddx_occolor)|Spravuje přenos **OLE_COLOR** dat mezi vlastností ovládacího prvku OLE a **OLE_COLOR** – datový člen.|  
|[Ddx_occolorro –](#ddx_occolorro)|Spravuje přenos **OLE_COLOR** dat mezi jen pro čtení vlastnost ovládacího prvku OLE a **OLE_COLOR** – datový člen.|  
|[Ddx_ocfloat –](#ddx_ocfloat)|Spravuje přenos **float** (nebo **dvojité**) dat mezi vlastností ovládacího prvku OLE a **float** (nebo **dvojité**) – datový člen.|  
|[Ddx_ocfloatro –](#ddx_ocfloatro)|Spravuje přenos **float** (nebo **dvojité**) dat mezi jen pro čtení vlastnost ovládacího prvku OLE a **float** (nebo **dvojité**) dat člen.|  
|[Ddx_ocint –](#ddx_ocint)|Spravuje přenos **int** (nebo **dlouho**) dat mezi vlastností ovládacího prvku OLE a **int** (nebo **dlouho**) – datový člen.|  
|[Ddx_ocintro –](#ddx_ocintro)|Spravuje přenos **int** (nebo **dlouho**) dat mezi jen pro čtení vlastnost ovládacího prvku OLE a **int** (nebo **dlouho**) – datový člen.|  
|[Ddx_ocshort –](#ddx_ocshort)|Spravuje přenos **krátké** dat mezi vlastností ovládacího prvku OLE a **krátké** – datový člen.|  
|[Ddx_ocshortro –](#ddx_ocshortro)|Spravuje přenos **krátké** dat mezi jen pro čtení vlastnost ovládacího prvku OLE a **krátké** – datový člen.|  
|[Ddx_octext –](#ddx_octext)|Spravuje přenos **CString** dat mezi vlastností ovládacího prvku OLE a **CString** – datový člen.|  
|[Ddx_octextro –](#ddx_octextro)|Spravuje přenos **CString** dat mezi jen pro čtení vlastnost ovládacího prvku OLE a **CString** – datový člen.|  
  
##  <a name="ddx_ocbool"></a>  Ddx_ocbool –  
 `DDX_OCBool` Funkce spravuje přenos **BOOL** formuláři dat mezi vlastností ovládacího prvku OLE v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a **BOOL** – datový člen dialogu, zobrazení formuláře, nebo objekt zobrazení ovládacího prvku.  
  
```   
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví:** afxdisp.h  
  
##  <a name="ddx_ocboolro"></a>  Ddx_ocboolro –  
 `DDX_OCBoolRO` Funkce spravuje přenos **BOOL** formuláři dat mezi vlastnost jen pro čtení OLE ovládacího prvku v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a **BOOL** dialogového okna, – datový člen zobrazení formuláře, nebo objekt zobrazení ovládacího prvku.  
  
```   
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    BOOL& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="ddx_occolor"></a>  Ddx_occolor –  
 `DDX_OCColor` Funkce spravuje přenos dat OLE_COLOR mezi vlastností ovládacího prvku OLE v dialogovém okně, zobrazení formuláře, nebo objekt zobrazení ovládacího prvku a členem OLE_COLOR dat dialogových oken, zobrazení formuláře nebo řízení objekt zobrazení.  
  
```   
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="ddx_occolorro"></a>  Ddx_occolorro –  
 `DDX_OCColorRO` Funkce spravuje přenos dat OLE_COLOR mezi vlastnost jen pro čtení OLE ovládacího prvku v dialogovém okně, zobrazení formuláře, nebo objekt zobrazení ovládacího prvku a členem OLE_COLOR dat dialogových oken, zobrazení formuláře nebo řízení objekt zobrazení.  
  
```   
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    OLE_COLOR& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="ddx_ocfloat"></a>  Ddx_ocfloat –  
 `DDX_OCFloat` Funkce spravuje přenos **float** (nebo **dvojité**) dat mezi vlastností ovládacího prvku OLE v dialogovém okně, tvoří zobrazení, nebo objekt zobrazení ovládacího prvku a **float** (nebo **dvojité**) – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```   
void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    float& value);

void AFXAPI DDX_OCFloat(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    double& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="ddx_ocfloatro"></a>  Ddx_ocfloatro –  
 `DDX_OCFloatRO` Funkce spravuje přenos **float** (nebo **dvojité**) dat mezi vlastnost jen pro čtení OLE ovládacího prvku v dialogovém okně, tvoří zobrazení, nebo objekt zobrazení ovládacího prvku a  **float** (nebo **dvojité**) – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```   
void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    float& value);

void AFXAPI DDX_OCFloatRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    double& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="ddx_ocint"></a>  Ddx_ocint –  
 `DDX_OCInt` Funkce spravuje přenos **int** (nebo **dlouho**) dat mezi vlastností ovládacího prvku OLE v dialogovém okně, tvoří zobrazení, nebo objekt zobrazení ovládacího prvku a **int**(nebo **dlouho**) – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```   
void AFXAPI DDX_OCInt(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    int& value);

void AFXAPI DDX_OCInt(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    long& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="ddx_ocintro"></a>  Ddx_ocintro –  
 `DDX_OCIntRO` Funkce spravuje přenos **int** (nebo **dlouho**) dat mezi vlastnost jen pro čtení OLE ovládacího prvku v dialogovém okně, tvoří zobrazení, nebo objekt zobrazení ovládacího prvku a **int** (nebo **dlouho**) – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```   
void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    int& value);

void AFXAPI DDX_OCIntRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    long& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="ddx_ocshort"></a>  Ddx_ocshort –  
 `DDX_OCShort` Funkce spravuje přenos krátké dat mezi vlastností ovládacího prvku OLE v dialogovém okně, zobrazení formuláře, nebo objekt zobrazení ovládacího prvku a short – datový člen dialogovém okně zobrazení formuláře nebo řízení objekt zobrazení.  
  
```   
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="ddx_ocshortro"></a>  Ddx_ocshortro –  
 `DDX_OCShortRO` Funkce spravuje přenos krátké dat mezi vlastnost jen pro čtení OLE ovládacího prvku v dialogovém okně, zobrazení formuláře, nebo objekt zobrazení ovládacího prvku a short – datový člen dialogovém okně zobrazení formuláře nebo řízení objekt zobrazení.  
  
```   
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    short& value);
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="ddx_octext"></a>  Ddx_octext –  
 **Ddx_octext –** funkce spravuje přenos **CString** formuláři dat mezi vlastností ovládacího prvku OLE v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a **CString** dat člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```   
void AFXAPI DDX_OCText(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel **CDataExchange** objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h  
  
##  <a name="ddx_octextro"></a>  Ddx_octextro –  
 `DDX_OCTextRO` Funkce spravuje přenos `CString` formuláři dat mezi vlastnost jen pro čtení OLE ovládacího prvku v dialogovém okně, zobrazení, nebo objekt zobrazení ovládacího prvku a `CString` – datový člen dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
```  
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,  
    int nIDC,  
    DISPID dispid,  
    CString& value); 
```  
  
### <a name="parameters"></a>Parametry  
 *pDX*  
 Ukazatel na `CDataExchange` objektu. Rozhraní framework poskytuje tento objekt k vytvoření kontextu dat systému exchange, včetně jeho směr.  
  
 *nIDC*  
 ID ovládacího prvku OLE v dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku.  
  
 *dispID*  
 Odesílání ID vlastnosti ovládacího prvku.  
  
 *value*  
 Odkaz na členské proměnné dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, ke které se vyměňují data.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  

### <a name="requirements"></a>Požadavky  
  **Záhlaví** afxdisp.h
    
## <a name="see-also"></a>Viz také  
 [Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
