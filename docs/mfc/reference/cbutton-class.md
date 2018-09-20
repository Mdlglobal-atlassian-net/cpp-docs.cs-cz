---
title: CButton – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
dev_langs:
- C++
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2f0f0ce6a893406fca73f25e040cbc3dbd29d08
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429939"
---
# <a name="cbutton-class"></a>CButton – třída

Poskytuje funkce pro ovládací prvky tlačítka Windows.

## <a name="syntax"></a>Syntaxe

```
class CButton : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CButton::CButton](#cbutton)|Vytvoří `CButton` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CButton::Create](#create)|Vytvoří ovládací prvek tlačítka Windows a připojí ho k `CButton` objektu.|
|[CButton::DrawItem](#drawitem)|Přepsání za účelem vykreslení vykreslovaných vlastníkem `CButton` objektu.|
|[CButton::GetBitmap](#getbitmap)|Načte popisovač rastrového obrázku dříve nastaven s [SetBitmap](#setbitmap).|
|[CButton::GetButtonStyle](#getbuttonstyle)|Načte informace o stylu ovládacího prvku tlačítko.|
|[CButton::GetCheck](#getcheck)|Načte stavu zaškrtnutí ovládacího prvku tlačítko.|
|[CButton::GetCursor](#getcursor)|Načte popisovač obrázek kurzoru dříve nastaven s [SetCursor](#setcursor).|
|[CButton::GetIcon](#geticon)|Načte popisovač ikony dříve nastaven s [SetIcon](#seticon).|
|[CButton::GetIdealSize](#getidealsize)|Načte ideální velikost ovládacího prvku tlačítko.|
|[CButton::GetImageList](#getimagelist)|Načte seznam obrázků na ovládací prvek tlačítka.|
|[CButton::GetNote](#getnote)|Obnoví komponenty Poznámka aktuální příkaz ovládacího prvku odkaz.|
|[CButton::GetNoteLength](#getnotelength)|Získá délku textu pro ovládací prvek odkazu aktuální příkaz.|
|[CButton::GetSplitGlyph](#getsplitglyph)|Načte piktogram přidružené k aktuální tlačítko rozdělení ovládání.|
|[CButton::GetSplitImageList](#getsplitimagelist)|Načte seznam obrázků pro aktuální tlačítko rozdělení ovládání.|
|[CButton::GetSplitInfo](#getsplitinfo)|Načte informace, které definují aktuální tlačítko rozdělení ovládání.|
|[CButton::GetSplitSize](#getsplitsize)|Načte ohraničující obdélník rozevíracího seznamu součástí aktuální tlačítko rozdělení ovládání.|
|[CButton::GetSplitStyle](#getsplitstyle)|Načte styly tlačítko rozdělení, které definují aktuální tlačítko rozdělení ovládání.|
|[CButton::GetState](#getstate)|Načte kontroly stavu, zvýraznění stavu a detailní stavu ovládacího prvku tlačítko.|
|[CButton::GetTextMargin](#gettextmargin)|Načte text okraji ovládacího prvku tlačítko.|
|[CButton::SetBitmap](#setbitmap)|Určuje rastrového obrázku zobrazeného na tlačítku.|
|[CButton::SetButtonStyle](#setbuttonstyle)|Změní styl tlačítka.|
|[CButton::SetCheck](#setcheck)|Nastaví stavu zaškrtnutí ovládacího prvku tlačítko.|
|[CButton::SetCursor](#setcursor)|Určuje obrázek kurzoru zobrazený na tlačítku.|
|[CButton::SetDropDownState](#setdropdownstate)|Nastaví stav rozevíracího seznamu na aktuální ovládací prvek tlačítka rozdělení.|
|[CButton::SetIcon](#seticon)|Určuje ikonu zobrazený na tlačítku.|
|[CButton::SetImageList](#setimagelist)|Nastaví obrázek seznamu ovládacího prvku tlačítko.|
|[CButton::SetNote](#setnote)|Nastaví poznámky na ovládací prvek odkazu aktuální příkaz.|
|[CButton::SetSplitGlyph](#setsplitglyph)|Přidruží zadaný piktogram aktuální tlačítko rozdělení ovládání.|
|[CButton::SetSplitImageList](#setsplitimagelist)|Přidruží aktuální tlačítko rozdělení ovládání seznamu obrázků.|
|[CButton::SetSplitInfo](#setsplitinfo)|Určuje informace, které definují aktuální tlačítko rozdělení ovládání.|
|[CButton::SetSplitSize](#setsplitsize)|Nastaví ohraničující obdélník rozevíracího seznamu součástí aktuální tlačítko rozdělení ovládání.|
|[CButton::SetSplitStyle](#setsplitstyle)|Nastaví styl aktuální tlačítko rozdělení ovládání.|
|[CButton::SetState](#setstate)|Nastaví zvýrazňování stavu ovládacího prvku tlačítko.|
|[CButton::SetTextMargin](#settextmargin)|Nastaví okraj textu ovládacího prvku tlačítka.|

## <a name="remarks"></a>Poznámky

Ovládací prvek tlačítko je malé, obdélníkové podřízené okno, které se dá kliknout a vypnout. Tlačítka může být použito samostatně nebo ve skupinách a buď být označeny nebo bez textu se zobrazí. Tlačítko obvykle změní vzhled, když na něj uživatel klikne.

Zaškrtávací políčko, přepínač a pushbutton jsou typické tlačítka. A `CButton` objektu se může stát, podle [tlačítko stylu](../../mfc/reference/styles-used-by-mfc.md#button-styles) na jeho inicializaci podle [vytvořit](#create) členskou funkci.

Kromě toho [cbitmapbutton –](../../mfc/reference/cbitmapbutton-class.md) třída odvozena z `CButton` podporuje vytvoření ovládací prvky tlačítek označené obrázky rastrový obrázek namísto textu. A `CBitmapButton` může mít samostatné rastrové obrázky pro tlačítko uživatele snižování kapacity, zaměřuje a zakázané stavy.

Ovládací prvek tlačítko můžete vytvořit z šablony dialogového okna nebo přímo v kódu. V obou případech se nejprve volat konstruktor `CButton` k sestavení kompletních `CButton` objektu; poté zavolejte `Create` členské funkci, která vytvoří Windows ovládacímu prvku tlačítko a připojte ji k `CButton` objektu.

Konstrukce může být jednoduchý proces ve třídě odvozené z `CButton`. Zápis konstruktoru pro odvozenou třídu a volání `Create` z v rámci konstruktoru.

Pokud chcete zpracovávat Windows oznamující zprávy odeslal ovládací prvek tlačítko k nadřazené úloze (obvykle třída odvozená z [CDialog](../../mfc/reference/cdialog-class.md)), přidat mapu zpráv položku a obslužná rutina zprávy členskou funkci na nadřazené třídu pro každou zprávu.

Každá položka mapování zpráv má následující podobu:

**ON_** oznámení **(**`id`, `memberFxn` **)**

kde `id` určuje Identifikátor podřízené okno ovládacího prvku odesílání oznámení a `memberFxn` je název nadřazené členské funkce mají napsané tak, aby oznámení.

Prototyp funkce nadřazeného objektu je následujícím způsobem:

**afx_msg** `void` `memberFxn` **();**

Potenciální položky mapování zpráv jsou následující:

|Položka mapování|Odesílat, když nadřazený...|
|---------------|----------------------------|
|ON_BN_CLICKED|Uživatel klikne na tlačítko.|
|ON_BN_DOUBLECLICKED|Uživatel dvakrát klikne na tlačítko.|

Pokud jste vytvořili `CButton` objekt z prostředku dialogového okna, `CButton` objekt je zničen automaticky, když uživatel zavře dialogové okno.

Pokud jste vytvořili `CButton` objekt v rámci časového období, možná budete muset zničit ho. Pokud jste vytvořili `CButton` objektů na haldě pomocí **nové** funkce, je nutné volat **odstranit** ovládacímu prvku tlačítko na objekt, který chcete zničit se při zavření Windows. Pokud jste vytvořili `CButton` objekt v zásobníku, nebo je vložený v nadřazeném objektu dialogového okna, je automaticky zničen.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cbutton"></a>  CButton::CButton

Vytvoří `CButton` objektu.

```
CButton();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

