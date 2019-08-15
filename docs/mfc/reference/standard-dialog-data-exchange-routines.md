---
title: Rutiny výměny dat standardního dialogového okna
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 47586f9cff0fcbe2cd7bad31f3d93fed08190830
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511579"
---
# <a name="standard-dialog-data-exchange-routines"></a>Rutiny výměny dat standardního dialogového okna

Toto téma obsahuje seznam standardních rutin pro výměnu dat dialogových oken, které se používají pro běžné ovládací prvky dialogového okna MFC.

> [!NOTE]
>  Standardní rutiny výměny dat dialogových oken se definují v hlavičkovém souboru afxdd_. h. Aplikace by však měly zahrnovat afxwin. h.

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

##  <a name="ddx_cbindex"></a>  DDX_CBIndex

Funkce spravuje přenos dat typu int mezi ovládacím prvkem pole se seznamem v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a datový člen **int** v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. `DDX_CBIndex`

```
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na `CDataExchange` objekt. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku

*index*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Když `DDX_CBIndex` je volána, *index* je nastaven na index aktuálního výběru pole se seznamem. Pokud není vybrána žádná položka, *index* je nastaven na hodnotu 0.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_cbstring"></a>  DDX_CBString

Funkce spravuje přenos dat mezi ovládacím prvkem pro úpravy ovládacího prvku pole se seznamem v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení `CString` ovládacího prvku a datového členu v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. `CString` `DDX_CBString`

```
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na `CDataExchange` objekt. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při `DDX_CBString` volání hodnoty je *hodnota* nastavena na aktuální výběr pole se seznamem. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec s nulovou délkou.

> [!NOTE]
>  Pokud je pole se seznamem rozevírací seznam, vyměňované vydaná hodnota je omezena na 255 znaků.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_cbstringexact"></a>  DDX_CBStringExact

Funkce spravuje přenos dat mezi ovládacím prvkem pro úpravy ovládacího prvku pole se seznamem v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení `CString` ovládacího prvku a datového členu v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. `CString` `DDX_CBStringExact`

```
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na `CDataExchange` objekt. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku pole se seznamem přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při `DDX_CBStringExact` volání hodnoty je *hodnota* nastavena na aktuální výběr pole se seznamem. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec s nulovou délkou.

> [!NOTE]
>  Pokud je pole se seznamem rozevírací seznam, vyměňované vydaná hodnota je omezena na 255 znaků.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_check"></a>  DDX_Check

Funkce spravuje přenos dat typu **int** mezi ovládacím prvkem zaškrtávací políčko v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a datový člen int v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. `DDX_Check`

```
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na `CDataExchange` objekt. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku zaškrtávací políčko přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při `DDX_Check` volání hodnoty je *hodnota* nastavena na aktuální stav ovládacího prvku zaškrtávací políčko. Seznam možných hodnot stavu naleznete v tématu [BM_GETCHECK](/windows/win32/Controls/bm-getcheck) v Windows SDK.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_control"></a>  DDX_Control

Funkce podtřídí ovládací prvek určený parametrem nIDC pro dialogové okno, formulářové zobrazení nebo objekt zobrazení ovládacího prvku. `DDX_Control`

```
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu.

*nIDC*<br/>
ID prostředku ovládacího prvku, který se má roztřídit

*rControl*<br/>
Odkaz na členskou proměnnou v dialogovém okně, formulářovém zobrazení nebo objekt zobrazení ovládacího prvku, který se vztahuje k zadanému ovládacímu prvku.

### <a name="remarks"></a>Poznámky

Objekt *PDX* je dodán rozhraním, když `DoDataExchange` je funkce volána. Proto by měla být volána pouze v rámci vašeho `DoDataExchange`přepsání. `DDX_Control`

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_datetimectrl"></a>  DDX_DateTimeCtrl

Funkce spravuje přenos dat data a času mezi ovládacím prvkem pro výběr data a času ( [atributu CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) v dialogovém okně nebo v objektu zobrazení formuláře a buď [CTime –](../../atl-mfc-shared/reference/ctime-class.md) nebo COleDateTime datový člen dialogového okna nebo formuláře. [](../../atl-mfc-shared/reference/coledatetime-class.md) `DDX_DateTimeCtrl` Zobrazit objekt

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
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru. Tento objekt nemusíte odstranit.

*nIDC*<br/>
ID prostředku ovládacího prvku pro výběr data a času přidruženého k členské proměnné.

*value*<br/>
V prvních dvou verzích odkaz na `CTime` nebo `COleDateTime` členskou proměnnou, dialogové okno, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují. Třetí verze, odkaz na `CString` objekt zobrazení ovládacího prvku data member.

### <a name="remarks"></a>Poznámky

Když `DDX_DateTimeCtrl` je volána, *hodnota* je nastavena na aktuální stav ovládacího prvku pro výběr data a času nebo je ovládací prvek nastaven na *hodnotu*v závislosti na směru výměny.

Ve třetí verzi výše `DDX_DateTimeCtrl` spravuje `CString` přenos dat mezi ovládacím prvkem data a času a datovým členem [CString](../../atl-mfc-shared/reference/cstringt-class.md) objektu zobrazení ovládacího prvku. Řetězec je formátován pomocí pravidel aktuálního národního prostředí pro formátování data a času.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

## <a name="ddx_managedcontrol"></a>  DDX_ManagedControl

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
Ukazatel [cdataexchange – třída](cdataexchange-class.md) objektu. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku přidruženého k vlastnosti ovládacího prvku

*control*<br/>
Odkaz na objekt [třídy CWinFormsControl](cwinformscontrol-class.md) .

### <a name="remarks"></a>Poznámky

`DDX_ManagedControl`volá [CWinFormsControl:: CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) , aby se vytvořil ovládací prvek, který odpovídá ID ovládacího prvku prostředku. Použijte `DDX_ManagedControl` k vytvoření ovládacích prvků z ID prostředků v [CDialog:: OnInitDialog](cdialog-class.md#oninitdialog). Pro výměnu dat nemusíte používat funkce DDX/DDV s ovládacími prvky model Windows Forms.

Další informace najdete v tématu [jak: Vytvoření datové vazby DDX/DDV pomocí model Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwinforms. h

##  <a name="ddx_ipaddress"></a>  DDX_IPAddress

`DDX_IPAddress` Funkce spravuje přenos dat mezi ovládacím prvkem IP adresa a datovým členem objektu zobrazení ovládacího prvku.

```
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na `CDataExchange` objekt. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

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

