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
ms.openlocfilehash: 669bdb18e378c4dc39bdc6d51ca1ebe7f93fa839
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78870609"
---
# <a name="cbutton-class"></a>CButton – třída

Poskytuje funkce pro ovládací prvky tlačítek Windows.

## <a name="syntax"></a>Syntaxe

```
class CButton : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CButton:: CButton](#cbutton)|Vytvoří objekt `CButton`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CButton:: Create](#create)|Vytvoří ovládací prvek tlačítko Windows a připojí ho k objektu `CButton`.|
|[CButton::D rawItem](#drawitem)|Přepište pro vykreslení objektu `CButton` vykresleného vlastníkem.|
|[CButton:: getbitmapa](#getbitmap)|Načte popisovač rastrového obrázku dříve nastaveného pomocí [SetBitmap](#setbitmap).|
|[CButton:: GetButtonStyle](#getbuttonstyle)|Načte informace o stylu ovládacího prvku tlačítko.|
|[CButton:: getcheck](#getcheck)|Načte stav kontroly ovládacího prvku tlačítko.|
|[CButton:: GetCursor](#getcursor)|Načte popisovač obrázku kurzoru, který jste dříve nastavili pomocí [SetCursor](#setcursor).|
|[CButton:: GetIcon](#geticon)|Načte popisovač ikony dříve nastaveného pomocí [SetIcon](#seticon).|
|[CButton:: GetIdealSize](#getidealsize)|Načte ideální velikost ovládacího prvku tlačítko.|
|[CButton:: GetImageList](#getimagelist)|Načte seznam obrázků ovládacího prvku tlačítko.|
|[CButton:: getnote](#getnote)|Načte komponentu poznámky aktuálního ovládacího prvku odkazu na příkazy.|
|[CButton:: GetNoteLength](#getnotelength)|Načte délku textu poznámky pro aktuální ovládací prvek odkazu na příkazy.|
|[CButton:: GetSplitGlyph](#getsplitglyph)|Načte glyf přidružený k aktuálnímu ovládacímu prvku tlačítko rozdělení.|
|[CButton:: GetSplitImageList](#getsplitimagelist)|Načte seznam obrázků pro aktuální ovládací prvek tlačítko rozdělení.|
|[CButton:: GetSplitInfo](#getsplitinfo)|Načte informace, které definují aktuální ovládací prvek tlačítko rozdělení.|
|[CButton:: GetSplitSize](#getsplitsize)|Načte ohraničující obdélník rozbalovací součásti aktuálního ovládacího prvku tlačítko rozdělení.|
|[CButton:: GetSplitStyle](#getsplitstyle)|Načte styly rozděleného tlačítka, které definují aktuální ovládací prvek tlačítko rozdělení.|
|[CButton:: GetState](#getstate)|Načte kontrolní stav, stav zvýraznění a stav fokusu ovládacího prvku tlačítko.|
|[CButton:: GetTextMargin](#gettextmargin)|Načte okraj textu ovládacího prvku tlačítko.|
|[CButton:: SetBitmap](#setbitmap)|Určuje rastrový obrázek, který má být zobrazen na tlačítku.|
|[CButton:: SetButtonStyle](#setbuttonstyle)|Změní styl tlačítka.|
|[CButton:: SetCheck](#setcheck)|Nastaví stav kontroly ovládacího prvku tlačítko.|
|[CButton:: SetCursor](#setcursor)|Určuje obrázek kurzoru, který má být zobrazen na tlačítku.|
|[CButton:: SetDropDownState](#setdropdownstate)|Nastaví stav rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.|
|[CButton:: SetIcon](#seticon)|Určuje ikonu, která se má zobrazit na tlačítku.|
|[CButton:: SetImageList](#setimagelist)|Nastaví seznam obrázků ovládacího prvku tlačítko.|
|[CButton:: SetNote](#setnote)|Nastaví poznámku na aktuálním ovládacím prvku odkaz na příkazy.|
|[CButton:: SetSplitGlyph](#setsplitglyph)|Přidruží zadaný glyf k aktuálnímu ovládacímu prvku tlačítko rozdělení.|
|[CButton:: SetSplitImageList](#setsplitimagelist)|Přidruží seznam obrázků k aktuálnímu ovládacímu prvku tlačítko rozdělení.|
|[CButton:: SetSplitInfo](#setsplitinfo)|Určuje informace, které definují aktuální ovládací prvek tlačítko rozdělení.|
|[CButton:: SetSplitSize](#setsplitsize)|Nastaví ohraničující obdélník komponenty rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.|
|[CButton:: SetSplitStyle](#setsplitstyle)|Nastaví styl aktuálního ovládacího prvku tlačítko rozdělení.|
|[CButton:: SetState](#setstate)|Nastaví stav zvýraznění ovládacího prvku tlačítko.|
|[CButton:: SetTextMargin](#settextmargin)|Nastaví okraj textu ovládacího prvku tlačítko.|

## <a name="remarks"></a>Poznámky

Tlačítko je malé a pravoúhlé dceřiné okno, na které se dá kliknout a zapnout nebo vypnout. Tlačítka se dají použít samostatně nebo ve skupinách a můžou být buď označená, nebo se musí zobrazovat bez textu. Tlačítko obvykle mění vzhled, když na něj uživatel klikne.

Typická tlačítka jsou zaškrtávací políčko, přepínač a (pushbutton). Objekt `CButton` může být kterýkoli z těchto, podle [stylu tlačítka](../../mfc/reference/styles-used-by-mfc.md#button-styles) zadaného při inicializaci pomocí funkce [Create](#create) member.

Kromě toho třída [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) odvozená od `CButton` podporuje vytváření ovládacích prvků tlačítko s popisky rastrových obrázků namísto textu. `CBitmapButton` může mít samostatné rastrové obrázky pro nahoru, dolů, soustředěné a zakázané stavy tlačítka.

Ovládací prvek tlačítko lze vytvořit buď pomocí šablony dialogového okna, nebo přímo v kódu. V obou případech nejprve zavolejte konstruktor `CButton` pro vytvoření objektu `CButton`; Potom zavolejte členskou funkci `Create` pro vytvoření ovládacího prvku tlačítko Windows a připojte ho k objektu `CButton`.

Konstrukce může být proces jednoho kroku ve třídě odvozené z `CButton`. Napište konstruktor pro odvozenou třídu a zavolejte `Create` z konstruktoru.

Chcete-li zpracovat zprávy s oznámením systému Windows odeslané ovládacím prvkem tlačítko do své nadřazené položky (obvykle třída odvozená z [CDialog](../../mfc/reference/cdialog-class.md)), přidejte položku mapování zpráv a členskou funkci obslužné rutiny zpráv do nadřazené třídy pro každou zprávu.

Každá položka mapování zpráv má následující podobu:

**Oznámení o\_** **(** _ID_, _memberFxn_ **)**

kde *ID* Určuje ID podřízeného okna ovládacího prvku odesílajícího oznámení a *memberFxn* je název nadřazené členské funkce, kterou jste napsali pro zpracování oznámení.

Prototyp funkce nadřazeného objektu je následující:

`afx_msg void memberFxn();`

Možné položky mapy zpráv jsou následující:

|Položka mapování|Odesílá se do nadřazeného objektu, když...|
|---------------|----------------------------|
|ON_BN_CLICKED|Uživatel klikne na tlačítko.|
|ON_BN_DOUBLECLICKED|Uživatel dvakrát klikne na tlačítko.|

Vytvoříte-li objekt `CButton` z dialogového okna prostředku, je objekt `CButton` automaticky zničen, když uživatel zavře dialogové okno.

Pokud vytvoříte objekt `CButton` v rámci okna, může být nutné jej zničit. Vytvoříte-li objekt `CButton` v haldě pomocí **nové** funkce, je nutné volat metodu **Delete** u objektu, aby jej bylo možné zničit, když uživatel zavře ovládací prvek tlačítko systému Windows. Vytvoříte-li objekt `CButton` v zásobníku nebo je vložen do nadřazeného objektu dialogového okna, je automaticky zničen.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cbutton"></a>CButton:: CButton

Vytvoří objekt `CButton`.

```
CButton();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