##  <a name="create"></a>  CButton::Create

Vytvoří ovládací prvek tlačítka Windows a připojí ho k `CButton` objektu.

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszCaption*<br/>
Určuje text, ovládací prvek tlačítko.

*dwStyle*<br/>
Určuje styl ovládacího prvku button. Použít libovolnou kombinaci [tlačítko styly](../../mfc/reference/styles-used-by-mfc.md#button-styles) k tlačítku.

*Rect*<br/>
Určuje velikost a umístění ovládací prvek tlačítko. Může se jednat buď `CRect` objektu nebo `RECT` struktury.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku tlačítko, obvykle `CDialog`. Nesmí být NULL.

*nID*<br/>
Určuje ID ovládacího prvku button.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CButton` objektu ve dvou krocích. Nejprve volat konstruktor a následně zavolat `Create`, což vytvoří ovládací prvek tlačítka Windows a připojí ho k `CButton` objektu.

WS_VISIBLE style je směru, je-li Windows odešle všechny zprávy, které jsou potřebné k aktivaci a zobrazeno tlačítko ovládacího prvku tlačítko.

Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) na ovládací prvek tlačítka:

- WS_CHILD vždy

- WS_VISIBLE obvykle

- WS_DISABLED jen zřídka

- WS_GROUP k seskupování ovládacích prvků

- WS_TABSTOP tlačítko v obsahovat pořadí procházení

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

##  <a name="drawitem"></a>  CButton::DrawItem

Volá se rozhraním, při úpravě vizuálního aspektu tlačítka nakresleného vlastníkem.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhým ukazatelem na [drawitemstruct –](../../mfc/reference/drawitemstruct-structure.md) struktury. Struktura obsahuje informace o položka, která má být vykreslena a typ kresby vyžaduje.

### <a name="remarks"></a>Poznámky

Tlačítka nakresleného vlastníkem má nastaven styl BS_OWNERDRAW. Přepsat tato členská funkce implementovat výkresu vykreslovaných vlastníkem `CButton` objektu. Aplikace by měl obnovit všechny grafiky zařízení rozhraní GDI systému objekty vybrané pro zadaný kontext zobrazení v *lpDrawItemStruct* před členské funkce skončí.

Viz také [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) hodnoty stylu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

##  <a name="getbitmap"></a>  CButton::GetBitmap

Voláním této členské funkce, chcete-li získat popisovač rastrový obrázek, dříve nastaven s [SetBitmap](#setbitmap), který je přidružený k tlačítku.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač rastrový obrázek. Hodnota NULL, pokud dříve není zadána žádná rastrového obrázku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="getbuttonstyle"></a>  CButton::GetButtonStyle

Načte informace o stylu ovládacího prvku tlačítko.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí styly tlačítek pro tuto `CButton` objektu. Tato funkce vrací pouze [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) hodnoty styl, některý další styly oken.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="getcheck"></a>  CButton::GetCheck

Načte stav zaškrtávací políčko nebo přepínací tlačítka.

```
int GetCheck() const;
```

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota z ovládacího prvku tlačítko vytvořené pomocí BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON nebo BS_3STATE style je jedním z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|BST_UNCHECKED|Stav tlačítka není zaškrtnuta.|
|BST_CHECKED|Kontroluje se stav tlačítka.|
|BST_INDETERMINATE|Stav tlačítka je neurčité (platí jenom v případě, že tlačítko má BS_3STATE nebo BS_AUTO3STATE style).|

Pokud tlačítko má jiný styl, vrácená hodnota je BST_UNCHECKED.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="getcursor"></a>  CButton::GetCursor

Voláním této členské funkce, chcete-li získat popisovač kurzoru, dříve nastaven s [SetCursor](#setcursor), který je přidružený k tlačítku.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač pro obrázek kurzoru. Hodnota NULL, pokud je již zadán žádný kurzor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="geticon"></a>  CButton::GetIcon

Voláním této členské funkce, chcete-li získat popisovač ikony, dříve nastaven s [SetIcon](#seticon), který je přidružený k tlačítku.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač ikony. Hodnota NULL, pokud dříve není zadána žádná ikona.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="getidealsize"></a>  CButton::GetIdealSize

Načte ideální velikost pro ovládací prvek tlačítko.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Parametry

*psize*<br/>
Ukazatel na aktuální velikost tlačítka.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkčnost BCM_GETIDEALSIZE zprávu, jak je popsáno v [tlačítka](https://msdn.microsoft.com/library/windows/desktop/bb775943) část sady Windows SDK.

##  <a name="getimagelist"></a>  CButton::GetImageList

Volejte tuto metodu za účelem získání seznamu obrázků z ovládacího prvku tlačítko.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parametry

*pbuttonImagelist*<br/>
Ukazatel na seznam obrázků `CButton` objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkčnost BCM_GETIMAGELIST zprávu, jak je popsáno v [tlačítka](https://msdn.microsoft.com/library/windows/desktop/bb775943) část sady Windows SDK.

##  <a name="getnote"></a>  CButton::GetNote

Načte text poznámky, které jsou přidružené k aktuální ovládací prvek odkazu příkazu.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpszNote*|[out] Ukazatel do vyrovnávací paměti, která má volající zodpovídá za přidělování a rušení přidělení. Pokud vrácená hodnota je TRUE, vyrovnávací paměť obsahuje text poznámky, který je přidružený aktuální příkaz Ovládací prvek odkazu; v opačném případě vyrovnávací paměť je beze změny.|
|*cchNote*|[out v] Ukazatel na proměnnou celého čísla bez znaménka.<br /><br /> Když tato metoda je volána, proměnná obsahuje velikost vyrovnávací paměti určené parametrem *lpszNote* parametru.<br /><br /> Pokud tato metoda vrátí hodnotu, pokud vrácená hodnota je TRUE proměnné obsahuje velikost poznámky přidružené k aktuální ovládací prvek odkazu příkazu. Pokud vrácená hodnota je FALSE, proměnná obsahuje velikost vyrovnávací paměti musí obsahovat poznámku.|

### <a name="return-value"></a>Návratová hodnota

V první přetížení [CString](../../atl-mfc-shared/using-cstring.md) objekt, který obsahuje text poznámky, které jsou přidružené k aktuální ovládací prvek odkazu příkazu.

-nebo-

V druhé přetížení je hodnota TRUE, pokud metoda úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_COMMANDLINK nebo BS_DEFCOMMANDLINK.

Tato metoda odesílá [BCM_GETNOTE](/windows/desktop/Controls/bcm-getnote) zprávu, která je popsána v sadě Windows SDK.

##  <a name="getnotelength"></a>  CButton::GetNoteLength

Získá délku textu pro ovládací prvek odkazu aktuální příkaz.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka textu poznámky v znaků Unicode 16 bitů, ovládací prvek odkazu aktuální příkaz.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_COMMANDLINK nebo BS_DEFCOMMANDLINK.

Tato metoda odesílá [BCM_GETNOTELENGTH](/windows/desktop/Controls/bcm-getnotelength) zprávu, která je popsána v sadě Windows SDK.

##  <a name="getsplitglyph"></a>  CButton::GetSplitGlyph

Načte piktogram přidružené k aktuální tlačítko rozdělení ovládání.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Návratová hodnota

Piktogram znak přiřazený k aktuální tlačítko rozdělení ovládání.

### <a name="remarks"></a>Poznámky

Glyf je fyzická reprezentace znaku v určité písmo. Například ovládací tlačítko rozdělení může být doplněny pomocí piktogram zaškrtávací políčko znak Unicode (U + 2713).

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) strukturu s BCSIF_GLYPH příznak a pak odešle, které konstrukce v [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) zprávu, která je popsána v Windows SDK. Po návratu funkce zprávy, tato metoda načte glyf z `himlGlyph` členu struktury.

##  <a name="getsplitimagelist"></a>  CButton::GetSplitImageList

Načte [seznamu obrázků](../../mfc/reference/cimagelist-class.md) aktuální ovládací prvek tlačítka rozdělení.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [atributu CImageList](../../mfc/reference/cimagelist-class.md) objektu.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) strukturu s BCSIF_IMAGE příznak a pak odešle, které konstrukce v [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) zprávu, která je popsána v Windows SDK. Po návratu funkce zprávy, tato metoda načte seznam obrázků z `himlGlyph` členu struktury.

##  <a name="getsplitinfo"></a>  CButton::GetSplitInfo

Načte parametry, které určují, jak Windows nakreslí aktuální tlačítko rozdělení ovládání.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pInfo*|[out] Ukazatel [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktura, která obdrží informace o aktuální tlačítko rozdělení ovládání. Volající zodpovídá za přidělování struktury.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda odesílá [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) zprávu, která je popsána v sadě Windows SDK.

##  <a name="getsplitsize"></a>  CButton::GetSplitSize

Načte ohraničující obdélník rozevíracího seznamu součástí aktuální tlačítko rozdělení ovládání.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pSize*|[out] Ukazatel [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktura, která přijímá popis obdélníku.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Po rozbalení ovládacího prvku tlačítko rozdělení může zobrazit rozevírací seznam součást, například ovládací prvek seznamu nebo ovládací prvek stránkování. Tato metoda načte ohraničující obdélník, který obsahuje komponentu rozevíracího seznamu.

Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) strukturu s BCSIF_SIZE příznak a pak odešle, které konstrukce v [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) zprávu, která je popsána v Windows SDK. Po návratu funkce zprávy, tato metoda načte z ohraničující obdélník `size` členu struktury.

##  <a name="getsplitstyle"></a>  CButton::GetSplitStyle

Načte styly tlačítko rozdělení, které definují aktuální tlačítko rozdělení ovládání.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová kombinace hodnot styly tlačítka rozdělení. Další informace najdete v tématu `uSplitStyle` člena [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Styly tlačítek rozdělení zadejte zarovnání, poměr stran a grafické podobě, pomocí kterého Windows nakreslí ikonu tlačítka rozdělení.

Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) strukturu s BCSIF_STYLE příznak a pak odešle, které konstrukce v [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) zprávu, která je popsána v Windows SDK. Po návratu funkce zprávy, tato metoda načte styly tlačítka rozdělení z `uSplitStyle` členu struktury.

##  <a name="getstate"></a>  CButton::GetState

Načte stav ovládacího prvku tlačítko.

```
UINT GetState() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitové pole, která obsahuje kombinaci hodnot, které označují aktuální stav ovládacího prvku tlačítko. V následující tabulce jsou uvedeny možné hodnoty.

|Stav tlačítka|Hodnota|Popis|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|Počáteční stav.|
|BST_CHECKED|0x0001|Ovládací prvek tlačítko zaškrtnuto.|
|BST_INDETERMINATE|0x0002|Stav je neurčité (možné, pouze když ovládacího prvku tlačítko má tři stavy).|
|BST_PUSHED|0x0004|Stisknutí ovládacího prvku tlačítko.|
|BST_FOCUS|0x0008|Ovládací prvek tlačítko má fokus.|

### <a name="remarks"></a>Poznámky

Ovládací prvek tlačítko Styl tlačítka BS_3STATE nebo BS_AUTO3STATE vytvoří zaškrtávací políčko, které má být třetí stav, který je pojmenován neurčitém stavu. Neurčitého stavu označuje, že políčko není zaškrtnuté ani není zaškrtnuto.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="gettextmargin"></a>  CButton::GetTextMargin

Volejte tuto metodu za účelem získání okraj textu `CButton` objektu.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parametry

*pmargin*<br/>
Ukazatel na okraj textu `CButton` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí okraj textu.

### <a name="remarks"></a>Poznámky

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkčnost BCM_GETTEXTMARGIN zprávu, jak je popsáno v [tlačítka](https://msdn.microsoft.com/library/windows/desktop/bb775943) část sady Windows SDK.

##  <a name="setbitmap"></a>  CButton::SetBitmap

Voláním této členské funkce přidružit nový rastrový obrázek na tlačítko.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Popisovač rastrový obrázek.

### <a name="return-value"></a>Návratová hodnota

Popisovač dříve přidružený k tlačítku rastrový obrázek.

### <a name="remarks"></a>Poznámky

Rastrový obrázek se automaticky umístí na tlačítku, umístěné uprostřed ve výchozím nastavení. Pokud je příliš velký pro tlačítko rastrový obrázek, bude oříznut na obou stranách. Můžete použít jiné možnosti zarovnání, včetně následujících:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Na rozdíl od [cbitmapbutton –](../../mfc/reference/cbitmapbutton-class.md), který používá čtyři rastrových obrázků za tlačítko, `SetBitmap` používá pouze jeden rastrového obrázku na tlačítku. Při stisknutí tlačítka se zobrazí rastrový obrázek posunout dolů a doprava.

Zodpovídáte za uvolňuje rastrový obrázek, když jste s ním hotovi.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="setbuttonstyle"></a>  CButton::SetButtonStyle

Změní styl tlačítka.

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
Určuje, [tlačítko stylu](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bRedraw*<br/>
Určuje, zda je překreslit tlačítko. Nenulová hodnota překreslí tlačítka. Hodnota 0 nelze ho překreslit tlačítko. Ve výchozím nastavení se měl překreslit tlačítko.

### <a name="remarks"></a>Poznámky

Použití `GetButtonStyle` členské funkce lze získat styl tlačítka. Nižší řád slova stylu tlačítko pro dokončení je styl tlačítka specifické.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="setcheck"></a>  CButton::SetCheck

Nastaví nebo obnoví stav zaškrtávací políčko nebo přepínací tlačítka.

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parametry

*nZkontrolujte*<br/>
Určuje stav kontroly. Tento parametr může být jeden z následujících akcí:

|Hodnota|Význam|
|-----------|-------------|
|BST_UNCHECKED|Nastavte stav tlačítka nezaškrtnuté.|
|BST_CHECKED|Nastavte stav tlačítka zkontrolovat.|
|BST_INDETERMINATE|Nastavte stav tlačítka na neurčitou. Tuto hodnotu lze použít pouze v případě, že tlačítko má BS_3STATE nebo BS_AUTO3STATE style.|

### <a name="remarks"></a>Poznámky

Tato členská funkce nemá žádný vliv na pushbutton.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="setcursor"></a>  CButton::SetCursor

Voláním této členské funkce přidružit nový kurzoru tlačítka.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parametry

*hCursor*<br/>
Popisovač kurzoru.

### <a name="return-value"></a>Návratová hodnota

Popisovač kurzor dříve přidružený k tlačítku.

### <a name="remarks"></a>Poznámky

Kurzor se automaticky umístí na tlačítku, umístěné uprostřed ve výchozím nastavení. Pokud je příliš velká pro tlačítko pro kurzor, bude oříznut na obou stranách. Můžete použít jiné možnosti zarovnání, včetně následujících:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Na rozdíl od [cbitmapbutton –](../../mfc/reference/cbitmapbutton-class.md), který používá čtyři rastrových obrázků za tlačítko, `SetCursor` používá pouze jeden ukazatel na tlačítku. Při stisknutí tlačítka se zobrazí kurzor posunout dolů a doprava.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="setdropdownstate"></a>  CButton::SetDropDownState

Nastaví stav rozevíracího seznamu na aktuální ovládací prvek tlačítka rozdělení.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*fDropDown*|[in] TRUE, pokud chcete nastavit stav BST_DROPDOWNPUSHED; v opačném případě hodnota FALSE.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Ovládací tlačítko rozdělení obsahuje styl BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON a obsahuje tlačítko a rozevírací šipku vpravo. Další informace najdete v tématu [styly](/windows/desktop/Controls/button-styles). Stav rozevíracího seznamu je obvykle nastavena, když uživatel klepne na šipku rozevíracího seznamu. Pomocí této metody můžete prostřednictvím kódu programu nastavit stav rozevíracího seznamu ovládacího prvku. Na šipku rozevíracího seznamu vykreslením označeno šedou barvou, které označují stav.

Tato metoda odesílá [BCM_SETDROPDOWNSTATE](/windows/desktop/Controls/bcm-setdropdownstate) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, *m_splitButton*, která je použita k programovému přístupu ke tlačítko rozdělení ovládání. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví stav ovládacího prvku tlačítko rozdělení k označení, že se posune na šipku rozevíracího seznamu.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

##  <a name="setelevationrequired"></a>  CButton::SetElevationRequired

Nastaví stav aktuální ovládací prvek tlačítko na `elevation required`, která je nutná pro ovládací prvek zobrazí ikona se zvýšenými oprávněními zabezpečení.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*fElevationRequired*|[in] True pro sadu `elevation required` stavu; jinak FALSE.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Pokud ovládací prvek tlačítka nebo příkaz odkazu vyžaduje zvýšená oprávnění k provedení akce, nastavte ovládací prvek na `elevation required` stavu. Následně Windows zobrazuje ikona štítu řízení uživatelských účtů (UAC) v ovládacím prvku. Další informace najdete v článku "Řízení uživatelských účtů" na [MSDN](http://go.microsoft.com/fwlink/p/?linkid=18507).

Tato metoda odesílá [BCM_SETSHIELD](/windows/desktop/Controls/bcm-setshield) zprávu, která je popsána v sadě Windows SDK.

##  <a name="seticon"></a>  CButton::SetIcon

Voláním této členské funkce přidružit novou ikonu tlačítka.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*hIcon*<br/>
Popisovač ikony.

### <a name="return-value"></a>Návratová hodnota

Popisovač ikony dříve přidružený k tlačítku.

### <a name="remarks"></a>Poznámky

Ikona se automaticky umístí na tlačítku, umístěné uprostřed ve výchozím nastavení. Pokud je příliš velký pro tlačítko přechodu na ikonu, bude oříznut na obou stranách. Můžete použít jiné možnosti zarovnání, včetně následujících:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Na rozdíl od [cbitmapbutton –](../../mfc/reference/cbitmapbutton-class.md), který používá čtyři rastrových obrázků za tlačítko, `SetIcon` používá jenom jednu ikonu na tlačítko. Při stisknutí tlačítka se zobrazí ikona posunout dolů a doprava.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="setimagelist"></a>  CButton::SetImageList

Voláním této metody lze nastavit na seznam obrázků `CButton` objektu.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parametry

*pbuttonImagelist*<br/>
Ukazatel na nový seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkčnost BCM_SETIMAGELIST zprávu, jak je popsáno v [tlačítka](https://msdn.microsoft.com/library/windows/desktop/bb775943) část sady Windows SDK.

##  <a name="setnote"></a>  CButton::SetNote

Nastaví text poznámky k aktuální ovládací prvek odkazu příkazu.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpszNote*|[in] Ukazatel na řetězec znaků Unicode, který je nastaven jako text poznámky pro ovládací prvek propojení příkazů.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_COMMANDLINK nebo BS_DEFCOMMANDLINK.

Tato metoda odesílá [BCM_SETNOTE](/windows/desktop/Controls/bcm-setnote) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, *m_cmdLink*, která je použít k programovému přístupu ke službě ovládací prvek propojení příkazů. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví text poznámky pro ovládací prvek propojení příkazů.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

##  <a name="setsplitglyph"></a>  CButton::SetSplitGlyph

Přidruží zadaný piktogram aktuální tlačítko rozdělení ovládání.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*chGlyph*|[in] Znak, který určuje glyfů pro použití jako na šipku rozevíracího seznamu tlačítko rozdělení.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, které mají styl tlačítka BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Glyf je fyzická reprezentace znaku v určité písmo. *ChGlyph* parametr se nepoužívá jako šifra, ale místo toho slouží k výběru piktogram ze sady definovaných systémem glyfů. Rozevírací šipku glyfu určený pomocí znaku "6" a vypadá podobně jako znak Unicode ČERNÉ mimo provoz SMĚŘUJÍCÍ TROJÚHELNÍK (U + 25BC).

Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktura s příznakem BCSIF_GLYPH a `himlGlyph` člena s *chGlyph* parametr a pak odešle struktury v [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) zprávu, která je popsána v sadě Windows SDK.

##  <a name="setsplitimagelist"></a>  CButton::SetSplitImageList

Přidruží [seznamu obrázků](../../mfc/reference/cimagelist-class.md) s aktuální tlačítko rozdělení ovládání.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pSplitImageList*|[in] Ukazatel [atributu CImageList](../../mfc/reference/cimagelist-class.md) objektu, který chcete přiřadit k aktuální tlačítko rozdělení ovládání.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktura s příznakem BCSIF_IMAGE a `himlGlyph` člena s *pSplitImageList* parametr a pak odešle v této struktury [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) zprávu, která je popsána v sadě Windows SDK.

##  <a name="setsplitinfo"></a>  CButton::SetSplitInfo

Určuje parametry, které určují, jak Windows nakreslí aktuální tlačítko rozdělení ovládání.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pInfo*|[in] Ukazatel [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) strukturu, která definuje aktuální tlačítko rozdělení ovládání.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda odesílá [BCM_SETSPLITINFO](/windows/desktop/Controls/bcm-setsplitinfo) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_splitButton`, která je použita k programovému přístupu ke tlačítko rozdělení ovládání.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu se změní glyf, který se používá pro šipku rozevíracího seznamu tlačítka rozdělení. Příklad nahradí směřující nahoru piktogram trojúhelník pro směřující dolů trojúhelník glyfu. Glyf, který se zobrazí, závisí na znak, který jste zadali v `himlGlyph` člena `BUTTON_SPLITINFO` struktury. Trojúhelník piktogram směřující dolů je určená znak "6"a trojúhelník piktogram směřující nahoru je určená znak "5". Porovnání najdete v tématu metodu pohodlí [CButton::SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

##  <a name="setsplitsize"></a>  CButton::SetSplitSize

Nastaví ohraničující obdélník rozevíracího seznamu součástí aktuální tlačítko rozdělení ovládání.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pSize*|[in] Ukazatel [velikost](https://msdn.microsoft.com/library/windows/desktop/dd145106) struktura, která popisuje ohraničující obdélník.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Po rozbalení ovládacího prvku tlačítko rozdělení může zobrazit rozevírací seznam součást, například ovládací prvek seznamu nebo ovládací prvek stránkování. Tato metoda určuje velikost ohraničující obdélník, který obsahuje komponentu rozevíracího seznamu.

Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktura s příznakem BCSIF_SIZE a `size` člena s *pSize* parametr a potom odešle, které struktury v [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_splitButton`, která je použita k programovému přístupu ke tlačítko rozdělení ovládání. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu zdvojnásobuje velikost na šipku rozevíracího seznamu tlačítko rozdělení.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

##  <a name="setsplitstyle"></a>  CButton::SetSplitStyle

Nastaví styl aktuální tlačítko rozdělení ovládání.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*uSplitStyle*|[in] Bitová kombinace hodnot styly tlačítka rozdělení. Další informace najdete v tématu `uSplitStyle` člena [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu lze používejte pouze s ovládacími prvky, jehož styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Styly tlačítek rozdělení zadejte zarovnání, poměr stran a grafické podobě, pomocí kterého Windows nakreslí ikonu tlačítka rozdělení. Další informace najdete v tématu `uSplitStyle` člena [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktury.

Tato metoda inicializuje `mask` členem [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) struktura s příznakem BCSIF_STYLE a `uSplitStyle` člena s *uSplitStyle* parametr a pak odešle struktury v [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_splitButton`, která je použita k programovému přístupu ke tlačítko rozdělení ovládání.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví styl šipky rozevírací tlačítko rozdělení. Styl BCSS_ALIGNLEFT zobrazí na šipku nalevo od tlačítka a styl BCSS_STRETCH zachová poměr stran na šipku rozevíracího seznamu při změně velikosti na tlačítko.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

##  <a name="setstate"></a>  CButton::SetState

Nastaví, zda ovládací prvek tlačítko je zvýrazněn, nebo ne.

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bHighlight*<br/>
Určuje, zda tlačítko je zvýrazněn. Nenulová hodnota zvýrazní tlačítko; Hodnota 0 odebere všechny zvýraznění.

### <a name="remarks"></a>Poznámky

Zvýraznění má vliv na vnější ovládací prvek tlačítko. Nemá žádný vliv na stav zaškrtávací políčko nebo přepínací tlačítka.

Ovládací prvek tlačítko je zvýrazněn automaticky, když uživatel klikne na tlačítko a obsahuje levé tlačítko myši. Zvýraznění se odebere, když uživatel uvolní tlačítko myši.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="settextmargin"></a>  CButton::SetTextMargin

Voláním této metody lze nastavit okraj textu `CButton` objektu.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parametry

*pmargin*<br/>
Ukazatel na novou okraj textu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkčnost BCM_SETTEXTMARGIN zprávu, jak je popsáno v [tlačítka](https://msdn.microsoft.com/library/windows/desktop/bb775943) část sady Windows SDK.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox – třída](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic – třída](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton – třída](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
