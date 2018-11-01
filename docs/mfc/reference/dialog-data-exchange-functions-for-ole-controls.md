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
ms.openlocfilehash: 5d330d8dd423927a3f4abbe6475a8d6219fa9af2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531245"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Funkce výměny dat dialogových oken pro ovládací prvky OLE

Toto téma obsahuje seznam DDX_OC funkce používané k výměně dat mezi vlastnost ovládacího prvku OLE v dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku a datový člen dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu.

### <a name="ddxoc-functions"></a>Funkce DDX_OC

|||
|-|-|
|[Ddx_ocbool –](#ddx_ocbool)|Spravuje přenos **BOOL** data mezi vlastnost ovládacího prvku OLE a **BOOL** datový člen.|
|[Ddx_ocboolro –](#ddx_ocboolro)|Spravuje přenos **BOOL** data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **BOOL** datový člen.|
|[Ddx_occolor –](#ddx_occolor)|Spravuje přenos **OLE_COLOR** data mezi vlastnost ovládacího prvku OLE a **OLE_COLOR** datový člen.|
|[Ddx_occolorro –](#ddx_occolorro)|Spravuje přenos **OLE_COLOR** data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **OLE_COLOR** datový člen.|
|[Ddx_ocfloat –](#ddx_ocfloat)|Spravuje přenos **float** (nebo **double**) data mezi vlastnost ovládacího prvku OLE a **float** (nebo **double**) datový člen.|
|[Ddx_ocfloatro –](#ddx_ocfloatro)|Spravuje přenos **float** (nebo **double**) data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **float** (nebo **double**) dat člen.|
|[Ddx_ocint –](#ddx_ocint)|Spravuje přenos **int** (nebo **dlouhé**) data mezi vlastnost ovládacího prvku OLE a **int** (nebo **dlouhé**) datový člen.|
|[Ddx_ocintro –](#ddx_ocintro)|Spravuje přenos **int** (nebo **dlouhé**) data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **int** (nebo **dlouhé**) datový člen.|
|[Ddx_ocshort –](#ddx_ocshort)|Spravuje přenos **krátký** data mezi vlastnost ovládacího prvku OLE a **krátký** datový člen.|
|[Ddx_ocshortro –](#ddx_ocshortro)|Spravuje přenos **krátký** data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **krátký** datový člen.|
|[Ddx_octext –](#ddx_octext)|Spravuje přenos **CString** data mezi vlastnost ovládacího prvku OLE a **CString** datový člen.|
|[Ddx_octextro –](#ddx_octextro)|Spravuje přenos **CString** data mezi jen pro čtení vlastnosti ovládacího prvku OLE a **CString** datový člen.|

##  <a name="ddx_ocbool"></a>  Ddx_ocbool –

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

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví:** afxdisp.h

##  <a name="ddx_ocboolro"></a>  Ddx_ocboolro –

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

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="ddx_occolor"></a>  Ddx_occolor –

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

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="ddx_occolorro"></a>  Ddx_occolorro –

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

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

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

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="ddx_ocfloatro"></a>  Ddx_ocfloatro –

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

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="ddx_ocint"></a>  Ddx_ocint –

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

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="ddx_ocintro"></a>  Ddx_ocintro –

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

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

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

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="ddx_ocshortro"></a>  Ddx_ocshortro –

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

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="ddx_octext"></a>  Ddx_octext –

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
Ukazatel **cdataexchange –** objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářové zobrazení nebo objekt ovládacího prvku zobrazení.

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

##  <a name="ddx_octextro"></a>  Ddx_octextro –

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

*identifikátor DISPID*<br/>
ID odbavení vlastnost ovládacího prvku.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo ovládacího prvku zobrazení objektu, pomocí kterého se vyměňují data.

### <a name="remarks"></a>Poznámky

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdisp.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