##  <a name="create"></a>CButton:: Create

Vytvoří ovládací prvek tlačítko Windows a připojí ho k objektu `CButton`.

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
Určuje text ovládacího prvku tlačítko.

*dwStyle*<br/>
Určuje styl ovládacího prvku tlačítko. Pro tlačítko použijte libovolnou kombinaci [stylů tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles) .

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku tlačítko. Může to být buď objekt `CRect`, nebo struktura `RECT`.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku tlačítko, obvykle `CDialog`. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku tlačítko.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Objekt `CButton` vytvoříte ve dvou krocích. Nejprve volejte konstruktor a potom zavolejte `Create`, čímž se vytvoří ovládací prvek tlačítko Windows a připojí ho k objektu `CButton`.

Pokud je zadán styl WS_VISIBLE, program Windows pošle ovládací prvek tlačítko všechny zprávy vyžadované k aktivaci a zobrazení tlačítka.

Použijte následující [Styly okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) pro ovládací prvek tlačítko:

- WS_CHILD vždycky

- WS_VISIBLE obvykle

- WS_DISABLED zřídka

- WS_GROUP seskupení ovládacích prvků

- Do pořadí procházení WS_TABSTOP zahrnout tlačítko

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

##  <a name="drawitem"></a>CButton::D rawItem

