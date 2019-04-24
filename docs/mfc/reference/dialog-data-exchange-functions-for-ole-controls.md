---
title: Funkce výměny dat dialogových oken pro ovládací prvky OLE
ms.date: 11/04/2016
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
helpviewer_keywords:
- OLE controls [MFC], DDX functions
- DDX (dialog data exchange), OLE support
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
ms.openlocfilehash: df96d44cefeb15d89653538c3006d109a97a21a7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322563"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Funkce výměny dat dialogových oken pro ovládací prvky OLE

Toto téma obsahuje seznam DDX_OC funkce používané k výměně dat mezi vlastnost ovládacího prvku OLE v dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku a datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

### <a name="ddxoc-functions"></a>DDX_OC Functions

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|Spravuje přenos **BOOL** data mezi vlastnost ovládacího prvku OLE a **BOOL** datový člen.|
|[DDX_OCBoolRO](#ddx_ocboolro)|Spravuje přenos **BOOL** data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **BOOL** datový člen.|
|[DDX_OCColor](#ddx_occolor)|Spravuje přenos **OLE_COLOR** data mezi vlastnost ovládacího prvku OLE a **OLE_COLOR** datový člen.|
|[DDX_OCColorRO](#ddx_occolorro)|Spravuje přenos **OLE_COLOR** data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **OLE_COLOR** datový člen.|
|[DDX_OCFloat](#ddx_ocfloat)|Spravuje přenos **float** (nebo **double**) data mezi vlastnost ovládacího prvku OLE a **float** (nebo **double**) datový člen.|
|[DDX_OCFloatRO](#ddx_ocfloatro)|Spravuje přenos **float** (nebo **double**) data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **float** (nebo **double**) dat člen.|
|[DDX_OCInt](#ddx_ocint)|Spravuje přenos **int** (nebo **dlouhé**) data mezi vlastnost ovládacího prvku OLE a **int** (nebo **dlouhé**) datový člen.|
|[DDX_OCIntRO](#ddx_ocintro)|Spravuje přenos **int** (nebo **dlouhé**) data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **int** (nebo **dlouhé**) datový člen.|
|[DDX_OCShort](#ddx_ocshort)|Spravuje přenos **krátký** data mezi vlastnost ovládacího prvku OLE a **krátký** datový člen.|
|[DDX_OCShortRO](#ddx_ocshortro)|Spravuje přenos **krátký** data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **krátký** datový člen.|
|[DDX_OCText](#ddx_octext)|Spravuje přenos **CString** data mezi vlastnost ovládacího prvku OLE a **CString** datový člen.|
|[DDX_OCTextRO](#ddx_octextro)|Spravuje přenos **CString** data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **CString** datový člen.|

##  <a name="ddx_ocbool"></a>  DDX_OCBool

`DDX_OCBool` Funkce spravuje přenos **BOOL** zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi vlastnost ovládacího prvku OLE v dialogovém okně a **BOOL** datový člen dialogu formulářového zobrazení, nebo objekt ovládacího prvku zobrazení.

```
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header:** afxdisp.h

##  <a name="ddx_ocboolro"></a>  DDX_OCBoolRO

`DDX_OCBoolRO` Funkce spravuje přenos **BOOL** zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi ovládacího prvku OLE v dialogovém okně vlastnosti jen pro čtení a **BOOL** datový člen dialogovém okně Formulářové zobrazení, nebo objekt ovládacího prvku zobrazení.

```
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="ddx_occolor"></a>  DDX_OCColor

`DDX_OCColor` Funkce spravuje přenos dat OLE_COLOR mezi vlastnost ovládacího prvku OLE v dialogovém okně zobrazit formulář nebo ovládací prvek zobrazení objektu a datový člen OLE_COLOR dialogového okna, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

```
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="ddx_occolorro"></a>  DDX_OCColorRO

`DDX_OCColorRO` Funkce spravuje přenos dat OLE_COLOR mezi vlastnost jen pro čtení z ovládacího prvku OLE v dialogovém okně zobrazit formulář nebo ovládací prvek zobrazení objektu a datový člen OLE_COLOR dialogového okna, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

```
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="ddx_ocfloat"></a>  Ddx_ocfloat –

`DDX_OCFloat` Funkce spravuje přenos **float** (nebo **double**) zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi vlastnost ovládacího prvku OLE v dialogovém okně a **float** (nebo **double**) datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

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

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="ddx_ocfloatro"></a>  DDX_OCFloatRO

`DDX_OCFloatRO` Funkce spravuje přenos **float** (nebo **double**) zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi ovládacího prvku OLE v dialogovém okně vlastnosti jen pro čtení a  **float** (nebo **double**) datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

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

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="ddx_ocint"></a>  DDX_OCInt

`DDX_OCInt` Funkce spravuje přenos **int** (nebo **dlouhé**) zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi vlastnost ovládacího prvku OLE v dialogovém okně a **int**(nebo **dlouhé**) datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

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

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="ddx_ocintro"></a>  DDX_OCIntRO

`DDX_OCIntRO` Funkce spravuje přenos **int** (nebo **dlouhé**) zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi ovládacího prvku OLE v dialogovém okně vlastnosti jen pro čtení a **int** (nebo **dlouhé**) datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

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

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="ddx_ocshort"></a>  Ddx_ocshort –

`DDX_OCShort` Funkce spravuje přenos krátkého data mezi vlastnost ovládacího prvku OLE v dialogovém okně zobrazit formulář nebo ovládací prvek zobrazení objektu a short – datový člen dialogového okna, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

```
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="ddx_ocshortro"></a>  DDX_OCShortRO

`DDX_OCShortRO` Funkce spravuje přenos krátkého data mezi vlastnost jen pro čtení z ovládacího prvku OLE v dialogovém okně zobrazit formulář nebo ovládací prvek zobrazení objektu a short – datový člen dialogového okna, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

```
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="ddx_octext"></a>  DDX_OCText

**Ddx_octext –** funkce spravuje přenos **CString** zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi vlastnost ovládacího prvku OLE v dialogovém okně a **CString** dat člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

```
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel **CDataExchange** objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

##  <a name="ddx_octextro"></a>  DDX_OCTextRO

`DDX_OCTextRO` Funkce spravuje přenos `CString` zobrazení, nebo objekt zobrazení ovládacího prvku formulář dat mezi ovládacího prvku OLE v dialogovém okně vlastnosti jen pro čtení a `CString` datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

```
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*dispid*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdisp.h

## <a name="see-also"></a>Viz také:

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
