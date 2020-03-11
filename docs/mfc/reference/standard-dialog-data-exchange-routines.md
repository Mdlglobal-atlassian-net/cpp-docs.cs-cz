---
title: Rutiny výměny dat standardního dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 47586f9cff0fcbe2cd7bad31f3d93fed08190830
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865156"
---
# <a name="standard-dialog-data-exchange-routines"></a>Rutiny výměny dat standardního dialogového okna

Toto téma obsahuje seznam standardních rutin pro výměnu dat dialogových oken, které se používají pro běžné ovládací prvky dialogového okna MFC.

> [!NOTE]
>  Standardní rutiny výměny dat dialogových oken jsou definovány v hlavičkovém souboru afxdd_. h. Aplikace by však měly zahrnovat afxwin. h.

### <a name="ddx-functions"></a>DDX Functions

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Inicializuje nebo načte index aktuálního výběru ovládacího prvku pole se seznamem.|
|[DDX_CBString](#ddx_cbstring)|Inicializuje nebo načte aktuální obsah pole pro úpravy ovládacího prvku pole se seznamem.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Inicializuje nebo načte aktuální obsah pole pro úpravy ovládacího prvku pole se seznamem.|
|[DDX_Check](#ddx_check)|Inicializuje nebo načte aktuální stav ovládacího prvku zaškrtávací políčko.|
|[DDX_Control](#ddx_control)|Roztřídí daný ovládací prvek v rámci dialogového okna.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Inicializuje nebo načte data nebo čas ovládacího prvku pro výběr data a času.|
|[DDX_IPAddress](#ddx_ipaddress)|Inicializuje nebo načte aktuální hodnotu ovládacího prvku IP adresa.|
|[DDX_LBIndex](#ddx_lbindex)|Inicializuje nebo načte index aktuálního výběru ovládacího prvku seznam.|
|[DDX_LBString](#ddx_lbstring)|Inicializuje nebo načte aktuální výběr v rámci ovládacího prvku seznamu.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Inicializuje nebo načte aktuální výběr v rámci ovládacího prvku seznamu.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Vytvoří ovládací prvek .NET, který odpovídá ID prostředku ovládacího prvku.|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Inicializuje nebo načte aktuální hodnotu ovládacího prvku měsíční kalendář.|
|[DDX_Radio](#ddx_radio)|Inicializuje nebo načte index ovládacího prvku přepínače založený na nule, který je aktuálně kontrolován v rámci skupiny ovládacích prvků Radio.|
|[DDX_Scroll](#ddx_scroll)|Inicializuje nebo načte aktuální pozici jezdce posunutí ovládacího prvku.|
|[DDX_Slider](#ddx_slider)|Inicializuje nebo načte aktuální pozici táhla ovládacího prvku posuvníku.|
|[DDX_Text](#ddx_text)|Inicializuje nebo načte aktuální hodnotu ovládacího prvku pro úpravy.|

##  <a name="ddx_cbindex"></a>DDX_CBIndex

Funkce `DDX_CBIndex` spravuje přenos dat typu **int** mezi ovládacím prvkem pole se seznamem v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a datový člen **int** v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

```
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt `CDataExchange`. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku

*indexovacím*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Když se zavolá `DDX_CBIndex`, *index* se nastaví na index aktuálního výběru pole se seznamem. Pokud není vybrána žádná položka, *index* je nastaven na hodnotu 0.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_cbstring"></a>DDX_CBString

Funkce `DDX_CBString` spravuje přenos dat `CString` mezi ovládacími prvky pro úpravy ovládacího prvku pole se seznamem v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a `CString` datový člen dialogového okna, formulářového zobrazení nebo objektu zobrazení ovládacího prvku.

```
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt `CDataExchange`. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při volání `DDX_CBString` je *hodnota* nastavena na aktuální výběr pole se seznamem. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec s nulovou délkou.

> [!NOTE]
>  Pokud je pole se seznamem rozevírací seznam, vyměňované vydaná hodnota je omezena na 255 znaků.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_cbstringexact"></a>DDX_CBStringExact

Funkce `DDX_CBStringExact` spravuje přenos dat `CString` mezi ovládacími prvky pro úpravy ovládacího prvku pole se seznamem v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a `CString` datový člen dialogového okna, formulářového zobrazení nebo objektu zobrazení ovládacího prvku.

```
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt `CDataExchange`. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při volání `DDX_CBStringExact` je *hodnota* nastavena na aktuální výběr pole se seznamem. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec s nulovou délkou.

> [!NOTE]
>  Pokud je pole se seznamem rozevírací seznam, vyměňované vydaná hodnota je omezena na 255 znaků.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_check"></a>DDX_Check

Funkce `DDX_Check` spravuje přenos dat typu **int** mezi ovládacím prvkem zaškrtávací políčko v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a datový člen **int** v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

```
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt `CDataExchange`. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku zaškrtávací políčko přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při volání `DDX_Check` je *hodnota* nastavena na aktuální stav ovládacího prvku zaškrtávací políčko. Seznam možných hodnot stavu naleznete v tématu [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) v Windows SDK.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_control"></a>DDX_Control

Funkce `DDX_Control` podtřídí ovládací prvek určený parametrem *nIDC*pro dialogové okno, formulářové zobrazení nebo objekt zobrazení ovládacího prvku.

```
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) .

*nIDC*<br/>
ID prostředku ovládacího prvku, který se má roztřídit

*rControl*<br/>
Odkaz na členskou proměnnou v dialogovém okně, formulářovém zobrazení nebo objekt zobrazení ovládacího prvku, který se vztahuje k zadanému ovládacímu prvku.

### <a name="remarks"></a>Poznámky

Objekt *PDX* je dodán rozhraním, když je volána funkce `DoDataExchange`. Proto by `DDX_Control` měla být volána pouze v rámci přepsání `DoDataExchange`.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_datetimectrl"></a>DDX_DateTimeCtrl

Funkce `DDX_DateTimeCtrl` spravuje přenos dat data a času mezi ovládacím prvkem pro výběr data a času ( [atributu CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) v dialogovém okně nebo v objektu zobrazení formuláře a buď [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , nebo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) datový člen objektu dialogového okna nebo zobrazení formuláře.

```
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

*pDX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru. Tento objekt nemusíte odstranit.

*nIDC*<br/>
ID prostředku ovládacího prvku pro výběr data a času přidruženého k členské proměnné.

*value*<br/>
V prvních dvou verzích odkaz na členskou proměnnou `CTime` nebo `COleDateTime`, dialogové okno, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují. V třetí verzi odkaz na objekt zobrazení ovládacího prvku `CString` datového člena.

### <a name="remarks"></a>Poznámky

Když je volána `DDX_DateTimeCtrl`, *hodnota* je nastavena na aktuální stav ovládacího prvku pro výběr data a času nebo je ovládací prvek nastaven na *hodnotu*v závislosti na směru výměny.

Ve třetí verzi výše `DDX_DateTimeCtrl` spravuje přenos dat `CString` mezi ovládacím [prvkem data a času a datovým](../../atl-mfc-shared/reference/cstringt-class.md) členem objektu zobrazení ovládacího prvku. Řetězec je formátován pomocí pravidel aktuálního národního prostředí pro formátování data a času.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

## <a name="ddx_managedcontrol"></a>DDX_ManagedControl

Vytvoří ovládací prvek .NET, který odpovídá ID prostředku ovládacího prvku.

### <a name="syntax"></a>Syntaxe

```
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt [třídy CDataExchange –](cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku přidruženého k vlastnosti ovládacího prvku

*control*<br/>
Odkaz na objekt [třídy CWinFormsControl](cwinformscontrol-class.md) .

### <a name="remarks"></a>Poznámky

`DDX_ManagedControl` volá [CWinFormsControl:: CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) , aby se vytvořil ovládací prvek, který odpovídá ID ovládacího prvku prostředku. Pomocí `DDX_ManagedControl` vytvořit ovládací prvky z ID prostředků v [CDialog:: OnInitDialog](cdialog-class.md#oninitdialog). Pro výměnu dat nemusíte používat funkce DDX/DDV s ovládacími prvky model Windows Forms.

Další informace naleznete v tématu [How to: How/DDV Data Binding with model Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms. h

##  <a name="ddx_ipaddress"></a>DDX_IPAddress

Funkce `DDX_IPAddress` spravuje přenos dat mezi ovládacím prvkem IP adresa a datovým členem objektu zobrazení ovládacího prvku.

```
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt `CDataExchange`. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku pro řízení IP adres přidruženého k vlastnosti ovládacího prvku.

*value*<br/>
Odkaz na hodnotu DWORD obsahující čtyři pole s hodnotou ovládacího prvku IP adresa. Tato pole jsou vyplněna nebo čtena následujícím způsobem.

|Pole|Bity obsahující hodnotu pole|
|-----------|-------------------------------------|
|3|0 až 7|
|2|8 až 15|
|1|16 až 23|
|0|24 až 31|

Použijte [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) Win32 ke čtení hodnoty, nebo použijte [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress) k vyplnění hodnoty. Tyto zprávy jsou popsány v Windows SDK.

### <a name="remarks"></a>Poznámky

Když je volána `DDX_IPAddress`, *hodnota* je buď čtena z ovládacího prvku IP adresa, *nebo je* zapsána do ovládacího prvku v závislosti na směru výměny.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_lbindex"></a>DDX_LBIndex

Funkce `DDX_LBIndex` spravuje přenos dat typu **int** mezi ovládacím prvkem seznam v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a datový člen **int** v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

```
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt `CDataExchange`. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku

*indexovacím*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Když se zavolá `DDX_LBIndex`, *index* se nastaví na index aktuálního výběru pole seznamu. Pokud není vybrána žádná položka, *index* je nastaven na hodnotu-1.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_lbstring"></a>DDX_LBString

Funkce `DDX_LBString` spravuje přenos dat `CString` mezi ovládacími prvky seznamu v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a `CString` datový člen dialogového okna, formulářového zobrazení nebo objektu zobrazení ovládacího prvku.

```
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt `CDataExchange`. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Když je zavolána `DDX_LBString` pro přenos dat do ovládacího prvku seznamu, je vybrána první položka v ovládacím prvku, jehož začátek odpovídá *hodnotě* . (Chcete-li porovnat celou položku místo pouze předpony, použijte [DDX_LBStringExact](#ddx_lbstringexact).) Pokud neexistují žádné shody, nejsou vybrány žádné položky. U porovnávání se nerozlišují malá a velká písmena.

Když je zavolána `DDX_LBString` pro přenos dat z ovládacího prvku seznam, *hodnota* je nastavena na aktuální výběr pole seznamu. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec s nulovou délkou.

> [!NOTE]
>  Pokud je seznamem rozevírací seznam, vyměňované hodnoty se omezí na 255 znaků.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_lbstringexact"></a>DDX_LBStringExact

Funkce `DDX_CBStringExact` spravuje přenos dat `CString` mezi ovládacími prvky pro úpravy ovládacího prvku seznam v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a `CString` datový člen dialogového okna, formulářového zobrazení nebo objektu zobrazení ovládacího prvku.

```
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt `CDataExchange`. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Když je zavolána `DDX_LBStringExact` pro přenos dat do ovládacího prvku seznamu, je vybrána první položka v ovládacím prvku, která odpovídá *hodnotě* . (Chcete-li porovnat pouze předponu, nikoli celou položku, použijte [DDX_LBString](#ddx_lbstring).) Pokud neexistují žádné shody, nejsou vybrány žádné položky. U porovnávání se nerozlišují malá a velká písmena.

Když je zavolána `DDX_CBStringExact` pro přenos dat z ovládacího prvku seznam, *hodnota* je nastavena na aktuální výběr pole seznamu. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec s nulovou délkou.

> [!NOTE]
>  Pokud je seznamem rozevírací seznam, vyměňované hodnoty se omezí na 255 znaků.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_monthcalctrl"></a>DDX_MonthCalCtrl

Funkce `DDX_MonthCalCtrl` spravuje přenos dat data mezi ovládacím prvkem měsíční kalendář ( [atributu CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a [CTime –](../../atl-mfc-shared/reference/ctime-class.md) nebo [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) datový člen v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

```
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

*pDX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru. Tento objekt nemusíte odstranit.

*nIDC*<br/>
ID prostředku ovládacího prvku měsíční kalendář přidruženého k členské proměnné.

*value*<br/>
Odkaz na členskou proměnnou `CTime` nebo `COleDateTime` v dialogovém okně, zobrazení formuláře nebo objektu zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Ovládací prvek spravuje pouze hodnotu data. Časová pole v objektu Time jsou nastavena tak, aby odrážela čas vytvoření okna ovládacího prvku nebo jakýkoli čas byl nastaven v ovládacím prvku s voláním `CMonthCalCtrl::SetCurSel`.

Při volání `DDX_MonthCalCtrl` je *hodnota* nastavena na aktuální stav ovládacího prvku měsíční kalendář.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_radio"></a>DDX_Radio

Funkce `DDX_Radio` spravuje přenos dat typu **int** mezi skupinou ovládacích prvků v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a datový člen **int** v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. Hodnota datového členu **int** je určena podle toho, který přepínač v rámci skupiny je vybrán.

```
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt `CDataExchange`. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku prvního ovládacího prvku přepínače ve skupině.

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při volání `DDX_Radio` je *hodnota* nastavena na aktuální stav skupiny ovládacích prvků Radio. Hodnota je nastavena jako index s hodnotou 0 ovládacího prvku přepínač, který je aktuálně zaškrtnuto, nebo-1, pokud nejsou zaškrtnuty žádné ovládací prvky přepínačů.

Například pro případ, že je zaškrtnuto první přepínač ve skupině (tlačítko s WS_GROUP Style), hodnota člena **int** je 0 a tak dále.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_scroll"></a>DDX_Scroll

Funkce `DDX_Scroll` spravuje přenos dat typu **int** mezi ovládacími prvky posuvníku v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a datový člen **int** v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

```
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt `CDataExchange`. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku posuvníku přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Když je volána `DDX_Scroll`, *hodnota* je nastavena na aktuální pozici ovládacího prvku táhla ovládacího prvku. Další informace o hodnotách přidružených k aktuální pozici jezdce ovládacího prvku naleznete v tématu [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) v Windows SDK.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_slider"></a>DDX_Slider

Funkce `DDX_Slider` spravuje přenos dat typu **int** mezi ovládacím prvkem posuvník v dialogovém okně nebo zobrazením formuláře a datovým členem **int** ovládacího prvku dialogového okna nebo zobrazení formuláře.

```
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku posuvník

*value*<br/>
Odkaz na hodnotu, která má být vyměněna. Tento parametr uchovává nebo nastavuje aktuální pozici ovládacího prvku posuvníku.

### <a name="remarks"></a>Poznámky

Když je volána `DDX_Slider`, *hodnota* je nastavena na aktuální pozici ovládacího prvku táhla ovládacího prvku nebo hodnota dostane pozici v závislosti na směru výměny.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md). Informace o ovládacích prvcích posuvníku naleznete v tématu [using atributu CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

##  <a name="ddx_text"></a>DDX_Text

Funkce `DDX_Text` spravuje přenos **int**, **uint**, **Long**, DWORD, `CString`, **float**nebo **Double** data mezi ovládacím prvkem pro úpravy v dialogovém okně, formulářovém zobrazení nebo zobrazením ovládacího prvku a datovým členem [CString](../../atl-mfc-shared/reference/cstringt-class.md) v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

```
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

*pDX*<br/>
Ukazatel na objekt [CDataExchange –](../../mfc/reference/cdataexchange-class.md) . Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku pro úpravy v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*value*<br/>
Odkaz na datový člen v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. Datový typ *hodnota* závisí na tom, které z přetížených verzí `DDX_Text` používáte.

### <a name="remarks"></a>Poznámky

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  Afxdd_ **záhlaví** . h

## <a name="see-also"></a>Viz také

[Rutiny ověřování dat standardního dialogového okna](standard-dialog-data-validation-routines.md)<br/>
[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog:: OnInitDialog](cdialog-class.md#oninitdialog)
