---
title: Rutiny ověřování dat standardního dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data validation routines
ms.assetid: 44dbc222-a897-4949-925e-7660e8964ccd
ms.openlocfilehash: 83e3e215ec8d66321bbac5a4a308b04ef69dc68c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372906"
---
# <a name="standard-dialog-data-validation-routines"></a>Rutiny ověřování dat standardního dialogového okna

Toto téma obsahuje seznam rutin ověřování standardních dialogových dat (DDV) používaných pro běžné ovládací prvky dialogového okna knihovny MFC.

> [!NOTE]
> Standardní rutiny výměny dialogových dat jsou definovány v souboru záhlaví afxdd_.h. Aplikace by však měly obsahovat afxwin.h.

### <a name="ddv-functions"></a>Funkce DDV

|||
|-|-|
|[DDV_MaxChars](#ddv_maxchars)|Ověří počet znaků v dané hodnotě ovládacího prvku nepřekročí dané maximum.|
|[DDV_MinMaxByte](#ddv_minmaxbyte)|Ověří, že daná hodnota ovládacího prvku nepřekročí daný rozsah **BYTE.**|
|[DDV_MinMaxDateTime](#ddv_minmaxdatetime)|Ověří danou hodnotu ovládacího prvku nepřekročí daný časový rozsah.|
|[DDV_MinMaxDouble](#ddv_minmaxdouble)|Ověří danou hodnotu ovládacího prvku nepřekročí daný **dvojitý** rozsah.|
|[DDV_MinMaxDWord](#ddv_minmaxdword)|Ověří danou hodnotu ovládacího prvku nepřekročí daný rozsah **DWORD.**|
|[DDV_MinMaxFloat](#ddv_minmaxfloat)|Ověří danou hodnotu ovládacího prvku nepřekročí daný **rozsah plovoucí.**|
|[DDV_MinMaxInt](#ddv_minmaxint)|Ověří danou hodnotu ovládacího prvku nepřekročí daný **rozsah int.**|
|[DDV_MinMaxLong](#ddv_minmaxlong)|Ověří danou hodnotu ovládacího prvku nepřekročí daný **dlouhý** rozsah.|
|[DDV_MinMaxLongLong](#ddv_minmaxlonglong)|Ověří danou řídicí hodnotu nepřekročí daný rozsah **LONGLONG.**|
|[DDV_MinMaxMonth](#ddv_minmaxmonth)|Ověří, že daná hodnota ovládacího prvku nepřesáhne dané časové období.|
|[DDV_MinMaxShort](#ddv_minmaxshort)|Ověří danou řídicí hodnotu nepřesáhne daný **krátký** rozsah.|
|[DDV_MinMaxSlider](#ddv_minmaxslider)|Ověří danou hodnotu ovládacího prvku posuvníku, která spadá do daného rozsahu.|
|[DDV_MinMaxUInt](#ddv_minmaxuint)|Ověří danou hodnotu ovládacího prvku nepřekročí daný rozsah **UINT.**|
|[DDV_MinMaxUnsigned](#ddv_minmaxuint)|Ověří, že daná řídicí hodnota spadá mezi dvě zadané hodnoty.|
|[DDV_MinMaxULongLong](#ddv_minmaxulonglong)|Ověří danou hodnotu ovládacího prvku nepřekročí daný rozsah **ULONGLONG.**|

## <a name="ddv_maxchars"></a><a name="ddv_maxchars"></a>DDV_MaxChars

Volání `DDV_MaxChars` ověřit, že množství znaků v ovládacím prvku přidružené *k hodnotě* nepřesahuje *nChars*.

```cpp
void AFXAPI DDV_MaxChars(
    CDataExchange* pDX,
    CString const& value,
    int nChars);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*nChars*<br/>
Maximální povolený počet znaků.

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxbyte"></a><a name="ddv_minmaxbyte"></a>DDV_MinMaxByte

Volání `DDV_MinMaxByte` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

```cpp
void AFXAPI DDV_MinMaxByte(
    CDataExchange* pDX,
    BYTE value,
    BYTE minVal,
    BYTE maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*minVal*<br/>
Minimální povolená hodnota (typu BYTE).

*maxVal*<br/>
Maximální povolená hodnota (typu BYTE).

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxdatetime"></a><a name="ddv_minmaxdatetime"></a>DDV_MinMaxDateTime

Volání `DDV_MinMaxDateTime` k ověření, že hodnota čas a datum v ovládacím prvku pro výběr data a času [(CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) přidruženého k *refValue* spadá mezi *refMinRange* a *refMaxRange*.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru. Tento objekt není nutné odstraňovat.

*refValue*<br/>
Odkaz na objekt [CTime](../../atl-mfc-shared/reference/ctime-class.md) nebo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) přidružený k členské proměnné dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku. Tento objekt obsahuje data, která mají být ověřena.

*refMinRange*<br/>
Minimální povolená hodnota data a času.

*refMaxRange*<br/>
Maximální povolená hodnota data a času.

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxdouble"></a><a name="ddv_minmaxdouble"></a>DDV_MinMaxDouble

Volání `DDV_MinMaxDouble` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

```cpp
void AFXAPI DDV_MinMaxDouble(
    CDataExchange* pDX,
    double const& value,
    double minVal,
    double maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*minVal*<br/>
Minimální hodnota (typu **double)** povolena.

*maxVal*<br/>
Maximální povolená hodnota (typu **double).**

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxdword"></a><a name="ddv_minmaxdword"></a>DDV_MinMaxDWord

Volání `DDV_MinMaxDWord` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

```cpp
void AFXAPI DDV_MinMaxDWord(
    CDataExchange* pDX,
    DWORD const& value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*minVal*<br/>
Minimální hodnota (typu DWORD) povolena.

*maxVal*<br/>
Maximální povolená hodnota (typu DWORD).

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxfloat"></a><a name="ddv_minmaxfloat"></a>DDV_MinMaxFloat

Volání `DDV_MinMaxFloat` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

```cpp
void AFXAPI DDV_MinMaxFloat(
    CDataExchange* pDX,
    float value,
    float minVal,
    float maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*minVal*<br/>
Minimální povolená hodnota (typu **float).**

*maxVal*<br/>
Maximální povolená hodnota (typu **float).**

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxint"></a><a name="ddv_minmaxint"></a>DDV_MinMaxInt

Volání `DDV_MinMaxInt` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

```cpp
void AFXAPI DDV_MinMaxInt(
    CDataExchange* pDX,
    int value,
    int minVal,
    int maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*minVal*<br/>
Minimální hodnota (typu **int**) povolena.

*maxVal*<br/>
Maximální povolená hodnota (typu **int).**

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxlong"></a><a name="ddv_minmaxlong"></a>DDV_MinMaxLong

Volání `DDV_MinMaxLong` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

```cpp
void AFXAPI DDV_MinMaxLong(
    CDataExchange* pDX,
    long value,
    long minVal,
    long maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*minVal*<br/>
Minimální povolená hodnota **(typu long).**

*maxVal*<br/>
Maximální povolená maximální hodnota **(typu long).**

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxlonglong"></a><a name="ddv_minmaxlonglong"></a>DDV_MinMaxLongLong

Volání `DDV_MinMaxLongLong` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

```cpp
void AFXAPI DDV_MinMaxLongLong(
    CDataExchange* pDX,
    LONGLONG value,
    LONGLONG minVal,
    LONGLONG maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*minVal*<br/>
Minimální hodnota (typu LONGLONG) povolena.

*maxVal*<br/>
Maximální povolená hodnota (typu LONGLONG).

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxmonth"></a><a name="ddv_minmaxmonth"></a>DDV_MinMaxMonth

Volání `DDV_MinMaxMonth` k ověření, že hodnota time/date v ovládacím prvku kalendáře měsíce ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) spojená s *refValue* spadá mezi *refMinRange* a *refMaxRange*.

```cpp
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

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*refValue*<br/>
Odkaz na objekt typu `CTime` `COleDateTime` nebo přidružený k členské proměnné objektu dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku. Tento objekt obsahuje data, která mají být ověřena. Knihovna MFC `DDV_MinMaxMonth` předá tento odkaz, když je volána.

*refMinRange*<br/>
Minimální povolená hodnota data a času.

*refMaxRange*<br/>
Maximální povolená hodnota data a času.

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxshort"></a><a name="ddv_minmaxshort"></a>DDV_MinMaxShort

Volání `DDV_MinMaxShort` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

```cpp
void AFXAPI DDV_MinMaxShort(
    CDataExchange* pDX,
    short value,
    short minVal,
    short maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*minVal*<br/>
Minimální povolená hodnota **(typu krátká).**

*maxVal*<br/>
Maximální povolená maximální hodnota **(typu krátká).**

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxslider"></a><a name="ddv_minmaxslider"></a>DDV_MinMaxSlider

Volání `DDV_MinMaxSlider` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

```cpp
void AFXAPI DDV_MinMaxSlider(
    CDataExchange* pDX,
    DWORD value,
    DWORD minVal,
    DWORD maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na hodnotu, která má být ověřena. Tento parametr uchovává nebo nastavuje aktuální pozici palce ovládacího prvku posuvníku.

*minVal*<br/>
Minimální povolená hodnota.

*maxVal*<br/>
Maximální povolená hodnota.

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Informace o ovládacích prvcích jezdce naleznete [v tématu Použití kláves CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxuint"></a><a name="ddv_minmaxuint"></a>DDV_MinMaxUInt

Volání `DDV_MinMaxUInt` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

```cpp
void AFXAPI DDV_MinMaxUInt(
    CDataExchange* pDX,
    UINT value,
    UINT minVal,
    UINT maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*minVal*<br/>
Minimální povolená hodnota (typu UINT).

*maxVal*<br/>
Maximální povolená hodnota (typu UINT).

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxulonglong"></a><a name="ddv_minmaxulonglong"></a>DDV_MinMaxULongLong

Volání `DDV_MinMaxULongLong` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

```cpp
void AFXAPI DDV_MinMaxULongLong(
    CDataExchange* pDX,
    ULONGLONG value,
    ULONGLONG  minVal ,
    ULONGLONG  maxVal);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*minVal*<br/>
Minimální hodnota (typu ULONGLONG) povolena.

*maxVal*<br/>
Maximální povolená hodnota (typu ULONGLONG).

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddv_minmaxunsigned"></a>DDV_MinMaxUnsigned

Volání `DDV_MinMaxUnsigned` k ověření, že hodnota v ovládacím prvku přidružené k *hodnotě* spadá mezi *minVal* a *maxVal*.

### <a name="syntax"></a>Syntaxe

```cpp
   void AFXAPI DDV_MinMaxUnsigned(
       CDataExchange* pDX,
       unsigned value,
       unsigned minVal,
       unsigned maxVal );
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, pomocí kterého jsou data ověřena.

*minVal*<br/>
Minimální hodnota (typu **neznaménka)** povolena.

*maxVal*<br/>
Maximální povolená maximální hodnota (typu **neznaménka).**

### <a name="remarks"></a>Poznámky

Další informace o ddv naleznete [v tématu Dialog Data Exchange and Validation](../dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdd_.h

## <a name="see-also"></a>Viz také

[Rutiny výměny dat standardního dialogového okna](standard-dialog-data-exchange-routines.md)<br/>
[Makra a globální](mfc-macros-and-globals.md)<br/>
[DDX_Slider](standard-dialog-data-exchange-routines.md#ddx_slider)<br/>
[DDX_FieldSlider](dialog-data-exchange-functions-for-crecordview-and-cdaorecordview.md#ddx_fieldslider)