Použijte Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress) ke čtení hodnoty, nebo použijte [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress) k vyplnění hodnoty. Tyto zprávy jsou popsány v Windows SDK.

### <a name="remarks"></a>Poznámky

Při `DDX_IPAddress` volání hodnoty je *hodnota* načtena buď z řízení IP adresy, nebo je zapsána do ovládacího prvku v závislosti na směru výměny.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_lbindex"></a>  DDX_LBIndex

Funkce spravuje přenos dat typu **int** mezi ovládacím prvkem seznamu v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a datový člen int v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. `DDX_LBIndex`

```
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na `CDataExchange` objekt. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku

*index*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Když `DDX_LBIndex` je volána, *index* je nastaven na index aktuálního výběru pole seznamu. Pokud není vybrána žádná položka, *index* je nastaven na hodnotu-1.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_lbstring"></a>  DDX_LBString

Funkce spravuje přenos dat mezi ovládacím prvkem seznamu v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení `CString` ovládacího prvku a datovým členem v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. `CString` `DDX_LBString`

```
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na `CDataExchange` objekt. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Když `DDX_LBString` je volána pro přenos dat do ovládacího prvku seznamu, je vybrána první položka v ovládacím prvku, jehož začátek odpovídá *hodnotě* . (Tak, aby odpovídaly celé položky, ne jenom předpony, použijte [DDX_LBStringExact](#ddx_lbstringexact).) Pokud neexistují žádné shody, nejsou vybrány žádné položky. U porovnávání se nerozlišují malá a velká písmena.

Když `DDX_LBString` je volána pro přenos dat z ovládacího prvku seznamu, je *hodnota* nastavena na aktuální výběr seznamu. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec s nulovou délkou.

> [!NOTE]
>  Pokud je seznamem rozevírací seznam, vyměňované hodnoty se omezí na 255 znaků.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_lbstringexact"></a>  DDX_LBStringExact

Funkce spravuje přenos dat mezi ovládacím prvkem pro úpravy ovládacího prvku seznam v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení `CString` ovládacího prvku a datový člen v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. `CString` `DDX_CBStringExact`

```
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na `CDataExchange` objekt. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku seznamu přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Když `DDX_LBStringExact` je volána pro přenos dat do ovládacího prvku seznamu, je vybrána první položka v ovládacím prvku, který odpovídá *hodnotě* . (Vyhledání pouze předponu místo celé položky [DDX_LBString](#ddx_lbstring) Pokud neexistují žádné shody, nejsou vybrány žádné položky. U porovnávání se nerozlišují malá a velká písmena.

Když `DDX_CBStringExact` je volána pro přenos dat z ovládacího prvku seznamu, je *hodnota* nastavena na aktuální výběr seznamu. Pokud není vybrána žádná položka, *hodnota* je nastavena na řetězec s nulovou délkou.

> [!NOTE]
>  Pokud je seznamem rozevírací seznam, vyměňované hodnoty se omezí na 255 znaků.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_monthcalctrl"></a>  DDX_MonthCalCtrl

Funkce spravuje přenos dat data mezi ovládacím prvkem měsíční kalendář ( [atributu CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a buď [CTime –](../../atl-mfc-shared/reference/ctime-class.md) , nebo datový člen COleDateTime dialogového okna, formulář [](../../atl-mfc-shared/reference/coledatetime-class.md) `DDX_MonthCalCtrl` zobrazení nebo řízení objektu zobrazení.

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
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru. Tento objekt nemusíte odstranit.

*nIDC*<br/>
ID prostředku ovládacího prvku měsíční kalendář přidruženého k členské proměnné.

*value*<br/>
Odkaz na `CTime` členskou proměnnou nebo `COleDateTime` v dialogovém okně, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Ovládací prvek spravuje pouze hodnotu data. Časová pole v objektu Time jsou nastavena tak, aby odrážela čas vytvoření okna ovládacího prvku nebo jakýkoli čas byl nastaven v ovládacím prvku pomocí volání `CMonthCalCtrl::SetCurSel`.

Při `DDX_MonthCalCtrl` volání hodnoty je *hodnota* nastavena na aktuální stav ovládacího prvku měsíční kalendář.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_radio"></a>  DDX_Radio

Funkce spravuje přenos dat typu **int** mezi skupinou ovládacích prvků v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a datový člen int v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. `DDX_Radio` Hodnota datového členu **int** je určena podle toho, který přepínač v rámci skupiny je vybrán.

```
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na `CDataExchange` objekt. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku prvního ovládacího prvku přepínače ve skupině.

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, formulářové zobrazení nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Při `DDX_Radio` volání hodnoty je *hodnota* nastavena na aktuální stav skupiny ovládacích prvků přepínač. Hodnota je nastavena jako index s hodnotou 0 ovládacího prvku přepínač, který je aktuálně zaškrtnuto, nebo-1, pokud nejsou zaškrtnuty žádné ovládací prvky přepínačů.

Například pro případ, že je zaškrtnuto první přepínač ve skupině (tlačítko se stylem WS_GROUP), hodnota člena **int** je 0 a tak dále.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_scroll"></a>  DDX_Scroll

Funkce spravuje přenos dat typu **int** mezi ovládacími prvky posuvníku v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku a datový člen int v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. `DDX_Scroll`

```
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel na `CDataExchange` objekt. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku posuvníku přidruženého k vlastnosti ovládacího prvku

*value*<br/>
Odkaz na členskou proměnnou dialogového okna, zobrazení formuláře nebo objekt zobrazení ovládacího prvku, se kterým se data vyměňují.

### <a name="remarks"></a>Poznámky

Když `DDX_Scroll` je volána, *hodnota* je nastavena na aktuální pozici ovládacího prvku táhla ovládacího prvku. Další informace o hodnotách přidružených k aktuální pozici jezdce ovládacího prvku naleznete v tématu [GetScrollPos](/windows/win32/api/winuser/nf-winuser-getscrollpos) v Windows SDK.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_slider"></a>  DDX_Slider

Funkce spravuje přenos dat typu int mezi ovládacím prvkem posuvník v dialogovém okně nebo zobrazením formuláře a datovým členem **int** ovládacího prvku v dialogovém okně nebo v objektu zobrazení formuláře. `DDX_Slider`

```
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parametry

*pDX*<br/>
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID prostředku ovládacího prvku posuvník

*value*<br/>
Odkaz na hodnotu, která má být vyměněna. Tento parametr uchovává nebo nastavuje aktuální pozici ovládacího prvku posuvníku.

### <a name="remarks"></a>Poznámky

Když `DDX_Slider` je volána, *hodnota* je nastavena na aktuální pozici ovládacího prvku Táhlo nebo hodnota dostane pozici v závislosti na směru výměny.

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md). Informace o ovládacích prvcích posuvníku naleznete v tématu [using atributu CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

##  <a name="ddx_text"></a>  DDX_Text

`CString` [](../../atl-mfc-shared/reference/cstringt-class.md)Funkce spravuje přenos int, uint, Long, DWORD,, float nebo Double data mezi ovládacím prvkem pro úpravy v dialogovém okně, formulářovém zobrazení nebo zobrazením ovládacího prvku a daty CString. `DDX_Text` člen dialogového okna, formulářového zobrazení nebo objektu zobrazení ovládacího prvku.

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
Ukazatel [CDataExchange](../../mfc/reference/cdataexchange-class.md) objektu. Rozhraní poskytuje tento objekt pro vytvoření kontextu výměny dat, včetně jeho směru.

*nIDC*<br/>
ID ovládacího prvku pro úpravy v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku.

*value*<br/>
Odkaz na datový člen v dialogovém okně, formulářovém zobrazení nebo objektu zobrazení ovládacího prvku. Datový typ *hodnota* závisí na tom, které z přetížených verzí `DDX_Text` použijete.

### <a name="remarks"></a>Poznámky

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Požadavky

  **Header** afxdd_. h

## <a name="see-also"></a>Viz také:

[Rutiny ověřování dat standardního dialogového okna](standard-dialog-data-validation-routines.md)<br/>
[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