Volá se rozhraním, když se změní vizuální aspekt tlačítka, které bylo vykresleno vlastníkem.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhý ukazatel na strukturu [DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) . Struktura obsahuje informace o položce, která se má vykreslit, a o požadovaném typu výkresu.

### <a name="remarks"></a>Poznámky

Tlačítko vykreslené vlastníkem má BS_OWNERDRAW sadu stylů. Přepište tuto členskou funkci pro implementaci vykreslování pro objekt `CButton` vykreslený vlastníkem. Aplikace by měla obnovit všechny objekty GDI (Graphic Device Interface) vybrané pro kontext zobrazení zadaný v *lpDrawItemStruct* před ukončením členské funkce.

Také se zobrazí hodnoty stylu [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

##  <a name="getbitmap"></a>CButton:: getbitmapa

Voláním této členské funkce získáte popisovač rastrového obrázku, který byl dříve nastaven pomocí [SetBitmap](#setbitmap), který je spojen s tlačítkem.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač rastrového obrázku. Hodnota NULL, pokud není předtím zadána žádná bitmapa.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="getbuttonstyle"></a>CButton:: GetButtonStyle

Načte informace o stylu ovládacího prvku tlačítko.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí styly tlačítek pro tento objekt `CButton`. Tato funkce vrátí pouze hodnoty stylu [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) , nikoli žádné jiné styly okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="getcheck"></a>CButton:: getcheck

Načte kontrolní stav přepínače nebo zaškrtávací políčko.

```
int GetCheck() const;
```

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota z ovládacího prvku tlačítko vytvořeného pomocí BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON nebo BS_3STATE stylu je jedna z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|BST_UNCHECKED|Stav tlačítka není zaškrtnuto.|
|BST_CHECKED|Stav tlačítka je zaškrtnuto.|
|BST_INDETERMINATE|Stav tlačítka je neurčitý (platí pouze v případě, že tlačítko má styl BS_3STATE nebo BS_AUTO3STATE).|

Pokud má tlačítko jiný styl, návratová hodnota je BST_UNCHECKED.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="getcursor"></a>CButton:: GetCursor

Voláním této členské funkce získáte popisovač kurzoru, který byl dříve nastaven pomocí [SetCursor](#setcursor), který je spojen s tlačítkem.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač obrázku kurzoru. Hodnota NULL, pokud není dříve zadána žádná pozice.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="geticon"></a>CButton:: GetIcon

Voláním této členské funkce získáte popisovač ikony, která byla dříve nastavena pomocí [SetIcon](#seticon), která je přidružena k tlačítku.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač ikony. Hodnota NULL, pokud není dříve zadána žádná ikona.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="getidealsize"></a>CButton:: GetIdealSize

Načte ideální velikost pro ovládací prvek tlačítko.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Parametry

*psize*<br/>
Ukazatel na aktuální velikost tlačítka.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce BCM_GETIDEALSIZE zprávy, jak je popsáno v části [tlačítka](/windows/win32/controls/buttons) Windows SDK.

##  <a name="getimagelist"></a>CButton:: GetImageList

Voláním této metody získáte seznam obrázků z ovládacího prvku tlačítko.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parametry

*pbuttonImagelist*<br/>
Ukazatel na seznam obrázků objektu `CButton`.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce BCM_GETIMAGELIST zprávy, jak je popsáno v části [tlačítka](/windows/win32/controls/buttons) Windows SDK.

##  <a name="getnote"></a>CButton:: getnote

Načte text poznámky přidružený k aktuálnímu ovládacímu prvku odkazu na příkazy.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpszNote*|mimo Ukazatel na vyrovnávací paměť, kterou volající je zodpovědný za přidělení a zrušení přidělení. Pokud je vrácená hodnota TRUE, obsahuje vyrovnávací paměť text poznámky, který je spojen s aktuálním ovládacím prvkem odkazu na příkazy; v opačném případě se vyrovnávací paměť nezměnila.|
|*cchNote*|[in, out] Ukazatel na unsigned integer proměnnou.<br /><br /> Při volání této metody proměnná obsahuje velikost vyrovnávací paměti určené parametrem *lpszNote* .<br /><br /> Pokud tato metoda vrátí hodnotu, pokud je hodnota TRUE, proměnná obsahuje velikost poznámky přidružené k aktuálnímu ovládacímu prvku odkazu na příkazy. Pokud je vrácená hodnota FALSE, proměnná obsahuje velikost vyrovnávací paměti, která musí obsahovat poznámku.|

### <a name="return-value"></a>Návratová hodnota

V prvním přetížení je objekt [CString](../../atl-mfc-shared/using-cstring.md) , který obsahuje text poznámky přidružený k aktuálnímu ovládacímu prvku odkazu na příkazy.

-nebo-

Ve druhém přetížení, TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_COMMANDLINK nebo BS_DEFCOMMANDLINK.

Tato metoda pošle zprávu [BCM_GETNOTE](/windows/win32/Controls/bcm-getnote) , která je popsána v Windows SDK.

##  <a name="getnotelength"></a>CButton:: GetNoteLength

Načte délku textu poznámky pro aktuální ovládací prvek odkazu na příkazy.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka textu poznámky v 16bitovém znacích Unicode pro aktuální ovládací prvek odkazu na příkazy.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_COMMANDLINK nebo BS_DEFCOMMANDLINK.

Tato metoda pošle zprávu [BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength) , která je popsána v Windows SDK.

##  <a name="getsplitglyph"></a>CButton:: GetSplitGlyph

Načte glyf přidružený k aktuálnímu ovládacímu prvku tlačítko rozdělení.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Návratová hodnota

Znak glyfu přidružený k aktuálnímu ovládacímu prvku tlačítko rozdělení

### <a name="remarks"></a>Poznámky

Glyf je fyzická reprezentace znaku v konkrétním písmu. Například ovládací prvek rozdělení tlačítka může být upravený pomocí glyfu znaku značky zaškrtnutí kódování Unicode (U + 2713).

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda inicializuje `mask` člena struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) s příznakem BCSIF_GLYPH a poté tuto strukturu pošle v [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávě, která je popsána v Windows SDK. Když funkce Message vrátí, tato metoda načte glyf z `himlGlyph` člena struktury.

##  <a name="getsplitimagelist"></a>CButton:: GetSplitImageList

Načte [seznam obrázků](../../mfc/reference/cimagelist-class.md) pro aktuální ovládací prvek tlačítko rozdělení.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [atributu CImageList](../../mfc/reference/cimagelist-class.md) .

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda inicializuje `mask` člena struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) s příznakem BCSIF_IMAGE a poté tuto strukturu pošle v [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávě, která je popsána v Windows SDK. Když funkce Message vrátí, tato metoda načte seznam obrázků z `himlGlyph` člena struktury.

##  <a name="getsplitinfo"></a>CButton:: GetSplitInfo

Načte parametry, které určují, jak systém Windows kreslí aktuální ovládací prvek tlačítko rozdělení.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pInfo*|mimo Ukazatel na strukturu [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) , která přijímá informace o aktuálním ovládacím prvku tlačítko rozdělení. Volající je zodpovědný za přidělování struktury.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda pošle zprávu [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , která je popsána v Windows SDK.

##  <a name="getsplitsize"></a>CButton:: GetSplitSize

Načte ohraničující obdélník rozbalovací součásti aktuálního ovládacího prvku tlačítko rozdělení.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pSize*|mimo Ukazatel na strukturu [velikosti](/windows/win32/api/windef/ns-windef-size) , která přijímá popis obdélníku.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Po rozbalení ovládacího prvku tlačítko rozdělení může zobrazit rozevírací komponentu, jako je například ovládací prvek seznamu nebo stránkování. Tato metoda načte ohraničující obdélník obsahující rozevírací komponentu.

Tato metoda inicializuje `mask` člena struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) s příznakem BCSIF_SIZE a poté tuto strukturu pošle v [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávě, která je popsána v Windows SDK. Když funkce Message vrátí, tato metoda načte ohraničovací obdélník z `size` člena struktury.

##  <a name="getsplitstyle"></a>CButton:: GetSplitStyle

Načte styly rozděleného tlačítka, které definují aktuální ovládací prvek tlačítko rozdělení.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitová kombinace stylů rozděleného tlačítka. Další informace najdete v tématu `uSplitStyle` členu struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Styly tlačítek rozdělení určují zarovnání, poměr stran a grafický formát, pomocí kterého systém Windows nakreslí ikonu rozděleného tlačítka.

Tato metoda inicializuje `mask` člena struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) s příznakem BCSIF_STYLE a poté tuto strukturu pošle v [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) zprávě, která je popsána v Windows SDK. Když funkce Message vrátí, tato metoda načte styly rozděleného tlačítka z `uSplitStyle` člena struktury.

##  <a name="getstate"></a>CButton:: GetState

Načte stav ovládacího prvku tlačítko.

```
UINT GetState() const;
```

### <a name="return-value"></a>Návratová hodnota

Bitové pole obsahující kombinaci hodnot, které označují aktuální stav ovládacího prvku tlačítko. V následující tabulce jsou uvedeny možné hodnoty.

|Stav tlačítka|Hodnota|Popis|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|Počáteční stav.|
|BST_CHECKED|0x0001|Ovládací prvek tlačítko je zaškrtnut.|
|BST_INDETERMINATE|0x0002|Stav je neurčitelné (možné pouze v případě, že ovládací prvek tlačítko má tři stavy).|
|BST_PUSHED|0x0004|Stiskne se ovládací prvek tlačítko.|
|BST_FOCUS|0x0008|Ovládací prvek tlačítko má fokus.|

### <a name="remarks"></a>Poznámky

Ovládací prvek tlačítko se stylem tlačítka BS_3STATE nebo BS_AUTO3STATE vytvoří zaškrtávací políčko, které má třetí stav s názvem neurčitý stav. Neurčený stav označuje, že zaškrtávací políčko není zaškrtnuto ani není zaškrtnuto.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="gettextmargin"></a>CButton:: GetTextMargin

Zavolejte tuto metodu pro získání okraje textu objektu `CButton`.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parametry

*pmargin*<br/>
Ukazatel na okraj textu objektu `CButton`.

### <a name="return-value"></a>Návratová hodnota

Vrátí okraj textu.

### <a name="remarks"></a>Poznámky

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce BCM_GETTEXTMARGIN zprávy, jak je popsáno v části [tlačítka](/windows/win32/controls/buttons) Windows SDK.

##  <a name="setbitmap"></a>CButton:: SetBitmap

Zavolejte tuto členskou funkci pro přidružení nové bitmapy k tlačítku.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parametry

*hBitmap*<br/>
Popisovač rastrového obrázku.

### <a name="return-value"></a>Návratová hodnota

Popisovač rastrového obrázku, který byl dříve přidružen k tlačítku.

### <a name="remarks"></a>Poznámky

Rastr bude automaticky umístěn na přední stěně tlačítka, ve výchozím nastavení na střed. Je-li rastrový obrázek pro tlačítko příliš velký, bude oříznut na obou stranách. Můžete zvolit další možnosti zarovnání, včetně následujících:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Na rozdíl od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), který používá čtyři rastrové obrázky na tlačítko, `SetBitmap` používá pro každé tlačítko pouze jednu rastrovou obrázek. Po stisknutí tlačítka se zobrazí rastrový obrázek pro posun dolů a doprava.

Zodpovídáte za vydání rastrového obrázku, když s ním budete hotovi.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="setbuttonstyle"></a>CButton:: SetButtonStyle

Změní styl tlačítka.

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
Určuje [styl tlačítka](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bRedraw*<br/>
Určuje, zda bude tlačítko překresleno. Nenulová hodnota překreslí tlačítko. Hodnota 0 nepřekreslí tlačítko. Ve výchozím nastavení je toto tlačítko překresleno.

### <a name="remarks"></a>Poznámky

K načtení stylu tlačítka použijte členskou funkci `GetButtonStyle`. Slovo s nižším pořadím pro styl tlačítka dokončit je stylem specifickým pro tlačítko.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="setcheck"></a>CButton:: SetCheck

Nastaví nebo obnoví stav kontroly přepínacího tlačítka nebo zaškrtávacího políčka.

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parametry

*Npokuste*<br/>
Určuje stav kontroly. Tento parametr může být jeden z následujících:

|Hodnota|Význam|
|-----------|-------------|
|BST_UNCHECKED|Nastavte stav tlačítka na nezaškrtnuto.|
|BST_CHECKED|Nastavte stav tlačítka na zaškrtnuto.|
|BST_INDETERMINATE|Nastavte stav tlačítka na neurčitý. Tato hodnota se dá použít jenom v případě, že má tlačítko styl BS_3STATE nebo BS_AUTO3STATE.|

### <a name="remarks"></a>Poznámky

Tato členská funkce nemá žádný vliv na (pushbutton).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="setcursor"></a>CButton:: SetCursor

Zavolejte tuto členskou funkci pro přidružení nového kurzoru k tlačítku.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parametry

*hCursor*<br/>
Popisovač kurzoru.

### <a name="return-value"></a>Návratová hodnota

Popisovač kurzoru, který byl dříve přidružen k tlačítku.

### <a name="remarks"></a>Poznámky

Kurzor se automaticky umístí na plochu tlačítka, která se ve výchozím nastavení nacentruje. Pokud je kurzor pro tlačítko příliš velký, bude oříznut na obou stranách. Můžete zvolit další možnosti zarovnání, včetně následujících:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Na rozdíl od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), který používá čtyři rastrové obrázky na tlačítko, `SetCursor` používá pouze jeden ukazatel na tlačítko. Po stisknutí tlačítka se kurzor zobrazí dolů a doprava.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="setdropdownstate"></a>CButton:: SetDropDownState

Nastaví stav rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*fDropDown*|pro TRUE pro nastavení stavu BST_DROPDOWNPUSHED; v opačném případě FALSE.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Ovládací prvek rozdělené tlačítko má styl BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON a skládá se z tlačítka a šipky rozevíracího seznamu na jeho pravé straně. Další informace naleznete v tématu [styly tlačítek](/windows/win32/Controls/button-styles). Pokud uživatel klikne na šipku rozevíracího seznamu, je obvykle nastaven stav rozevíracího seznamu. Tuto metodu použijte, chcete-li programově nastavit stav rozevíracího seznamu ovládacího prvku. Rozevírací šipka se vykreslí šedě, aby označovala stav.

Tato metoda pošle zprávu [BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, *m_splitButton*, která se používá k programovému přístupu k ovládacímu prvku tlačítko rozdělení. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví stav ovládacího prvku tlačítko rozdělení tak, aby označoval, že je vložena šipka rozevíracího seznamu.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

##  <a name="setelevationrequired"></a>CButton:: SetElevationRequired

Nastaví stav aktuálního ovládacího prvku tlačítko na `elevation required`, což je nezbytné, aby ovládací prvek zobrazil ikonu se zvýšeným zabezpečením.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*fElevationRequired*|pro TRUE pro nastavení stavu `elevation required`; v opačném případě FALSE.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud ovládací prvek odkaz na tlačítko nebo příkaz pro provedení akce vyžaduje zvýšené oprávnění zabezpečení, nastavte ovládací prvek na stav `elevation required`. Následně Windows v ovládacím prvku zobrazí ikonu ochrany nástrojem Řízení uživatelských účtů (UAC). Další informace najdete v tématu "řízení uživatelských účtů" na [webu MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507).

Tato metoda pošle zprávu [BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield) , která je popsána v Windows SDK.

##  <a name="seticon"></a>CButton:: SetIcon

Zavolejte tuto členskou funkci pro přidružení nové ikony k tlačítku.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parametry

*hIcon*<br/>
Popisovač ikony.

### <a name="return-value"></a>Návratová hodnota

Popisovač ikony, která byla dříve přidružena k tlačítku.

### <a name="remarks"></a>Poznámky

Ikona se automaticky umístí na plochu tlačítka, která se ve výchozím nastavení nacentruje. Pokud je ikona pro tlačítko příliš velká, bude oříznuta na obě strany. Můžete zvolit další možnosti zarovnání, včetně následujících:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

Na rozdíl od [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), který používá čtyři rastrové obrázky na tlačítko, `SetIcon` používá pro každé tlačítko pouze jednu ikonu. Po stisknutí tlačítka se zobrazí ikona, která se posune dolů a doprava.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="setimagelist"></a>CButton:: SetImageList

Voláním této metody nastavíte seznam obrázků objektu `CButton`.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parametry

*pbuttonImagelist*<br/>
Ukazatel na nový seznam obrázků.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce BCM_SETIMAGELIST zprávy, jak je popsáno v části [tlačítka](/windows/win32/controls/buttons) Windows SDK.

##  <a name="setnote"></a>CButton:: SetNote

Nastaví text poznámky pro aktuální ovládací prvek odkazu na příkazy.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpszNote*|pro Ukazatel na řetězec v kódování Unicode, který je nastaven jako text poznámky pro ovládací prvek odkazu na příkazy.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_COMMANDLINK nebo BS_DEFCOMMANDLINK.

Tato metoda pošle zprávu [BCM_SETNOTE](/windows/win32/Controls/bcm-setnote) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, *m_cmdLink*, která se používá k programovému přístupu k ovládacímu prvku odkaz na příkazy. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví text poznámky pro ovládací prvek odkaz na příkazy.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

##  <a name="setsplitglyph"></a>CButton:: SetSplitGlyph

Přidruží zadaný glyf k aktuálnímu ovládacímu prvku tlačítko rozdělení.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*chGlyph*|pro Znak, který určuje glyf, který se má použít jako šipka rozevíracího seznamu s rozděleným tlačítkem.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, které mají styl tlačítka BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Glyf je fyzická reprezentace znaku v konkrétním písmu. Parametr *chGlyph* se nepoužívá jako glyf, ale místo toho se používá pro výběr glyfu ze sady glyfů definovaných v systému. Výchozí hodnota šipky rozevíracího seznamu je určena znakem "6" a podobá se znaku Unicode černou čárkou směřující trojúhelník (U + 25BC).

Tato metoda inicializuje `mask` člena struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) s příznakem BCSIF_GLYPH a `himlGlyph`ým členem s parametrem *chGlyph* a poté tuto strukturu pošle do zprávy [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , která je popsána v Windows SDK.

##  <a name="setsplitimagelist"></a>CButton:: SetSplitImageList

Přidruží [seznam obrázků](../../mfc/reference/cimagelist-class.md) k aktuálnímu ovládacímu prvku tlačítko rozdělení.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pSplitImageList*|pro Ukazatel na objekt [atributu CImageList](../../mfc/reference/cimagelist-class.md) , který chcete přiřadit k aktuálnímu ovládacímu prvku tlačítko rozdělení.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda inicializuje `mask` člena struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) s příznakem BCSIF_IMAGE a `himlGlyph`ým členem s parametrem *pSplitImageList* a poté tuto strukturu pošle do zprávy [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , která je popsána v Windows SDK.

##  <a name="setsplitinfo"></a>CButton:: SetSplitInfo

Určuje parametry, které určují, jak systém Windows kreslí aktuální ovládací prvek tlačítko rozdělení.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pInfo*|pro Ukazatel na strukturu [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) , která definuje aktuální ovládací prvek tlačítko rozdělení.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Tato metoda pošle zprávu [BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_splitButton`, která se používá k programovému přístupu k ovládacímu prvku tlačítko rozdělení.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu změní glyf, který se používá pro šipku rozevíracího seznamu tlačítka rozdělení. V příkladu je nahrazen trojúhelník směřující nahoru pro výchozí glyf trojúhelníku směřující dolů. Zobrazený glyf závisí na znaku, který zadáte v `himlGlyph` členu struktury `BUTTON_SPLITINFO`. Piktogram trojúhelníku směřující dolů je určen znakem "6" a hvězdičkou trojúhelníku směřující nahoru je určena znakem "5". Pro porovnání si přečtěte metodu pohodlí, [CButton:: SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

##  <a name="setsplitsize"></a>CButton:: SetSplitSize

Nastaví ohraničující obdélník komponenty rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pSize*|pro Ukazatel na strukturu [velikosti](/windows/win32/api/windef/ns-windef-size) , která popisuje ohraničující obdélník.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Po rozbalení ovládacího prvku tlačítko rozdělení může zobrazit rozevírací komponentu, jako je například ovládací prvek seznamu nebo stránkování. Tato metoda určuje velikost ohraničujícího obdélníku obsahujícího rozevírací komponentu.

Tato metoda inicializuje `mask` člena struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) s příznakem BCSIF_SIZE a `size`ým členem s parametrem *psize* a poté tuto strukturu pošle do zprávy [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_splitButton`, která se používá k programovému přístupu k ovládacímu prvku tlačítko rozdělení. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu zdvojnásobí velikost šipky rozevíracího seznamu tlačítka rozdělení.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

##  <a name="setsplitstyle"></a>CButton:: SetSplitStyle

Nastaví styl aktuálního ovládacího prvku tlačítko rozdělení.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*uSplitStyle*|pro Bitová kombinace stylů rozděleného tlačítka. Další informace najdete v tématu `uSplitStyle` členu struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte pouze s ovládacími prvky, jejichž styl tlačítka je BS_SPLITBUTTON nebo BS_DEFSPLITBUTTON.

Styly tlačítek rozdělení určují zarovnání, poměr stran a grafický formát, pomocí kterého systém Windows nakreslí ikonu rozděleného tlačítka. Další informace najdete v tématu `uSplitStyle` členu struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .

Tato metoda inicializuje `mask` člena struktury [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) s příznakem BCSIF_STYLE a `uSplitStyle`ým členem s parametrem *uSplitStyle* a poté tuto strukturu pošle do zprávy [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_splitButton`, která se používá k programovému přístupu k ovládacímu prvku tlačítko rozdělení.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví styl šipky rozevíracího seznamu tlačítka rozdělení. Styl BCSS_ALIGNLEFT zobrazuje šipku na levé straně tlačítka a styl BCSS_STRETCH při změně velikosti tlačítka zachovává proporce šipky rozevíracího seznamu.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

##  <a name="setstate"></a>CButton:: SetState

Nastaví, zda je ovládací prvek tlačítko zvýrazněn nebo nikoli.

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Parametry

*bHighlight*<br/>
Určuje, zda má být zvýrazněno tlačítko. Nenulová hodnota zvýrazní tlačítko. hodnota 0 odebere jakékoli zvýraznění.

### <a name="remarks"></a>Poznámky

Zvýrazňování má vliv na vnější část ovládacího prvku tlačítko. Nemá žádný vliv na stav kontroly přepínače ani zaškrtávací políčko.

Ovládací prvek tlačítko se automaticky zvýrazní, když uživatel klikne na levé tlačítko myši. Zvýraznění se odebere, když uživatel uvolní tlačítko myši.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="settextmargin"></a>CButton:: SetTextMargin

Zavolejte tuto metodu pro nastavení okraje textu objektu `CButton`.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parametry

*pmargin*<br/>
Ukazatel na novou hranici textu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce BCM_SETTEXTMARGIN zprávy, jak je popsáno v části [tlačítka](/windows/win32/controls/buttons) Windows SDK.

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
