---
title: Třída CStatusBarCtrl
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
ms.openlocfilehash: 57d040a7efd87d384e0aaa6275593bc91f38cc86
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753045"
---
# <a name="cstatusbarctrl-class"></a>Třída CStatusBarCtrl

Poskytuje funkce ovládacího prvku společného stavového řádku systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStavový panelctrl::cStavový panelctrl](#cstatusbarctrl)|Vytvoří `CStatusBarCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStavový panel::Vytvořit](#create)|Vytvoří ovládací prvek stavového řádku `CStatusBarCtrl` a připojí jej k objektu.|
|[CStavový panel::CreateEX](#createex)|Vytvoří ovládací prvek stavového řádku se zadanými `CStatusBarCtrl` rozšířenými styly systému Windows a připojí jej k objektu.|
|[CStatusBarCtrl::DrawItem](#drawitem)|Nazývá se při změně vizuální aspekt ovládacího prvku stavového řádku kreslení vlastníka.|
|[CStavový panel ctrl::GetBorders](#getborders)|Načte aktuální šířky vodorovných a svislých ohraničení ovládacího prvku stavového řádku.|
|[CStavový panel::GetIcon](#geticon)|Načte ikonu dílu (označovaného také jako podokno) v aktuálním ovládacím prvku stavového řádku.|
|[CStatusBarCtrl::GetParts](#getparts)|Načte počet součástí v ovládacím prvku stavového řádku.|
|[CStatusBarCtrl::GetRect](#getrect)|Načte ohraničovací obdélník dílu v ovládacím prvku stavového řádku.|
|[CStavový panel ctrl::gettext](#gettext)|Načte text z dané části ovládacího prvku stavového řádku.|
|[CStavový panel ctrl::gettextlength](#gettextlength)|Načte délku textu ve znacích z dané části ovládacího prvku stavového řádku.|
|[CStavový panel ctrl::GetTipText](#gettiptext)|Načte text popisu podokna ve stavovém řádku.|
|[CStavový panelCtrl::IsSimple](#issimple)|Zkontroluje ovládací prvek stavového okna a zjistí, zda je v jednoduchém režimu.|
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí ve stavovém řádku.|
|[CStavový panel::SetIcon](#seticon)|Nastaví ikonu podokna na stavovém řádku.|
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Nastaví minimální výšku kreslicí plochy ovládacího prvku stavového řádku.|
|[CStavový panel Ctrl::SetParts](#setparts)|Nastaví počet dílů v ovládacím prvku stavového řádku a souřadnici pravéhrany každého dílu.|
|[CStavový panel Ctrl::SetSimple](#setsimple)|Určuje, zda ovládací prvek stavového řádku zobrazuje jednoduchý text nebo `SetParts`zda jsou zobrazeny všechny součásti ovládacího prvku nastavené předchozím voláním aplikace .|
|[CStavový panel ctrl:settext](#settext)|Nastaví text v dané části ovládacího prvku stavového řádku.|
|[CStavový panel ctrl::settiptext](#settiptext)|Nastaví text popisu podokna ve stavovém řádku.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek stavového řádku" je vodorovné okno, obvykle zobrazené v dolní části nadřazeného okna, ve kterém aplikace může zobrazit různé druhy informací o stavu. Ovládací prvek stavového řádku lze rozdělit na části a zobrazit tak více než jeden typ informací.

Tento ovládací prvek `CStatusBarCtrl` (a tedy třída) je k dispozici pouze pro programy spuštěné v systémech Windows 95/98 a Windows NT verze 3.51 a novějších.

Další informace o `CStatusBarCtrl`použití naleznete v [tématech Ovládací prvky](../../mfc/controls-mfc.md) a [Použití kláves CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="cstatusbarctrlcreate"></a><a name="create"></a>CStavový panel::Vytvořit

Vytvoří ovládací prvek stavového řádku `CStatusBarCtrl` a připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl ovládacího prvku stavového řádku. Použijte libovolnou kombinaci stylů ovládacích prvků stavového řádku uvedených v [seznamu Běžné styly ovládacího prvku](/windows/win32/Controls/common-control-styles) v sadě Windows SDK. Tento parametr musí obsahovat WS_CHILD styl. Měl by také obsahovat WS_VISIBLE styl.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku stavového řádku. Může to být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/windows/win32/api/windef/ns-windef-rect) struktury.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího `CDialog`prvku stavového řádku, obvykle . Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku stavového řádku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CStatusBarCtrl` ve dvou krocích. Nejprve zavolejte konstruktoru `Create`a potom volání , který vytvoří ovládací `CStatusBarCtrl` prvek stavového řádku a připojí jej k objektu.

Výchozí pozice stavového okna je v dolní části nadřazeného okna, ale můžete určit styl CCS_TOP, aby se zobrazil v horní části klientské oblasti nadřazeného okna. Můžete určit styl SBARS_SIZEGRIP, který bude zahrnovat uzel pro změnu velikosti na pravém konci stavového okna. Kombinování CCS_TOP a SBARS_SIZEGRIP stylů se nedoporučuje, protože výsledný uzel pro změnu velikosti není funkční, i když jej systém nakreslí ve stavovém okně.

Chcete-li vytvořit stavový řádek s rozšířenými styly oken, `Create`zavolejte [cstatusbarctrl::CreateEx](#createex) místo .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

## <a name="cstatusbarctrlcreateex"></a><a name="createex"></a>CStavový panel::CreateEX

Vytvoří ovládací prvek (podřízené okno) a `CStatusBarCtrl` přidruží jej k objektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyl*<br/>
Určuje rozšířený styl vytvářeného ovládacího prvku. Seznam rozšířených stylů systému Windows naleznete v parametru *dwExStyle* pro [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) v sadě Windows SDK.

*dwStyl*<br/>
Určuje styl ovládacího prvku stavového řádku. Použijte libovolnou kombinaci stylů ovládacích prvků stavového řádku uvedených v [seznamu Běžné styly ovládacího prvku](/windows/win32/Controls/common-control-styles) v sadě Windows SDK. Tento parametr musí obsahovat WS_CHILD styl. Měl by také obsahovat WS_VISIBLE styl.

*Rect*<br/>
Odkaz na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu popisující velikost a umístění okna, které mají být vytvořeny, v klientských souřadnicích *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládací prvek.

*Nid*<br/>
ID podřízeného okna ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Místo `CreateEx` funkce [Vytvořit](#create) použijte použití rozšířených stylů systému Windows určených **předmluvou**rozšířeného stylu systému Windows WS_EX_ .

## <a name="cstatusbarctrlcstatusbarctrl"></a><a name="cstatusbarctrl"></a>CStavový panelctrl::cStavový panelctrl

Vytvoří `CStatusBarCtrl` objekt.

```
CStatusBarCtrl();
```

## <a name="cstatusbarctrldrawitem"></a><a name="drawitem"></a>CStatusBarCtrl::DrawItem

Volat rámci při změny vizuální aspekt ovládacího prvku stavový řádek kreslení vlastníka.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhý ukazatel na strukturu [DRAWITEMSTRUCT,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) která obsahuje informace o požadovaném typu výkresu.

### <a name="remarks"></a>Poznámky

Člen `itemAction` `DRAWITEMSTRUCT` struktury definuje kreslicí akci, která má být provedena.

Ve výchozím nastavení tato členská funkce neprovede žádné. Přepsat tuto členovou funkci implementovat výkres `CStatusBarCtrl` pro objekt nakreslení vlastníka.

Aplikace by měla obnovit všechny objekty rozhraní grafického zařízení (GDI) vybrané pro kontext zobrazení dodaný v *lpDrawItemStruct* před ukončením této členské funkce.

## <a name="cstatusbarctrlgetborders"></a><a name="getborders"></a>CStavový panel ctrl::GetBorders

Načte aktuální šířky ovládacího prvku stavového řádku vodorovných a svislých ohraničení a prostoru mezi obdélníky.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Parametry

*pHranice*<br/>
Adresa celého pole se třemi prvky. První prvek obdrží šířku vodorovného ohraničení, druhý obdrží šířku svislého ohraničení a třetí obdrží šířku ohraničení mezi obdélníky.

*nHorz*<br/>
Odkaz na celé číslo, které přijímá šířku vodorovného ohraničení.

*nVertovat*<br/>
Odkaz na celé číslo, které přijímá šířku svislého ohraničení.

*nSpacing*<br/>
Odkaz na celé číslo, které přijímá šířku ohraničení mezi obdélníky.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Tato ohraničení určují mezery mezi vnějším okrajem ovládacího prvku a obdélníky v ovládacím prvku, které obsahují text.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

## <a name="cstatusbarctrlgeticon"></a><a name="geticon"></a>CStavový panel::GetIcon

Načte ikonu dílu (označovaného také jako podokno) v aktuálním ovládacím prvku stavového řádku.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iČást*|[v] Nula index části, která obsahuje ikonu, která má být načtena. Pokud je tento parametr -1, stavový řádek se považuje za stavový řádek jednoduchého režimu.|

### <a name="return-value"></a>Návratová hodnota

Popisovač na ikonu, pokud je metoda úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu SB_GETICON,](/windows/win32/Controls/sb-geticon) která je popsána v sadě Windows SDK.

Ovládací prvek stavového řádku se skládá z řádku podoken výstupu textu, které jsou také známé jako části. Další informace o stavovém řádku naleznete [v tématu Implementace stavového řádku v knihovně MFC](../../mfc/status-bar-implementation-in-mfc.md) a [Nastavení režimu objektu CStatusBarCtrl](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_statusBar`která se používá pro přístup k aktuálnímu ovládacímu prvku stavového řádku. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Příklad

Následující příklad kódu zkopíruje ikonu do dvou podoken aktuálního ovládacího prvku stavového řádku. V dřívější části příkladu kódu jsme vytvořili ovládací prvek stavového řádku se třemi podokny a pak přidali ikonu do prvního podokna. Tento příklad načte ikonu z prvního podokna a přidá ji do druhého a třetího podokna.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

## <a name="cstatusbarctrlgetparts"></a><a name="getparts"></a>CStatusBarCtrl::GetParts

Načte počet součástí v ovládacím prvku stavového řádku.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Parametry

*nČásti*<br/>
Počet částí, pro které chcete načíst souřadnice. Pokud je tento parametr větší než počet částí v ovládacím prvku, zpráva načte souřadnice pouze pro existující součásti.

*pČásti*<br/>
Adresa celého pole se stejným počtem prvků jako počet částí určených *nParts*. Každý prvek v poli obdrží souřadnici klienta pravéhrany odpovídající části. Pokud je prvek nastaven na - 1, pozice pravéhrany pro tuto část se rozprostírá k pravému okraji stavového řádku.

### <a name="return-value"></a>Návratová hodnota

Počet částí v ovládacím prvku, pokud je úspěšný, nebo nula jinak.

### <a name="remarks"></a>Poznámky

Tato členská funkce také načte souřadnici pravéhrany daného počtu dílů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

## <a name="cstatusbarctrlgetrect"></a><a name="getrect"></a>CStatusBarCtrl::GetRect

Načte ohraničovací obdélník dílu v ovládacím prvku stavového řádku.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Nulový index dílu, jehož ohraničovací obdélník má být načten.

*lpRect*<br/>
Adresa [rect](/windows/win32/api/windef/ns-windef-rect) struktury, která přijímá ohraničující obdélník.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

## <a name="cstatusbarctrlgettext"></a><a name="gettext"></a>CStavový panel ctrl::gettext

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
Adresa vyrovnávací paměti, která obdrží text. Tento parametr je řetězec ukončený nulou.

*nPane*<br/>
Nulový index dílu, ze kterého chcete načíst text.

*pTyp*<br/>
Ukazatel na celé číslo, které přijímá informace o typu. Typ může být jedna z těchto hodnot:

- **0** Text je nakreslen s ohraničením, které se zobrazí níže než rovina stavového řádku.

- SBT_NOBORDERS Text je vykreslen bez ohraničení.

- SBT_POPOUT Text je nakreslený s ohraničením, které se zobrazí výše než rovina stavového řádku.

- SBT_OWNERDRAW Pokud má text SBT_OWNERDRAW typ výkresu, *pType* obdrží tuto zprávu a vrátí 32bitovou hodnotu přidruženou k textu namísto délky a typu operace.

### <a name="return-value"></a>Návratová hodnota

Délka textu nebo [cstring](../../atl-mfc-shared/reference/cstringt-class.md) obsahující aktuální text ve znacích.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

## <a name="cstatusbarctrlgettextlength"></a><a name="gettextlength"></a>CStavový panel ctrl::gettextlength

Načte délku textu z dané části ovládacího prvku stavového řádku ve znacích.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Nulový index dílu, ze kterého chcete načíst text.

*pTyp*<br/>
Ukazatel na celé číslo, které přijímá informace o typu. Typ může být jedna z těchto hodnot:

- **0** Text je nakreslen s ohraničením, které se zobrazí níže než rovina stavového řádku.

- SBT_NOBORDERS Text je vykreslen bez ohraničení.

- SBT_OWNERDRAW Text je nakreslen nadřazeným oknem.

- SBT_POPOUT Text je nakreslený s ohraničením, které se zobrazí výše než rovina stavového řádku.

### <a name="return-value"></a>Návratová hodnota

Délka textu ve znacích.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

## <a name="cstatusbarctrlgettiptext"></a><a name="gettiptext"></a>CStavový panel ctrl::GetTipText

Načte text popisu podokna ve stavovém řádku.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Index stavového řádku založený na nule pro příjem textu popisu.

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt obsahující text, který má být použit v popisku.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

## <a name="cstatusbarctrlissimple"></a><a name="issimple"></a>CStavový panelCtrl::IsSimple

Zkontroluje ovládací prvek stavového okna a zjistí, zda je v jednoduchém režimu.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je ovládací prvek stavového okna v jednoduchém režimu; jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple)zprávy Win32 , jak je popsáno v sadě Windows SDK.

## <a name="cstatusbarctrlsetbkcolor"></a><a name="setbkcolor"></a>CStatusBarCtrl::SetBkColor

Nastaví barvu pozadí ve stavovém řádku.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parametry

*Čr*<br/>
COLORREF, která určuje novou barvu pozadí. Zadejte CLR_DEFAULT hodnotu, která způsobí, že stavový řádek použije výchozí barvu pozadí.

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF,](/windows/win32/gdi/colorref) která představuje předchozí výchozí barvu pozadí.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/sb-setbkcolor)Win32 SB_SETBKCOLOR , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

## <a name="cstatusbarctrlseticon"></a><a name="seticon"></a>CStavový panel::SetIcon

Nastaví ikonu podokna na stavovém řádku.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Nulový index podokna, který obdrží ikonu. Pokud je tento parametr -1, stavový řádek se považuje za jednoduchý stavový řádek.

*hIkona*<br/>
Popisovat na ikonu, která má být nastavena. Pokud je tato hodnota null, ikona je odebrána z dílu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [SB_SETICON](/windows/win32/Controls/sb-seticon)zprávy Win32 , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [cstatusbarctrl::SetBkColor](#setbkcolor).

## <a name="cstatusbarctrlsetminheight"></a><a name="setminheight"></a>CStatusBarCtrl::SetMinHeight

Nastaví minimální výšku kreslicí plochy ovládacího prvku stavového řádku.

```cpp
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Parametry

*nMin*<br/>
Minimální výška ovládacího prvku v pixelech.

### <a name="remarks"></a>Poznámky

Minimální výška je součet *nMin* a dvojnásobek šířky v pixelech svislého ohraničení ovládacího prvku stavového řádku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

## <a name="cstatusbarctrlsetparts"></a><a name="setparts"></a>CStavový panel Ctrl::SetParts

Nastaví počet dílů v ovládacím prvku stavového řádku a souřadnici pravéhrany každého dílu.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Parametry

*nČásti*<br/>
Počet částí, které chcete nastavit. Počet dílů nemůže být větší než 255.

*pŠířky*<br/>
Adresa celého pole se stejným počtem prvků jako části určené *nParts*. Každý prvek v poli určuje umístění v souřadnicích klienta pravéhranné části. Pokud je prvek - 1, poloha pravé hrany pro tuto část se rozšiřuje na pravou hranu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

## <a name="cstatusbarctrlsetsimple"></a><a name="setsimple"></a>CStavový panel Ctrl::SetSimple

Určuje, zda ovládací prvek stavového řádku zobrazuje jednoduchý text nebo zda jsou zobrazeny všechny součásti ovládacího prvku nastavené předchozím voláním [SetParts](#setparts).

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Parametry

*bJednoduché*<br/>
[v] Příznak typu zobrazení. Pokud je tento parametr TRUE, ovládací prvek zobrazí jednoduchý text; pokud je false, zobrazí více částí.

### <a name="return-value"></a>Návratová hodnota

Vždy vrátí hodnotu 0.

### <a name="remarks"></a>Poznámky

Pokud aplikace změní ovládací prvek stavového řádku z nejednoduché na jednoduché nebo naopak, systém okamžitě překreslí ovládací prvek.

## <a name="cstatusbarctrlsettext"></a><a name="settext"></a>CStavový panel ctrl:settext

Nastaví text v dané části ovládacího prvku stavového řádku.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Adresa řetězce s nulovým ukončením určujícího nastavený text. Pokud *nType* je SBT_OWNERDRAW, *lpszText* představuje 32 bitů dat.

*nPane*<br/>
Nulový index dílu, který má být nastaven. Pokud je tato hodnota 255, předpokládá se, že ovládací prvek stavového řádku je jednoduchý ovládací prvek, který má pouze jednu část.

*nTyp*<br/>
Typ operace kreslení. Seznam možných hodnot naleznete [SB_SETTEXT zprávu.](/windows/win32/Controls/sb-settext)

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Zpráva zruší platnost části ovládacího prvku, který byl změněn, přimět jej k zobrazení nového textu, když ovládací prvek další obdrží zprávu WM_PAINT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

## <a name="cstatusbarctrlsettiptext"></a><a name="settiptext"></a>CStavový panel ctrl::settiptext

Nastaví text popisu podokna ve stavovém řádku.

```cpp
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parametry

*nPane*<br/>
Index stavového řádku založený na nule pro příjem textu popisu.

*pszTipText*<br/>
Ukazatel na řetězec obsahující text popisu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/sb-settiptext)Win32 SB_SETTIPTEXT , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CToolBarctrl](../../mfc/reference/ctoolbarctrl-class.md)
