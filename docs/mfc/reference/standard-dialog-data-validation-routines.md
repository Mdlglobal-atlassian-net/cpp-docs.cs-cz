---
title: Rutiny ověřování dat standardního dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 77b08945c99b9e9e2652a40e5710d8c4e89846b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309990"
---
# <a name="standard-dialog-data-validation-routines"></a>Rutiny ověřování dat standardního dialogového okna

Toto téma uvádí rutiny ověřování (DDV) dat standardního dialogového okna pro běžné ovládací prvky dialogového okna knihovny MFC.

> [!NOTE]
>  Rutiny výměny dat standardního dialogového okna jsou definovány v souboru afxdd_.h záhlaví. Ale aplikace by měla obsahovat afxwin.h.

### <a name="ddv-functions"></a>Funkce DDV

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Ověřuje, že počet znaků v hodnotě daný ovládací prvek není delší než daný maximum.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Ověří nepřekročí hodnotu daného ovládacího prvku daný **BAJTŮ** rozsahu.|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Ověřuje, že daný ovládací prvek hodnotu nepřekročí za dané časové období.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Ověří nepřekročí hodnotu daného ovládacího prvku daný **double** rozsahu.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Ověří nepřekročí hodnotu daný ovládací prvek daného **DWORD** rozsahu.|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Ověří nepřekročí hodnotu daného ovládacího prvku daný **float** rozsahu.|
|[DDV_MinMaxInt](#ddv_minmaxint)|Ověří nepřekročí hodnotu daný ovládací prvek daného **int** rozsahu.|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Ověří nepřekročí hodnotu daného ovládacího prvku daný **dlouhé** rozsahu.|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Ověří nepřekročí hodnotu daný ovládací prvek daného **LONGLONG** rozsahu.|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Ověřuje, že hodnota daný ovládací prvek není delší než daný rozsah.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Ověří nepřekročí hodnotu daného ovládacího prvku daný **krátký** rozsahu.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Ověřuje, že hodnota ovládacího prvku posuvník dané spadá do daného rozsahu.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Ověří nepřekročí hodnotu daný ovládací prvek daného **UINT** rozsahu.|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Ověřuje, že hodnota daný ovládací prvek leží mezi dvěma zadanými hodnotami.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Ověří nepřekročí hodnotu daný ovládací prvek daného **ULONGLONG** rozsahu.|

##  <a name="ddv_maxchars"></a>  DDV_MaxChars

Volání `DDV_MaxChars` k ověření, že počet znaků v ovládacím prvku přidružené *hodnotu* nepřekročí *nChars*.

```
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*nChars*<br/>
Maximální povolený počet znaků.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxbyte"></a>  DDV_MinMaxByte

Volání `DDV_MinMaxByte` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

```
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*minVal*<br/>
Minimální hodnotu (typu BYTE) povoleny.

*maxVal*<br/>
Maximální hodnotu (typu BYTE) povoleny.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxdatetime"></a>  DDV_MinMaxDateTime

Volání `DDV_MinMaxDateTime` k ověření, že ovládací prvek hodnotu času a data v výběr data a času ( [atributu CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) přidružené k *refValue* leží mezi *refMinRange*a *refMaxRange*.

```
void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxDateTime(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr. Není nutné odstranit tento objekt.

*refValue*<br/>
Odkaz na [CTime](../../atl-mfc-shared/reference/ctime-class.md) nebo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objekt přidružený k proměnné člena dialogové okno, zobrazení formuláře nebo ovládací prvek zobrazení objektu. Tento objekt obsahuje data, která mají být ověřen.

*refMinRange*<br/>
Minimální povolená hodnota data a času.

*refMaxRange*<br/>
Povolená hodnota maximální datum a čas.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxdouble"></a>  DDV_MinMaxDouble

Volání `DDV_MinMaxDouble` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

```
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*minVal*<br/>
Minimální hodnotu (typu **double**) povoleny.

*maxVal*<br/>
Maximální hodnotu (typu **double**) povoleny.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxdword"></a>  DDV_MinMaxDWord

Volání `DDV_MinMaxDWord` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

```
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*minVal*<br/>
Minimální hodnotu (typu DWORD) povoleny.

*maxVal*<br/>
Maximální hodnotu (typu DWORD) povoleny.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxfloat"></a>  Ddv_minmaxfloat –

Volání `DDV_MinMaxFloat` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

```
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*minVal*<br/>
Minimální hodnotu (typu **float**) povoleny.

*maxVal*<br/>
Maximální hodnotu (typu **float**) povoleny.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxint"></a>  DDV_MinMaxInt

Volání `DDV_MinMaxInt` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

```
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*minVal*<br/>
Minimální hodnotu (typu **int**) povoleny.

*maxVal*<br/>
Maximální hodnotu (typu **int**) povoleny.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxlong"></a>  DDV_MinMaxLong

Volání `DDV_MinMaxLong` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

```
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*minVal*<br/>
Minimální hodnotu (typu **dlouhé**) povoleny.

*maxVal*<br/>
Maximální hodnotu (typu **dlouhé**) povoleny.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxlonglong"></a>  DDV_MinMaxLongLong

Volání `DDV_MinMaxLongLong` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

```
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*minVal*<br/>
Minimální hodnotu (typu LONGLONG) povoleny.

*maxVal*<br/>
Maximální hodnotu (typu LONGLONG) povoleny.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxmonth"></a>  DDV_MinMaxMonth

Volání `DDV_MinMaxMonth` k ověření, že hodnota času a data v měsíčním kalendáři ovládací prvek ( [atributu CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) přidružené k *refValue* leží mezi *refMinRange* a *refMaxRange*.

```
void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    CTime& refValue,
    const CTime* refMinRange,
    const CTime* refMaxRange);

void AFXAPI DDV_MinMaxMonth(
    CDataExchange* pDX,
    COleDateTime& refValue,
    const COleDateTime* refMinRange,
    const COleDateTime* refMaxRange);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*refValue*<br/>
Odkaz na objekt typu `CTime` nebo `COleDateTime` přidružený k členské proměnné dialogového okna, zobrazení formuláře nebo ovládací prvek zobrazení objektu. Tento objekt obsahuje data, která mají být ověřen. Předá MFC to odkazovat při `DDV_MinMaxMonth` je volána.

*refMinRange*<br/>
Minimální povolená hodnota data a času.

*refMaxRange*<br/>
Povolená hodnota maximální datum a čas.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxshort"></a>  DDV_MinMaxShort

Volání `DDV_MinMaxShort` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

```
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*minVal*<br/>
Minimální hodnotu (typu **krátký**) povoleny.

*maxVal*<br/>
Maximální hodnotu (typu **krátký**) povoleny.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxslider"></a>  DDV_MinMaxSlider

Volání `DDV_MinMaxSlider` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

```
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na hodnotu, která má být ověřen. Tento parametr obsahuje nebo nastaví aktuální pozici thumb ovládacího prvku posuvník.

*minVal*<br/>
Minimální povolená hodnota.

*maxVal*<br/>
Maximální povolená hodnota.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md). Informace o ovládacích prvcích posuvníku, naleznete v tématu [používání atributu CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxuint"></a>  DDV_MinMaxUInt

Volání `DDV_MinMaxUInt` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

```
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*minVal*<br/>
Minimální hodnotu (typu UINT) povoleny.

*maxVal*<br/>
Maximální hodnotu (typu UINT) povoleny.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

##  <a name="ddv_minmaxulonglong"></a>  DDV_MinMaxULongLong

Volání `DDV_MinMaxULongLong` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

```
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*minVal*<br/>
Minimální hodnotu (typu ULONGLONG) povoleny.

*maxVal*<br/>
Maximální hodnotu (typu ULONGLONG) povoleny.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_.h

## <a name="ddvminmaxunsigned"></a>DDV_MinMaxUnsigned

Volání `DDV_MinMaxUnsigned` k ověření, že hodnota v ovládacím prvku přidružené *hodnotu* leží mezi *minVal* a *maxVal*.

### <a name="syntax"></a>Syntaxe

```
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel `CDataExchange` objektu. Architektura dodává tento objekt k vytvoření kontextu výměny dat, včetně jeho směr.

*value*<br/>
Odkaz na proměnnou člena dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého se data ověřena.

*minVal*<br/>
Minimální hodnotu (typu **bez znaménka** ) povoleny.

*maxVal*<br/>
Maximální hodnotu (typu **bez znaménka** ) povoleny.

### <a name="remarks"></a>Poznámky

Další informace o DDV najdete v tématu [výměna dat dialogových oken a ověření](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdd_.h

## <a name="see-also"></a>Viz také:

[Rutiny výměny dat standardního dialogového okna](standard-dialog-data-exchange-routines.md)<br/>
[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
