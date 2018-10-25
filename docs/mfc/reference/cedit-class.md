---
title: Cedit – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
dev_langs:
- C++
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc11631b6a9b4c675d488d69c5575a89853e64a3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079269"
---
# <a name="cedit-class"></a>Cedit – třída

Poskytuje funkce pro Windows textové pole.

## <a name="syntax"></a>Syntaxe

```
class CEdit : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CEdit::CEdit](#cedit)|Vytvoří `CEdit` objekt ovládacího prvku.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|Určuje, jestli operace edit-control je možné vrátit zpět.|
|[CEdit::CharFromPos](#charfrompos)|Načte indexy řádku a znak nejblíže určené pozici znaku.|
|[CEdit::Clear](#clear)|Odstraní (vymaže) v aktuálním výběru (pokud existuje) upravit ovládací prvek.|
|[CEdit::Copy](#copy)|Zkopíruje aktuální výběr (pokud existuje) v textovém poli ve formátu CF_TEXT do schránky.|
|[CEdit::Create](#create)|Vytvoří ovládací prvek pro úpravy Windows a připojí ho k `CEdit` objektu.|
|[CEdit::Cut](#cut)|Ovládací prvek v aktuálním výběru (pokud existuje) úpravy odstraní (kusů) a formátování odstraněný text do schránky. v CF_TEXT kopie.|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Resetuje ovládací prvek (vymaže) příznak zpět úpravy.|
|[CEdit::FmtLines](#fmtlines)|Zapnutí nebo vypnutí nastaví zahrnutí obnovitelně oddělených koncem řádku znaků v rámci víceřádkové textové pole.|
|[CEdit::GetCueBanner](#getcuebanner)|Načte text, který se zobrazí jako textové upozornění nebo tip do ovládacího prvku edit, když ovládací prvek je prázdný a nemá fokus.|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Určuje nejvyšší viditelné řádku do ovládacího prvku pro úpravy.|
|[CEdit::GetHandle](#gethandle)|Načte popisovač paměť, která je právě přiděleno pro ovládací prvek upravit více řádků.|
|[CEdit::GetHighlight](#gethighlight)|Získá indexy počáteční a koncové znaky v rozsahu textu, který je zvýrazněn v aktuální ovládací prvek pro úpravy.|
|[CEdit::GetLimitText](#getlimittext)|Získá maximální množství textu, to `CEdit` může obsahovat.|
|[CEdit::GetLine](#getline)|Načte řádek textu z ovládacího prvku pro úpravy.|
|[CEdit::GetLineCount](#getlinecount)|Získá počet řádků v ovládacím prvku pro úpravy více řádků.|
|[CEdit::GetMargins](#getmargins)|Získá levý a pravý okraj pro tento `CEdit`.|
|[CEdit::GetModify](#getmodify)|Určuje, zda byly upraveny obsah ovládacího prvku pro úpravy.|
|[CEdit::GetPasswordChar](#getpasswordchar)|Získá znak hesla zobrazí v ovládacím prvku upravovat, když uživatel zadá text.|
|[CEdit::GetRect](#getrect)|Získá formátovací obdélníku ovládacího prvku pro úpravy.|
|[CEdit::GetSel](#getsel)|Získá umístění první a poslední znak v aktuálním výběru ovládacího prvku pro úpravy.|
|[CEdit::HideBalloonTip](#hideballoontip)|Skryje všechny tipu v bublině přidružené k aktuální ovládací prvek pro úpravy.|
|[CEdit::LimitText](#limittext)|Omezení délky textu, který může uživatel zadat do ovládacího prvku pro úpravy.|
|[CEdit::LineFromChar](#linefromchar)|Získá číslo řádku, který obsahuje index zadaný znak řádku.|
|[CEdit::LineIndex](#lineindex)|Získá znakový index řádku v rámci víceřádkové textové pole.|
|[CEdit::LineLength](#linelength)|Načte délku řádku do ovládacího prvku pro úpravy.|
|[CEdit::LineScroll](#linescroll)|Posouvá text víceřádkové textové pole.|
|[CEdit::Paste](#paste)|Vloží data ze schránky do textového pole na aktuální pozici kurzoru. Data budou vložena pouze v případě, že obsahuje data ve formátu CF_TEXT do schránky.|
|[CEdit::PosFromChar](#posfromchar)|Načte souřadnice levého horního rohu index zadaný znak.|
|[CEdit::ReplaceSel](#replacesel)|Nahradí zadaný text v aktuálním výběru ovládacího prvku pro úpravy.|
|[CEdit::SetCueBanner](#setcuebanner)|Nastaví text, který se zobrazí jako textové upozornění nebo tip do ovládacího prvku edit, když ovládací prvek je prázdný a nemá fokus.|
|[CEdit::SetHandle](#sethandle)|Nastaví popisovač k místní paměti, který se použije víceřádkové textové pole.|
|[CEdit::SetHighlight](#sethighlight)|Vybraná vystoupení a rozsah textu, který se zobrazí v aktuálních ovládacích prvků pro úpravy.|
|[CEdit::SetLimitText](#setlimittext)|Nastaví maximální množství textu, to `CEdit` může obsahovat.|
|[CEdit::SetMargins](#setmargins)|Nastaví levý a pravý okraj pro tuto `CEdit`.|
|[CEdit::SetModify](#setmodify)|Nastaví nebo vymaže příznak úprav pro ovládací prvek upravit.|
|[CEdit::SetPasswordChar](#setpasswordchar)|Nastaví nebo odebere znak hesla zobrazí v ovládacím prvku upravovat, když uživatel zadá text.|
|[CEdit::SetReadOnly](#setreadonly)|Nastaví stav textové pole jen pro čtení.|
|[CEdit::SetRect](#setrect)|Nastaví formátování obdélník víceřádkové textové pole a aktualizuje ovládacího prvku.|
|[CEdit::SetRectNP](#setrectnp)|Nastaví formátování obdélník víceřádkové textové pole bez překreslení ovládacího prvku okna.|
|[CEdit::SetSel](#setsel)|Vybere rozsah znaků v textové pole.|
|[CEdit::SetTabStops](#settabstops)|Nastaví zarážky v řádku více ovládacích prvků pro úpravy.|
|[CEdit::ShowBalloonTip](#showballoontip)|Zobrazí zobrazení tipu v bublině, který je přidružený aktuální ovládací prvek pro úpravy.|
|[CEdit::Undo](#undo)|Vrátí poslední operace edit-control.|

## <a name="remarks"></a>Poznámky

Textové pole je obdélníková podřízené okno, ve kterém může uživatel zadat text.

Prvek pro úpravy můžete vytvořit z šablony dialogového okna nebo přímo v kódu. V obou případech se nejprve volat konstruktor `CEdit` k sestavení kompletních `CEdit` objekt a potom voláním [vytvořit](#create) členské funkci, která vytvoří Windows ovládacích prvků pro úpravy a připojte ji k `CEdit` objektu.

Konstrukce může být jednoduchý proces ve třídě odvozené z `CEdit`. Zápis konstruktoru pro odvozenou třídu a volání `Create` z v rámci konstruktoru.

`CEdit` dědí významné funkce `CWnd`. K nastavení a načtení textu ze `CEdit` objektu, použijte `CWnd` členské funkce [SetWindowText](cwnd-class.md#setwindowtext) a [getwindowtext –](cwnd-class.md#getwindowtext), které set nebo get řídit celý obsah úpravy, i když ho je víceřádkového ovládacího prvku. Řádky textu v ovládacím prvku víceřádkové jsou odděleny "\r\n" znakové sekvence. Navíc pokud textové pole je víceřádkové, získání a nastavení část textu ovládacího prvku pomocí volání `CEdit` členské funkce [GetLine](#getline), [SetSel](#setsel), [GetSel](#getsel)a [ ReplaceSel](#replacesel).

Pokud chcete zpracovávat Windows oznamující zprávy odeslal ovládacího prvku pro úpravy k nadřazené úloze (obvykle třída odvozená z `CDialog`), přidat mapu zpráv položku a obslužná rutina zprávy členskou funkci na nadřazené třídu pro každou zprávu.

Každá položka mapování zpráv má následující podobu:

  **ON_**_oznámení_**(** _id_**,** _memberFxn_ **)**

kde `id` identifikátor podřízené okno ovládacího prvku pro úpravy, posílání oznámení, a `memberFxn` je název nadřazené členské funkce mají napsané tak, aby oznámení.

Prototyp funkce nadřazeného objektu je následujícím způsobem:

**afx_msg** void memberFxn **();**

Tady je seznam možných položky mapování zpráv a popis případy, ve kterých se mají být odeslány do nadřazené:

- ON_EN_CHANGE uživatel přijal akci, která může mít změnit text v ovládacím prvku upravovat. Na rozdíl od EN_UPDATE zprávy oznámení přijde tato oznámení po dokončení aktualizace zobrazení Windows.

- ON_EN_ERRSPACE ovládací prvek pro úpravy nemůže přidělit dostatek paměti k uspokojení konkrétní žádost.

- ON_EN_HSCROLL uživatel klikne na tlačítko ovládacího prvku edit vodorovný posuvník. Nadřazené okno se zobrazí oznámení předtím, než se aktualizuje na obrazovce.

- ON_EN_KILLFOCUS textové pole ztratí vstupní fokus.

- ON_EN_MAXTEXT aktuální vložení překročil zadaný počet znaků pro ovládací prvek pro úpravy a byla zkrácena. Také odesílá se, když ovládací prvek úprav nemá styl ES_AUTOHSCROLL a počet znaků, které mají být vloženy by být delší než šířka ovládacích prvků pro úpravy. Také odesílá se, když ovládací prvek upravit styl ES_AUTOVSCROLL nemá a celkový počet řádků, které jsou výsledkem vkládání textu by být delší než výška ovládacích prvků pro úpravy.

- ON_EN_SETFOCUS posílají, když ovládací prvek úprav nastaven vstupní fokus.

- ON_EN_UPDATE ovládací prvek pro úpravy je o text zobrazení změnit. Odeslat po ovládací prvek má formátovaný text, ale před jeho obrazovek text tak, že můžete změnit velikost okna, v případě potřeby.

- ON_EN_VSCROLL uživatel klikne na tlačítko ovládacího prvku edit svislý posuvník. Nadřazené okno se zobrazí oznámení předtím, než se aktualizuje na obrazovce.

Pokud jste vytvořili `CEdit` objektu v dialogovém okně `CEdit` objekt je zničen automaticky, když uživatel zavře dialogové okno.

Pokud jste vytvořili `CEdit` objekt z prostředku dialogového okna pomocí editoru dialogových oken `CEdit` objekt je zničen automaticky, když uživatel zavře dialogové okno.

Pokud jste vytvořili `CEdit` objektů v okně a také je nutné ji odstranit. Pokud jste vytvořili `CEdit` objekt v zásobníku, je automaticky zničen. Pokud jste vytvořili `CEdit` objektů na haldě pomocí **nové** funkce, je nutné volat **odstranit** na objekt, který chcete zničit ho, když uživatel ukončí Windows ovládacích prvků pro úpravy. Pokud přidělení paměti v `CEdit` objektu, přepsat `CEdit` destruktor k uvolnění přidělení.

Chcete-li změnit určité styly v ovládacím prvku upravit (například ES_READONLY) je nutné odeslat konkrétní zprávy do ovládacího prvku, namísto použití [ModifyStyle](cwnd-class.md#modifystyle). Zobrazit [styly ovládacího prvku pro úpravy](/windows/desktop/Controls/edit-control-styles) ve Windows SDK.

Další informace o `CEdit`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="canundo"></a>  CEdit::CanUndo

Voláním této funkce určí, jestli může být poslední operaci úpravy vrátit zpět.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud poslední operaci úprav lze je vrátit zpět voláním `Undo` členské funkce; 0, pokud není možné vrátit zpět.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [EM_CANUNDO](/windows/desktop/Controls/em-canundo) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit::Undo](#undo).

##  <a name="cedit"></a>  CEdit::CEdit

Vytvoří `CEdit` objektu.

```
CEdit();
```

### <a name="remarks"></a>Poznámky

Použití [vytvořit](#create) k sestavení kompletních Windows ovládacích prvků pro úpravy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

##  <a name="charfrompos"></a>  CEdit::CharFromPos

Voláním této funkce načtete řádků od nuly a indexy znak znaku nejbližší bod zadaný v tomto `CEdit` ovládacího prvku

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Parametry

*PT*<br/>
Souřadnice bodu v klientské oblasti tohoto `CEdit` objektu.

### <a name="return-value"></a>Návratová hodnota

Znakový index v nižší řád slova a index řádku v vyšší řád slova.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato členská funkce je k dispozici od verze Windows 95 a Windows NT 4.0.

Další informace najdete v tématu [EM_CHARFROMPOS](/windows/desktop/Controls/em-charfrompos) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

##  <a name="clear"></a>  CEdit::Clear

Voláním této funkce pro odstranění (Vymazat) aktuálního výběru (pokud existuje) v textovém poli.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

Odstranění prováděné `Clear` lze je vrátit zpět voláním [zpět](#undo) členskou funkci.

Chcete-li odstranit aktuální výběr a umístí odstranil obsah do schránky, zavolejte [Vyjmout](#cut) členskou funkci.

Další informace najdete v tématu [WM_CLEAR](/windows/desktop/dataxchg/wm-clear) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

##  <a name="copy"></a>  CEdit::Copy

Voláním této funkce coy aktuálního výběru (pokud existuje) v textovém poli ve formátu CF_TEXT do schránky.

```
void Copy();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [WM_COPY](/windows/desktop/dataxchg/wm-copy) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

