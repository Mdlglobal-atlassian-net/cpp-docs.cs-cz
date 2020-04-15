---
title: CButton – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 05ad60855cd03115cf88ab2b51e56e6a26822035
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352449"
---
# <a name="cbutton-class"></a>CButton – třída

Poskytuje funkce ovládacích prvků tlačítek systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CButton : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CButton::CButton](#cbutton)|Vytvoří `CButton` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CButton::Vytvořit](#create)|Vytvoří ovládací prvek tlačítka systému `CButton` Windows a připojí jej k objektu.|
|[CButton::DsurItem](#drawitem)|Přepsánína nakreslit `CButton` objekt nakreslený vlastníkem.|
|[CButton::GetBitmap](#getbitmap)|Načte popisovač rastrového mapu dříve nastaveného pomocí [setBitmap](#setbitmap).|
|[CButton::GetButtonStyle](#getbuttonstyle)|Načte informace o stylu ovládacího prvku tlačítka.|
|[CButton::GetCheck](#getcheck)|Načte stav kontroly ovládacího prvku tlačítka.|
|[CButton::GetCursor](#getcursor)|Načte popisovač obrázku kurzoru dříve nastavené s [SetCursor](#setcursor).|
|[CButton::GetIcon](#geticon)|Načte popisovač ikony dříve nastavené pomocí [funkce SetIcon](#seticon).|
|[CButton::GetIdealSize](#getidealsize)|Načte ideální velikost ovládacího prvku tlačítka.|
|[CButton::GetImageList](#getimagelist)|Načte seznam obrázků ovládacího prvku tlačítka.|
|[CButton::GetNote](#getnote)|Načte komponentu poznámky aktuálního ovládacího prvku propojení příkazů.|
|[CButton::GetNoteLength](#getnotelength)|Načte délku textu poznámky pro aktuální ovládací prvek propojení příkazů.|
|[CButton::GetSplitGlyph](#getsplitglyph)|Načte glyf přidružený k aktuálnímu ovládacímu prvku tlačítka rozdělení.|
|[CButton::GetSplitImageList](#getsplitimagelist)|Načte seznam obrázků pro aktuální ovládací prvek tlačítka rozdělení.|
|[CButton::GetSplitInfo](#getsplitinfo)|Načte informace, které definují aktuální ovládací prvek tlačítka rozdělení.|
|[CButton::GetSplitSize](#getsplitsize)|Načte ohraničovací obdélník rozevírací součásti aktuálního ovládacího prvku tlačítka rozdělení.|
|[CButton::GetSplitStyle](#getsplitstyle)|Načte styly rozdělených tlačítek, které definují aktuální ovládací prvek tlačítka rozdělení.|
|[CButton::GetState](#getstate)|Načte stav kontroly, zvýrazní stav a zaostří na ovládací prvek tlačítka.|
|[CButton::GetTextMargin](#gettextmargin)|Načte textový okraj ovládacího prvku tlačítka.|
|[CButton::SetBitmap](#setbitmap)|Určuje bitmapu, která má být zobrazena na tlačítku.|
|[CButton::SetButtonStyle](#setbuttonstyle)|Změní styl tlačítka.|
|[CButton::SetCheck](#setcheck)|Nastaví stav kontroly ovládacího prvku tlačítka.|
|[CButton::SetCursor](#setcursor)|Určuje obrázek kurzoru, který se má zobrazit na tlačítku.|
|[CButton::SetDropDownState](#setdropdownstate)|Nastaví rozevírací stav aktuálního ovládacího prvku tlačítka rozdělení.|
|[CButton::SetIcon](#seticon)|Určuje ikonu, která se má na tlačítku zobrazit.|
|[CButton::SetImageList](#setimagelist)|Nastaví seznam obrázků ovládacího prvku tlačítka.|
|[CButton::SetNote](#setnote)|Nastaví poznámku v aktuálním ovládacím prvku propojení příkazů.|
|[CButton::SetSplitGlyph](#setsplitglyph)|Přidruží zadaný glyf k aktuálnímu ovládacímu prvku tlačítka rozdělení.|
|[CButton::SetSplitImageList](#setsplitimagelist)|Přidruží seznam obrázků k aktuálnímu ovládacímu prvku tlačítka rozdělení.|
|[CButton::SetSplitInfo](#setsplitinfo)|Určuje informace, které definují aktuální ovládací prvek tlačítka rozdělení.|
|[CButton::SetSplitSize](#setsplitsize)|Nastaví ohraničovací obdélník rozevírací součásti aktuálního ovládacího prvku tlačítka rozdělení.|
|[CButton::SetSplitStyle](#setsplitstyle)|Nastaví styl aktuálního ovládacího prvku tlačítka rozdělení.|
|[CButton::SetState](#setstate)|Nastaví stav zvýraznění ovládacího prvku tlačítka.|
|[CButton::SetTextMargin](#settextmargin)|Nastaví textový okraj ovládacího prvku tlačítka.|

## <a name="remarks"></a>Poznámky

Ovládací prvek tlačítka je malé obdélníkové podřízené okno, na které lze klepnout. Tlačítka lze použít samostatně nebo ve skupinách a mohou být označena nebo zobrazena bez textu. Tlačítko obvykle změní vzhled, když na něj uživatel klepne.

Typická tlačítka jsou zaškrtávací políčko, přepínací tlačítko a tlačítko. Objekt `CButton` se může stát libovolným z těchto, podle [stylu tlačítka](../../mfc/reference/styles-used-by-mfc.md#button-styles) určeného při jeho inicializaci členovou funkcí [Create.](#create)

Kromě toho třída [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) odvozená z `CButton` podporuje vytváření ovládacích prvků tlačítek označených bitmapovými obrazy namísto textu. A `CBitmapButton` může mít samostatné rastrové obrázky pro tlačítka nahoru, dolů, zaměřené a zakázané stavy.

Ovládací prvek tlačítka můžete vytvořit buď ze šablony dialogového okna, nebo přímo v kódu. V obou případech nejprve `CButton` volání konstruktoru k vytvoření objektu; `CButton` potom volání `Create` členské funkce k vytvoření ovládacího prvku `CButton` tlačítka systému Windows a připojit jej k objektu.

Konstrukce může být jednostupňový proces ve `CButton`třídě odvozené z . Napište konstruktor pro odvozené `Create` třídy a volání z uvnitř konstruktoru.

Pokud chcete zpracovat zprávy oznámení systému Windows odeslané ovládacím prvkem tlačítka jeho nadřazené (obvykle třídy odvozené z [CDialog](../../mfc/reference/cdialog-class.md)), přidejte položku mapy zprávy a členskou funkci obslužné rutiny zprávy do nadřazené třídy pro každou zprávu.

Každá položka mapy zpráv má následující podobu:

**ON\_**_Oznámení_ **(** _id_, _memberFxn_ **)**

kde *id* určuje ID podřízeného okna ovládacího prvku odesílání oznámení a *memberFxn* je název nadřazené členské funkce, kterou jste napsali pro zpracování oznámení.

Prototyp funkce nadřazeného objektu je následující:

`afx_msg void memberFxn();`

Potenciální položky mapy zpráv jsou následující:

|Položka mapy|Odesláno rodiči, když...|
|---------------|----------------------------|
|ON_BN_CLICKED|Uživatel klepne na tlačítko.|
|ON_BN_DOUBLECLICKED|Uživatel poklepe na tlačítko.|

Pokud vytvoříte `CButton` objekt z prostředku `CButton` dialogu, objekt se automaticky zničí, když uživatel zavře dialogové okno.

Pokud vytvoříte `CButton` objekt v okně, bude pravděpodobně nutné jej zničit. Pokud vytvoříte `CButton` objekt na haldě pomocí **nové** funkce, musíte volat **delete** na objekt zničit, když uživatel zavře ovládací prvek tlačítka systému Windows. Pokud vytvoříte `CButton` objekt v zásobníku nebo je vložen do nadřazeného dialogového okna, bude automaticky zničen.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cbuttoncbutton"></a><a name="cbutton"></a>CButton::CButton

Vytvoří `CButton` objekt.

```
CButton();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

## <a name="cbuttoncreate"></a><a name="create"></a>CButton::Vytvořit

Vytvoří ovládací prvek tlačítka systému `CButton` Windows a připojí jej k objektu.

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszTitulek*<br/>
Určuje text ovládacího prvku tlačítka.

*dwStyl*<br/>
Určuje styl ovládacího prvku tlačítka. Na tlačítko použijte libovolnou kombinaci [stylů tlačítek.](../../mfc/reference/styles-used-by-mfc.md#button-styles)

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku tlačítka. Může to být `CRect` objekt `RECT` nebo struktura.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího `CDialog`prvku tlačítka, obvykle . Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku tlačítka.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CButton` dvou krocích. Nejprve zavolejte konstruktoru `Create`a potom volání , který vytvoří `CButton` ovládací prvek tlačítka systému Windows a připojí jej k objektu.

Pokud je uveden styl WS_VISIBLE, systém Windows odešle ovládací prvek tlačítka všechny zprávy potřebné k aktivaci a zobrazení tlačítka.

U ovládacího prvku tlačítka použijte následující [styly oken:](../../mfc/reference/styles-used-by-mfc.md#window-styles)

- WS_CHILD vždy

- WS_VISIBLE Obvykle

- WS_DISABLED Zřídka

- WS_GROUP Chcete-li seskupit ovládací prvky

- WS_TABSTOP Chcete-li zahrnout tlačítko v pořadí tabulátorů

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

## <a name="cbuttondrawitem"></a><a name="drawitem"></a>CButton::DsurItem

Volat rámci při vizuální aspekt nakreslené ho vlastníka tlačítko se změnilo.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhý ukazatel na [drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) struktury. Struktura obsahuje informace o položce, která má být vykreslena, a o typu požadovaného výkresu.

### <a name="remarks"></a>Poznámky

Tlačítko nakreslené vlastníkem má sadu BS_OWNERDRAW stylu. Přepište tuto členovou funkci a implementujte výkres pro objekt nakreslený `CButton` vlastníkem. Aplikace by měla obnovit všechny objekty rozhraní grafického zařízení (GDI) vybrané pro kontext zobrazení dodaný v *lpDrawItemStruct* před ukončením členské funkce.

Viz také [hodnoty stylu BS_.](../../mfc/reference/styles-used-by-mfc.md#button-styles)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

## <a name="cbuttongetbitmap"></a><a name="getbitmap"></a>CButton::GetBitmap

Volání této členské funkce získat popisovač rastrového mapu, dříve nastavena s [SetBitmap](#setbitmap), který je spojen s tlačítkem.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Návratová hodnota

Úchyt rastrového plánu. NULL, pokud není dříve zadána žádná bitmapa.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttongetbuttonstyle"></a><a name="getbuttonstyle"></a>CButton::GetButtonStyle

Načte informace o stylu ovládacího prvku tlačítka.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí styly tlačítek `CButton` pro tento objekt. Tato funkce vrátí pouze [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) hodnoty stylu, nikoli žádný z ostatních stylů okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttongetcheck"></a><a name="getcheck"></a>CButton::GetCheck

Načte stav zaškrtnutí přepínacího tlačítka nebo zaškrtávacího políčka.

```
int GetCheck() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota z ovládacího prvku tlačítka vytvořeného pomocí stylu BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON nebo BS_3STATE je jednou z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|BST_UNCHECKED|Stav tlačítka není zaškrtnut.|
|BST_CHECKED|Je zaškrtnut stav tlačítka.|
|BST_INDETERMINATE|Stav tlačítka je neurčitý (platí pouze v případě, že tlačítko má BS_3STATE nebo BS_AUTO3STATE stylu).|

Pokud má tlačítko jiný styl, vrácená hodnota je BST_UNCHECKED.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttongetcursor"></a><a name="getcursor"></a>CButton::GetCursor

Volání této členské funkce získat popisovač kurzoru, dříve nastavena s [SetCursor](#setcursor), který je spojen s tlačítkem.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Návratová hodnota

Úchyt k obrázku kurzoru. Null, pokud je dříve zadán žádný kurzor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttongeticon"></a><a name="geticon"></a>CButton::GetIcon

Volání této členské funkce získat popisovač ikony, dříve nastavena s [SetIcon](#seticon), který je přidružen k tlačítku.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Návratová hodnota

Úchyt k ikoně. Null, pokud není dříve zadána žádná ikona.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttongetidealsize"></a><a name="getidealsize"></a>CButton::GetIdealSize

Načte ideální velikost pro ovládací prvek tlačítka.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Parametry

*pvelikost*<br/>
Ukazatel na aktuální velikost tlačítka.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce BCM_GETIDEALSIZE zprávy, jak je popsáno v části [Tlačítka](/windows/win32/controls/buttons) sady Windows SDK.

## <a name="cbuttongetimagelist"></a><a name="getimagelist"></a>CButton::GetImageList

Volání této metody získat seznam obrázků z ovládacího prvku tlačítka.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parametry

*pbuttonImagelist*<br/>
Ukazatel na seznam obrázků `CButton` objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce zprávy BCM_GETIMAGELIST, jak je popsáno v části [Tlačítka](/windows/win32/controls/buttons) sady Windows SDK.

## <a name="cbuttongetnote"></a><a name="getnote"></a>CButton::GetNote

Načte text poznámky přidružený k aktuálnímu ovládacímu prvku propojení příkazů.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpszPoznámka*|[out] Ukazatel na vyrovnávací paměť, která volající je zodpovědný za přidělení a zrušení přidělení. Pokud je vrácená hodnota TRUE, vyrovnávací paměť obsahuje text poznámky, který je přidružen k aktuálnímu ovládacímu prvku propojení příkazů; v opačném případě vyrovnávací paměti je beze změny.|
|*cchPoznámka*|[dovnitř, ven] Ukazatel na nepodepsanou integer ovou proměnnou.<br /><br /> Při volání této metody proměnná obsahuje velikost vyrovnávací paměti určené parametrem *lpszNote.*<br /><br /> Pokud je tato metoda vrácená hodnota PRAVDA, proměnná obsahuje velikost poznámky přidružené k aktuálnímu ovládacímu prvku propojení příkazů. Pokud je vrácená hodnota FALSE, proměnná obsahuje velikost vyrovnávací paměti požadovanou k zobrazení poznámky.|

### <a name="return-value"></a>Návratová hodnota

V prvním přetížení [CString](../../atl-mfc-shared/using-cstring.md) objekt, který obsahuje text poznámky spojené s aktuální ovládací prvek propojení příkazu.

-nebo-

V druhé přetížení TRUE Pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_COMMANDLINK nebo BS_DEFCOMMANDLINK.

Tato metoda odešle [zprávu BCM_GETNOTE,](/windows/win32/Controls/bcm-getnote) která je popsána v sadě Windows SDK.

## <a name="cbuttongetnotelength"></a><a name="getnotelength"></a>CButton::GetNoteLength

Načte délku textu poznámky pro aktuální ovládací prvek propojení příkazů.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka textu poznámky v 16bitových znacích Unicode pro aktuální ovládací prvek propojení příkazů.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_COMMANDLINK nebo BS_DEFCOMMANDLINK.

Tato metoda odešle [zprávu BCM_GETNOTELENGTH,](/windows/win32/Controls/bcm-getnotelength) která je popsána v sadě Windows SDK.

## <a name="cbuttongetsplitglyph"></a><a name="getsplitglyph"></a>CButton::GetSplitGlyph

Načte glyf přidružený k aktuálnímu ovládacímu prvku tlačítka rozdělení.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Návratová hodnota

Znak glyfu přidružený k aktuálnímu ovládacímu prvku tlačítka rozdělení.

### <a name="remarks"></a>Poznámky

Glyf je fyzická reprezentace znaku v určitém písmu. Ovládací prvek rozděleného tlačítka může být například zdoben glyfem znaku zaškrtnutí unicode (U + 2713).

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda inicializuje `mask` člen [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury s příznakem BCSIF_GLYPH a potom odešle tuto strukturu v [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávy, která je popsána v sadě Windows SDK. Když funkce zprávy vrátí, tato metoda načte glyf z `himlGlyph` člena struktury.

## <a name="cbuttongetsplitimagelist"></a><a name="getsplitimagelist"></a>CButton::GetSplitImageList

Načte [seznam obrázků](../../mfc/reference/cimagelist-class.md) pro aktuální ovládací prvek tlačítka rozdělení.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CImageList.](../../mfc/reference/cimagelist-class.md)

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda inicializuje `mask` člen [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury s příznakem BCSIF_IMAGE a potom odešle tuto strukturu ve [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávy, která je popsána v sadě Windows SDK. Když funkce zprávy vrátí, tato metoda načte `himlGlyph` seznam obrázků z člena struktury.

## <a name="cbuttongetsplitinfo"></a><a name="getsplitinfo"></a>CButton::GetSplitInfo

Načte parametry, které určují, jak systém Windows nakreslí aktuální ovládací prvek tlačítka rozdělení.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pInformace*|[out] Ukazatel na [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) strukturu, která přijímá informace o aktuálním ovládacím prvku tlačítka rozdělení. Volající je zodpovědný za přidělení struktury.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda odešle [zprávu BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) která je popsána v sadě Windows SDK.

## <a name="cbuttongetsplitsize"></a><a name="getsplitsize"></a>CButton::GetSplitSize

Načte ohraničovací obdélník rozevírací součásti aktuálního ovládacího prvku tlačítka rozdělení.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pVelikost*|[out] Ukazatel na [size](/windows/win32/api/windef/ns-windef-size) strukturu, která obdrží popis obdélníku.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Když je ovládací prvek rozdělit tlačítko rozbalen, může zobrazit rozevírací součást, jako je ovládací prvek seznamu nebo ovládací prvek operátoru. Tato metoda načte ohraničující obdélník, který obsahuje rozevírací součást.

Tato metoda inicializuje `mask` člen [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury s příznakem BCSIF_SIZE a potom odešle tuto strukturu v [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávy, která je popsána v sadě Windows SDK. Když funkce zprávy vrátí, tato metoda načte `size` ohraničující obdélník z člena struktury.

## <a name="cbuttongetsplitstyle"></a><a name="getsplitstyle"></a>CButton::GetSplitStyle

Načte styly rozdělených tlačítek, které definují aktuální ovládací prvek tlačítka rozdělení.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová kombinace stylů rozdělených tlačítek. Další informace naleznete `uSplitStyle` v člen [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Styly rozdělených tlačítek určují zarovnání, poměr stran a grafický formát, s nimiž systém Windows nakreslí ikonu rozděleného tlačítka.

Tato metoda inicializuje `mask` člen [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury s příznakem BCSIF_STYLE a potom odešle tuto strukturu v [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávy, která je popsána v sadě Windows SDK. Když funkce zprávy vrátí, tato metoda načte `uSplitStyle` styly rozděleného tlačítka z člena struktury.

## <a name="cbuttongetstate"></a><a name="getstate"></a>CButton::GetState

Načte stav ovládacího prvku tlačítka.

```
UINT GetState() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitové pole, které obsahuje kombinaci hodnot, které označují aktuální stav ovládacího prvku tlačítka. V následující tabulce jsou uvedeny možné hodnoty.

|Stav tlačítka|Hodnota|Popis|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|Počáteční stav.|
|BST_CHECKED|0x0001|Ovládací prvek tlačítka je zaškrtnut.|
|BST_INDETERMINATE|0x0002|Stav je neurčitý (je to možné pouze v případě, že ovládací prvek tlačítka má tři stavy).|
|BST_PUSHED|0x0004|Stisknese ovládací prvek tlačítka.|
|BST_FOCUS|0x0008|Ovládací prvek tlačítka má fokus.|

### <a name="remarks"></a>Poznámky

Ovládací prvek tlačítka se stylem BS_3STATE nebo BS_AUTO3STATE tlačítka vytvoří zaškrtávací políčko, které má třetí stav s názvem Neurčitý stav. Neurčitý stav označuje, že zaškrtávací políčko není zaškrtnuto ani nezaškrtnuto.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttongettextmargin"></a><a name="gettextmargin"></a>CButton::GetTextMargin

Volání této metody získat textový `CButton` okraj objektu.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parametry

*pmargin*<br/>
Ukazatel na textový okraj `CButton` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí textový okraj.

### <a name="remarks"></a>Poznámky

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce zprávy BCM_GETTEXTMARGIN, jak je popsáno v části [Tlačítka](/windows/win32/controls/buttons) sady Windows SDK.

## <a name="cbuttonsetbitmap"></a><a name="setbitmap"></a>CButton::SetBitmap

Volání této členské funkce přidružit novou bitmapu s tlačítkem.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Popisovač rastrového obrázek.

### <a name="return-value"></a>Návratová hodnota

Popisovač rastrového plánu dříve přidruženého k tlačítku.

### <a name="remarks"></a>Poznámky

Bitmapa bude automaticky umístěna na plochu tlačítka, ve výchozím nastavení vystředěná. Pokud je bitmapa pro tlačítko příliš velká, bude oříznuta na obou stranách. Můžete zvolit další možnosti zarovnání, včetně následujících možností:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Na rozdíl od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), který `SetBitmap` používá čtyři bitmapy na tlačítko, používá pouze jednu bitmapu na tlačítko. Po stisknutí tlačítka se zobrazí bitmapa, která se posune dolů a doprava.

Jste zodpovědní za uvolnění rastrového mapu, když jste hotovi s ním.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttonsetbuttonstyle"></a><a name="setbuttonstyle"></a>CButton::SetButtonStyle

Změní styl tlačítka.

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nStyl*<br/>
Určuje [styl tlačítka](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bPřekreslit*<br/>
Určuje, zda má být tlačítko překresleno. Nenulová hodnota překreslí tlačítko. Hodnota 0 nepřekreslí tlačítko. Tlačítko je ve výchozím nastavení překresleno.

### <a name="remarks"></a>Poznámky

Pomocí `GetButtonStyle` členské funkce načtěte styl tlačítka. Slovo nízkého řádu celého stylu tlačítka je styl specifický pro tlačítko.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttonsetcheck"></a><a name="setcheck"></a>CButton::SetCheck

Nastaví nebo obnoví stav zaškrtnutí přepínacího tlačítka nebo zaškrtávacího políčka.

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parametry

*nKontrola*<br/>
Určuje stav kontroly. Tento parametr může být jeden z následujících:

|Hodnota|Význam|
|-----------|-------------|
|BST_UNCHECKED|Nastavte stav tlačítka na nezaškrtnutý.|
|BST_CHECKED|Nastavte stav tlačítka na zaškrtnutí.|
|BST_INDETERMINATE|Nastavte stav tlačítka na neurčitý. Tuto hodnotu lze použít pouze v případě, že tlačítko má styl BS_3STATE nebo BS_AUTO3STATE.|

### <a name="remarks"></a>Poznámky

Tato členská funkce nemá žádný vliv na tlačítko.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttonsetcursor"></a><a name="setcursor"></a>CButton::SetCursor

Volání této členské funkce přidružit nový kurzor s tlačítkem.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parametry

*hKurzor*<br/>
Úchyt kurzoru.

### <a name="return-value"></a>Návratová hodnota

Popisovač kurzoru dříve přidružené k tlačítku.

### <a name="remarks"></a>Poznámky

Kurzor bude automaticky umístěn na ploše tlačítka, ve výchozím nastavení vystředěný. Pokud je kurzor pro tlačítko příliš velký, bude oříznut na obou stranách. Můžete zvolit další možnosti zarovnání, včetně následujících možností:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Na rozdíl od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), který `SetCursor` používá čtyři bitmapy na tlačítko, používá pouze jeden kurzor na tlačítko. Po stisknutí tlačítka se kurzor posune dolů a doprava.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttonsetdropdownstate"></a><a name="setdropdownstate"></a>CButton::SetDropDownState

Nastaví rozevírací stav aktuálního ovládacího prvku tlačítka rozdělení.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*fDropDown*|[v] TRUE pro nastavení BST_DROPDOWNPUSHED stavu; jinak NEPRAVDA.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Ovládací prvek rozděleného tlačítka má styl BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON a skládá se z tlačítka a rozevírací šipky vpravo. Další informace naleznete v [tématu Styly tlačítek](/windows/win32/Controls/button-styles). Obvykle je stav rozevíracího seznamu nastaven, když uživatel klepne na šipku rozevíracího seznamu. Pomocí této metody můžete programově nastavit rozevírací stav ovládacího prvku. Rozevírací šipka je nakreslena stínově, aby se označil stav.

Tato metoda odešle [zprávu BCM_SETDROPDOWNSTATE,](/windows/win32/Controls/bcm-setdropdownstate) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou *m_splitButton*, která se používá k programovému přístupu k ovládacímu prvku tlačítka rozdělení. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví stav ovládacího prvku rozdělit tlačítko označuje, že šipka rozevíracího seznamu je stisknuto.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

## <a name="cbuttonsetelevationrequired"></a><a name="setelevationrequired"></a>CButton::Nastavit zvýšení oprávněníPožadováno

Nastaví stav aktuálního ovládacího prvku tlačítka na `elevation required`, což je nezbytné pro zobrazení ikony zabezpečení se zvýšenými oprávněními.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*fElevationRequired*|[v] TRUE pro `elevation required` nastavení stavu; jinak NEPRAVDA.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud ovládací prvek tlačítka nebo propojení příkazů vyžaduje oprávnění se zvýšeným `elevation required` zabezpečením k provedení akce, nastavte ovládací prvek na stav. Následně systém Windows zobrazí ikonu štítu řízení uživatelských účtů (UAC) na ovládacím prvku. Další informace naleznete v tématu "Řízení uživatelských účtů" na [msdn](https://go.microsoft.com/fwlink/p/?linkid=18507).

Tato metoda odešle [zprávu BCM_SETSHIELD,](/windows/win32/Controls/bcm-setshield) která je popsána v sadě Windows SDK.

## <a name="cbuttonseticon"></a><a name="seticon"></a>CButton::SetIcon

Volání této členské funkce přidružit novou ikonu s tlačítkem.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*hIkona*<br/>
Popisovač ikony.

### <a name="return-value"></a>Návratová hodnota

Popisovač ikony dříve přidružené k tlačítku.

### <a name="remarks"></a>Poznámky

Ikona bude automaticky umístěna na ploše tlačítka, ve výchozím nastavení vystředěna. Pokud je ikona pro tlačítko příliš velká, bude oříznuta na obou stranách. Můžete zvolit další možnosti zarovnání, včetně následujících možností:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Na rozdíl od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), který `SetIcon` používá čtyři bitmapy na tlačítko, používá pouze jednu ikonu na tlačítko. Po stisknutí tlačítka se ikona zobrazí, aby se posunula dolů a doprava.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttonsetimagelist"></a><a name="setimagelist"></a>CButton::SetImageList

Volání této metody nastavit seznam `CButton` obrázků objektu.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parametry

*pbuttonImagelist*<br/>
Ukazatel na nový seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce zprávy BCM_SETIMAGELIST, jak je popsáno v části [Tlačítka](/windows/win32/controls/buttons) sady Windows SDK.

## <a name="cbuttonsetnote"></a><a name="setnote"></a>CButton::SetNote

Nastaví text poznámky pro aktuální ovládací prvek spojnice příkazů.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpszPoznámka*|[v] Ukazatel na řetězec Unicode, který je nastaven jako text poznámky pro ovládací prvek propojení příkazů.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_COMMANDLINK nebo BS_DEFCOMMANDLINK.

Tato metoda odešle [zprávu BCM_SETNOTE,](/windows/win32/Controls/bcm-setnote) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou *m_cmdLink*, která se používá k programovému přístupu k ovládacímu prvku propojení příkazů. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví text poznámky pro ovládací prvek propojení příkazů.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

## <a name="cbuttonsetsplitglyph"></a><a name="setsplitglyph"></a>CButton::SetSplitGlyph

Přidruží zadaný glyf k aktuálnímu ovládacímu prvku tlačítka rozdělení.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*chGlyph*|[v] Znak, který určuje glyf, který se má použít jako šipka rozevíracího seznamu tlačítka rozdělení.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, které mají styl tlačítka BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Glyf je fyzická reprezentace znaku v určitém písmu. Parametr *chGlyph* se nepoužívá jako glyf, ale místo toho se používá k výběru glyfu ze sady systémově definovaných glyfů. Výchozí glyf rozevírací šipky je určen znakem "6" a podobá se znaku Unicode BLACK DOWN-POINTING TRIANGLE (U + 25 BC).

Tato metoda `mask` inicializuje člen [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury s příznakem BCSIF_GLYPH a `himlGlyph` člen s *parametrem chGlyph* a potom odešle tuto strukturu v [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávy, která je popsána v sadě Windows SDK.

## <a name="cbuttonsetsplitimagelist"></a><a name="setsplitimagelist"></a>CButton::SetSplitImageList

Přidruží [seznam obrázků](../../mfc/reference/cimagelist-class.md) k aktuálnímu ovládacímu prvku tlačítka rozdělení.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*seznam pSplitImageList*|[v] Ukazatel na [cImageList](../../mfc/reference/cimagelist-class.md) objekt přiřadit aktuální ovládací prvek rozdělit tlačítko.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda `mask` inicializuje člen [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury s příznakem BCSIF_IMAGE a `himlGlyph` člen s parametrem *pSplitImageList* a potom odešle tuto strukturu ve [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávě, která je popsána v sadě Windows SDK.

## <a name="cbuttonsetsplitinfo"></a><a name="setsplitinfo"></a>CButton::SetSplitInfo

Určuje parametry, které určují, jak systém Windows nakreslí aktuální ovládací prvek tlačítka rozdělení.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pInformace*|[v] Ukazatel na [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) strukturu, která definuje aktuální ovládací prvek tlačítka rozdělení.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda odešle [zprávu BCM_SETSPLITINFO,](/windows/win32/Controls/bcm-setsplitinfo) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_splitButton`která se používá k programovému přístupu k ovládacímu prvku tlačítka rozdělení.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu změní glyf, který se používá pro šipku rozevíracího seznamu rozdělovací tlačítka. Příklad nahradí glyf trojúhelníku směřujícím nahoru pro výchozí glyf trojúhelníku směřujícího dolů. Symbol glyfu, který se zobrazí, `himlGlyph` závisí na `BUTTON_SPLITINFO` znaku, který zadáte v členu struktury. Glyf trojúhelníku směřujícího dolů je určen znakem "6" a glyf směřující nahoru je určen znakem "5". Pro srovnání naleznete v metodě pohodlí [CButton::SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

## <a name="cbuttonsetsplitsize"></a><a name="setsplitsize"></a>CButton::SetSplitSize

Nastaví ohraničovací obdélník rozevírací součásti aktuálního ovládacího prvku tlačítka rozdělení.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pVelikost*|[v] Ukazatel na [size](/windows/win32/api/windef/ns-windef-size) strukturu, která popisuje ohraničující obdélník.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Když je ovládací prvek rozdělit tlačítko rozbalen, může zobrazit rozevírací součást, jako je ovládací prvek seznamu nebo ovládací prvek operátoru. Tato metoda určuje velikost ohraničujícího obdélníku, který obsahuje rozevírací součást.

Tato metoda `mask` inicializuje člen [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury s příznakem BCSIF_SIZE a `size` člen s parametrem *pSize* a potom odešle tuto strukturu v [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávě popsané v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_splitButton`která se používá k programovému přístupu k ovládacímu prvku tlačítka rozdělení. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu zdvojnásobuje velikost šipky rozevíracího seznamu rozděleného tlačítka.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

## <a name="cbuttonsetsplitstyle"></a><a name="setsplitstyle"></a>CButton::SetSplitStyle

Nastaví styl aktuálního ovládacího prvku tlačítka rozdělení.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*uSplitStyle*|[v] Bitová kombinace stylů rozdělených tlačítek. Další informace naleznete `uSplitStyle` v člen [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Styly rozdělených tlačítek určují zarovnání, poměr stran a grafický formát, s nimiž systém Windows nakreslí ikonu rozděleného tlačítka. Další informace naleznete `uSplitStyle` v člen [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury.

Tato metoda `mask` inicializuje člen [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) struktury s příznakem BCSIF_STYLE a `uSplitStyle` člen s parametrem *uSplitStyle* a potom odešle tuto strukturu ve [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávě popsané v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_splitButton`která se používá k programovému přístupu k ovládacímu prvku tlačítka rozdělení.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví styl šipky rozevíracího seznamu rozděleného tlačítka. Styl BCSS_ALIGNLEFT zobrazí šipku na levé straně tlačítka a styl BCSS_STRETCH zachová proporce šipky rozevíracího seznamu při změně velikosti tlačítka.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

## <a name="cbuttonsetstate"></a><a name="setstate"></a>CButton::SetState

Nastaví, zda je ovládací prvek tlačítka zvýrazněn nebo ne.

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bZvýraznění*<br/>
Určuje, zda má být tlačítko zvýrazněno. Nenulová hodnota zvýrazní tlačítko; hodnota 0 odebere jakékoli zvýraznění.

### <a name="remarks"></a>Poznámky

Zvýraznění ovlivňuje vnější část ovládacího prvku tlačítka. Nemá žádný vliv na stav zaškrtnutí přepínacího tlačítka nebo zaškrtávacího políčka.

Ovládací prvek tlačítka se automaticky zvýrazní, když uživatel klikne a podrží levé tlačítko myši. Zvýraznění je odebráno, když uživatel uvolní tlačítko myši.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttonsettextmargin"></a><a name="settextmargin"></a>CButton::SetTextMargin

Volání této metody nastavit textový `CButton` okraj objektu.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parametry

*pmargin*<br/>
Ukazatel na nový textový okraj.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce zprávy BCM_SETTEXTMARGIN, jak je popsáno v části [Tlačítka](/windows/win32/controls/buttons) sady Windows SDK.

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Třída CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic – třída](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton – třída](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
