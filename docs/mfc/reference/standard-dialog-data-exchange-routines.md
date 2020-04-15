---
title: Rutiny výměny dat standardního dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 83d4a66cd3ec41008506b55f0b351fd9bcbc24b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372933"
---
# <a name="standard-dialog-data-exchange-routines"></a>Rutiny výměny dat standardního dialogového okna

Toto téma obsahuje seznam rutin standardní výměny dialogových dat (DDX) používaných pro běžné ovládací prvky dialogového okna knihovny MFC.

> [!NOTE]
> Standardní rutiny výměny dialogových dat jsou definovány v souboru záhlaví afxdd_.h. Aplikace by však měly obsahovat afxwin.h.

### <a name="ddx-functions"></a>Funkce DDX

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Inicializuje nebo načte index aktuálního výběru ovládacího prvku pole se seznamem.|
|[DDX_CBString](#ddx_cbstring)|Inicializuje nebo načte aktuální obsah editačního pole ovládacího prvku pole se seznamem.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Inicializuje nebo načte aktuální obsah editačního pole ovládacího prvku pole se seznamem.|
|[DDX_Check](#ddx_check)|Inicializuje nebo načte aktuální stav ovládacího prvku zaškrtávacího políčka.|
|[DDX_Control](#ddx_control)|Podtřídy daného ovládacího prvku v dialogovém okně.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Inicializuje nebo načte data data a/nebo čas ovládacího prvku pro výběr data a času.|
|[DDX_IPAddress](#ddx_ipaddress)|Inicializuje nebo načte aktuální hodnotu ovládacího prvku IP adresy.|
|[DDX_LBIndex](#ddx_lbindex)|Inicializuje nebo načte index aktuálního výběru ovládacího prvku seznamu.|
|[DDX_LBString](#ddx_lbstring)|Inicializuje nebo načte aktuální výběr v rámci ovládacího prvku seznamu.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Inicializuje nebo načte aktuální výběr v rámci ovládacího prvku seznamu.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Vytvoří ovládací prvek .NET odpovídající ID prostředku ovládacího prvku.|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Inicializuje nebo načte aktuální hodnotu ovládacího prvku kalendáře měsíce.|
|[DDX_Radio](#ddx_radio)|Inicializuje nebo načte 0-založený index rádiového řízení, který je aktuálně kontrolován v rámci skupiny rádiového řízení.|
|[DDX_Scroll](#ddx_scroll)|Inicializuje nebo načte aktuální pozici palce ovládacího prvku posouvání.|
|[DDX_Slider](#ddx_slider)|Inicializuje nebo načte aktuální pozici palce ovládacího prvku posuvníku.|
|[DDX_Text](#ddx_text)|Inicializuje nebo načte aktuální hodnotu ovládacího prvku pro úpravy.|

## <a name="ddx_cbindex"></a><a name="ddx_cbindex"></a>DDX_CBIndex

Funkce `DDX_CBIndex` spravuje přenos **dat int** mezi ovládacím prvkem pole se seznamem v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem **int** dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku.

*Index*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt ovládacího prvku, se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při `DDX_CBIndex` volání je *index* nastaven na index aktuálního výběru pole se seznamem. Pokud není vybrána žádná položka, *index* je nastaven na 0.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_cbstring"></a><a name="ddx_cbstring"></a>DDX_CBString

Funkce `DDX_CBString` spravuje přenos `CString` dat mezi ovládacím prvkem upravit ovládací prvek pole se seznamem v dialogovém `CString` okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt ovládacího prvku, se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při `DDX_CBString` volání je *hodnota* nastavena na aktuální výběr pole se seznamem. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec nulové délky.

> [!NOTE]
> Pokud je pole se seznamem rozevírací seznam, je vyměněná hodnota omezena na 255 znaků.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_cbstringexact"></a><a name="ddx_cbstringexact"></a>DDX_CBStringExact

Funkce `DDX_CBStringExact` spravuje přenos `CString` dat mezi ovládacím prvkem upravit ovládací prvek pole se seznamem v dialogovém `CString` okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt ovládacího prvku, se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při `DDX_CBStringExact` volání je *hodnota* nastavena na aktuální výběr pole se seznamem. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec nulové délky.

> [!NOTE]
> Pokud je pole se seznamem rozevírací seznam, je vyměněná hodnota omezena na 255 znaků.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_check"></a><a name="ddx_check"></a>DDX_Check

Funkce `DDX_Check` spravuje přenos **int** dat mezi ovládacím prvkem zaškrtávacího políčka v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem **int** dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku zaškrtávacího políčka přidruženého k vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt ovládacího prvku, se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při `DDX_Check` volání je *hodnota* nastavena na aktuální stav ovládacího prvku zaškrtávacího políčka. Seznam možných hodnot stavu naleznete [v tématu BM_GETCHECK](/windows/win32/Controls/bm-getcheck) v sadě Windows SDK.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_control"></a><a name="ddx_control"></a>DDX_Control

Funkce `DDX_Control` podřcovává ovládací prvek, určený *nIDC*, dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*nIDC*<br/>
ID prostředku ovládacího prvku, který má být podtřídou.

*rControl*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objektovládacího zobrazení související se zadaným ovládacím prvkem.

### <a name="remarks"></a>Poznámky

Objekt *pDX* je dodáván rámci `DoDataExchange` při volání funkce. Proto `DDX_Control` by měla být volána `DoDataExchange`pouze v rámci přepsání .

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_datetimectrl"></a><a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl

Funkce `DDX_DateTimeCtrl` spravuje přenos dat a/nebo času mezi ovládacím prvkem výběru data a času [(CDateTimeCtrl)](../../mfc/reference/cdatetimectrl-class.md)v dialogovém okně nebo objektu zobrazení formuláře a datovým členem [CTime](../../atl-mfc-shared/reference/ctime-class.md) nebo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) dialogového okna nebo objektu zobrazení formuláře.

```cpp
void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru. Tento objekt není nutné odstraňovat.

*nIDC*<br/>
ID prostředku ovládacího prvku pro výběr data a času přidruženého k členské proměnné.

*Hodnotu*<br/>
V prvních dvou verzích odkaz `CTime` na `COleDateTime` proměnnou nebo člen, dialogové okno, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, se kterým se vyměňují data. Ve třetí verzi odkaz na `CString` objekt zobrazení ovládacího prvku člena dat.

### <a name="remarks"></a>Poznámky

Při `DDX_DateTimeCtrl` volání je *hodnota* nastavena na aktuální stav ovládacího prvku výběru data a času nebo je ovládací prvek nastaven na *hodnotu*v závislosti na směru výměny.

Ve třetí verzi `DDX_DateTimeCtrl` výše spravuje přenos `CString` dat mezi ovládacím prvkem data a datovým členem [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu zobrazení ovládacího prvku. Řetězec je formátován pomocí aktuálního národního prostředí pravidla pro formátování dat a časů.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_managedcontrol"></a><a name="ddx_managedcontrol"></a>DDX_ManagedControl

Vytvoří ovládací prvek .NET odpovídající ID prostředku ovládacího prvku.

### <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [třídy CDataExchange.](cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku přidruženého k vlastnosti ovládacího prvku.

*Ovládací prvek*<br/>
Odkaz na objekt [třídy CWinFormsControl.](cwinformscontrol-class.md)

### <a name="remarks"></a>Poznámky

`DDX_ManagedControl`volá [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) k vytvoření ovládacího prvku odpovídajícího ID ovládacího prvku prostředku. Slouží `DDX_ManagedControl` k vytvoření ovládacích prvků z ID prostředků v [cdialog::OnInitDialog](cdialog-class.md#oninitdialog). Pro výměnu dat není nutné používat funkce DDX/DDV s ovládacími prvky Windows Forms.

Další informace naleznete v [tématu How to: Do DDX/DDV Data Binding with Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms.h

## <a name="ddx_ipaddress"></a><a name="ddx_ipaddress"></a>DDX_IPAddress

Funkce `DDX_IPAddress` spravuje přenos dat mezi ovládacím prvkem IP Address a datovým členem objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku IP Adresa přidruženého k vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na dword obsahující hodnotu čtyř polí ovládacího prvku IP Address. Pole jsou vyplněna nebo přečtena následujícím způsobem.

|Pole|Bity obsahující hodnotu pole|
|-----------|-------------------------------------|
|3|0 až 7|
|2|8 až 15|
|1|16 až 23|
|0|24 až 31|

Použijte [Win32 IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) číst hodnotu nebo použijte [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress) k vyplnění hodnoty. Tyto zprávy jsou popsány v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Při `DDX_IPAddress` volání *je hodnota* buď číst z ovládacího prvku IP Adresa nebo *hodnota* je zapsána do ovládacího prvku, v závislosti na směru výměny.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_lbindex"></a><a name="ddx_lbindex"></a>DDX_LBIndex

Funkce `DDX_LBIndex` spravuje přenos **int** dat mezi ovládacím prvkem seznamu v dialogovém okně, zobrazeníformuláře nebo objektu zobrazení ovládacího prvku a datovým členem **int** dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku.

*Index*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt ovládacího prvku, se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při `DDX_LBIndex` volání je *index* nastaven na index aktuálního výběru seznamu. Pokud není vybrána žádná položka, *index* je nastaven na -1.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_lbstring"></a><a name="ddx_lbstring"></a>DDX_LBString

Funkce `DDX_LBString` spravuje přenos `CString` dat mezi ovládacím prvkem seznamu v dialogovém okně, zobrazení `CString` formuláře nebo objektu zobrazení ovládacího prvku a datovým členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt ovládacího prvku, se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Když `DDX_LBString` je volána k přenosu dat do ovládacího prvku seznamu, je vybrána první položka v ovládacím prvku, jehož počáteční shoda *odpovídá hodnotě.* (Chcete-li shodovat s celou položkou, nikoli pouze s předponou, použijte [DDX_LBStringExact](#ddx_lbstringexact).) Pokud nejsou žádné shody, jsou vybrány žádné položky. Shoda je malá a velká písmena.

Když `DDX_LBString` je volána k přenosu dat z ovládacího prvku seznamu, *hodnota* je nastavena na aktuální výběr seznamu. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec nulové délky.

> [!NOTE]
> Pokud je seznam rozevíracím seznamem, je vyměněná hodnota omezena na 255 znaků.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_lbstringexact"></a><a name="ddx_lbstringexact"></a>DDX_LBStringExact

Funkce `DDX_CBStringExact` spravuje přenos `CString` dat mezi ovládacím prvkem upravit ovládací prvek seznamu v dialogovém okně, `CString` zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt ovládacího prvku, se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Když `DDX_LBStringExact` je volána k přenosu dat do ovládacího prvku seznamu, je vybrána první položka v ovládacím prvku, která odpovídá *hodnotě.* (Chcete-li porovnat pouze předponu než celou položku, použijte [DDX_LBString](#ddx_lbstring).) Pokud nejsou žádné shody, jsou vybrány žádné položky. Shoda je malá a velká písmena.

Když `DDX_CBStringExact` je volána k přenosu dat z ovládacího prvku seznamu, *hodnota* je nastavena na aktuální výběr seznamu. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec nulové délky.

> [!NOTE]
> Pokud je seznam rozevíracím seznamem, je vyměněná hodnota omezena na 255 znaků.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_monthcalctrl"></a><a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl

Funkce `DDX_MonthCalCtrl` spravuje přenos dat data mezi ovládacím prvkem kalendáře měsíce [(CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem [CTime](../../atl-mfc-shared/reference/ctime-class.md) nebo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru. Tento objekt není nutné odstraňovat.

*nIDC*<br/>
ID zdroje ovládacího prvku kalendáře měsíce přidruženého k členské proměnné.

*Hodnotu*<br/>
Odkaz na `CTime` proměnnou nebo `COleDateTime` člen dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Ovládací prvek spravuje pouze hodnotu data. Časová pole v objektu time jsou nastavena tak, aby odrážela čas vytvoření ovládacího `CMonthCalCtrl::SetCurSel`okna nebo jakýkoli čas nastavený v ovládacím prvku s voláním .

Při `DDX_MonthCalCtrl` volání je *hodnota* nastavena na aktuální stav ovládacího prvku kalendáře měsíce.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_radio"></a><a name="ddx_radio"></a>DDX_Radio

Funkce `DDX_Radio` spravuje přenos **int** dat mezi skupinou rádiového ovládacího prvku v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku a datovým členem **int** dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku. Hodnota datového prvku **int** je určena podle toho, které přepínač ve skupině je vybráno.

```cpp
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku prvního rádiového ovládacího prvku ve skupině.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, zobrazení formuláře nebo objekt ovládacího prvku, se kterým se vyměňují data.

### <a name="remarks"></a>Poznámky

Při `DDX_Radio` volání je *hodnota* nastavena na aktuální stav skupiny rádiového řízení. Hodnota je nastavena jako 0-založený index rádiového řízení, který je aktuálně zaškrtnut, nebo -1, pokud nejsou kontrolovány žádné rádiové ovládací prvky.

Například v případě, že je zaškrtnuto první přepínací tlačítko ve skupině (tlačítko s WS_GROUP stylem), je hodnota **int** member 0 a tak dále.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_scroll"></a><a name="ddx_scroll"></a>DDX_Scroll

Funkce `DDX_Scroll` spravuje přenos **int** dat mezi ovládacím prvkem posuvníku v dialogovém okně, zobrazeníformuláře nebo objektu zobrazení ovládacího prvku a datovým členem **int** dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na `CDataExchange` objekt. Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku posuvníku přidruženého k vlastnosti ovládacího prvku.

*Hodnotu*<br/>
Odkaz na člennou proměnnou dialogového okna, objektzobrazení formuláře nebo ovládacího prvku, se kterým jsou data vyměňována.

### <a name="remarks"></a>Poznámky

Při `DDX_Scroll` volání je *hodnota* nastavena na aktuální pozici palce ovládacího prvku. Další informace o hodnotách přidružených k aktuální pozici ovládacího prvku palce, naleznete v tématu [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) v sadě Windows SDK.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_slider"></a><a name="ddx_slider"></a>DDX_Slider

Funkce `DDX_Slider` spravuje přenos **int** dat mezi ovládacím prvkem posuvníku v dialogovém okně nebo **formulářovém** zobrazení a datovým členem dialogového okna nebo objektu zobrazení formuláře.

```cpp
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku posuvníku.

*Hodnotu*<br/>
Odkaz na hodnotu, která má být vyměněna. Tento parametr uchovává nebo nastavuje aktuální polohu ovládacího prvku posuvníku.

### <a name="remarks"></a>Poznámky

Při `DDX_Slider` volání je *hodnota* nastavena na aktuální pozici palce ovládacího prvku nebo hodnota obdrží pozici, v závislosti na směru výměny.

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md). Informace o ovládacích prvcích jezdce naleznete [v tématu Použití kláves CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="ddx_text"></a><a name="ddx_text"></a>DDX_Text

Funkce `DDX_Text` spravuje přenos **int**, **UINT**, **long** `CString`, DWORD, , **float**nebo **double** data mezi ovládacím prvkem pro úpravy v dialogovém okně, zobrazení formuláře nebo zobrazení ovládacího prvku a datovým členem [CString](../../atl-mfc-shared/reference/cstringt-class.md) dialogového okna, zobrazení formuláře nebo objektu zobrazení ovládacího prvku.

```cpp
void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    short& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    int& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    UINT& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    long& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    CString& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    float& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    double& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>Parametry

*Pdx*<br/>
Ukazatel na objekt [CDataExchange.](../../mfc/reference/cdataexchange-class.md) Rámec poskytuje tento objekt k vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku pro úpravy v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*Hodnotu*<br/>
Odkaz na datový člen v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku. Datový typ *hodnoty* závisí na tom, které `DDX_Text` z přetížených verzí používáte.

### <a name="remarks"></a>Poznámky

Další informace o ddx naleznete [v tématu Dialog Data Exchange and Validation](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdd_.h

## <a name="see-also"></a>Viz také

[Rutiny ověřování dat standardního dialogového okna](standard-dialog-data-validation-routines.md)<br/>
[Makra a globální](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
