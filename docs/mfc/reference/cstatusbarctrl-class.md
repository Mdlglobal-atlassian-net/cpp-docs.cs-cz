---
title: CStatusBarCtrl – třída
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
ms.openlocfilehash: 8c33aa4d77eeeeca69e50dc63982ff4d7e8bd505
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865532"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl – třída

Poskytuje funkce pro běžný ovládací prvek stavového řádku systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStatusBarCtrl:: CStatusBarCtrl](#cstatusbarctrl)|Vytvoří objekt `CStatusBarCtrl`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStatusBarCtrl:: Create](#create)|Vytvoří ovládací prvek stavového řádku a připojí ho k objektu `CStatusBarCtrl`.|
|[CStatusBarCtrl:: CreateEx](#createex)|Vytvoří ovládací prvek stavového řádku se zadanými rozšířenými styly Windows a připojí ho k objektu `CStatusBarCtrl`.|
|[CStatusBarCtrl::D rawItem](#drawitem)|Volá se, když se změní vizuální aspekt ovládacího prvku pro vykreslení stavového řádku.|
|[CStatusBarCtrl:: GetBorders](#getborders)|Načte aktuální šířku vodorovného a svislého ohraničení ovládacího prvku stavového řádku.|
|[CStatusBarCtrl:: GetIcon](#geticon)|Načte ikonu součásti (také označované jako podokno) v aktuálním ovládacím prvku stavového řádku.|
|[CStatusBarCtrl:: GetParts](#getparts)|Načte počet částí v ovládacím prvku stavový řádek.|
|[CStatusBarCtrl:: GetRect](#getrect)|Načte ohraničující obdélník součásti v ovládacím prvku stavový řádek.|
|[CStatusBarCtrl:: GetText](#gettext)|Načte text z dané části ovládacího prvku stavového řádku.|
|[CStatusBarCtrl:: GetTextLength](#gettextlength)|Načte délku textu z dané části ovládacího prvku stavového řádku (ve znacích).|
|[CStatusBarCtrl:: GetTipText](#gettiptext)|Načte text popisku podokna ve stavovém řádku.|
|[CStatusBarCtrl:: jednoduchá](#issimple)|Kontroluje ovládací prvek stavového okna a zjišťuje, zda je v jednoduchém režimu.|
|[CStatusBarCtrl:: SetBkColor](#setbkcolor)|Nastaví barvu pozadí ve stavovém řádku.|
|[CStatusBarCtrl:: SetIcon](#seticon)|Nastaví ikonu podokna ve stavovém řádku.|
|[CStatusBarCtrl:: SetMinHeight](#setminheight)|Nastaví minimální výšku oblasti vykreslování ovládacího prvku stavového řádku.|
|[CStatusBarCtrl:: SetParts](#setparts)|Nastaví počet částí v ovládacím prvku stavový řádek a souřadnice pravého okraje každé části.|
|[CStatusBarCtrl:: SetSimple](#setsimple)|Určuje, zda ovládací prvek stavového řádku zobrazuje jednoduchý text nebo zobrazuje všechny části ovládacího prvku nastavené předchozím voláním `SetParts`.|
|[CStatusBarCtrl:: SetText](#settext)|Nastaví text v dané části ovládacího prvku stavového řádku.|
|[CStatusBarCtrl:: SetTipText](#settiptext)|Nastaví text popisku podokna ve stavovém řádku.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek stavového řádku" je horizontální okno, obvykle se zobrazuje v dolní části nadřazeného okna, ve kterém může aplikace zobrazit různé druhy informací o stavu. Ovládací prvek stavového řádku lze rozdělit na části pro zobrazení více než jednoho typu informací.

Tento ovládací prvek (a proto třída `CStatusBarCtrl`) je k dispozici pouze pro programy, které jsou spuštěny v systémech Windows 95/98 a Windows NT verze 3,51 a novější.

Další informace o použití `CStatusBarCtrl`naleznete v tématu [Controls](../../mfc/controls-mfc.md) and [using CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="create"></a>CStatusBarCtrl:: Create

Vytvoří ovládací prvek stavového řádku a připojí ho k objektu `CStatusBarCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl ovládacího prvku stavového řádku. Použít libovolnou kombinaci stylů ovládacích prvků stavového řádku, které jsou uvedeny v části [Běžné styly ovládacích prvků](/windows/win32/Controls/common-control-styles) v Windows SDK. Tento parametr musí zahrnovat styl WS_CHILD. Měl by také obsahovat styl WS_VISIBLE.

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku stavového řádku. Může to být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo struktura [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku stavového řádku, obvykle `CDialog`. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku stavového řádku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Sestavíte `CStatusBarCtrl` ve dvou krocích. Nejprve volejte konstruktor a potom zavolejte `Create`, čímž se vytvoří ovládací prvek stavového řádku a připojí se k objektu `CStatusBarCtrl`.

Výchozí pozice stavového okna je podél dolního okraje nadřazeného okna, ale můžete určit styl CCS_TOP, který se zobrazí v horní části klientské oblasti nadřazeného okna. Můžete určit styl SBARS_SIZEGRIP pro zahrnutí úchytu pro změnu velikosti na pravé straně stavového okna. Kombinování CCS_TOP a SBARS_SIZEGRIP stylů se nedoporučuje, protože výsledné úchyty pro změnu velikosti nejsou funkční, i když ho systém vykreslí v okně stav.

Chcete-li vytvořit stavový řádek pomocí rozšířených stylů oken, zavolejte [CStatusBarCtrl:: CreateEx](#createex) namísto `Create`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

##  <a name="createex"></a>CStatusBarCtrl:: CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ho k objektu `CStatusBarCtrl`.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Určuje rozšířený styl ovládacího prvku, který se vytváří. Seznam rozšířených stylů Windows naleznete v parametru *dwExStyle* pro [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v Windows SDK.

*dwStyle*<br/>
Určuje styl ovládacího prvku stavového řádku. Použít libovolnou kombinaci stylů ovládacích prvků stavového řádku, které jsou uvedeny v části [Běžné styly ovládacích prvků](/windows/win32/Controls/common-control-styles) v Windows SDK. Tento parametr musí zahrnovat styl WS_CHILD. Měl by také obsahovat styl WS_VISIBLE.

*OBD*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) popisující velikost a umístění okna, které má být vytvořeno, v souřadnicích klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládacímu prvku.

*nID*<br/>
ID podřízeného okna ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Použijte `CreateEx` namísto [Create](#create) k použití rozšířených stylů Windows, které jsou určené **WS_EX_m**ve stylu rozšířených stylů Windows.

##  <a name="cstatusbarctrl"></a>CStatusBarCtrl:: CStatusBarCtrl

Vytvoří objekt `CStatusBarCtrl`.

```
CStatusBarCtrl();
```

##  <a name="drawitem"></a>CStatusBarCtrl::D rawItem

Volá se rozhraním, když se změní vizuální aspekt ovládacího prvku na stavovém řádku pro vykreslování vlastníka.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhý ukazatel na strukturu [DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) , která obsahuje informace o typu požadované kresby.

### <a name="remarks"></a>Poznámky

`itemAction` člen struktury `DRAWITEMSTRUCT` definuje akci kreslení, která má být provedena.

Ve výchozím nastavení tato členská funkce neprovede žádnou akci. Přepište tuto členskou funkci pro implementaci vykreslování pro objekt `CStatusBarCtrl` vykreslený vlastníkem.

Aplikace by měla obnovit všechny objekty GDI (Graphic Device Interface) vybrané pro kontext zobrazení zadaný v *lpDrawItemStruct* před ukončením této členské funkce.

##  <a name="getborders"></a>CStatusBarCtrl:: GetBorders

Načte aktuální šířku vodorovného a svislého ohraničení ovládacího prvku stavového řádku a prostoru mezi obdélníky.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Parametry

*pBorders*<br/>
Adresa pole typu Integer má tři prvky. První prvek přijímá šířku vodorovného ohraničení, druhá přijímá šířku svislého ohraničení a třetí přijímá šířku ohraničení mezi obdélníky.

*nHorz*<br/>
Odkaz na celé číslo, které přijímá šířku vodorovného ohraničení.

*Veďte*<br/>
Odkaz na celé číslo, které přijímá šířku svislého ohraničení.

*nSpacing*<br/>
Odkaz na celé číslo, které přijímá šířku ohraničení mezi obdélníky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Tato ohraničení určují mezery mezi vnějším okrajem ovládacího prvku a obdélníky v rámci ovládacího prvku, který obsahuje text.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

##  <a name="geticon"></a>CStatusBarCtrl:: GetIcon

Načte ikonu součásti (také označované jako podokno) v aktuálním ovládacím prvku stavového řádku.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iPart*|pro Index založený na nule součásti, která obsahuje ikonu, která má být načtena. Pokud je tento parametr-1, bude se stavový řádek považovat za jednoduchý režim stavový řádek.|

### <a name="return-value"></a>Návratová hodnota

Popisovač na ikonu, pokud byla metoda úspěšná; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [SB_GETICON](/windows/win32/Controls/sb-geticon) , která je popsána v Windows SDK.

Ovládací prvek stavového řádku se skládá z řádku podoken textových výstupů, které jsou také označovány jako části. Další informace o stavovém řádku naleznete v tématu [Implementace stavového řádku v prostředí MFC](../../mfc/status-bar-implementation-in-mfc.md) a [Nastavení režimu objektu CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_statusBar`, která se používá pro přístup k aktuálnímu ovládacímu prvku stavového řádku. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Příklad

Následující příklad kódu zkopíruje ikonu do dvou podoken aktuálního ovládacího prvku stavového řádku. V dřívější části příkladu kódu jsme vytvořili ovládací prvek stavového řádku se třemi podokny a pak jste přidali ikonu do prvního podokna. V tomto příkladu se načte ikona z prvního podokna a pak se přidá do druhého a třetího podokna.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

##  <a name="getparts"></a>CStatusBarCtrl:: GetParts

Načte počet částí v ovládacím prvku stavový řádek.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Parametry

*nParts*<br/>
Počet částí, pro které se mají načíst souřadnice Pokud je tento parametr větší než počet částí v ovládacím prvku, zpráva načte pouze souřadnice pro existující části.

*pParts*<br/>
Adresa pole typu Integer, které má stejný počet prvků jako počet částí určených parametrem *nParts*. Každý prvek v poli obdrží souřadnici klienta na pravém okraji příslušné části. Pokud je prvek nastaven na hodnotu-1, pozice pravého okraje této části se rozšíří do pravého okraje stavového řádku.

### <a name="return-value"></a>Návratová hodnota

Počet částí v ovládacím prvku v případě úspěchu nebo nula jinak.

### <a name="remarks"></a>Poznámky

Tato členská funkce také načte souřadnici pravého okraje daného počtu částí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

##  <a name="getrect"></a>CStatusBarCtrl:: GetRect

Načte ohraničující obdélník součásti v ovládacím prvku stavový řádek.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Index založený na nule součásti, jejíž ohraničující obdélník má být načten.

*lpRect*<br/>
Adresa struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , která přijímá ohraničující obdélník.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

##  <a name="gettext"></a>CStatusBarCtrl:: GetText

Načte text z dané části ovládacího prvku stavového řádku.

```
CString GetText(
    int nPane,
    int* pType = NULL) const;

int GetText(
    LPCTSTR lpszText,
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Adresa vyrovnávací paměti, která přijímá text Tento parametr je řetězec zakončený hodnotou null.

*nPane*<br/>
Index založený na nule součásti, ze které se má načíst text

*pType*<br/>
Ukazatel na celé číslo, které obdrží informace o typu. Typ může být jedna z těchto hodnot:

- **0** text se vykreslí s ohraničením, které se má snížit, než rovina stavového řádku.

- SBT_NOBORDERS se text vykreslí bez ohraničení.

- SBT_POPOUT se text vykreslí ohraničením, aby se zobrazilo větší než rovina stavového řádku.

- SBT_OWNERDRAW je-li text typu vykreslování SBT_OWNERDRAW, *pType* obdrží tuto zprávu a vrátí hodnotu 32 spojenou s textem místo délky a typu operace.

### <a name="return-value"></a>Návratová hodnota

Délka textu nebo [CString](../../atl-mfc-shared/reference/cstringt-class.md) , která obsahuje aktuální text.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

##  <a name="gettextlength"></a>CStatusBarCtrl:: GetTextLength

Načte délku textu z dané části ovládacího prvku stavového řádku (ve znacích).

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Index založený na nule součásti, ze které se má načíst text

*pType*<br/>
Ukazatel na celé číslo, které obdrží informace o typu. Typ může být jedna z těchto hodnot:

- **0** text se vykreslí s ohraničením, které se má snížit, než rovina stavového řádku.

- SBT_NOBORDERS se text vykreslí bez ohraničení.

- SBT_OWNERDRAW je text vykreslen nadřazeným oknem.

- SBT_POPOUT se text vykreslí ohraničením, aby se zobrazilo větší než rovina stavového řádku.

### <a name="return-value"></a>Návratová hodnota

Délka textu v znacích

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

##  <a name="gettiptext"></a>CStatusBarCtrl:: GetTipText

Načte text popisku podokna ve stavovém řádku.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Index podokna stavového řádku založený na nule, který získá text popisku.

### <a name="return-value"></a>Návratová hodnota

Objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující text, který má být použit v popisku.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

##  <a name="issimple"></a>CStatusBarCtrl:: jednoduchá

Kontroluje ovládací prvek stavového okna a zjišťuje, zda je v jednoduchém režimu.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je ovládací prvek stavového okna v jednoduchém režimu; jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple), jak je popsáno v Windows SDK.

##  <a name="setbkcolor"></a>CStatusBarCtrl:: SetBkColor

Nastaví barvu pozadí ve stavovém řádku.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parametry

*znaky*<br/>
Hodnota COLORREF, která určuje novou barvu pozadí. Zadejte hodnotu CLR_DEFAULT, která způsobí, že se ve stavovém řádku bude používat výchozí barva pozadí.

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) , která představuje předchozí výchozí barvu pozadí.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

##  <a name="seticon"></a>CStatusBarCtrl:: SetIcon

Nastaví ikonu podokna ve stavovém řádku.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Index založený na nule podokna, který obdrží ikonu. Pokud je tento parametr-1, předpokládá se, že se stavový řádek nachází v jednoduchém stavovém řádku.

*hIcon*<br/>
Nastavte popisovač na ikonu, která se má nastavit. Pokud je tato hodnota NULL, ikona se odebere z části.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [SB_SETICON](/windows/win32/Controls/sb-seticon), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CStatusBarCtrl:: SetBkColor](#setbkcolor).

##  <a name="setminheight"></a>CStatusBarCtrl:: SetMinHeight

Nastaví minimální výšku oblasti vykreslování ovládacího prvku stavového řádku.

```
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Parametry

*Nminimum*<br/>
Minimální výška ovládacího prvku v pixelech

### <a name="remarks"></a>Poznámky

Minimální výška je součet *nminimum* a dvojnásobku šířky (v pixelech) svislého ohraničení ovládacího prvku na stavovém řádku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

##  <a name="setparts"></a>CStatusBarCtrl:: SetParts

Nastaví počet částí v ovládacím prvku stavový řádek a souřadnice pravého okraje každé části.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Parametry

*nParts*<br/>
Počet částí, které mají být nastaveny. Počet částí nemůže být větší než 255.

*pWidths*<br/>
Adresa pole typu Integer, které má stejný počet prvků jako části určené parametrem *nParts*. Každý prvek v poli určuje pozici v souřadnicích klienta na pravé straně příslušné části. Pokud je prvek-1, pozice pravého okraje této části se rozšiřuje na pravý okraj ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

##  <a name="setsimple"></a>CStatusBarCtrl:: SetSimple

Určuje, zda ovládací prvek stavového řádku zobrazuje jednoduchý text nebo zobrazuje všechny části ovládacího prvku nastavené předchozím voláním metody [SetParts](#setparts).

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Parametry

*bSimple*<br/>
pro Příznak typu zobrazení Pokud má tento parametr hodnotu TRUE, ovládací prvek zobrazí jednoduchý text; Pokud je hodnota FALSE, zobrazí se více částí.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

Pokud vaše aplikace změní ovládací prvek stavového řádku z nejednoduchého na jednoduchý nebo naopak, systém ovládací prvek ihned překreslí.

##  <a name="settext"></a>CStatusBarCtrl:: SetText

Nastaví text v dané části ovládacího prvku stavového řádku.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Adresa řetězce zakončeného hodnotou null určující text, který se má nastavit Pokud je *noznámení* SBT_OWNERDRAW, *lpszText* představuje 32 bitů dat.

*nPane*<br/>
Index založený na nule části, kterou chcete nastavit. Pokud je tato hodnota 255, je ovládací prvek stavového řádku považován za jednoduchý ovládací prvek, který má pouze jednu část.

*Noznámení*<br/>
Typ operace kreslení Seznam možných hodnot naleznete v [SB_SETTEXT zprávě](/windows/win32/Controls/sb-settext) .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Zpráva zruší platnost části ovládacího prvku, který se změnil, což způsobí, že se zobrazí nový text, když ovládací prvek příště obdrží zprávu WM_PAINT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

##  <a name="settiptext"></a>CStatusBarCtrl:: SetTipText

Nastaví text popisku podokna ve stavovém řádku.

```
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Index podokna stavového řádku založený na nule, který získá text popisku.

*pszTipText*<br/>
Ukazatel na řetězec obsahující text popisku.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl – třída](../../mfc/reference/ctoolbarctrl-class.md)
