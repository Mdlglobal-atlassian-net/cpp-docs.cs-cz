---
title: CEdit – třída
ms.date: 09/12/2018
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
ms.openlocfilehash: 94769a6fb3c5fceefda96b54cebb35b0533a8afa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753218"
---
# <a name="cedit-class"></a>CEdit – třída

Poskytuje funkce ovládacího prvku pro úpravy systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CEdit : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CEdit::CEditovat](#cedit)|Vytvoří `CEdit` řídicí objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|Určuje, zda lze operaci kontroly úprav vrátit zpět.|
|[CEdit::CharFromPos](#charfrompos)|Načte indexy řádků a znaků pro znak, který je nejblíže zadané pozici.|
|[CEdit::Vymazat](#clear)|Odstraní (vymaže) aktuální výběr (pokud existuje) v ovládacím prvku úprav.|
|[CEdit::Kopírovat](#copy)|Zkopíruje aktuální výběr (pokud existuje) v ovládacím prvku pro úpravy do schránky ve CF_TEXT formátu.|
|[CEdit::Vytvořit](#create)|Vytvoří ovládací prvek pro úpravy `CEdit` systému Windows a připojí jej k objektu.|
|[CEdit::Vyjmout](#cut)|Odstraní (vyjme) aktuální výběr (pokud existuje) v ovládacím prvku pro úpravy a zkopíruje odstraněný text do schránky ve formátu CF_TEXT.|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Obnoví (vymaže) příznak zrušení ovládacího prvku pro úpravy.|
|[CEdit::FmtLines](#fmtlines)|Nastaví zahrnutí znaků měkkého konce řádku zapnunebo vypne v rámci víceřádkového ovládacího prvku pro úpravy.|
|[CEdit::GetCueBanner](#getcuebanner)|Načte text, který je zobrazen jako text cue, nebo tip, v ovládacím prvku upravit, když je ovládací prvek prázdný a nemá fokus.|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Určuje nejvyšší viditelnou čáru v ovládacím prvku pro úpravy.|
|[CEdit::GetHandle](#gethandle)|Načte popisovač do paměti, která je aktuálně přidělena pro víceřádkový ovládací prvek pro úpravy.|
|[CEdit::GetHighlight](#gethighlight)|Získá indexy počáteční a koncové znaky v rozsahu textu, který je zvýrazněn v aktuální ovládací prvek úpravy.|
|[CEdit::GetLimitText](#getlimittext)|Získá maximální množství textu, který `CEdit` může obsahovat.|
|[CEdit::GetLine](#getline)|Načte řádek textu z ovládacího prvku pro úpravy.|
|[CEdit::GetLineCount](#getlinecount)|Načte počet řádků v ovládacím prvku pro úpravy více řádků.|
|[CEdit::GetMargins](#getmargins)|Získá levý a pravý okraj `CEdit`pro toto .|
|[CEdit::GetModify](#getmodify)|Určuje, zda byl obsah ovládacího prvku pro úpravy změněn.|
|[CEdit::GetPasswordChar](#getpasswordchar)|Načte znak hesla zobrazený v ovládacím prvku pro úpravy, když uživatel zadá text.|
|[CEdit::GetRect](#getrect)|Získá formátovací obdélník ovládacího prvku upravit.|
|[CEdit::GetSel](#getsel)|Získá první a poslední znak pozice aktuálního výběru v ovládacím prvku upravit.|
|[CEdit::HideBalloonTip](#hideballoontip)|Skryje všechny špičky pozice přidružené k aktuálnímu ovládacímu prvku úprav.|
|[CEdit::LimitText](#limittext)|Omezuje délku textu, který může uživatel zadat do ovládacího prvku pro úpravy.|
|[CEdit::LineFromchar](#linefromchar)|Načte číslo řádku, který obsahuje zadaný index znaků.|
|[CEdit::LineIndex](#lineindex)|Načte index znaků řádku v rámci víceřádkového ovládacího prvku pro úpravy.|
|[CEdit::Délka čáry](#linelength)|Načte délku řádku v ovládacím prvku pro úpravy.|
|[CEdit::LineScroll](#linescroll)|Posune text víceřádkového ovládacího prvku pro úpravy.|
|[CEdit::Paste](#paste)|Vloží data ze schránky do ovládacího prvku pro úpravy v aktuální pozici kurzoru. Data se vkládají pouze v případě, že schránka obsahuje data v CF_TEXT formátu.|
|[CEdit::PosFromChar](#posfromchar)|Načte souřadnice levého horního rohu zadaného indexu znaků.|
|[CEdit::ReplaceSel](#replacesel)|Nahradí aktuální výběr v ovládacím prvku úprav zadaným textem.|
|[CEdit::SetCueBanner](#setcuebanner)|Nastaví text, který je zobrazen jako textový pokyn nebo tip, v ovládacím prvku pro úpravy, když je ovládací prvek prázdný a nemá fokus.|
|[CEdit::SetHandle](#sethandle)|Nastaví popisovač na místní paměť, která bude použita víceřádkovým ovládacím prvkem pro úpravy.|
|[CEdit::SetHighlight](#sethighlight)|Zvýrazní rozsah textu, který se zobrazí v aktuálním ovládacím prvku úprav.|
|[CEdit::SetLimitText](#setlimittext)|Nastaví maximální množství `CEdit` textu, které může obsahovat.|
|[CEdit::SetMargins](#setmargins)|Nastaví levý a pravý `CEdit`okraj pro toto .|
|[CEdit::SetModify](#setmodify)|Nastaví nebo vymaže příznak změny ovládacího prvku pro úpravy.|
|[CEdit::SetPasswordChar](#setpasswordchar)|Nastaví nebo odebere znak hesla zobrazený v ovládacím prvku pro úpravy, když uživatel zadá text.|
|[CEdit::SetReadOnly](#setreadonly)|Nastaví stav ovládacího prvku pro úpravy jen pro čtení.|
|[CEdit::SetRect](#setrect)|Nastaví formátovací obdélník víceřádkového ovládacího prvku pro úpravy a aktualizuje ovládací prvek.|
|[CEdit::SetRectNP](#setrectnp)|Nastaví formátovací obdélník víceřádkového ovládacího prvku pro úpravy bez překreslení okna ovládacího prvku.|
|[CEdit::SetSel](#setsel)|Vybere rozsah znaků v ovládacím prvku pro úpravy.|
|[CEdit::SetTabstops](#settabstops)|Nastaví zarážky tabulátoru v ovládacím prvku pro úpravy více řádků.|
|[CEdit::Zobrazit BalloonTip](#showballoontip)|Zobrazí špičku pozice, která je přidružena k aktuálnímu ovládacímu prvku pro úpravy.|
|[CEdit::Vrátit se k ní](#undo)|Obrátí poslední operaci úprava-řízení.|

## <a name="remarks"></a>Poznámky

Ovládací prvek pro úpravy je obdélníkové podřízené okno, ve kterém může uživatel zadávat text.

Ovládací prvek pro úpravy můžete vytvořit buď ze šablony dialogového okna, nebo přímo v kódu. V obou případech nejprve `CEdit` volání konstruktoru k vytvoření objektu, `CEdit` pak volání [Vytvořit](#create) členská `CEdit` funkce vytvořit ovládací prvek pro úpravy systému Windows a připojit jej k objektu.

Konstrukce může být jednostupňový proces ve `CEdit`třídě odvozené z . Napište konstruktor pro odvozené `Create` třídy a volání z uvnitř konstruktoru.

`CEdit`dědí významné funkce `CWnd`od . Chcete-li nastavit a `CEdit` načíst `CWnd` text z objektu, použijte členské funkce [SetWindowText](cwnd-class.md#setwindowtext) a [GetWindowText](cwnd-class.md#getwindowtext), které nastavují nebo získávají celý obsah ovládacího prvku pro úpravy, i když se jedná o víceřádkový ovládací prvek. Řádky textu ve víceřádkovém ovládacím prvku jsou odděleny sekvencemi znaků \r\n. Také pokud editační ovládací prvek je víceřádkový, získat a `CEdit` nastavit část textu ovládacího prvku voláním členské funkce [GetLine](#getline), [SetSel](#setsel), [GetSel](#getsel), a [ReplaceSel](#replacesel).

Pokud chcete zpracovávat zprávy oznámení systému Windows odeslané ovládacím prvkem `CDialog`pro úpravy do nadřazeného ovládacího prvku (obvykle třídy odvozené z ), přidejte do nadřazené třídy pro každou zprávu funkci položky mapy zprávy a obslužné rutiny zprávy.

Každá položka mapy zpráv má následující podobu:

  **oznámení ON_**_NOTIFICATION_**(** _id_**,** _memberFxn_ **)**

kde `id` určuje ID podřízeného okna ovládacího prvku `memberFxn` pro úpravy odesílajícího oznámení a je název nadřazené členské funkce, kterou jste napsali pro zpracování oznámení.

Prototyp funkce nadřazeného objektu je následující:

**afx_msg** člen voidFxn **( );**

Následuje seznam možných položek mapy zpráv a popis případů, ve kterých by byly odeslány nadřazenému:

- ON_EN_CHANGE Uživatel provedl akci, která mohla změnit text v ovládacím prvku pro úpravy. Na rozdíl od EN_UPDATE oznámení je tato zpráva odeslána po aktualizaci zobrazení systémem Windows.

- ON_EN_ERRSPACE Ovládací prvek pro úpravy nemůže přidělit dostatek paměti pro splnění konkrétního požadavku.

- ON_EN_HSCROLL Uživatel klepne na vodorovný posuvník ovládacího prvku pro úpravy. Nadřazené okno je oznámeno před aktualizací obrazovky.

- ON_EN_KILLFOCUS Ovládací prvek pro úpravy ztratí vstupní fokus.

- ON_EN_MAXTEXT Aktuální vložení překročilo zadaný počet znaků pro ovládací prvek úprava a bylo zkráceno. Odesláno také v případě, že ovládací prvek pro úpravy nemá ES_AUTOHSCROLL stylu a počet znaků, které mají být vloženy, by překročil šířku ovládacího prvku pro úpravy. Odesláno také v případě, že ovládací prvek pro úpravy nemá ES_AUTOVSCROLL stylu a celkový počet řádků vyplývajících z vložení textu by překročil výšku ovládacího prvku úprav.

- ON_EN_SETFOCUS Odesláno, když ovládací prvek pro úpravy obdrží vstupní fokus.

- ON_EN_UPDATE Ovládací prvek úprav se chystá zobrazit změněný text. Odesláno poté, co ovládací prvek zformátoval text, ale před tím, než promítá text tak, aby velikost okna mohla být v případě potřeby změněna.

- ON_EN_VSCROLL Uživatel klepne na svislý posuvník ovládacího prvku pro úpravy. Nadřazené okno je oznámeno před aktualizací obrazovky.

Pokud vytvoříte `CEdit` objekt v dialogovém `CEdit` okně, objekt se automaticky zničí, když uživatel zavře dialogové okno.

Pokud vytvoříte `CEdit` objekt z prostředku dialogu pomocí `CEdit` dialogového editoru, objekt se automaticky zničí, když uživatel zavře dialogové okno.

Pokud vytvoříte `CEdit` objekt v okně, může být také nutné jej zničit. Pokud vytvoříte `CEdit` objekt v zásobníku, je automaticky zničen. Pokud vytvoříte `CEdit` objekt na haldě pomocí **nové** funkce, musíte volat **delete** na objekt zničit, když uživatel ukončí ovládací prvek pro úpravy systému Windows. Pokud přidělíte všechny `CEdit` paměti v `CEdit` objektu, přepsat destruktor k vyřazení přidělení.

Chcete-li upravit určité styly v ovládacím prvku pro úpravy (například ES_READONLY), musíte do ovládacího prvku odeslat určité zprávy namísto použití [modifystyle](cwnd-class.md#modifystyle). Viz [Úpravy stylů ovládacích prvků](/windows/win32/Controls/edit-control-styles) v sadě Windows SDK.

Další informace `CEdit`naleznete v tématu [Controls](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](cobject-class.md)

[CCmdCíl](ccmdtarget-class.md)

[Cwnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a>CEdit::CanUndo

Volání této funkce k určení, zda lze vrátit zpět poslední operaci úprav.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud lze poslední operaci úprav vrátit `Undo` zpět voláním členské funkce; 0, pokud jej nelze vrátit zpět.

### <a name="remarks"></a>Poznámky

Další informace naleznete v [EM_CANUNDO](/windows/win32/Controls/em-canundo) sady Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CEdit::Undo](#undo).

## <a name="ceditcedit"></a><a name="cedit"></a>CEdit::CEditovat

Vytvoří `CEdit` objekt.

```
CEdit();
```

### <a name="remarks"></a>Poznámky

Pomocí [příkazu Vytvořit](#create) vytvořte ovládací prvek pro úpravy systému Windows.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a>CEdit::CharFromPos

Volánítéto funkce k načtení indexů čáry a znaků na základě nuly `CEdit` znaku, který je nejblíže zadanému bodu v tomto ovládacím prvku.

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Souřadnice bodu v klientské `CEdit` oblasti tohoto objektu.

### <a name="return-value"></a>Návratová hodnota

Index znaků v dolním pořadí WORD a řádek index v word vysokého řádu.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Tato členská funkce je k dispozici počínaje systémy Windows 95 a Windows NT 4.0.

Další informace naleznete [v tématu EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a>CEdit::Vymazat

Volání této funkce odstranit (vymazat) aktuální výběr (pokud existuje) v ovládacím prvku upravit.

```cpp
void Clear();
```

### <a name="remarks"></a>Poznámky

Odstranění provedené `Clear` pomocí lze vrátit zpět voláním členské funkce [Zpět.](#undo)

Chcete-li odstranit aktuální výběr a umístit odstraněný obsah do schránky, zavolejte členskou funkci [Vyjmout.](#cut)

Další informace naleznete v [WM_CLEAR](/windows/win32/dataxchg/wm-clear) sady Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a>CEdit::Kopírovat

Volání této funkce koze aktuální výběr (pokud existuje) v ovládacím prvku upravit do schránky ve formátu CF_TEXT.

```cpp
void Copy();
```

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu WM_COPY](/windows/win32/dataxchg/wm-copy) sady Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a>CEdit::Vytvořit

Vytvoří ovládací prvek pro úpravy `CEdit` systému Windows a připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl ovládacího prvku pro úpravy. Aplikujte na ovládací prvek libovolnou kombinaci [stylů úprav.](styles-used-by-mfc.md#edit-styles)

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku pro úpravy. Může se `CRect` na `RECT` hrachu chovat jako objekt nebo struktura.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího `CDialog`prvku pro úpravy (obvykle a). Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku pro úpravy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je inicializace úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CEdit` dvou krocích. Nejprve zavolejte `CEdit` konstruktoru `Create`a potom volání , který vytvoří `CEdit` ovládací prvek pro úpravy systému Windows a připojí jej k objektu.

Při `Create` spuštění odesílá systém Windows do ovládacího prvku úprav zprávy [WM_NCCREATE](/windows/win32/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize), [WM_CREATE](/windows/win32/winmsg/wm-create)a [WM_GETMINMAXINFO.](/windows/win32/winmsg/wm-getminmaxinfo)

Tyto zprávy jsou ve výchozím nastavení zpracovány členy [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate)a [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) v `CWnd` základní třídě. Chcete-li rozšířit výchozí zpracování zpráv, odvodit třídu z `CEdit`, přidejte mapu zpráv do nové třídy a přepsat výše uvedené funkce obsluhy zprávy. Přepište `OnCreate`, například provést potřebnou inicializaci pro novou třídu.

Použijte následující [styly oken](styles-used-by-mfc.md#window-styles) u ovládacího prvku pro úpravy.

- WS_CHILD vždy

- WS_VISIBLE Obvykle

- WS_DISABLED Zřídka

- WS_GROUP Chcete-li seskupit ovládací prvky

- WS_TABSTOP Chcete-li zahrnout ovládací prvek úpravy do pořadí tabulátorů

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a>CEdit::Vyjmout

Voláním této funkce odstraňte (vyjměte) aktuální výběr (pokud existuje) v ovládacím prvku pro úpravy a zkopírujte odstraněný text do schránky ve formátu CF_TEXT.

```cpp
void Cut();
```

### <a name="remarks"></a>Poznámky

Odstranění provedené `Cut` pomocí lze vrátit zpět voláním členské funkce [Zpět.](#undo)

Chcete-li odstranit aktuální výběr bez umístění odstraněného textu do schránky, zavolejte členskou funkci [Vymazat.](#clear)

Další informace naleznete v [tématu WM_CUT](/windows/win32/dataxchg/wm-cut) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a>CEdit::EmptyUndoBuffer

Volání této funkce obnovit (vymazat) příznak vrátit úpravy ovládacího prvku.

```cpp
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Poznámky

Ovládací prvek pro úpravy nyní nebude moci vrátit zpět poslední operaci. Příznak zpět je nastaven vždy, když lze operaci v rámci ovládacího prvku úprav vrátit zpět.

Příznak vrátit je automaticky vymazána vždy, když [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) nebo [SetHandle](#sethandle) `CWnd` členské funkce jsou volány.

Další informace naleznete v [tématu EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) sady Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a>CEdit::FmtLines

Voláním této funkce nastavte zahrnutí znaků měkkého konce řádku zapnunebo vypněte v rámci víceřádkového ovládacího prvku pro úpravy.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Parametry

*bAddEOL*<br/>
Určuje, zda mají být vloženy znaky měkkého zalomení řádku. Hodnota TRUE vloží znaky; hodnota FALSE je odstraní.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud dojde k formátování; jinak 0.

### <a name="remarks"></a>Poznámky

Zalomení měkkého řádku se skládá ze dvou návratů vozíku a posuvu řádku vloženého na konec řádku, který je přerušen z důvodu zalamování slova. Pevný konec řádku se skládá z jednoho konce vozíku a posuvu řádku. Řádky, které končí pevným zalomením linky, nejsou ovlivněny . `FmtLines`

Systém Windows bude `CEdit` reagovat pouze v případě, že objekt je víceřádkový ovládací prvek pro úpravy.

`FmtLines`ovlivňuje pouze vyrovnávací paměť vrácenou [gethandle](#gethandle) a text vrácený [WM_GETTEXT](/windows/win32/winmsg/wm-gettext). Nemá žádný vliv na zobrazení textu v ovládacím prvku pro úpravy.

Další informace naleznete v [tématu EM_FMTLINES](/windows/win32/Controls/em-fmtlines) sady Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a>CEdit::GetCueBanner

Načte text, který je zobrazen jako text ový pokyn nebo tip, v ovládacím prvku pro úpravy, když je ovládací prvek prázdný.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[out] Ukazatel na řetězec, který obsahuje text cue.

*cchText*<br/>
[v] Počet znaků, které mohou být přijaty. Toto číslo zahrnuje ukončující znak NULL.

### <a name="return-value"></a>Návratová hodnota

Pro první přetížení TRUE, pokud je metoda úspěšná; jinak FALSE.

Pro druhé přetížení [CString,](../../atl-mfc-shared/using-cstring.md) který obsahuje tágo text, pokud je metoda úspěšná; v opačném případě prázdný řetězec ("").

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu EM_GETCUEBANNER,](/windows/win32/Controls/em-getcuebanner) která je popsána v sadě Windows SDK. Další informace naleznete v [Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext) makru.

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a>CEdit::GetFirstVisibleLine

Volánítéto funkce k určení nejvyšší viditelné čáry v ovládacím prvku úprav.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Návratová hodnota

Nulový index nejvyšší viditelné čáry. U jednořádkových ovládacích prvků pro úpravy je vrácená hodnota 0.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a>CEdit::GetHandle

Volání této funkce načíst popisovač do paměti aktuálně přidělené pro víceřádkový ovládací prvek úprav.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač místní paměti, který identifikuje vyrovnávací paměť, která obsahuje obsah ovládacího prvku úprav. Pokud dojde k chybě, jako je například odeslání zprávy do jednoho řádkového ovládacího prvku úprav, je vrácená hodnota 0.

### <a name="remarks"></a>Poznámky

Popisovač je popisovač místní paměti a může být používán některou z funkcí paměti **místní** ho systému Windows, které berou popisovač místní paměti jako parametr.

`GetHandle`zpracovává pouze víceřádkovými ovládacími prvky pro úpravy.

Volání `GetHandle` víceřádkového ovládacího prvku pro úpravy v dialogovém okně pouze v případě, že dialogové okno bylo vytvořeno se sadou příznaku DS_LOCALEDIT stylu. Pokud styl DS_LOCALEDIT není nastaven, stále získáte nenulovou vrácenou hodnotu, ale vrácenou hodnotu nebudete moci použít.

> [!NOTE]
> `GetHandle`nebude fungovat se systémem Windows 95/98. Pokud zavoláte `GetHandle` v systému Windows 95/98, vrátí hodnotu NULL. `GetHandle`bude fungovat tak, jak je popsáno v systému Windows NT, verze 3.51 a novější.

Další informace naleznete v [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) sady Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a>CEdit::GetHighlight

Získá indexy první a poslední znak v rozsahu textu, který je zvýrazněn v aktuální ovládací prvek úpravy.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pichStart*|[out] Nulový index prvního znaku v rozsahu textu, který je zvýrazněn.|
|*pichEnd*|[out] Nulový index posledního znaku v rozsahu textu, který je zvýrazněn.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu EM_GETHILITE,](/windows/win32/Controls/em-gethilite) která je popsána v sadě Windows SDK. Obě `SetHighlight` `GetHighlight` a jsou aktuálně povoleny pouze pro sestavení UNICODE.

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a>CEdit::GetLimitText

Volání této členské funkce získat omezení `CEdit` textu pro tento objekt.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální textový limit v TCHARs `CEdit` pro tento objekt.

### <a name="remarks"></a>Poznámky

Limit textu je maximální množství textu v TCHARs, které může ovládací prvek pro úpravy přijmout.

> [!NOTE]
> Tato členská funkce je k dispozici počínaje systémy Windows 95 a Windows NT 4.0.

Další informace naleznete v [tématu EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a>CEdit::GetLine

Volání této funkce načíst řádek textu z ovládacího prvku upravit a umístí jej *do lpszBuffer*.

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
Určuje číslo řádku, které má být načteno z víceřádkového ovládacího prvku pro úpravy. Čísla řádků jsou od nuly; hodnota 0 určuje první řádek. Tento parametr je ignorován jednořádkovým ovládacím prvkem pro úpravy.

*lpszBuffer*<br/>
Odkazuje na vyrovnávací paměť, která obdrží kopii řádku. První slovo vyrovnávací paměti musí určit maximální počet TCHARs, které lze zkopírovat do vyrovnávací paměti.

*nMaxLength*<br/>
Určuje maximální počet znaků TCHAR, které lze zkopírovat do vyrovnávací paměti. `GetLine`umístí tuto hodnotu do prvního slova *lpszBuffer* před provedením volání systému Windows.

### <a name="return-value"></a>Návratová hodnota

Počet skutečně zkopírovaných znaků. Vrácená hodnota je 0, pokud je číslo řádku určené *nIndex* větší než počet řádků v ovládacím prvku pro úpravy.

### <a name="remarks"></a>Poznámky

Zkopírovaný řádek neobsahuje znak null-termination.

Další informace naleznete v [EM_GETLINE](/windows/win32/Controls/em-getline) sady Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CEdit::GetLineCount](#getlinecount).

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a>CEdit::GetLineCount

Voláním této funkce načtěte počet řádků v ovládacím prvku pro úpravy více řádků.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Celé číslo obsahující počet řádků v ovládacím prvku úprav více řádků. Pokud do ovládacího prvku úprav nebyl zadán žádný text, je vrácená hodnota 1.

### <a name="remarks"></a>Poznámky

`GetLineCount`je zpracována pouze víceřádkovými ovládacími prvky pro úpravy.

Další informace naleznete v [tématu EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) sady Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a>CEdit::GetMargins

Volání této členské funkce načíst levé a pravé okraje tohoto ovládacího prvku úpravy.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka levého okraje v dolním pořadí WORD a šířka pravého okraje v wordu nejvyššího řádu.

### <a name="remarks"></a>Poznámky

Okraje se měří v pixelech.

> [!NOTE]
> Tato členská funkce je k dispozici počínaje systémy Windows 95 a Windows NT 4.0.

Další informace naleznete v [tématu EM_GETMARGINS](/windows/win32/Controls/em-getmargins) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [ceditview::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditgetmodify"></a><a name="getmodify"></a>CEdit::GetModify

Volání této funkce k určení, zda byl změněn obsah ovládacího prvku pro úpravy.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byl obsah ovládacího prvku pro úpravy změněn; 0, pokud zůstaly nezměněny.

### <a name="remarks"></a>Poznámky

Systém Windows udržuje interní příznak označující, zda byl změněn obsah ovládacího prvku úprav. Tento příznak je vymazánpři prvním vytvoření ovládacího prvku pro úpravy a může být také vymazán voláním členské funkce [SetModify.](#setmodify)

Další informace naleznete v [tématu EM_GETMODIFY](/windows/win32/Controls/em-getmodify) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a>CEdit::GetPasswordChar

Volánítéto funkce načíst znak hesla, který se zobrazí v ovládacím prvku upravit, když uživatel zadá text.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Návratová hodnota

Určuje znak, který má být zobrazen místo znaku, který uživatel zadali. Vrácená hodnota je NULL, pokud neexistuje žádný znak hesla.

### <a name="remarks"></a>Poznámky

Pokud vytvoříte ovládací prvek pro úpravy s ES_PASSWORD stylem, knihovna DLL, která ovládací prvek podporuje, určuje výchozí znak hesla. Manifest nebo [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) metoda určuje, která DLL podporuje ovládací prvek úprav. Pokud uživatel32.dll podporuje ovládací prvek pro úpravy, výchozí znak hesla je ASTERISK ('*', U + 002A). Pokud comctl32.dll verze 6 podporuje ovládací prvek úprav, výchozí znak je BLACK CIRCLE ('●', U + 25CF). Další informace o tom, která dll a verze podporuje běžné ovládací prvky, naleznete v [tématu Shell a Common Controls Versions](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\)).

Tato metoda odešle [zprávu EM_GETPASSWORDCHAR,](/windows/win32/Controls/em-getpasswordchar) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a>CEdit::GetRect

Voláním této funkce získáte formátovací obdélník ovládacího prvku pro úpravy.

```cpp
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu, která obdrží formátovací obdélník.

### <a name="remarks"></a>Poznámky

Formátovací obdélník je omezující obdélník textu, který je nezávislý na velikosti okna úprava-řízení.

Formátovací obdélník víceřádkového ovládacího prvku pro úpravy lze upravit pomocí členských funkcí [SetRect](#setrect) a [SetRectNP.](#setrectnp)

Další informace naleznete v [EM_GETRECT](/windows/win32/Controls/em-getrect) sady Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CEdit::LimitText](#limittext).

## <a name="ceditgetsel"></a><a name="getsel"></a>CEdit::GetSel

Volání této funkce získat počáteční a koncové pozice znaků aktuální výběr (pokud existuje) v ovládacím prvku úprav, pomocí návratové hodnoty nebo parametry.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>Parametry

*nStartChar*<br/>
Odkaz na celé číslo, které obdrží pozici prvního znaku v aktuálním výběru.

*nEndChar*<br/>
Odkaz na celé číslo, které obdrží pozici prvního nevybraného znaku za koncem aktuálního výběru.

### <a name="return-value"></a>Návratová hodnota

Verze, která vrací DWORD vrátí hodnotu, která obsahuje počáteční pozici ve slově nižšího řádu a pozici prvního nevybraného znaku po konci výběru ve slově nejvyššího řádu.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu EM_GETSEL](/windows/win32/Controls/em-getsel) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a>CEdit::HideBalloonTip

Skryje všechny špičky pozice přidružené k aktuálnímu ovládacímu prvku úprav.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato funkce odešle [zprávu EM_HIDEBALLOONTIP,](/windows/win32/Controls/em-hideballoontip) která je popsána v sadě Windows SDK.

## <a name="ceditlimittext"></a><a name="limittext"></a>CEdit::LimitText

Volání této funkce omezit délku textu, který uživatel může zadat do ovládacího prvku úprav.

```cpp
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Parametry

*nChars*<br/>
Určuje délku (v TCHARs) textu, který může uživatel zadat. Pokud je tento parametr 0, délka textu je nastavena na UINT_MAX bajtů. Toto je výchozí chování.

### <a name="remarks"></a>Poznámky

Změna limitu textu omezí pouze text, který může uživatel zadat. Nemá žádný vliv na žádný text, který je již v ovládacím prvku pro úpravy, ani nemá `CWnd`vliv na délku textu zkopírovaného do ovládacího prvku upravit člennou funkcí [SetWindowText](cwnd-class.md#setwindowtext) v aplikaci . Pokud aplikace používá `SetWindowText` funkci k umístění více textu do ovládacího `LimitText`prvku pro úpravy, než je určeno ve volání , může uživatel odstranit libovolný text v ovládacím prvku pro úpravy. Omezení textu však zabrání uživateli v nahrazení existujícího textu novým textem, pokud odstranění aktuálního výběru nezpůsobí, že text klesne pod textový limit.

> [!NOTE]
> Ve win32 (Windows NT a Windows 95/98) [nahradí SetLimitText](#setlimittext) tuto funkci.

Další informace naleznete v [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) sady Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a>CEdit::LineFromchar

Volání této funkce načíst číslo řádku, který obsahuje zadaný index znaků.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje hodnotu indexu na základě nuly pro požadovaný znak v textu ovládacího prvku úpravy nebo obsahuje -1. Pokud *nIndex* je -1, určuje aktuální řádek, to znamená řádek, který obsahuje stříška.

### <a name="return-value"></a>Návratová hodnota

Číslo řádku na základě nuly řádku obsahujícího index znaků určený *nIndex*. Pokud *nIndex* je -1, je vráceno číslo řádku, který obsahuje první znak výběru. Pokud není k dispozici žádný výběr, je vráceno aktuální číslo řádku.

### <a name="remarks"></a>Poznámky

Index znaků je počet znaků od začátku ovládacího prvku pro úpravy.

Tato členská funkce je používána pouze víceřádkovými ovládacími prvky pro úpravy.

Další informace naleznete v [tématu EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a>CEdit::LineIndex

Volání této funkce načíst index znaků řádku v rámci ovládacího prvku pro úpravy více řádků.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*nLinka*<br/>
Obsahuje hodnotu indexu pro požadovaný řádek v textu ovládacího prvku úpravy nebo obsahuje -1. Pokud *nLine* je -1, určuje aktuální řádek, to znamená řádek, který obsahuje stříška.

### <a name="return-value"></a>Návratová hodnota

Index znaků řádku určeného v *nLine* nebo -1, pokud je zadané číslo řádku větší než počet řádků v ovládacím prvku pro úpravy.

### <a name="remarks"></a>Poznámky

Index znaků je počet znaků od začátku ovládacího prvku pro úpravy k zadanému řádku.

Tato členská funkce je zpracována pouze víceřádkovými ovládacími prvky pro úpravy.

Další informace naleznete v [tématu EM_LINEINDEX](/windows/win32/controls/em-lineindex) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a>CEdit::Délka čáry

Načte délku řádku v ovládacím prvku pro úpravy.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*nLinka*<br/>
Nula na základě indexu znaku v řádku, jehož délka má být načten. Výchozí hodnota je -1.

### <a name="return-value"></a>Návratová hodnota

U jednořádkových ovládacích prvků pro úpravy je vrácená hodnota délka textu v ovládacím prvku úprav v tcharech v tcharech.

U víceřádkových ovládacích prvků pro úpravy je vrácená hodnota délkou řádku určeného parametrem *nLine* v TCHARs. U textu ANSI je délka počet bajtů v řádku; pro text Unicode je délka počtu znaků v řádku. Délka neobsahuje znak návrat vozíku na konci řádku.

Pokud je parametr *nLine* větší než počet znaků v ovládacím prvku, vrácená hodnota je nulová.

Pokud je parametr *nLine* -1, vrácená hodnota je počet nevybraných znaků v řádcích obsahujících vybrané znaky. Například pokud výběr sahá od čtvrtého znaku jednoho řádku až po osmý znak od konce dalšího řádku, vrácená hodnota je 10. To znamená tři znaky na prvním řádku a sedm na dalším řádku.

Další informace o typu TCHAR naleznete v řádku TCHAR v tabulce v [datových typech systému Windows](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Poznámky

Tato metoda je podporována [zprávou EM_LINELENGTH,](/windows/win32/Controls/em-linelength) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CEdit::LineIndex](#lineindex).

## <a name="ceditlinescroll"></a><a name="linescroll"></a>CEdit::LineScroll

Voláním této funkce můžete posouvat text víceřádkového ovládacího prvku pro úpravy.

```cpp
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Parametry

*nŘádky*<br/>
Určuje počet řádků, které se mají posouvat svisle.

*nChars*<br/>
Určuje počet pozic znaků, které se mají posouvat vodorovně. Tato hodnota je ignorována, pokud má ovládací prvek úprav y ES_RIGHT nebo ES_CENTER stylu.

### <a name="remarks"></a>Poznámky

Tato členská funkce je zpracována pouze víceřádkovými ovládacími prvky pro úpravy.

Ovládací prvek úpravse se neposune svisle za poslední řádek textu v ovládacím prvku úprav. Pokud aktuální řádek plus počet řádků určený *nLines* překročí celkový počet řádků v ovládacím prvku pro úpravy, hodnota se upraví tak, aby se poslední řádek ovládacího prvku pro úpravy posunul na začátek okna úprava-ovládací prvek.

`LineScroll`lze použít k vodorovnému posunu za poslední znak libovolného řádku.

Další informace naleznete [v tématu EM_LINESCROLL](/windows/win32/Controls/em-linescroll) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CEdit::GetFirstVisibleLine](#getfirstvisibleline).

## <a name="ceditpaste"></a><a name="paste"></a>CEdit::Paste

Voláním této funkce vložte data ze `CEdit` schránky do bodu vložení.

```cpp
void Paste();
```

### <a name="remarks"></a>Poznámky

Data se vkládají pouze v případě, že schránka obsahuje data v CF_TEXT formátu.

Další informace naleznete v [tématu WM_PASTE](/windows/win32/dataxchg/wm-paste) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a>CEdit::PosFromChar

Volání této funkce získat pozici (vlevo v rohu vlevo `CEdit` v rohu) daného znaku v rámci tohoto objektu.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Parametry

*Nchar*<br/>
Index na základě nuly zadaného znaku.

### <a name="return-value"></a>Návratová hodnota

Souřadnice levého horního rohu znaku *určeného nChar*.

### <a name="remarks"></a>Poznámky

Znak je určen zadáním jeho nulové hodnoty indexu. Pokud *nChar* je větší než index posledního znaku v tomto `CEdit` objektu, vrácená hodnota určuje souřadnice pozice znaku těsně za poslední znak v tomto `CEdit` objektu.

> [!NOTE]
> Tato členská funkce je k dispozici počínaje systémy Windows 95 a Windows NT 4.0.

Další informace naleznete v [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) sady Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CEdit::LineFromChar](#linefromchar).

## <a name="ceditreplacesel"></a><a name="replacesel"></a>CEdit::ReplaceSel

Voláním této funkce nahradíte aktuální výběr v ovládacím prvku pro úpravy textem určeným *lpszNewText*.

```cpp
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszNewText*<br/>
Odkazuje na řetězec s ukončeným hodnotou null obsahující náhradní text.

*bCanUndo*<br/>
Chcete-li určit, že tuto funkci lze vrátit zpět, nastavte hodnotu tohoto parametru na hodnotu TRUE . Výchozí hodnota je FALSE.

### <a name="remarks"></a>Poznámky

Nahradí pouze část textu v ovládacím prvku pro úpravy. Pokud chcete nahradit celý text, použijte členovou funkci [CWnd::SetWindowText.](cwnd-class.md#setwindowtext)

Pokud není k dispozici žádný aktuální výběr, náhradní text se vloží do aktuálního umístění kurzoru.

Další informace naleznete v [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) sady Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CEdit::LineIndex](#lineindex).

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a>CEdit::SetCueBanner

Nastaví text, který je zobrazen jako textový pokyn nebo tip, v ovládacím prvku pro úpravy, když je ovládací prvek prázdný.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[v] Ukazatel na řetězec, který obsahuje pokyn k zobrazení v ovládacím prvku pro úpravy.

*fDrawWhenFocused*<br/>
[v] Pokud false, cue banner není nakreslena, když uživatel klepne v ovládacím prvku upravit a dává ovládací prvek fokus.

Pokud true, tágo banner je nakreslena i v případě, že ovládací prvek má fokus. Tágo banner zmizí, když uživatel začne psát v ovládacím prvku.

Výchozí hodnota je FALSE.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu EM_SETCUEBANNER,](/windows/win32/Controls/em-setcuebanner) která je popsána v sadě Windows SDK. Další informace naleznete v [makru Edit_SetCueBannerTextFocused.](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused)

### <a name="example"></a>Příklad

Následující příklad ukazuje metodu [CEdit::SetCueBanner.](#setcuebanner)

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a>CEdit::SetHandle

Volání této funkce nastavit popisovač na místní paměti, která bude použita víceřádkový ovládací prvek pro úpravy.

```cpp
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Parametry

*hVyrovnávací paměť*<br/>
Obsahuje popisovač místní paměti. Tento popisovač musí být vytvořen předchozím voláním funkce [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) Windows pomocí příznaku LMEM_MOVEABLE. Předpokládá se, že paměť obsahuje řetězec ukončený hodnotou null. Pokud tomu tak není, první bajt přidělené paměti by měla být nastavena na 0.

### <a name="remarks"></a>Poznámky

Ovládací prvek pro úpravy pak použije tuto vyrovnávací paměť k uložení aktuálně zobrazeného textu namísto přidělení vlastní vyrovnávací paměti.

Tato členská funkce je zpracována pouze víceřádkovými ovládacími prvky pro úpravy.

Před aplikace nastaví nový popisovač paměti, by měla použít [GetHandle](#gethandle) členské funkce získat popisovač `LocalFree` do vyrovnávací paměti aktuální paměti a uvolnit tuto paměť pomocí funkce systému Windows.

`SetHandle`vymaže vyrovnávací paměť zpět (členská funkce [CanUndo](#canundo) pak vrátí 0) a příznak vnitřní změny (členská funkce [GetModify](#getmodify) pak vrátí hodnotu 0). Okno úprava-řízení je překresleno.

Tuto členskou funkci můžete použít v ovládacím prvku pro úpravy více řádků v dialogovém okně pouze v případě, že jste vytvořili dialogové okno se sadou DS_LOCALEDIT příznakstylu.

> [!NOTE]
> `GetHandle`nebude fungovat se systémem Windows 95/98. Pokud zavoláte `GetHandle` v systému Windows 95/98, vrátí hodnotu NULL. `GetHandle`bude fungovat tak, jak je popsáno v systému Windows NT, verze 3.51 a novější.

Další informace naleznete [v tématech EM_SETHANDLE](/windows/win32/Controls/em-sethandle), [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)a [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a>CEdit::SetHighlight

Zvýrazní rozsah textu, který se zobrazí v aktuálním ovládacím prvku úprav.

```cpp
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ichStart*|[v] Nulový index prvního znaku v rozsahu textu, který chcete zvýraznit.|
|*ichEnd*|[v] Nulový index posledního znaku v rozsahu textu, který chcete zvýraznit.|

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu EM_SETHILITE,](/windows/win32/Controls/em-sethilite) která je popsána v sadě Windows SDK.  Tato metoda odešle [zprávu EM_SETHILITE,](/windows/win32/Controls/em-sethilite) která je popsána v sadě Windows SDK. Oba `SetHighlight` `GetHighlight` a jsou povoleny pouze pro sestavení UNICODE.

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a>CEdit::SetLimitText

Volánítéto členské funkce nastavit textový `CEdit` limit pro tento objekt.

```cpp
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Parametry

*nMax*<br/>
Nový limit textu ve znacích.

### <a name="remarks"></a>Poznámky

Limit textu je maximální množství textu ve znacích, které může ovládací prvek pro úpravy přijmout.

Změna limitu textu omezí pouze text, který může uživatel zadat. Nemá žádný vliv na žádný text, který je již v ovládacím prvku pro úpravy, ani nemá `CWnd`vliv na délku textu zkopírovaného do ovládacího prvku upravit člennou funkcí [SetWindowText](cwnd-class.md#setwindowtext) v aplikaci . Pokud aplikace používá `SetWindowText` funkci k umístění více textu do ovládacího `LimitText`prvku pro úpravy, než je určeno ve volání , může uživatel odstranit libovolný text v ovládacím prvku pro úpravy. Omezení textu však zabrání uživateli v nahrazení existujícího textu novým textem, pokud odstranění aktuálního výběru nezpůsobí, že text klesne pod textový limit.

Tato funkce nahrazuje [LimitText](#limittext) ve win32.

Další informace naleznete v [tématu EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [ceditview::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmargins"></a><a name="setmargins"></a>CEdit::SetMargins

Volání této metody nastavit levý a pravý okraj tohoto ovládacího prvku úpravy.

```cpp
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Parametry

*nVlevo*<br/>
Šířka nového levého okraje v obrazových bodech.

*nVpravo*<br/>
Šířka nového pravého okraje v obrazových bodech.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Tato členská funkce je k dispozici počínaje systémy Windows 95 a Windows NT 4.0.

Další informace naleznete v [tématu EM_SETMARGINS](/windows/win32/Controls/em-setmargins) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [ceditview::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmodify"></a><a name="setmodify"></a>CEdit::SetModify

Voláním této funkce nastavte nebo zrušte zaškrtnutí upraveného příznaku ovládacího prvku pro úpravy.

```cpp
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bZměněno*<br/>
Hodnota TRUE označuje, že text byl změněn a hodnota FALSE označuje, že je nezměněn. Ve výchozím nastavení je nastaven upravený příznak.

### <a name="remarks"></a>Poznámky

Upravený příznak označuje, zda byl změněn text v ovládacím prvku úprav. Je automaticky nastavena vždy, když uživatel změní text. Jeho hodnota může být načtena pomocí členské funkce [GetModify.](#getmodify)

Další informace naleznete v [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) sady Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CEdit::GetModify](#getmodify).

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a>CEdit::SetPasswordChar

Voláním této funkce nastavte nebo odeberte znak hesla zobrazený v ovládacím prvku pro úpravy, když uživatel zadá text.

```cpp
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Parametry

*Ch*<br/>
Určuje znak, který má být zobrazen místo znaku zadaného uživatelem. Pokud *ch* je 0, skutečné znaky zadané uživatelem jsou zobrazeny.

### <a name="remarks"></a>Poznámky

Je-li nastaven znak hesla, zobrazí se pro každý znak, který uživatel zadá, zobrazen.

Tato členská funkce nemá žádný vliv na víceřádkový ovládací prvek pro úpravy.

Když `SetPasswordChar` je volána `CEdit` členská funkce, překreslí všechny viditelné znaky pomocí znaku určeného *ch*.

Pokud je ovládací prvek pro [úpravy](styles-used-by-mfc.md#edit-styles) vytvořen ES_PASSWORD stylem, je <strong>\*</strong>výchozí znak hesla nastaven na hvězdičku ( ). Tento styl je `SetPasswordChar` odebrán, pokud je volána s *ch* nastavit 0.

Další informace naleznete v [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) sady Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a>CEdit::SetReadOnly

Volá tuto funkci nastavit stav jen pro čtení upravit ovládacíprvek.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bReadOnly*<br/>
Určuje, zda má být nastaven nebo odebírán stav ovládacího prvku pro úpravy jen pro čtení. Hodnota TRUE nastaví stav jen pro čtení; hodnota FALSE nastaví stav pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je operace úspěšná, nebo 0, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Aktuální nastavení lze nalézt testováním [příznaku ES_READONLY](styles-used-by-mfc.md#edit-styles) v návratové hodnotě [CWnd::GetStyle](cwnd-class.md#getstyle).

Další informace naleznete v [tématu EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a>CEdit::SetRect

Volání této funkce nastavit rozměry obdélníku pomocí zadané souřadnice.

```cpp
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu `CRect` nebo objekt, který určuje nové rozměry formátovacího obdélníku.

### <a name="remarks"></a>Poznámky

Tento člen je zpracován pouze víceřádkovými ovládacími prvky pro úpravy.

Slouží `SetRect` k nastavení obdélníku formátování víceřádkového ovládacího prvku pro úpravy. Formátovací obdélník je omezující obdélník textu, který je nezávislý na velikosti okna úprava-řízení. Při prvním vytvoření ovládacího prvku pro úpravy je formátovací obdélník stejný jako klientská oblast okna úprava-ovládací prvek. Pomocí `SetRect` členské funkce může aplikace zvětšit nebo zmenšit formátovací obdélník než okno pro úpravy a řízení.

Pokud ovládací prvek pro úpravy nemá žádný posuvník, text bude oříznut, nikoli zabalen, pokud je formátovací obdélník větší než okno. Pokud ovládací prvek úprav obsahuje ohraničení, formátovací obdélník se zmenší o velikost ohraničení. Pokud upravíte obdélník `GetRect` vrácený členovou funkcí, musíte odebrat velikost ohraničení před předáním obdélníku `SetRect`.

Když `SetRect` je volána, text ovládacího prvku úprav je také přeformátován a znovu zobrazen.

Další informace naleznete v [EM_SETRECT](/windows/win32/Controls/em-setrect) sady Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a>CEdit::SetRectNP

Voláním této funkce nastavte formátovací obdélník víceřádkového ovládacího prvku pro úpravy.

```cpp
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu `CRect` nebo objekt, který určuje nové rozměry obdélníku.

### <a name="remarks"></a>Poznámky

Formátovací obdélník je omezující obdélník textu, který je nezávislý na velikosti okna úprava-řízení.

`SetRectNP`je shodná `SetRect` s členovou funkcí s tím rozdílem, že okno úprava ovládacího prvku není překresleno.

Při prvním vytvoření ovládacího prvku pro úpravy je formátovací obdélník stejný jako klientská oblast okna úprava-ovládací prvek. Voláním `SetRectNP` členské funkce může aplikace zvětšit nebo zmenšit formátovací obdélník než okno pro úpravy a řízení.

Pokud ovládací prvek pro úpravy nemá žádný posuvník, text bude oříznut, nikoli zabalen, pokud je formátovací obdélník větší než okno.

Tento člen je zpracován pouze víceřádkovými ovládacími prvky pro úpravy.

Další informace naleznete v [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) sady Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CEdit::SetRect](#setrect).

## <a name="ceditsetsel"></a><a name="setsel"></a>CEdit::SetSel

Voláním této funkce vyberte rozsah znaků v ovládacím prvku pro úpravy.

```cpp
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>Parametry

*dwVýběr*<br/>
Určuje počáteční pozici ve slově nižšího řádu a koncovou pozici ve slově nejvyššího řádu. Pokud je slovo nižšího řádu 0 a slovo nejvyššího řádu je -1, je vybrán veškerý text v ovládacím prvku pro úpravy. Pokud je slovo nižšího řádu -1, bude odebrán libovolný aktuální výběr.

*bNoScroll*<br/>
Označuje, zda stříška by měla být posunuta do zobrazení. Pokud false, stříška je posunuta do zobrazení. Pokud TRUE, stříška není posouván do zobrazení.

*nStartChar*<br/>
Určuje počáteční pozici. Pokud *nStartChar* je 0 a *nEndChar* je -1, je vybrán veškerý text v ovládacím prvku pro úpravy. Pokud *nStartChar* je -1, bude odebrán libovolný aktuální výběr.

*nEndChar*<br/>
Určuje koncovou pozici.

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu EM_SETSEL](/windows/win32/Controls/em-setsel) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CEdit::GetSel](#getsel).

## <a name="ceditsettabstops"></a><a name="settabstops"></a>CEdit::SetTabstops

Voláním této funkce nastavte zarážky tabulátoru v ovládacím prvku pro úpravy více řádků.

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Určuje, že zarážky tabulátoru mají být nastaveny v každé dialogové jednotky *cxEachStop.*

*nTabStops*<br/>
Určuje počet zarážek tabulátorů obsažených v *rgTabStops*. Toto číslo musí být větší než 1.

*rgTabStops*<br/>
Odkazuje na pole nepodepsaných celáčísel určujících zarážky tabulátorů v jednotkách dialogů. Jednotka dialogu je vodorovná nebo svislá vzdálenost. Jedna vodorovná jednotka dialogu se rovná jedné čtvrtině aktuální jednotky základní šířky dialogu a 1 svislá jednotka dialogu se rovná jedné osmině aktuální jednotky základní výšky dialogu. Základní jednotky dialogu se počítají na základě výšky a šířky aktuálního systémového písma. Funkce `GetDialogBaseUnits` Systému Windows vrátí aktuální základní jednotky dialogového okna v obrazových bodech.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byly karty nastaveny; jinak 0.

### <a name="remarks"></a>Poznámky

Při kopírování textu do víceřádkového ovládacího prvku úprav způsobí libovolný znak karty v textu vygenerování místa až do další zarážky tabulátoru.

Chcete-li nastavit zarážky tabulátoru na výchozí velikost 32 dialogových jednotek, zavolejte bezparametrovou verzi této členské funkce. Chcete-li nastavit zarážky tabulátoru na jinou velikost než 32, zavolejte verzi s parametrem *cxEachStop.* Chcete-li nastavit zarážky tabulátoru na pole velikostí, použijte verzi se dvěma parametry.

Tato členská funkce je zpracována pouze víceřádkovými ovládacími prvky pro úpravy.

`SetTabStops`automaticky nepřekreslí editační okno. Pokud změníte zarážky tabulátoru pro text, který je již v ovládacím prvku pro úpravy, zavolejte [CWnd::InvalidateRect](cwnd-class.md#invalidaterect) a překreslením editačního okna.

Další informace naleznete [v tématu EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) a [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad [ceditview::SetTabStops](ceditview-class.md#settabstops).

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a>CEdit::Zobrazit BalloonTip

Zobrazí špičku pozice, která je přidružena k aktuálnímu ovládacímu prvku pro úpravy.

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
|*pEditovatpopis*|[v] Ukazatel na strukturu [EDITBALLOONTIP,](/windows/win32/api/commctrl/ns-commctrl-editballoontip) která popisuje špičku pozice.|
|*lpszNázev*|[v] Ukazatel na řetězec Unicode, který obsahuje název tipu pozice.|
|*lpszText*|[v] Ukazatel na řetězec Unicode, který obsahuje text tipu bubliny.|
|*ttiIcon*|[v] **INT,** který určuje typ ikony přidružit ke špičce bubliny. Výchozí hodnota je TTI_NONE. Další informace naleznete `ttiIcon` v člen [editballoontip](/windows/win32/api/commctrl/ns-commctrl-editballoontip) struktury.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato funkce odešle [zprávu EM_SHOWBALLOONTIP,](/windows/win32/Controls/em-showballoontip) která je popsána v sadě Windows SDK. Další informace naleznete v [Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip) makru.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_cedit`která se používá pro přístup k aktuálnímu ovládacímu prvku pro úpravy. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Příklad

Následující příklad kódu zobrazuje tip pozice pro ovládací prvek úprav. Metoda [CEdit::ShowBalloonTip](#showballoontip) určuje text nadpisu a bublinového tipu.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a>CEdit::Vrátit se k ní

Voláním této funkce můžete vrátit zpět poslední operaci úprava-řízení.

```
BOOL Undo();
```

### <a name="return-value"></a>Návratová hodnota

U jednořádkového ovládacího prvku pro úpravy je vrácená hodnota vždy nenulová. Pro víceřádkový ovládací prvek pro úpravy je vrácená hodnota nenulová, pokud je operace vrácení zpět úspěšná, nebo 0, pokud se operace vrácení zpět nezdaří.

### <a name="remarks"></a>Poznámky

Operaci zpět lze také vrátit zpět. Odstraněný text můžete například obnovit pomocí `Undo`prvního volání aplikace . Dokud nedochází k žádné operaci úprav, můžete text znovu odebrat `Undo`pomocí druhého volání .

Další informace naleznete v [tématu EM_UNDO](/windows/win32/Controls/em-undo) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Viz také

[Vzorek knihovny MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](cwnd-class.md)<br/>
[CButton – třída](cbutton-class.md)<br/>
[Třída CComboBox](ccombobox-class.md)<br/>
[CListBox – třída](clistbox-class.md)<br/>
[CScrollBar – třída](cscrollbar-class.md)<br/>
[CStatic – třída](cstatic-class.md)<br/>
[CDialog – třída](cdialog-class.md)
