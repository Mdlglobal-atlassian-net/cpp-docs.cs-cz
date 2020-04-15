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
ms.openlocfilehash: 61a5983eec13902ed4b0e397e3befca4860977d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365770"
---
# <a name="dialog-data-exchange-functions-for-ole-controls"></a>Funkce výměny dat dialogových oken pro ovládací prvky OLE

Toto téma obsahuje seznam funkcí DDX_OC používaných k výměně dat mezi vlastností ovládacího prvku OLE v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

### <a name="ddx_oc-functions"></a>DDX_OC funkce

|||
|-|-|
|[DDX_OCBool](#ddx_ocbool)|Spravuje přenos dat **BOOL** mezi vlastností ovládacího prvku OLE a datovým členem **BOOL.**|
|[DDX_OCBoolRO](#ddx_ocboolro)|Spravuje přenos dat **BOOL** mezi vlastností ole ovládacího prvku jen pro čtení a datovým členem **BOOL.**|
|[DDX_OCColor](#ddx_occolor)|Spravuje přenos **dat OLE_COLOR** mezi vlastností ovládacího prvku OLE a **OLE_COLOR** datovým členem.|
|[DDX_OCColorRO](#ddx_occolorro)|Spravuje přenos **OLE_COLOR** dat mezi vlastností ole ovládacího prvku jen pro čtení a **OLE_COLOR** datovým členem.|
|[DDX_OCFloat](#ddx_ocfloat)|Spravuje přenos **plovoucích** (nebo **dvojitých)** dat mezi vlastností ovládacího prvku OLE a **plovoucím** (nebo **dvojitým)** datovým členem.|
|[DDX_OCFloatRO](#ddx_ocfloatro)|Spravuje přenos **plovoucích** (nebo **dvojitých)** dat mezi vlastností ole ovládacího prvku jen pro čtení a **plovoucím** (nebo **dvojitým)** datovým členem.|
|[DDX_OCInt](#ddx_ocint)|Spravuje přenos **int** (nebo **dlouhých)** dat mezi vlastností ovládacího prvku OLE a datovým členem **int** (nebo **long).**|
|[DDX_OCIntRO](#ddx_ocintro)|Spravuje přenos **int** (nebo **dlouhých)** dat mezi vlastností ole ovládacího prvku OLE jen pro čtení a datovým členem **int** (nebo **long).**|
|[DDX_OCShort](#ddx_ocshort)|Spravuje přenos **krátkých** dat mezi vlastností ovládacího prvku OLE a **krátkým** datovým členem.|
|[DDX_OCShortRO](#ddx_ocshortro)|Spravuje přenos **krátkých** dat mezi vlastností ole ovládacího prvku jen pro čtení a **krátkým** datovým členem.|
|[DDX_OCText](#ddx_octext)|Spravuje přenos dat **CString** mezi vlastností ovládacího prvku OLE a datovým členem **CString.**|
|[DDX_OCTextRO](#ddx_octextro)|Spravuje přenos dat **CString** mezi vlastností ole ovládacího prvku jen pro čtení a datovým členem **CString.**|

## <a name="ddx_ocbool"></a><a name="ddx_ocbool"></a>DDX_OCBool

Funkce `DDX_OCBool` spravuje přenos dat **BOOL** mezi vlastností ovládacího prvku OLE v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem datového prvku **BOOL** dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_OCBool(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví:** afxdisp.h

## <a name="ddx_ocboolro"></a><a name="ddx_ocboolro"></a>DDX_OCBoolRO

Funkce `DDX_OCBoolRO` spravuje přenos dat **BOOL** mezi vlastností ovládacího prvku OLE jen pro čtení v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem datového prvku **BOOL** dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_OCBoolRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    BOOL& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="ddx_occolor"></a><a name="ddx_occolor"></a>DDX_OCColor

Funkce `DDX_OCColor` spravuje přenos dat OLE_COLOR mezi vlastností ovládacího prvku OLE v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a OLE_COLOR datovým členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_OCColor(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="ddx_occolorro"></a><a name="ddx_occolorro"></a>DDX_OCColorRO

Funkce `DDX_OCColorRO` spravuje přenos OLE_COLOR dat mezi vlastností ovládacího prvku OLE jen pro čtení v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a OLE_COLOR datovým členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_OCColorRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    OLE_COLOR& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="ddx_ocfloat"></a><a name="ddx_ocfloat"></a>DDX_OCFloat

Funkce `DDX_OCFloat` spravuje přenos **plovoucích** (nebo **dvojitých)** dat mezi vlastností ovládacího prvku OLE v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a **plovoucím** (nebo **dvojitým)** datovým členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
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

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="ddx_ocfloatro"></a><a name="ddx_ocfloatro"></a>DDX_OCFloatRO

Funkce `DDX_OCFloatRO` spravuje přenos **plovoucích** (nebo **dvojitých)** dat mezi vlastností ovládacího prvku OLE jen pro čtení v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a **plovoucím** (nebo **dvojitým)** datovým členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
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

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="ddx_ocint"></a><a name="ddx_ocint"></a>DDX_OCInt

Funkce `DDX_OCInt` spravuje přenos **int** (nebo **dlouhých)** dat mezi vlastností ovládacího prvku OLE v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem **int** (nebo **long)** dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
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

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="ddx_ocintro"></a><a name="ddx_ocintro"></a>DDX_OCIntRO

Funkce `DDX_OCIntRO` spravuje přenos **int** (nebo **dlouhých)** dat mezi vlastností ovládacího prvku OLE jen pro čtení v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem **int** (nebo **long)** dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
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

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="ddx_ocshort"></a><a name="ddx_ocshort"></a>DDX_OCShort

Funkce `DDX_OCShort` spravuje přenos krátkých dat mezi vlastností ovládacího prvku OLE v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a krátkým datovým členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_OCShort(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="ddx_ocshortro"></a><a name="ddx_ocshortro"></a>DDX_OCShortRO

Funkce `DDX_OCShortRO` spravuje přenos krátkých dat mezi vlastností ovládacího prvku OLE jen pro čtení v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a krátkým datovým členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_OCShortRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    short& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="ddx_octext"></a><a name="ddx_octext"></a>DDX_OCText

Funkce **DDX_OCText** spravuje přenos dat **CString** mezi vlastností ovládacího prvku OLE v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem **CString** dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_OCText(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt **CDataExchange.** Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="ddx_octextro"></a><a name="ddx_octextro"></a>DDX_OCTextRO

Funkce `DDX_OCTextRO` spravuje přenos `CString` dat mezi vlastností ovládacího prvku OLE jen pro čtení v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým `CString` členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_OCTextRO(
    CDataExchange* pDX,
    int nIDC,
    DISPID dispid,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku OLE v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Dispid*<br/>
ID odeslání vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdisp.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