##  <a name="create"></a>  CEdit::Create

Vytvoří ovládací prvek pro úpravy Windows a připojí ho k `CEdit` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl textové pole. Použít libovolnou kombinaci [styly pro úpravy](styles-used-by-mfc.md#edit-styles) do ovládacího prvku.

*Rect*<br/>
Určuje velikost a umístění textové pole. Může být `CRect` objektu nebo `RECT` struktury.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku úprav (obvykle `CDialog`). Nesmí být NULL.

*nID*<br/>
Určuje ID textové pole.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se inicializace je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CEdit` objektu ve dvou krocích. Nejprve volat `CEdit` konstruktor a poté zavolejte `Create`, což vytvoří ovládací prvek pro úpravy Windows a připojí ho k `CEdit` objektu.

Když `Create` spustí, odešle Windows [WM_NCCREATE](/windows/desktop/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/desktop/winmsg/wm-nccalcsize), [WM_CREATE](/windows/desktop/winmsg/wm-create), a [WM_GETMINMAXINFO](/windows/desktop/winmsg/wm-getminmaxinfo) zprávy pro ovládací prvek pro úpravy.

Tyto zprávy jsou zpracovány ve výchozím nastavení [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate), a [ongetminmaxinfo –](cwnd-class.md#ongetminmaxinfo) členské funkce v `CWnd` základní třídy. Pokud chcete rozšířit výchozí zpracování zpráv, odvoďte třídu z `CEdit`mapy zpráv na novou třídu a přidejte výše obslužná rutina zprávy členské funkce přepsat. Přepsat `OnCreate`, například k provedení potřebných inicializace pro novou třídu.

Použijte následující [styly oken](styles-used-by-mfc.md#window-styles) do ovládacího prvku pro úpravy.

- WS_CHILD vždy

- WS_VISIBLE obvykle

- WS_DISABLED jen zřídka

- WS_GROUP k seskupování ovládacích prvků

- WS_TABSTOP zahrnují ovládací prvek pro úpravy v pořadí procházení

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

##  <a name="cut"></a>  CEdit::Cut

Voláním této funkce, odstranit (vyjmutí) (pokud existuje) aktuálnímu výběru v textovém poli a zkopírujte do schránky ve formátu CF_TEXT odstraněný text.

```
void Cut();
```

### <a name="remarks"></a>Poznámky

Odstranění prováděné `Cut` lze je vrátit zpět voláním [zpět](#undo) členskou funkci.

Chcete-li odstranit aktuální výběr bez umístění odstraněný text do schránky, zavolejte [vymazat](#clear) členskou funkci.

Další informace najdete v tématu [WM_CUT](/windows/desktop/dataxchg/wm-cut) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

##  <a name="emptyundobuffer"></a>  CEdit::EmptyUndoBuffer

Voláním této funkce resetování (Vymazat) příznak vrácení ovládacího prvku pro úpravy.

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Poznámky

Ovládací prvek pro úpravy teď budou moct vrátit zpět poslední operaci. Pokaždé, když se operace v rámci ovládacího prvku pro úpravy mohou být vráceny zpět, je nastaven příznak vrácení zpět.

Příznak vrácení zpět je automaticky vymazána vždy, když [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) nebo [SetHandle](#sethandle) `CWnd` členské funkce jsou volány.

Další informace najdete v tématu [EM_EMPTYUNDOBUFFER](/windows/desktop/Controls/em-emptyundobuffer) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

##  <a name="fmtlines"></a>  CEdit::FmtLines

Voláním této funkce pro nastavení zapnutí nebo vypnutí zahrnutí znaků obnovitelně oddělených koncem řádku v rámci víceřádkové textové pole.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Parametry

*bAddEOL*<br/>
Určuje, zda mají být vloženy obnovitelně oddělených koncem řádku znaků. Hodnota TRUE vloží znaků. Odebere hodnotu FALSE.

### <a name="return-value"></a>Návratová hodnota

Formátování dojde k nenulovou hodnotu, pokud existuje; jinak 0.

### <a name="remarks"></a>Poznámky

Konec řádku obnovitelně se skládá z dva konce řádků a odřádkování vložit na konec řádku, které bylo přerušeno z důvodu zabalení aplikace word. Konec řádku pevný se skládá z jednoho návrat na začátek a konce řádku. Řádky, které končí zalomení řádku pevný nejsou ovlivněny `FmtLines`.

Windows bude reagovat jen v případě, `CEdit` objekt je víceřádkové textové pole.

`FmtLines` vyrovnávací paměť, vrátí se týká pouze [gethandle –](#gethandle) a text vrácený [WM_GETTEXT](/windows/desktop/winmsg/wm-gettext). Nemá žádný vliv na zobrazení textu v textovém poli.

Další informace najdete v tématu [EM_FMTLINES](/windows/desktop/Controls/em-fmtlines) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

##  <a name="getcuebanner"></a>  CEdit::GetCueBanner

Načte text, který se zobrazí jako textové upozornění nebo tip do ovládacího prvku edit, když ovládací prvek je prázdný.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[out] Ukazatel na řetězec, který obsahuje text upozornění.

*cchText*<br/>
[in] Počet znaků, které může být přijata. Toto číslo zahrnuje ukončující znak NULL.

### <a name="return-value"></a>Návratová hodnota

Pro první přetížení hodnotu TRUE, pokud je metoda úspěšná. v opačném případě FALSE.

Pro druhé přetížení [CString](../../atl-mfc-shared/using-cstring.md) , který obsahuje text upozornění, pokud je metoda úspěšná; v opačném případě prázdný řetězec ("").

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [EM_GETCUEBANNER](/windows/desktop/Controls/em-getcuebanner) zprávu, která je popsána v sadě Windows SDK. Další informace najdete v tématu [Edit_GetCueBannerText](/windows/desktop/api/commctrl/nf-commctrl-edit_getcuebannertext) – makro.

##  <a name="getfirstvisibleline"></a>  CEdit::GetFirstVisibleLine

Voláním této funkce k určení nejvyššího viditelné řádku do ovládacího prvku edit.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Návratová hodnota

Z nuly vycházející index řádku nejvyššího viditelné. Pro jednořádková ovládací prvky vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [EM_GETFIRSTVISIBLELINE](/windows/desktop/Controls/em-getfirstvisibleline) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

##  <a name="gethandle"></a>  CEdit::GetHandle

Volání této funkce načtete popisovač je paměť přidělená aktuálně pro ovládací prvek upravit více řádků.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač místní paměti, který identifikuje vyrovnávací paměti, která uchovává obsah ovládacího prvku pro úpravy. Pokud dojde k chybě, jako je odeslání zprávy do ovládacího prvku pole, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Popisovač je popisovač místní paměti a můžou používat podle těchto sloupců **místní** paměti funkcí Windows, které přijímají místní paměti zpracovat jako parametr.

`GetHandle` zpracovává pouze ovládacích prvcích pro úpravy více řádků.

Volání `GetHandle` pro ovládací prvek upravit více řádků v dialogovém okně pouze v případě, že dialogové okno byl vytvořen s příznakem styl DS_LOCALEDIT. Pokud není nastaven styl DS_LOCALEDIT, dostanete nenulovou návratovou hodnotu, ale nebudete moct používat vrácené hodnoty.

> [!NOTE]
> `GetHandle` nebude fungovat s Windows 95/98. Při volání `GetHandle` ve Windows 95/98, vrátí hodnotu NULL. `GetHandle` bude fungovat, jak je uvedeno v části Windows NT verze 3.51 a vyšší.

Další informace najdete v tématu [EM_GETHANDLE](/windows/desktop/Controls/em-gethandle) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

##  <a name="gethighlight"></a>  CEdit::GetHighlight

Získá indexy první a poslední znak v rozsahu textu, který je zvýrazněn v aktuální ovládací prvek pro úpravy.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pichStart*|[out] Z nuly vycházející index prvního znaku v rozsahu text, který je zvýrazněn.|
|*pichEnd*|[out] Z nuly vycházející index posledního znaku v rozsahu text, který je zvýrazněn.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [EM_GETHILITE](/windows/desktop/Controls/em-gethilite) zprávu, která je popsána v sadě Windows SDK. Obě `SetHighlight` a `GetHighlight` aktuálně nejsou povoleny pro UNICODE pouze sestavení.

##  <a name="getlimittext"></a>  CEdit::GetLimitText

Voláním této členské funkce se získat text limit pro to `CEdit` objektu.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální text limit, v bajtech pro tuto `CEdit` objektu.

### <a name="remarks"></a>Poznámky

Limit textu je maximální množství textu v bajtech, které přijímají ovládací prvek pro úpravy.

> [!NOTE]
>  Tato členská funkce je k dispozici od verze Windows 95 a Windows NT 4.0.

Další informace najdete v tématu [EM_GETLIMITTEXT](/windows/desktop/Controls/em-getlimittext) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

##  <a name="getline"></a>  CEdit::GetLine

Voláním této funkce k načtení řádku textu z ovládacího prvku pro úpravy a umístí jej do *lpszBuffer*.

```
int GetLine(
    int nIndex,
    LPTSTR lpszBuffer) const;

int GetLine(
    int nIndex,
    LPTSTR lpszBuffer,
    int nMaxLength) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje číslo řádku k načtení z řádku více ovládacích prvků pro úpravy. Čísla řádků jsou počítány od nuly; Hodnota 0 určuje první řádek. Tento parametr je ignorován v jednořádkové textové pole.

*lpszBuffer*<br/>
Body do vyrovnávací paměti, která obdrží kopii řádku. První slovo vyrovnávací paměti musí určit maximální počet znaků, které je možné zkopírovat do vyrovnávací paměti.

*nMaxLength*<br/>
Určuje maximální počet bajtů, které je možné zkopírovat do vyrovnávací paměti. `GetLine` umístí tato hodnota první slovo *lpszBuffer* před provedením volání do Windows.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů ve skutečnosti zkopírovány. Vrácená hodnota je 0, pokud určené číslo řádku *nIndex* je větší než počet řádků v textovém poli.

### <a name="remarks"></a>Poznámky

Zkopírovaného řádku neobsahuje znak ukončení hodnotou null.

Další informace najdete v tématu [EM_GETLINE](/windows/desktop/Controls/em-getline) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit::GetLineCount](#getlinecount).

##  <a name="getlinecount"></a>  CEdit::GetLineCount

Volání této funkce načtete počet řádků v řádku více ovládacích prvků pro úpravy.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Celé číslo obsahující počet řádků v řádku více ovládacích prvků pro úpravy. Pokud nebyl zadán žádný text do textového pole, vrácená hodnota je 1.

### <a name="remarks"></a>Poznámky

`GetLineCount` je zpracována pouze v ovládacích prvcích pro úpravy více řádků.

Další informace najdete v tématu [EM_GETLINECOUNT](/windows/desktop/Controls/em-getlinecount) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

##  <a name="getmargins"></a>  CEdit::GetMargins

Voláním této členské funkce k načtení levý a pravý okraj tento ovládací prvek pro úpravy.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka levého okraje na nižší řád slova a šířka pravého okraje v vyšší řád slova.

### <a name="remarks"></a>Poznámky

Okraje se měří v pixelech.

> [!NOTE]
>  Tato členská funkce je k dispozici od verze Windows 95 a Windows NT 4.0.

Další informace najdete v tématu [EM_GETMARGINS](/windows/desktop/Controls/em-getmargins) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="getmodify"></a>  CEdit::GetModify

Voláním této funkce k určení, zda byly upraveny obsah ovládacího prvku pro úpravy.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byly změněny obsah textové pole; 0, pokud mají zůstalo beze změny.

### <a name="remarks"></a>Poznámky

Windows udržuje interní příznak označující, zda byly změněny obsah ovládacího prvku pro úpravy. Tento příznak se vymaže při prvním vytvoření ovládacího prvku pro úpravy a může také vymazat voláním [SetModify](#setmodify) členskou funkci.

Další informace najdete v tématu [EM_GETMODIFY](/windows/desktop/Controls/em-getmodify) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

##  <a name="getpasswordchar"></a>  CEdit::GetPasswordChar

Voláním této funkce načtete znak hesla, která se zobrazí v ovládacím prvku upravovat, když uživatel zadá text.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Návratová hodnota

Určuje znak zobrazený namísto znaku, který uživatel zadal. Vrácená hodnota je NULL, pokud neexistuje žádný znak hesla.

### <a name="remarks"></a>Poznámky

Pokud vytvoříte ovládací prvek pro úpravy stylu ES_PASSWORD, určuje knihovnu DLL, která podporuje ovládací prvek výchozí znak hesla. Manifest nebo [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) metoda určuje, které knihovny DLL podporuje ovládací prvek pro úpravy. Pokud user32.dll podporuje ovládací prvek pro úpravy, výchozí znak hesla je hvězdička ("*", U + 002A). Pokud verze souboru comctl32.dll 6 podporuje ovládací prvek pro úpravy, je výchozí znakovou KRUH ČERNÉ ("●", U + 25CF). Další informace o který podporuje knihovnu DLL a verze běžných ovládacích prvků naleznete v tématu [prostředí a verze běžných ovládacích prvků](https://msdn.microsoft.com/library/windows/desktop/bb776779).

Tato metoda odesílá [EM_GETPASSWORDCHAR](/windows/desktop/Controls/em-getpasswordchar) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

##  <a name="getrect"></a>  CEdit::GetRect

Voláním této funkce získáte formátování obdélníku ovládacího prvku pro úpravy.

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lprect –*<br/>
Odkazuje `RECT` struktura, která přijímá formátování obdélník.

### <a name="remarks"></a>Poznámky

Formátování obdélníku je omezující obdélník text, který je nezávislý na velikost okna textové pole.

Můžete upravit formátování obdélník víceřádkové textové pole [setrect –](#setrect) a [SetRectNP](#setrectnp) členské funkce.

Další informace najdete v tématu [EM_GETRECT](/windows/desktop/Controls/em-getrect) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit::LimitText](#limittext).

##  <a name="getsel"></a>  CEdit::GetSel

Voláním této funkce můžete získat počáteční a koncovou pozicí znak aktuálního výběru (pokud existuje) v ovládacím prvku upravovat pomocí parametry nebo návratovou hodnotu.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>Parametry

*nStartChar*<br/>
Odkaz na celé číslo, které se zobrazí pozice prvního znaku v aktuálním výběru.

*nEndChar*<br/>
Odkaz na celé číslo, které se zobrazí pozice první nevybrané znaku za koncem aktuálního výběru.

### <a name="return-value"></a>Návratová hodnota

Verze, která vrátí hodnotu typu DWORD vrátí hodnotu, která obsahuje počáteční pozice v nižší řád slova a pozice prvního znaku nevybrané za koncem výběr v vyšší řád slova.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [EM_GETSEL](/windows/desktop/Controls/em-getsel) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

##  <a name="hideballoontip"></a>  CEdit::HideBalloonTip

Skryje všechny tipu v bublině přidružené k aktuální ovládací prvek pro úpravy.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato funkce posílá [EM_HIDEBALLOONTIP](/windows/desktop/Controls/em-hideballoontip) zprávu, která je popsána v sadě Windows SDK.

##  <a name="limittext"></a>  CEdit::LimitText

Voláním této funkce pro omezení délky textu, který může uživatel zadat do ovládacího prvku pro úpravy.

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Parametry

*nChars*<br/>
Určuje délku (v bajtech), který může uživatel zadat text. Pokud má parametr hodnotu 0, délka textu je nastavena na UINT_MAX bajtů. Toto je výchozí chování.

### <a name="remarks"></a>Poznámky

Změna limitu text omezuje pouze text, který může uživatel zadat. Již nemá žádný vliv na žádný text v textovém poli, ani to ovlivní délka textu zkopírován do ovládacího prvku pro úpravy ve [SetWindowText](cwnd-class.md#setwindowtext) členskou funkci `CWnd`. Pokud aplikace používá `SetWindowText` umístit více textu do ovládacího prvku edit, než je zadaný ve volání funkce `LimitText`, uživatel může odstranit některé z textu v textovém poli. Ale limit textu se zabrání uživateli v nahraďte existující text novým textem, není-li odstranit aktuální výběr způsobí, že text, který má klesnou pod limit textu.

> [!NOTE]
>  V systému Win32 (Windows NT a Windows 95/98), [SetLimitText](#setlimittext) nahrazuje tuto funkci.

Další informace najdete v tématu [EM_LIMITTEXT](/windows/desktop/Controls/em-limittext) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

##  <a name="linefromchar"></a>  CEdit::LineFromChar

Volání této funkce načtete číslo řádku, který obsahuje index zadaný znak řádku.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje hodnotu index o základu 0 pro požadovaný znak v textu ovládacího prvku pro úpravy nebo -1. Pokud *nIndex* se -1, určuje aktuální řádek, to znamená, že řádek obsahuje blikající kurzor.

### <a name="return-value"></a>Návratová hodnota

Počet řádků od nuly řádek obsahující znakový index určené *nIndex*. Pokud *nIndex* se -1, číslo řádku, který obsahuje první znak výběr se vrátí. Pokud není nic vybráno, vrátí se aktuální číslo řádku.

### <a name="remarks"></a>Poznámky

Znakový index je počet znaků od začátku ovládacích prvků pro úpravy.

Tato členská funkce se používá pouze v ovládacích prvcích pro úpravy více řádků.

Další informace najdete v tématu [EM_LINEFROMCHAR](/windows/desktop/Controls/em-linefromchar) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

##  <a name="lineindex"></a>  CEdit::LineIndex

Volání této funkce načtete znakový index řádku v rámci řádku více ovládacích prvků pro úpravy.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*Online*<br/>
Obsahuje hodnotu indexu pro požadovaný řádek z ovládacího prvku pro úpravy textu nebo -1. Pokud *využívat* se -1, určuje aktuální řádek, to znamená, že řádek obsahuje blikající kurzor.

### <a name="return-value"></a>Návratová hodnota

Znakový index řádku zadaném v *využívat* nebo -1, pokud zadaný počet řádků je větší než počet řádků v textovém poli.

### <a name="remarks"></a>Poznámky

Znakový index je počet znaků od začátku textovém poli na určený řádek.

Tato členská funkce je zpracována pouze v ovládacích prvcích pro úpravy více řádků.

Další informace najdete v tématu [EM_LINEINDEX](https://msdn.microsoft.com/library/windows/desktop/bb761611) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

##  <a name="linelength"></a>  CEdit::LineLength

Načte délku řádku do ovládacího prvku pro úpravy.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*Online*<br/>
Index založený na nule znak na řádku, jehož délka má být načtena. Výchozí hodnota je -1.

### <a name="return-value"></a>Návratová hodnota

Pro jednořádková ovládací prvky vrácená hodnota je v TCHARs, délka textu v textovém poli.

Pro víceřádková textová pole, je návratová hodnota délka řádku určené v TCHARs, *využívat* parametru. Pro text v kódu ANSI délka je počet bajtů v řádku. pro text v kódu Unicode délka je počet znaků v řádku. Délka neobsahovalo znak návratu na konci řádku.

Pokud *využívat* parametr je větší než počet znaků v ovládacím prvku, vrácená hodnota je nula.

Pokud *využívat* -1 je parametr, návratová hodnota je počet nevybraných znaky na řádcích, které obsahují vybrané znaky. Například pokud výběr sahá od čtvrtý znak jednoho řádku prostřednictvím osmého znaků z konce zalamovat, vrácená hodnota je 10. To znamená tři znaky na první řádek a sedm na další.

Další informace o typu TCHAR, najdete v článku TCHAR řádek v tabulce v [datové typy Windows](/windows/desktop/WinProg/windows-data-types).

### <a name="remarks"></a>Poznámky

Tato metoda je podporována [EM_LINELENGTH](/windows/desktop/Controls/em-linelength) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit::LineIndex](#lineindex).

##  <a name="linescroll"></a>  CEdit::LineScroll

Volání této funkce můžete posunout text řádku více ovládacích prvků pro úpravy.

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Parametry

*nLines*<br/>
Určuje počet řádků pro posunout svisle.

*nChars*<br/>
Určuje počet pozic znaků vodorovně posouvat. Tato hodnota je ignorována, pokud má ES_RIGHT nebo ES_CENTER stylu ovládacího prvku pro úpravy.

### <a name="remarks"></a>Poznámky

Tato členská funkce je zpracována pouze ovládacích prvcích pro úpravy více řádků.

Ovládací prvek pro úpravy neposouvá svisle za poslední řádek textu v textovém poli. Pokud aktuální řádek plus počet řádků, které jsou určené *nLines* překročí celkový počet řádků v textovém poli, hodnota se upraví tak, že poslední řádek ovládacích prvků pro úpravy je přechod na horní části okna textové pole.

`LineScroll` je možné po poslední znak libovolném řádku posouvat vodorovně.

Další informace najdete v tématu [EM_LINESCROLL](/windows/desktop/Controls/em-linescroll) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit::GetFirstVisibleLine](#getfirstvisibleline).

##  <a name="paste"></a>  CEdit::Paste

Voláním této funkce vložení dat ze schránky do `CEdit` na pozici kurzoru.

```
void Paste();
```

### <a name="remarks"></a>Poznámky

Data budou vložena pouze v případě, že obsahuje data ve formátu CF_TEXT do schránky.

Další informace najdete v tématu [WM_PASTE](/windows/desktop/dataxchg/wm-paste) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

##  <a name="posfromchar"></a>  CEdit::PosFromChar

Voláním této funkce získáte pozice (levý horní roh) daného znaku v rámci této `CEdit` objektu.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
Index založený na nule zadaný znak.

### <a name="return-value"></a>Návratová hodnota

Souřadnice levého horního rohu znakem určeným ve *nChar*.

### <a name="remarks"></a>Poznámky

Znak, který je zadán tím, že její hodnota index založený na nule. Pokud *nChar* je větší než index poslední znak v tomto `CEdit` objektu, návratová hodnota určuje souřadnice pozice znaku pouze po poslední znak v tomto `CEdit` objektu.

> [!NOTE]
>  Tato členská funkce je k dispozici od verze Windows 95 a Windows NT 4.0.

Další informace najdete v tématu [EM_POSFROMCHAR](/windows/desktop/Controls/em-posfromchar) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit::LineFromChar](#linefromchar).

##  <a name="replacesel"></a>  CEdit::ReplaceSel

Voláním této funkce k nahrazení aktuální výběr v ovládacím prvku pro úpravy s textem určeným parametrem *lpszNewText*.

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszNewText*<br/>
Odkazuje na řetězec zakončený hodnotou null obsahující Nahrazovací text.

*bCanUndo*<br/>
Chcete-li určit, že tuto funkci lze vrátit zpět, nastavte hodnotu tohoto parametru na hodnotu TRUE. Výchozí hodnota je FALSE.

### <a name="remarks"></a>Poznámky

Nahrazuje pouze část textu v ovládacím prvku upravovat. Pokud chcete nahradit veškerý text, použijte [CWnd::SetWindowText](cwnd-class.md#setwindowtext) členskou funkci.

Pokud nebyla vybrána žádná aktuální položka, Nahrazovací text je vložen do aktuálního umístění kurzoru.

Další informace najdete v tématu [EM_REPLACESEL](/windows/desktop/Controls/em-replacesel) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit::LineIndex](#lineindex).

##  <a name="setcuebanner"></a>  CEdit::SetCueBanner

Nastaví text, který se zobrazí jako textové upozornění nebo tip, v editací řídit, kdy ovládací prvek je prázdný.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[in] Ukazatel na řetězec, který obsahuje upozornění zobrazíte v textovém poli.

*fDrawWhenFocused*<br/>
[in] Pokud má hodnotu FALSE, startovací banner není vykresleno, když uživatel klikne do oblasti ovládacího prvku pro úpravy a poskytuje ovládací prvek fokus.

Při hodnotě TRUE se banner startovací vykreslením i v případě, že ovládací prvek má fokus. Banner upozornění zmizí při spuštění uživatelem na typ v ovládacím prvku.

Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je metoda úspěšná. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [EM_SETCUEBANNER](/windows/desktop/Controls/em-setcuebanner) zprávu, která je popsána v sadě Windows SDK. Další informace najdete v tématu [Edit_SetCueBannerTextFocused](/windows/desktop/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) – makro.

### <a name="example"></a>Příklad

Následující příklad ukazuje, [CEdit::SetCueBanner](#setcuebanner) metody.

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

##  <a name="sethandle"></a>  CEdit::SetHandle

Volání této funkce nastavíte popisovače k místní paměti, který se použije čárou více ovládacích prvků pro úpravy.

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Parametry

*hBuffer*<br/>
Obsahuje popisovač pro místní paměti. Tento popisovač musí být vytvořen voláním předchozí [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc) pomocí LMEM_MOVEABLE příznak funkce Windows. Paměť se předpokládá, že obsahují řetězec zakončený hodnotou null. Pokud to není tento případ, první bajt přidělené paměti by měla nastavena na hodnotu 0.

### <a name="remarks"></a>Poznámky

Ovládací prvek pro úpravy poté použije tuto vyrovnávací paměť pro ukládání aktuálně zobrazený text namísto přidělení vyrovnávací paměti.

Tato členská funkce je zpracována pouze ovládacích prvcích pro úpravy více řádků.

Předtím, než aplikace nastaví nový popisovač paměti, používejte [gethandle –](#gethandle) členskou funkci získat popisovač aktuální vyrovnávací paměti a uvolnit, že při použití paměti `LocalFree` funkce Windows.

`SetHandle` Vymaže zpět vyrovnávací paměti ( [CanUndo](#canundo) členská funkce vrátí 0) a příznak interní změny ( [GetModify](#getmodify) členská funkce vrátí 0). Textové pole okno se překreslí.

V dialogovém okně můžete použít tato členská funkce v ovládacím prvku pro úpravy více řádků, pouze v případě, že vytvoříte dialogové okno s příznakem styl DS_LOCALEDIT.

> [!NOTE]
> `GetHandle` nebude fungovat s Windows 95/98. Při volání `GetHandle` ve Windows 95/98, vrátí hodnotu NULL. `GetHandle` bude fungovat, jak je uvedeno v části Windows NT verze 3.51 a vyšší.

Další informace najdete v tématu [EM_SETHANDLE](/windows/desktop/Controls/em-sethandle), [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc), a [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

##  <a name="sethighlight"></a>  CEdit::SetHighlight

Vybraná vystoupení a rozsah textu, který se zobrazí v aktuálních ovládacích prvků pro úpravy.

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ichStart*|[in] Z nuly vycházející index prvního znaku v rozsahu text, abyste měli na očích.|
|*ichEnd*|[in] Z nuly vycházející index posledního znaku v rozsahu text, abyste měli na očích.|

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [EM_SETHILITE](/windows/desktop/Controls/em-sethilite) zprávu, která je popsána v sadě Windows SDK.  Tato metoda odesílá [EM_SETHILITE](/windows/desktop/Controls/em-sethilite) zprávu, která je popsána v sadě Windows SDK. Obě `SetHighlight` a `GetHighlight` jde jenom sestavení kódování UNICODE.

##  <a name="setlimittext"></a>  CEdit::SetLimitText

Voláním této členské funkce se nastavit limit textu pro tento `CEdit` objektu.

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Parametry

*Nmaximum*<br/>
Nový text limit, ve znacích.

### <a name="remarks"></a>Poznámky

Limit textu je maximální množství textu, ve znacích, které ovládací prvek pro úpravy může přijmout.

Změna limitu text omezuje pouze text, který může uživatel zadat. Již nemá žádný vliv na žádný text v textovém poli, ani to ovlivní délka textu zkopírován do ovládacího prvku pro úpravy ve [SetWindowText](cwnd-class.md#setwindowtext) členskou funkci `CWnd`. Pokud aplikace používá `SetWindowText` umístit více textu do ovládacího prvku edit, než je zadaný ve volání funkce `LimitText`, uživatel může odstranit některé z textu v textovém poli. Ale limit textu se zabrání uživateli v nahraďte existující text novým textem, není-li odstranit aktuální výběr způsobí, že text, který má klesnou pod limit textu.

Tato funkce nahrazuje [LimitText](#limittext) v systému Win32.

Další informace najdete v tématu [EM_SETLIMITTEXT](/windows/desktop/Controls/em-setlimittext) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="setmargins"></a>  CEdit::SetMargins

Voláním této metody lze nastavit levý a pravý okraj tento ovládací prvek pro úpravy.

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Parametry

*nLeft*<br/>
Šířka nové levý okraj v pixelech.

*nRight*<br/>
Šířka nové pravý okraj v pixelech.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato členská funkce je k dispozici od verze Windows 95 a Windows NT 4.0.

Další informace najdete v tématu [EM_SETMARGINS](/windows/desktop/Controls/em-setmargins) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="setmodify"></a>  CEdit::SetModify

Voláním této funkce nastavit nebo zrušte příznak upravené pro ovládací prvek upravit.

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Hodnota TRUE označuje, že byl změněn text a hodnota FALSE označuje, že je verzí bez úprav. Ve výchozím nastavení je nastavit příznak upravené.

### <a name="remarks"></a>Poznámky

Upravené příznak určuje, zda byl změněn text v textovém poli. Je automaticky nastaven pokaždé, když uživatel změní text. Jeho hodnotu může načíst s [GetModify](#getmodify) členskou funkci.

Další informace najdete v tématu [EM_SETMODIFY](/windows/desktop/Controls/em-setmodify) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit::GetModify](#getmodify).

##  <a name="setpasswordchar"></a>  CEdit::SetPasswordChar

Voláním této funkce, nastavení nebo odebrání znak hesla zobrazí v ovládacím prvku upravovat, když uživatel zadá text.

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Určuje znak, aby se zobrazovaly místo znaky zadané uživatelem. Pokud *ch* je 0, zobrazují se skutečnými znaky zadané uživatelem.

### <a name="remarks"></a>Poznámky

Když nastavíte znak hesla, zobrazí se tento znak pro každý znak zadaného uživatelem.

Tato členská funkce nemá žádný vliv na řádku více ovládacích prvků pro úpravy.

Když `SetPasswordChar` členská funkce je volána, `CEdit` překreslí všechny viditelné znaky použití znaku určené *ch*.

Pokud ovládací prvek pro úpravy je vytvořen pomocí [ES_PASSWORD](styles-used-by-mfc.md#edit-styles) styl, výchozí znak hesla je nastaven na hvězdičku ( <strong>\*</strong>). Tento styl je odebrána, pokud `SetPasswordChar` volána s *ch* nastavena na hodnotu 0.

Další informace najdete v tématu [EM_SETPASSWORDCHAR](/windows/desktop/Controls/em-setpasswordchar) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

##  <a name="setreadonly"></a>  CEdit::SetReadOnly

Volá tuto funkci pro nastavení jen pro čtení stavu ovládacího prvku pro úpravy.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bReadOnly*<br/>
Určuje, zda nastavení nebo odebrání stavu jen pro čtení ovládacích prvků pro úpravy. Hodnota TRUE, nastaví stav jen pro čtení; hodnota FALSE, nastaví stav pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je operace úspěšná, nebo dojde k 0, pokud chybu.

### <a name="remarks"></a>Poznámky

Aktuální nastavení můžete zobrazit tak testování [ES_READONLY](styles-used-by-mfc.md#edit-styles) příznak v návratové hodnotě [CWnd::GetStyle](cwnd-class.md#getstyle).

Další informace najdete v tématu [EM_SETREADONLY](/windows/desktop/Controls/em-setreadonly) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

##  <a name="setrect"></a>  CEdit::SetRect

Volání této funkce nastavíte rozměry obdélníku pomocí zadaných souřadnic.

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lprect –*<br/>
Odkazuje `RECT` struktury nebo `CRect` objekt, který určuje nové rozměry formátování obdélník.

### <a name="remarks"></a>Poznámky

Tento člen je zpracována pouze ovládacích prvcích pro úpravy více řádků.

Použití `SetRect` formátování obdélník řádku více ovládacích prvků pro úpravy. Formátování obdélníku je omezující obdélník text, který je nezávislý na velikost okna textové pole. Při prvním vytvoření ovládacího prvku pro úpravy, formátování obdélníku je stejný jako klientské oblasti okna textové pole. S použitím `SetRect` členskou funkci aplikace provést formátování obdélník větší nebo menší než časový interval pro textové pole.

Pokud textové pole nemá žádné posuvník, text bude oříznut, není zabalena, pokud formátování obdélník větší než časové období. Obsahuje-li ovládací prvek pro úpravy ohraničení, formátování obdélník sníží velikost ohraničení. Pokud upravíte obdélník vrátí `GetRect` členskou funkci, musíte odebrat velikost ohraničení předáte obdélník `SetRect`.

Když `SetRect` je volána, ovládací prvek pro úpravy textu je také přeformátovali a zobrazí znovu.

Další informace najdete v tématu [EM_SETRECT](/windows/desktop/Controls/em-setrect) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

##  <a name="setrectnp"></a>  CEdit::SetRectNP

Volání této funkce nastavíte formátování obdélník řádku více ovládacích prvků pro úpravy.

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lprect –*<br/>
Odkazuje `RECT` struktury nebo `CRect` objekt, který určuje nové rozměry obdélníku.

### <a name="remarks"></a>Poznámky

Formátování obdélníku je omezující obdélník text, který je nezávislý na velikost okna textové pole.

`SetRectNP` je stejný jako `SetRect` členské funkce s tím rozdílem, že v okně Upravit ovládací prvek není překreslení.

Při prvním vytvoření ovládacího prvku pro úpravy, formátování obdélníku je stejný jako klientské oblasti okna textové pole. Při volání `SetRectNP` členskou funkci aplikace provést formátování obdélník větší nebo menší než časový interval pro textové pole.

Pokud textové pole nemá žádné posuvník, text bude oříznut, není zabalena, pokud formátování obdélník větší než časové období.

Tento člen je zpracována pouze ovládacích prvcích pro úpravy více řádků.

Další informace najdete v tématu [EM_SETRECTNP](/windows/desktop/Controls/em-setrectnp) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit::SetRect](#setrect).

##  <a name="setsel"></a>  CEdit::SetSel

Voláním této funkce můžete vybrat rozsah znaků v textové pole.

```
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>Parametry

*dwSelection*<br/>
Určuje počáteční pozici v nižší řád slova a koncovou pozici vyšší řád slova. Pokud nižší řád slova je 0 a vyšší řád slova, je -1, je vybrat veškerý text v textovém poli. Pokud nižší řád slova se -1, odeberou se všechny aktuální výběr.

*bNoScroll*<br/>
Určuje, zda blikající kurzor by měl být přešli do zobrazení. Pokud má hodnotu FALSE, je přesunut do zobrazení oblasti blikajícího kurzoru. Pokud je hodnota TRUE, není přesunut do zobrazení oblasti blikajícího kurzoru.

*nStartChar*<br/>
Určuje počáteční pozici. Pokud *nStartChar* je 0 a *nEndChar* se -1, vše je vybraný text v textovém poli. Pokud *nStartChar* se -1, se odebere všechny aktuální výběr.

*nEndChar*<br/>
Určuje koncovou pozici.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [EM_SETSEL](/windows/desktop/Controls/em-setsel) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit::GetSel](#getsel).

##  <a name="settabstops"></a>  CEdit::SetTabStops

Volání této funkce nastavíte zarážky v řádku více ovládacích prvků pro úpravy.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Určuje, že zarážek je možné nastavit na každých *cxEachStop* jednotkách dialogového okna.

*nTabStops*<br/>
Určuje počet zarážek tabulátoru, které jsou součástí *rgTabStops*. Tato hodnota musí být větší než 1.

*rgTabStops*<br/>
Odkazuje na pole celých čísel bez znaménka určující kartě zastaví v jednotkách dialogového okna. Dialogové okno jednotka je vodorovném nebo svislém distance. 1 jednotka vodorovné dialogového okna je rovna čtvrtinu aktuální jednotku základní šířky dialogového okna a 1 jednotka svislé dialogového okna je rovna 28 jedním z aktuální jednotky pro základní výška dialogové okno. Dialogové okno základní jednotky se vypočítávají na základě výšku a šířku aktuální systémové písmo. `GetDialogBaseUnits` Windows funkce vrátí aktuální dialogové okno základní jednotky v pixelech.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla nastavena na kartách; jinak 0.

### <a name="remarks"></a>Poznámky

Když text bude zkopírován do více řádků textové pole, způsobí, že libovolný znak tabulátoru v textu místo vygenerování až na další zarážku.

K nastavení zarážek na výchozí velikost 32 jednotkách dialogového okna, volání bez parametrů verze tuto členskou funkci. Chcete-li nastavení zarážek na velikost než 32, zavolejte na verzi pomocí *cxEachStop* parametru. K nastavení zarážek na celou řadu velikostí, použijte verzi se dvěma parametry.

Tato členská funkce je zpracována pouze v ovládacích prvcích pro úpravy více řádků.

`SetTabStops` není překreslí automaticky okna upravit. Pokud změníte tabulátoru textu již v textovém poli, volejte [CWnd::InvalidateRect](cwnd-class.md#invalidaterect) překreslení okna upravit.

Další informace najdete v tématu [EM_SETTABSTOPS](/windows/desktop/Controls/em-settabstops) a [GetDialogBaseUnits](/windows/desktop/api/winuser/nf-winuser-getdialogbaseunits) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEditView::SetTabStops](ceditview-class.md#settabstops).

##  <a name="showballoontip"></a>  CEdit::ShowBalloonTip

Zobrazí zobrazení tipu v bublině, který je přidružený aktuální ovládací prvek pro úpravy.

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pEditBalloonTip*|[in] Ukazatel [EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip) struktura, která popisuje tipu v bublině.|
|*lpszTitle*|[in] Ukazatel na řetězec znaků Unicode, který obsahuje název tipu v bublině.|
|*lpszText*|[in] Ukazatel na řetězec znaků Unicode, který obsahuje text tipu bublina.|
|*ttiIcon*|[in] **INT** , který určuje typ ikona spojená s tipu v bublině. Výchozí hodnota je TTI_NONE. Další informace najdete v tématu `ttiIcon` člena [EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip) struktury.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato funkce posílá [EM_SHOWBALLOONTIP](/windows/desktop/Controls/em-showballoontip) zprávu, která je popsána v sadě Windows SDK. Další informace najdete v tématu [Edit_ShowBalloonTip](/windows/desktop/api/commctrl/nf-commctrl-edit_showballoontip) – makro.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_cedit`, která je pro přístup k aktuální ovládací prvek pro úpravy. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Příklad

Následující příklad kódu zobrazuje zobrazení tipu v bublině pro ovládací prvek upravit. [CEdit::ShowBalloonTip](#showballoontip) metody Určuje název a bubliny text tipu.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

##  <a name="undo"></a>  CEdit::Undo

Voláním této funkce vrátit zpět poslední operace edit-control.

```
BOOL Undo();
```

### <a name="return-value"></a>Návratová hodnota

Jednořádkové textové pole vrácená hodnota je vždy nenulový. Pro ovládací prvek upravit více řádků, vrácená hodnota je nenulová, pokud je operace vrácení zpět úspěšná, nebo 0, pokud selže operace vrácení zpět.

### <a name="remarks"></a>Poznámky

Operace zpět může být také vrátit zpět. Například můžete obnovit odstraněný text s prvním volání `Undo`. Za předpokladu, neexistuje žádná síťová operaci úprav, můžete odebrat text s druhé volání `Undo`.

Další informace najdete v tématu [EM_UNDO](/windows/desktop/Controls/em-undo) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC CALCDRIV](../../visual-cpp-samples.md)<br/>
[Ukázka CMNCTRL2 knihovny MFC](../../visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](cwnd-class.md)<br/>
[CButton – třída](cbutton-class.md)<br/>
[CComboBox – třída](ccombobox-class.md)<br/>
[CListBox – třída](clistbox-class.md)<br/>
[CScrollBar – třída](cscrollbar-class.md)<br/>
[CStatic – třída](cstatic-class.md)<br/>
[CDialog – třída](cdialog-class.md)
