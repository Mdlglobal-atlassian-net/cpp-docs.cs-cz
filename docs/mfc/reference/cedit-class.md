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
ms.openlocfilehash: 5ad8784f3bff999eec046aa91f52b1cd164764e5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506793"
---
# <a name="cedit-class"></a>CEdit – třída

Poskytuje funkce pro ovládací prvek Windows Edit.

## <a name="syntax"></a>Syntaxe

```
class CEdit : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CEdit::CEdit](#cedit)|Vytvoří objekt ovládacího prvku. `CEdit`|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|Určuje, zda lze provést operaci úpravy ovládacího prvku.|
|[CEdit::CharFromPos](#charfrompos)|Načte index řádků a znaků pro znak nejblíže zadané pozici.|
|[CEdit:: Clear](#clear)|Odstraní (vymaže) aktuální výběr (pokud existuje) v ovládacím prvku pro úpravy.|
|[CEdit:: Copy](#copy)|Zkopíruje aktuální výběr (pokud existuje) v ovládacím prvku pro úpravy do schránky ve formátu CF_TEXT.|
|[CEdit:: Create](#create)|Vytvoří ovládací prvek Windows Edit a připojí ho k `CEdit` objektu.|
|[CEdit:: vyjmout](#cut)|Odstraní (vyjme) aktuální výběr (pokud existuje) v ovládacím prvku pro úpravy a zkopíruje odstraněný text do schránky ve formátu CF_TEXT.|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Obnoví (vymaže) příznak vrácení ovládacího prvku pro úpravy.|
|[CEdit::FmtLines](#fmtlines)|Nastaví zahrnutí měkkého znaku zalomení řádku do nebo z víceřádkového ovládacího prvku pro úpravy.|
|[CEdit::GetCueBanner](#getcuebanner)|Načte text, který se zobrazí jako textová hromádka nebo tip, v ovládacím prvku pro úpravy, když je ovládací prvek prázdný a nemá fokus.|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Určuje horní viditelnou čáru v ovládacím prvku pro úpravy.|
|[CEdit:: GetHandle](#gethandle)|Načte popisovač do paměti, která je aktuálně přidělena pro víceřádkový ovládací prvek pro úpravy.|
|[CEdit:: getzvýrazňovat](#gethighlight)|Získá indexy počátečních a koncových znaků v oblasti textu zvýrazněné v aktuálním ovládacím prvku pro úpravy.|
|[CEdit::GetLimitText](#getlimittext)|Získá maximální množství textu `CEdit` , který může obsahovat.|
|[CEdit:: getline](#getline)|Načte řádek textu z ovládacího prvku pro úpravy.|
|[CEdit::GetLineCount](#getlinecount)|Načte počet řádků v ovládacím prvku víceřádkového úprav.|
|[CEdit:: getmarže](#getmargins)|Získá levý a pravý okraj pro toto `CEdit`.|
|[CEdit::GetModify](#getmodify)|Určuje, zda byl upraven obsah textového ovládacího prvku.|
|[CEdit::GetPasswordChar](#getpasswordchar)|Načte znak hesla zobrazený v ovládacím prvku pro úpravy, když uživatel zadá text.|
|[CEdit::GetRect](#getrect)|Získá obdélník formátování ovládacího prvku pro úpravy.|
|[CEdit::GetSel](#getsel)|Získá první a poslední znak pozice aktuálního výběru v ovládacím prvku pro úpravy.|
|[CEdit::HideBalloonTip](#hideballoontip)|Skryje libovolný tip v bublině přidružený k aktuálnímu ovládacímu prvku pro úpravy.|
|[CEdit::LimitText](#limittext)|Omezí délku textu, který může uživatel zadat do textového pole.|
|[CEdit::LineFromChar](#linefromchar)|Načte číslo řádku, který obsahuje zadaný index znaků.|
|[CEdit::LineIndex](#lineindex)|Načte index znaku čáry v rámci víceřádkového ovládacího prvku pro úpravy.|
|[CEdit::LineLength](#linelength)|Načte délku čáry v ovládacím prvku pro úpravy.|
|[CEdit::LineScroll](#linescroll)|Posune text víceřádkového ovládacího prvku pro úpravy.|
|[CEdit::P kopírovat](#paste)|Vloží data ze schránky do ovládacího prvku pro úpravy na aktuální pozici kurzoru. Data jsou vložena pouze v případě, že schránka obsahuje data ve formátu CF_TEXT.|
|[CEdit::PosFromChar](#posfromchar)|Načte souřadnice levého horního rohu zadaného indexu znaků.|
|[CEdit::ReplaceSel](#replacesel)|Nahradí aktuální výběr v ovládacím prvku pro úpravy zadaným textem.|
|[CEdit::SetCueBanner](#setcuebanner)|Nastaví text, který se zobrazí jako textová hromádka nebo tip, v ovládacím prvku pro úpravy, když je ovládací prvek prázdný a nemá fokus.|
|[CEdit::SetHandle](#sethandle)|Nastaví popisovač na místní paměť, která bude použita víceřádkovým ovládacím prvkem pro úpravy.|
|[CEdit::SetHighlight](#sethighlight)|Zvýrazní rozsah textu, který se zobrazí v aktuálním ovládacím prvku pro úpravy.|
|[CEdit::SetLimitText](#setlimittext)|Nastaví maximální množství textu `CEdit` , který může obsahovat.|
|[CEdit::SetMargins](#setmargins)|Nastaví levý a pravý okraj pro toto `CEdit`.|
|[CEdit::SetModify](#setmodify)|Nastaví nebo zruší příznak změny pro ovládací prvek pro úpravy.|
|[CEdit::SetPasswordChar](#setpasswordchar)|Nastaví nebo odebere znak hesla zobrazený v ovládacím prvku pro úpravy, když uživatel zadá text.|
|[CEdit::SetReadOnly](#setreadonly)|Nastaví stav jen pro čtení ovládacího prvku pro úpravy.|
|[CEdit::SetRect](#setrect)|Nastaví obdélník formátování víceřádkového ovládacího prvku pro úpravy a aktualizuje ovládací prvek.|
|[CEdit::SetRectNP](#setrectnp)|Nastaví obdélník formátování víceřádkového ovládacího prvku pro úpravy bez nutnosti překreslení okna ovládacího prvku.|
|[CEdit::SetSel](#setsel)|Vybere rozsah znaků v textovém ovládacím prvku.|
|[CEdit::SetTabStops](#settabstops)|Nastaví zarážky tabulátoru v víceřádkovém textovém ovládacím prvku.|
|[CEdit::ShowBalloonTip](#showballoontip)|Zobrazí Tip bubliny, který je přidružen k aktuálnímu ovládacímu prvku pro úpravy.|
|[CEdit:: Undo](#undo)|Vrátí poslední operaci úpravy ovládacího prvku.|

## <a name="remarks"></a>Poznámky

Ovládací prvek pro úpravy je obdélníkové podřízené okno, ve kterém může uživatel zadat text.

Můžete vytvořit ovládací prvek pro úpravy buď ze šablony dialogového okna, nebo přímo v kódu. V obou případech nejprve zavolejte `CEdit` konstruktor pro `CEdit` vytvoření objektu a potom zavolejte funkci [Create](#create) member pro vytvoření ovládacího prvku Windows `CEdit` Edit a připojte jej k objektu.

Konstrukce může být proces jednoho kroku ve třídě odvozené z `CEdit`. Napište konstruktor pro odvozenou třídu a zavolejte `Create` v rámci konstruktoru.

`CEdit`dědí významné funkce z `CWnd`. Chcete-li nastavit a načíst text `CEdit` z objektu, `CWnd` použijte členské funkce [SetWindowText](cwnd-class.md#setwindowtext) a [GetWindowText](cwnd-class.md#getwindowtext), které nastaví nebo získá celý obsah ovládacího prvku pro úpravy, i když se jedná o víceřádkový ovládací prvek. Textové řádky ve víceřádkovém ovládacím prvku jsou oddělené sekvencemi znaků "\r\n". Také, pokud je ovládací prvek pro úpravy Víceřádkový, získat a nastavit část textu `CEdit` ovládacího prvku voláním členu Functions getline, [SetSel](#setsel), [GetSel](#getsel)a [ReplaceSel](#replacesel). [](#getline)

Pokud chcete zpracovat oznamovací zprávy systému Windows odeslané ovládacím prvkem pro úpravy do nadřazené (obvykle třídy odvozené z `CDialog`), přidejte položku mapování zpráv a členskou funkci obslužné rutiny zpráv do nadřazené třídy pro každou zprávu.

Každá položka mapování zpráv má následující podobu:

  **ON_** _Oznámení_ **(** _ID_ **;** _memberFxn_ **)**

kde `id` Určuje ID podřízeného okna ovládacího prvku pro úpravy, který odesílá oznámení, `memberFxn` a je název nadřazené členské funkce, kterou jste napsali pro zpracování oznámení.

Prototyp funkce nadřazeného objektu je následující:

**afx_msg** void memberFxn **( );**

Následuje seznam možných položek map zpráv a popis případů, ve kterých by se odesílaly do nadřazeného objektu:

- ON_EN_CHANGE uživatel učinil akci, která pravděpodobně změnila text v ovládacím prvku pro úpravy. Na rozdíl od zprávy s oznámením EN_UPDATE se tato zpráva oznámení pošle po aktualizaci displeje systémem Windows.

- ON_EN_ERRSPACE ovládací prvek pro úpravy nemůže přidělit dostatek paměti pro splnění konkrétní žádosti.

- ON_EN_HSCROLL uživatel klikne na vodorovný posuvník ovládacího prvku pro úpravy. Nadřazené okno je oznámeno před aktualizací obrazovky.

- ON_EN_KILLFOCUS ovládací prvek pro úpravy ztratí fokus vstupu.

- ON_EN_MAXTEXT aktuální vložení překročilo zadaný počet znaků pro ovládací prvek pro úpravy a byl zkrácen. Odesílá se také v případě, že ovládací prvek pro úpravy nemá styl ES_AUTOHSCROLL a počet znaků, které mají být vloženy, by překročil šířku ovládacího prvku pro úpravy. Odesílá se také v případě, že ovládací prvek pro úpravy nemá styl ES_AUTOVSCROLL a celkový počet řádků, který je výsledkem vložení textu, by překročil výšku ovládacího prvku pro úpravy.

- ON_EN_SETFOCUS se odesílá, když ovládací prvek pro úpravy přijme fokus vstupu.

- ON_EN_UPDATE ovládací prvek pro úpravy bude zobrazovat změněný text. Odesílá se poté, co ovládací prvek naformátoval text, ale před tím, než se text dokončí, aby velikost okna bylo možné v případě potřeby změnit.

- ON_EN_VSCROLL uživatel klikne na svislý posuvník ovládacího prvku pro úpravy. Nadřazené okno je oznámeno před aktualizací obrazovky.

Vytvoříte- `CEdit` li v dialogovém okně objekt `CEdit` , bude objekt automaticky zničen, když uživatel zavře dialogové okno.

Pokud vytvoříte `CEdit` objekt z dialogového okna prostředku pomocí editoru dialogového okna `CEdit` , objekt je automaticky zničen, když uživatel zavře dialogové okno.

Pokud vytvoříte `CEdit` objekt v rámci okna, může být také nutné jej zničit. Vytvoříte-li `CEdit` objekt v zásobníku, bude automaticky zničen. Vytvoříte `CEdit` -li objekt na haldě pomocí **nové** funkce, je nutné volat metodu **Delete** u objektu, aby jej bylo možné zničit, když uživatel ukončí ovládací prvek Windows Edit. Pokud přidělíte paměť v `CEdit` objektu, `CEdit` přepište destruktor k Dispose přidělení.

Chcete-li upravit určité styly v ovládacím prvku pro úpravy (například ES_READONLY), je nutné odeslat konkrétní zprávy ovládacímu prvku namísto použití [ModifyStyle](cwnd-class.md#modifystyle). Viz [Úpravy stylů ovládacích prvků](/windows/win32/Controls/edit-control-styles) v Windows SDK.

Další informace o `CEdit`naleznete v tématu [Controls](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="canundo"></a>CEdit::CanUndo

Voláním této funkce určíte, zda je možné vrátit poslední operaci úprav.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud lze poslední operaci Edit vrátit zpět voláním `Undo` členské funkce; 0, pokud ji nelze vrátit zpět.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [EM_CANUNDO](/windows/win32/Controls/em-canundo) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit:: Undo](#undo).

##  <a name="cedit"></a>CEdit::CEdit

`CEdit` Vytvoří objekt.

```
CEdit();
```

### <a name="remarks"></a>Poznámky

Použijte [vytvořit](#create) k sestavení ovládacího prvku Windows Edit.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

##  <a name="charfrompos"></a>CEdit::CharFromPos

Voláním této funkce načtete řádkové a znakové indexy znaku, který je nejblíže zadanému bodu v tomto `CEdit` ovládacím prvku.

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Parametry

*bodů*<br/>
Souřadnice bodu v klientské oblasti tohoto `CEdit` objektu.

### <a name="return-value"></a>Návratová hodnota

Index znaku v SLOVech s nižším pořadím a index čáry v aplikaci s vysokým pořadím.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato členská funkce je k dispozici počínaje systémy Windows 95 a Windows NT 4,0.

Další informace najdete v tématu [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

##  <a name="clear"></a>CEdit:: Clear

Voláním této funkce odstraníte (zrušíte) aktuální výběr (pokud existuje) v textovém poli.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

Odstranění provedené pomocí `Clear` lze zrušit voláním členské funkce [zpět](#undo) .

Chcete-li odstranit aktuální výběr a umístit odstraněný obsah do schránky, zavolejte funkci [Vyjmout](#cut) člen.

Další informace najdete v tématu [WM_CLEAR](/windows/win32/dataxchg/wm-clear) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

##  <a name="copy"></a>CEdit:: Copy

Voláním této funkce Coy aktuální výběr (pokud existuje) v ovládacím prvku pro úpravy do schránky ve formátu CF_TEXT.

```
void Copy();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [WM_COPY](/windows/win32/dataxchg/wm-copy) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

##  <a name="create"></a>CEdit:: Create

Vytvoří ovládací prvek Windows Edit a připojí ho k `CEdit` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl ovládacího prvku pro úpravy. Použití libovolné kombinace [stylů úprav](styles-used-by-mfc.md#edit-styles) pro ovládací prvek

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku pro úpravy. Může být `CRect` objekt nebo `RECT` struktura.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku pro úpravy (obvykle a `CDialog`). Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku pro úpravy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je inicializace úspěšná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`CEdit` Vytvoříte objekt ve dvou krocích. Nejprve zavolejte `CEdit` konstruktor a potom zavolejte `Create`, čímž se vytvoří ovládací prvek Windows Edit a `CEdit` připojí se k objektu.

Když `Create` se spustí, Windows pošle zprávy [WM_NCCREATE](/windows/win32/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize), [WM_CREATE](/windows/win32/winmsg/wm-create)a [WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo) ovládacímu prvku pro úpravy.

Tyto zprávy jsou ve výchozím nastavení zpracovávány členskými funkcemi [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [Create](cwnd-class.md#oncreate)a [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) v `CWnd` základní třídě. Chcete-li zvětšit výchozí zpracování zprávy, odvodit třídu `CEdit`z, přidat do nové třídy mapu zprávy a přepsat výše uvedené členské funkce obslužné rutiny zpráv. Přepsání `OnCreate`, například k provedení potřebné inicializace pro novou třídu.

Použijte následující [Styly okna](styles-used-by-mfc.md#window-styles) pro ovládací prvek pro úpravy.

- WS_CHILD vždycky

- WS_VISIBLE obvykle

- WS_DISABLED málokdy

- WS_GROUP do skupinových ovládacích prvků

- WS_TABSTOP zahrnutí ovládacího prvku pro úpravy do pořadí procházení

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

##  <a name="cut"></a>CEdit:: vyjmout

Voláním této funkce se odstraní (vyjme) aktuální výběr (pokud existuje) v ovládacím prvku pro úpravy a zkopíruje odstraněný text do schránky ve formátu CF_TEXT.

```
void Cut();
```

### <a name="remarks"></a>Poznámky

Odstranění provedené pomocí `Cut` lze zrušit voláním členské funkce [zpět](#undo) .

Chcete-li odstranit aktuální výběr bez umístění odstraněného textu do schránky, zavolejte funkci [clear](#clear) member.

Další informace najdete v tématu [WM_CUT](/windows/win32/dataxchg/wm-cut) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

##  <a name="emptyundobuffer"></a>CEdit::EmptyUndoBuffer

Voláním této funkce resetujete (Clear) příznak vrácení ovládacího prvku pro úpravy.

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Poznámky

Textové pole nyní nebude moci vrátit poslední operaci zpět. Příznak vrácení zpět je nastaven vždy, když je možné vrátit operaci v rámci textového ovládacího prvku.

Příznak vrácení zpět je automaticky vymazán při volání členských funkcí [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) nebo [SetHandle](#sethandle) `CWnd` .

Další informace najdete v tématu [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

##  <a name="fmtlines"></a>CEdit::FmtLines

Voláním této funkce nastavíte do víceřádkového ovládacího prvku pro úpravy zahrnutí měkkého znaku zalomení řádku.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Parametry

*bAddEOL*<br/>
Určuje, zda mají být vloženy měkké znaky zalomení řádku. Hodnota TRUE vloží znaky; Hodnota FALSE je odstraní.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud dojde k formátování; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Měkké zalomení řádku se skládá ze dvou návratových znaků a LF vloženého na konec řádku, který je přerušen z důvodu zalamování slov. Přerušení pevného řádku se skládá z jednoho návratu na začátek řádku a z čárového kanálu. Řádky, které končí koncem pevného řádku, nejsou ovlivněny `FmtLines`.

Systém Windows odpoví pouze v případě `CEdit` , že je objekt ovládacím prvkem víceřádkové textové pole.

`FmtLines`ovlivňuje pouze vyrovnávací paměť vrácenou [](#gethandle) funkcí GetHandle a text vrácený funkcí [WM_GETTEXT](/windows/win32/winmsg/wm-gettext). Nemá žádný vliv na zobrazení textu v ovládacím prvku pro úpravy.

Další informace najdete v tématu [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

##  <a name="getcuebanner"></a>CEdit::GetCueBanner

Načte text, který se zobrazí jako textová hromádka nebo tip, v ovládacím prvku pro úpravy, když je ovládací prvek prázdný.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
mimo Ukazatel na řetězec, který obsahuje text startovacího textu.

*cchText*<br/>
pro Počet znaků, které lze přijmout. Toto číslo zahrnuje ukončující znak NULL.

### <a name="return-value"></a>Návratová hodnota

Pro první přetížení, TRUE, pokud je metoda úspěšná; v opačném případě FALSE.

Pro druhé přetížení je [CString](../../atl-mfc-shared/using-cstring.md) , která obsahuje text startovacího textu, pokud je metoda úspěšná; v opačném případě prázdný řetězec ("").

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner) , která je popsána v Windows SDK. Další informace najdete v tématu makro [Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext) .

##  <a name="getfirstvisibleline"></a>CEdit::GetFirstVisibleLine

Voláním této funkce určíte horní viditelnou čáru v ovládacím prvku pro úpravy.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule z horního viditelného řádku. Pro textové ovládací prvky s jedním řádkem je vrácená hodnota 0.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

##  <a name="gethandle"></a>CEdit:: GetHandle

Voláním této funkce načtete popisovač k aktuálně přidělené paměti pro víceřádkový ovládací prvek pro úpravy.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Návratová hodnota

Obslužná rutina místní paměti identifikující vyrovnávací paměť, která uchovává obsah ovládacího prvku pro úpravy. Pokud dojde k chybě, jako je například odeslání zprávy do jednořádkového ovládacího prvku pro úpravy, vrácená hodnota je 0.

### <a name="remarks"></a>Poznámky

Popisovač je obslužná rutina místní paměti a může ji použít kterákoli z **místních** funkcí paměti Windows, které jako parametr přijímají popisovač místní paměti.

`GetHandle`je zpracována pouze víceřádkovými ovládacími prvky pro úpravy.

Volání `GetHandle` víceřádkového ovládacího prvku pro úpravy v dialogovém okně, pouze pokud bylo dialogové okno vytvořeno pomocí nastaveného příznaku stylu DS_LOCALEDIT. Pokud není nastaven styl DS_LOCALEDIT, stále se zobrazuje Nenulová návratová hodnota, ale nebudete moci použít vrácenou hodnotu.

> [!NOTE]
> `GetHandle`nebude fungovat se systémem Windows 95/98. Pokud zavoláte `GetHandle` ve Windows 95/98, vrátí hodnotu null. `GetHandle`bude fungovat jak je uvedeno v části Windows NT, verze 3,51 a novější.

Další informace najdete v tématu [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

##  <a name="gethighlight"></a>CEdit:: getzvýrazňovat

Načte indexy prvního a posledního znaku v rozsahu textu, který je zvýrazněný v aktuálním ovládacím prvku pro úpravy.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pichStart*|mimo Index prvního znaku založený na nule v oblasti zvýrazněného textu|
|*pichEnd*|mimo Index posledního znaku založený na nule v rozsahu zvýrazněného textu|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [EM_GETHILITE](/windows/win32/Controls/em-gethilite) , která je popsána v Windows SDK. `SetHighlight` A`GetHighlight` v současné době jsou povoleny pouze pro sestavení Unicode.

##  <a name="getlimittext"></a>CEdit::GetLimitText

Voláním této členské funkce získáte omezení textu pro tento `CEdit` objekt.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální omezení textu v TCHARs pro tento `CEdit` objekt.

### <a name="remarks"></a>Poznámky

Omezení textu je maximální množství textu v TCHARs, které může ovládací prvek pro úpravy přijmout.

> [!NOTE]
>  Tato členská funkce je k dispozici počínaje systémy Windows 95 a Windows NT 4,0.

Další informace najdete v tématu [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

##  <a name="getline"></a>CEdit:: getline

Voláním této funkce načtete řádek textu z ovládacího prvku pro úpravy a umístíte ho do *lpszBuffer*.

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
Určuje číslo řádku, které se má načíst z víceřádkového ovládacího prvku pro úpravy. Čísla řádků jsou počítána od nuly. hodnota 0 určuje první řádek. Tento parametr je ignorován v jednom řádku textového ovládacího prvku.

*lpszBuffer*<br/>
Odkazuje na vyrovnávací paměť, která obdrží kopii řádku. První slovo vyrovnávací paměti musí určovat maximální počet TCHARs, které se dají zkopírovat do vyrovnávací paměti.

*nMaxLength*<br/>
Určuje maximální počet TCHAR znaků, které lze zkopírovat do vyrovnávací paměti. `GetLine`před provedením volání Windows umístí tuto hodnotu do prvního slova *lpszBuffer* .

### <a name="return-value"></a>Návratová hodnota

Počet skutečně zkopírovaných znaků. Návratová hodnota je 0, pokud číslo řádku určené parametrem *nIndex* je větší než počet řádků v ovládacím prvku pro úpravy.

### <a name="remarks"></a>Poznámky

Zkopírovaný řádek neobsahuje znak ukončení hodnoty null.

Další informace najdete v tématu [EM_GETLINE](/windows/win32/Controls/em-getline) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit:: GetLineCount](#getlinecount).

##  <a name="getlinecount"></a>CEdit::GetLineCount

Voláním této funkce načtete počet řádků v víceřádkovém textovém ovládacím prvku.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Celé číslo obsahující počet řádků v ovládacím prvku víceřádkové úpravy. Pokud do ovládacího prvku pro úpravy nebyl zadán žádný text, vrácená hodnota je 1.

### <a name="remarks"></a>Poznámky

`GetLineCount`je zpracována pouze pomocí víceřádkových textových ovládacích prvků.

Další informace najdete v tématu [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

##  <a name="getmargins"></a>CEdit:: getmarže

Zavolejte tuto členskou funkci pro načtení levého a pravého okraje tohoto ovládacího prvku pro úpravy.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka levého okraje v aplikaci s nízkým pořadím a Šířka pravého okraje ve SLOVě s vysokým pořadím.

### <a name="remarks"></a>Poznámky

Okraje se měří v pixelech.

> [!NOTE]
>  Tato členská funkce je k dispozici počínaje systémy Windows 95 a Windows NT 4,0.

Další informace najdete v tématu [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="getmodify"></a>CEdit:: GetModify

Voláním této funkce určíte, zda byl upraven obsah textového ovládacího prvku.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud došlo ke změně obsahu řízení úprav; 0, pokud by zůstaly beze změny.

### <a name="remarks"></a>Poznámky

Systém Windows udržuje vnitřní příznak označující, zda došlo ke změně obsahu textového ovládacího prvku. Tento příznak je vymazán při prvním vytvoření textového ovládacího prvku a lze jej také vymazat voláním členské funkce [SetModify](#setmodify) .

Další informace najdete v tématu [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

##  <a name="getpasswordchar"></a>CEdit::GetPasswordChar

Voláním této funkce načtete znak hesla, který se zobrazí v ovládacím prvku pro úpravy, když uživatel zadá text.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Návratová hodnota

Určuje znak, který se má zobrazit místo znaku, který uživatel zadal. Návratová hodnota má hodnotu NULL, pokud žádný znak hesla neexistuje.

### <a name="remarks"></a>Poznámky

Pokud vytvoříte ovládací prvek pro úpravy se stylem ES_PASSWORD, knihovna DLL, která podporuje ovládací prvek, určí výchozí znak hesla. Manifest nebo metoda [vyžaduje InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) určuje, která knihovna DLL podporuje ovládací prvek pro úpravy. Pokud User32. dll podporuje ovládací prvek pro úpravy, výchozí znak hesla je HVĚZDIČKa (*, U + 002A). Pokud Comctl32. dll verze 6 podporuje ovládací prvek pro úpravy, výchozí znak je černý kroužek (' ● ', U + 25CF). Další informace o tom, která knihovna DLL a verze podporuje běžné ovládací prvky, najdete v tématu [prostředí a běžné verze ovládacích prvků](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\)).

Tato metoda pošle zprávu [EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

##  <a name="getrect"></a>CEdit:: GetRect

Voláním této funkce získáte obdélník formátování ovládacího prvku pro úpravy.

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu, která přijímá obdélník formátování.

### <a name="remarks"></a>Poznámky

Formátovací obdélník je omezující obdélník textu, který je nezávislý na velikosti okna pro úpravu ovládacího prvku.

Formátovací obdélník víceřádkového ovládacího prvku pro úpravy lze upravit pomocí členských funkcí [SetRect](#setrect) a [SetRectNP](#setrectnp) .

Další informace najdete v tématu [EM_GETRECT](/windows/win32/Controls/em-getrect) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit:: LimitText](#limittext).

##  <a name="getsel"></a>CEdit::GetSel

Voláním této funkce získáte počáteční a koncovou pozici znaku aktuálního výběru (pokud existuje) v ovládacím prvku pro úpravy pomocí návratové hodnoty nebo parametrů.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>Parametry

*nStartChar*<br/>
Odkaz na celé číslo, které získá pozici prvního znaku v aktuálním výběru.

*nEndChar*<br/>
Odkaz na celé číslo, které získá pozici prvního nevybraného znaku po konci aktuálního výběru.

### <a name="return-value"></a>Návratová hodnota

Verze, která vrací hodnotu DWORD, vrací hodnotu, která obsahuje počáteční pozici ve slovu s nižším pořadím a pozici prvního nevybraného znaku po konci výběru v aplikaci s vysokým pořadím.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [EM_GETSEL](/windows/win32/Controls/em-getsel) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

##  <a name="hideballoontip"></a>CEdit::HideBalloonTip

Skryje libovolný tip v bublině přidružený k aktuálnímu ovládacímu prvku pro úpravy.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato funkce pošle zprávu [EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip) , která je popsána v Windows SDK.

##  <a name="limittext"></a>  CEdit::LimitText

Voláním této funkce omezíte délku textu, který uživatel může zadat do textového pole.

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
Určuje délku (v TCHARs) textu, který může uživatel zadat. Pokud je tento parametr 0, délka textu je nastavená na UINT_MAX bajtů. Toto je výchozí chování.

### <a name="remarks"></a>Poznámky

Změna omezení textu omezí pouze text, který uživatel může zadat. Nemá žádný vliv na žádný text, který je již v ovládacím prvku pro úpravy, ani na délku kopírovaného textu do textového pole pomocí členské funkce [SetWindowText](cwnd-class.md#setwindowtext) v `CWnd`. Pokud aplikace používá `SetWindowText` funkci k umístění většího textu do ovládacího prvku pro úpravy, než je určeno v volání, `LimitText`uživatel může odstranit libovolný text v ovládacím prvku pro úpravy. Omezení textu však zabrání uživateli nahradit stávající text novým textem, pokud odstraněním aktuálního výběru způsobí, že text nebude pod omezením textu.

> [!NOTE]
>  V systému Win32 (Windows NT a Windows 95/98) nahrazuje tato funkce [SetLimitText](#setlimittext) .

Další informace najdete v tématu [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

##  <a name="linefromchar"></a>CEdit::LineFromChar

Voláním této funkce načtete číslo řádku, který obsahuje zadaný index znaků.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje hodnotu indexu založenou na nule pro požadovaný znak v textu ovládacího prvku nebo obsahuje-1. Pokud je *nIndex* -1, určuje aktuální řádek, tj. řádek, který obsahuje blikající kurzor.

### <a name="return-value"></a>Návratová hodnota

Číslo řádku založené na nule řádku obsahujícího index znaku určený parametrem *nIndex*. Pokud *nIndex* je-1, vrátí se číslo řádku, který obsahuje první znak výběru. Pokud žádný výběr není, vrátí se aktuální číslo řádku.

### <a name="remarks"></a>Poznámky

Index znaků je počet znaků od začátku ovládacího prvku pro úpravy.

Tato členská funkce je používána pouze víceřádkovými ovládacími prvky pro úpravy.

Další informace najdete v tématu [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

##  <a name="lineindex"></a>CEdit::LineIndex

Voláním této funkce načtete index znaků čáry v rámci víceřádkového ovládacího prvku pro úpravy.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*nLine*<br/>
Obsahuje hodnotu indexu požadovaného řádku v textu ovládacího prvku pro úpravy nebo obsahuje hodnotu-1. Pokud je *nline* -1, určuje aktuální řádek, tj. řádek, který obsahuje blikající kurzor.

### <a name="return-value"></a>Návratová hodnota

Index znaku řádku zadaného v *nline* nebo-1, pokud je zadané číslo řádku větší než počet řádků v ovládacím prvku pro úpravy.

### <a name="remarks"></a>Poznámky

Index znaků je počet znaků od začátku ovládacího prvku pro úpravy na zadaný řádek.

Tato členská funkce je zpracována pouze pomocí víceřádkových textových ovládacích prvků.

Další informace najdete v tématu [EM_LINEINDEX](/windows/win32/controls/em-lineindex) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

##  <a name="linelength"></a>CEdit::LineLength

Načte délku čáry v ovládacím prvku pro úpravy.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Parametry

*nLine*<br/>
Index založený na nule znaku v řádku, jehož délka má být načtena. Výchozí hodnota je-1.

### <a name="return-value"></a>Návratová hodnota

Pro jednořádkové textové ovládací prvky je návratovou hodnotou délka textu v textovém poli TCHARs.

Pro víceřádkové textové ovládací prvky je návratová hodnota délka v TCHARs řádku zadaného parametrem *nline* . V případě textu ANSI je délka počet bajtů na řádku. v případě textu v kódu Unicode je délka počet znaků na řádku. Délka nezahrnuje znak návratu na začátek řádku na konci řádku.

Pokud je parametr *nline* větší než počet znaků v ovládacím prvku, vrácená hodnota je nula.

Pokud je parametr *nline* -1, návratová hodnota je počet nevybraných znaků v řádcích, které obsahují vybrané znaky. Například pokud výběr sahá od čtvrtého znaku jednoho řádku až po osmý znak po konci dalšího řádku, návratová hodnota je 10. To znamená tři znaky na prvním řádku a sedm v dalším.

Další informace o TCHAR typu naleznete v řádku TCHAR v tabulce v [datových typech systému Windows](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Poznámky

Tato metoda je podporována zprávou [EM_LINELENGTH](/windows/win32/Controls/em-linelength) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit:: LineIndex](#lineindex).

##  <a name="linescroll"></a>CEdit::LineScroll

Voláním této funkce se posune text víceřádkového ovládacího prvku pro úpravy.

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Parametry

*nLines*<br/>
Určuje počet řádků, které mají být posunuty svisle.

*nChar*<br/>
Určuje počet pozic znaků, které mají být posunuty vodorovně. Tato hodnota se ignoruje v případě, že má ovládací prvek pro úpravy buď styl ES_RIGHT, nebo ES_CENTER.

### <a name="remarks"></a>Poznámky

Tato členská funkce je zpracována pouze víceřádkovými ovládacími prvky pro úpravy.

Ovládací prvek pro úpravy se neposouvá svisle za poslední řádek textu v ovládacím prvku pro úpravy. Pokud aktuální řádek plus počet řádků určený parametrem *nLines* překračuje celkový počet řádků v ovládacím prvku pro úpravy, hodnota se upraví tak, aby se poslední řádek v ovládacím prvku pro úpravy přesunul do horní části okna pro úpravu ovládacího prvku.

`LineScroll`dá se použít k posunu vodorovně za poslední znak každého řádku.

Další informace najdete v tématu [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit:: GetFirstVisibleLine](#getfirstvisibleline).

##  <a name="paste"></a>CEdit::P kopírovat

Voláním této funkce vložíte data ze schránky do `CEdit` bodu vložení.

```
void Paste();
```

### <a name="remarks"></a>Poznámky

Data jsou vložena pouze v případě, že schránka obsahuje data ve formátu CF_TEXT.

Další informace najdete v tématu [WM_PASTE](/windows/win32/dataxchg/wm-paste) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

##  <a name="posfromchar"></a>  CEdit::PosFromChar

Voláním této funkce získáte pozici (v levém horním rohu) daného znaku v rámci tohoto `CEdit` objektu.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
Index s nulovým základem zadaného znaku.

### <a name="return-value"></a>Návratová hodnota

Souřadnice levého horního rohu znaku určeného v poli *nchar*

### <a name="remarks"></a>Poznámky

Znak je určen tím, že poskytuje hodnotu indexu založenou na nule. Pokud je *nchar* větší než index posledního znaku v tomto `CEdit` objektu, vrácená hodnota určuje souřadnice pozice znaku hned za posledním znakem v tomto `CEdit` objektu.

> [!NOTE]
>  Tato členská funkce je k dispozici počínaje systémy Windows 95 a Windows NT 4,0.

Další informace najdete v tématu [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit:: LineFromChar](#linefromchar).

##  <a name="replacesel"></a>CEdit::ReplaceSel

Voláním této funkce nahradíte aktuální výběr v ovládacím prvku pro úpravy textem zadaným parametrem *lpszNewText*.

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszNewText*<br/>
Odkazuje na řetězec zakončený hodnotou null obsahující nahrazující text.

*bCanUndo*<br/>
Chcete-li určit, že tato funkce může být vrácena zpět, nastavte hodnotu tohoto parametru na hodnotu TRUE. Výchozí hodnota je FALSE (NEPRAVDA).

### <a name="remarks"></a>Poznámky

Nahradí pouze část textu v ovládacím prvku pro úpravy. Chcete-li nahradit celý text, použijte členskou funkci [CWnd:: SetWindowText](cwnd-class.md#setwindowtext) .

Pokud není k dispozici žádný výběr, bude nahrazený text vložen do aktuálního umístění kurzoru.

Další informace najdete v tématu [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit:: LineIndex](#lineindex).

##  <a name="setcuebanner"></a>CEdit::SetCueBanner

Nastaví text, který se zobrazí jako textová hromádka nebo tip, v ovládacím prvku pro úpravy, když je ovládací prvek prázdný.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
pro Ukazatel na řetězec, který obsahuje hromádku pro zobrazení v ovládacím prvku pro úpravy.

*fDrawWhenFocused*<br/>
pro Pokud je hodnota FALSE, banner se nezobrazí, když uživatel klikne v ovládacím prvku pro úpravy a udělí fokus ovládacímu prvku.

Pokud má hodnotu TRUE, je hromádka hromádky i v případě, že ovládací prvek má fokus. Pokud uživatel zahájí psaní ovládacího prvku, nápis hromádky zmizí.

Výchozí hodnota je FALSE (NEPRAVDA).

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner) , která je popsána v Windows SDK. Další informace najdete v tématu makro [Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) .

### <a name="example"></a>Příklad

Následující příklad ukazuje metodu [CEdit:: SetCueBanner](#setcuebanner) .

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

##  <a name="sethandle"></a>CEdit::SetHandle

Voláním této funkce nastavíte popisovač na místní paměť, která bude použita víceřádkovým ovládacím prvkem pro úpravy.

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Parametry

*hBuffer*<br/>
Obsahuje popisovač do místní paměti. Tento popisovač musí být vytvořen předchozím voláním funkce [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) systému Windows pomocí příznaku LMEM_MOVEABLE. Předpokládá se, že paměť obsahuje řetězec zakončený hodnotou null. V takovém případě by měl být první bajt přidělené paměti nastaven na hodnotu 0.

### <a name="remarks"></a>Poznámky

Ovládací prvek pro úpravy pak použije tuto vyrovnávací paměť k uložení aktuálně zobrazeného textu namísto přidělení vlastní vyrovnávací paměti.

Tato členská funkce je zpracována pouze víceřádkovými ovládacími prvky pro úpravy.

Předtím, než aplikace nastaví novou obslužnou rutinu paměti, měla by [](#gethandle) použít funkci getHandler, která získá popisovač do aktuální vyrovnávací paměti a uvolní tuto paměť pomocí `LocalFree` funkce Windows.

`SetHandle`vymaže vyrovnávací paměť pro vrácení zpět (členská funkce [CanUndo](#canundo) pak vrátí 0) a příznak interní změny (členská funkce GetModify pak vrátí 0). [](#getmodify) Dojde k překreslení okna pro úpravu ovládacího prvku.

Tuto členskou funkci můžete v dialogovém okně víceřádkového textového pole použít pouze v případě, že jste vytvořili dialogové okno s nastaveným příznakem stylu DS_LOCALEDIT.

> [!NOTE]
> `GetHandle`nebude fungovat se systémem Windows 95/98. Pokud zavoláte `GetHandle` ve Windows 95/98, vrátí hodnotu null. `GetHandle`bude fungovat jak je uvedeno v části Windows NT, verze 3,51 a novější.

Další informace naleznete v tématu [EM_SETHANDLE](/windows/win32/Controls/em-sethandle), [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)a [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

##  <a name="sethighlight"></a>CEdit::SetHighlight

Zvýrazní rozsah textu, který se zobrazí v aktuálním ovládacím prvku pro úpravy.

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*ichStart*|pro Index prvního znaku založený na nule v oblasti textu, který se má zvýraznit|
|*ichEnd*|pro Nulový index posledního znaku v oblasti textu, který se má zvýraznit|

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [EM_SETHILITE](/windows/win32/Controls/em-sethilite) , která je popsána v Windows SDK.  Tato metoda pošle zprávu [EM_SETHILITE](/windows/win32/Controls/em-sethilite) , která je popsána v Windows SDK. `SetHighlight` A`GetHighlight` jsou povoleny pouze pro sestavení Unicode.

##  <a name="setlimittext"></a>  CEdit::SetLimitText

Chcete-li nastavit omezení pro text pro tento `CEdit` objekt, zavolejte tuto členskou funkci.

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Parametry

*Nmaximum*<br/>
Nový omezení textu v znacích.

### <a name="remarks"></a>Poznámky

Omezení textu je maximální množství textu ve znacích, které může ovládací prvek pro úpravy přijmout.

Změna omezení textu omezí pouze text, který uživatel může zadat. Nemá žádný vliv na žádný text, který je již v ovládacím prvku pro úpravy, ani na délku kopírovaného textu do textového pole pomocí členské funkce [SetWindowText](cwnd-class.md#setwindowtext) v `CWnd`. Pokud aplikace používá `SetWindowText` funkci k umístění většího textu do ovládacího prvku pro úpravy, než je určeno v volání, `LimitText`uživatel může odstranit libovolný text v ovládacím prvku pro úpravy. Omezení textu však zabrání uživateli nahradit stávající text novým textem, pokud odstraněním aktuálního výběru způsobí, že text nebude pod omezením textu.

Tato funkce nahrazuje [LimitText](#limittext) v systému Win32.

Další informace najdete v tématu [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="setmargins"></a>CEdit::SetMargins

Voláním této metody nastavte levý a pravý okraj tohoto ovládacího prvku pro úpravy.

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Parametry

*nLeft*<br/>
Šířka nového levého okraje v pixelech

*nRight*<br/>
Šířka nového pravého okraje (v pixelech)

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato členská funkce je k dispozici počínaje systémy Windows 95 a Windows NT 4,0.

Další informace najdete v tématu [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="setmodify"></a>CEdit::SetModify

Voláním této funkce nastavíte nebo zrušíte upravený příznak pro ovládací prvek pro úpravy.

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parametry

*bModified*<br/>
Hodnota TRUE značí, že text byl změněn a hodnota FALSE označuje, že je nezměněný. Ve výchozím nastavení je nastaven příznak upraveno.

### <a name="remarks"></a>Poznámky

Upravený příznak označuje, zda byl text v ovládacím prvku pro úpravy změněn. Automaticky se nastaví vždy, když uživatel změní text. Její hodnotu lze načíst pomocí členské funkce [GetModify](#getmodify) .

Další informace najdete v tématu [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit:: GetModify](#getmodify).

##  <a name="setpasswordchar"></a>CEdit::SetPasswordChar

Voláním této funkce nastavíte nebo odeberete znak hesla zobrazený v ovládacím prvku pro úpravy, když uživatel zadá text.

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Určuje znak, který má být zobrazen místo znaku zadaného uživatelem. Pokud je hodnota *ch* 0, zobrazí se skutečné znaky zadané uživatelem.

### <a name="remarks"></a>Poznámky

Když je nastaven znak hesla, zobrazí se tento znak pro každý znak typu uživatel.

Tato členská funkce nemá žádný vliv na víceřádkový ovládací prvek pro úpravy.

`SetPasswordChar` Přivolání členské funkce překreslí všechny viditelné znaky pomocí znaku určeného parametrem ch `CEdit` .

Pokud je ovládací prvek pro úpravy vytvořen pomocí stylu [ES_PASSWORD](styles-used-by-mfc.md#edit-styles) , je výchozí znak hesla nastaven na hvězdičku ( <strong>\*</strong>). Tento styl se odebere, `SetPasswordChar` Pokud se volá s *ch* nastaveným na 0.

Další informace najdete v tématu [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

##  <a name="setreadonly"></a>CEdit::SetReadOnly

Volá tuto funkci pro nastavení stavu pouze pro čtení ovládacího prvku pro úpravy.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bReadOnly*<br/>
Určuje, zda se má pro ovládací prvek pro úpravy nastavit nebo odebrat stav jen pro čtení. Hodnota TRUE nastaví stav na jen pro čtení; Hodnota FALSE nastaví stav na čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je operace úspěšná, nebo 0, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Aktuální nastavení lze nalézt otestováním příznaku [ES_READONLY](styles-used-by-mfc.md#edit-styles) v návratové hodnotě [CWnd:: GetStyle](cwnd-class.md#getstyle).

Další informace najdete v tématu [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

##  <a name="setrect"></a>CEdit::SetRect

Voláním této funkce nastavíte rozměry obdélníku pomocí zadaných souřadnic.

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu nebo `CRect` objekt, které určují nové rozměry obdélníku formátování.

### <a name="remarks"></a>Poznámky

Tento člen je zpracován pouze pomocí víceřádkových textových ovládacích prvků.

Slouží `SetRect` k nastavení obdélníku formátování víceřádkového ovládacího prvku pro úpravy. Formátovací obdélník je omezující obdélník textu, který je nezávislý na velikosti okna pro úpravu ovládacího prvku. Při prvním vytvoření ovládacího prvku pro úpravy je obdélník formátování stejný jako klientská oblast okna Upravit ovládací prvek. Pomocí `SetRect` členské funkce může aplikace nastavit obdélník formátování větší nebo menší než okno pro úpravu ovládacího prvku.

Pokud ovládací prvek pro úpravy nemá žádný posuvník, text bude oříznut, nikoli zabalený, pokud je obdélník formátování vytvořen větší než okno. Pokud ovládací prvek pro úpravy obsahuje ohraničení, je obdélník formátování zmenšen o velikost ohraničení. Pokud upravíte obdélník vrácený `GetRect` funkcí členské funkce, je nutné odstranit velikost ohraničení před předáním obdélníku do. `SetRect`

Když `SetRect` je volána, text textového ovládacího prvku je také přeformátován a znovu zobrazen.

Další informace najdete v tématu [EM_SETRECT](/windows/win32/Controls/em-setrect) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

##  <a name="setrectnp"></a>CEdit::SetRectNP

Voláním této funkce nastavíte obdélník formátování víceřádkového ovládacího prvku pro úpravy.

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Odkazuje na `RECT` strukturu nebo `CRect` objekt, které určují nové rozměry obdélníku.

### <a name="remarks"></a>Poznámky

Formátovací obdélník je omezující obdélník textu, který je nezávislý na velikosti okna pro úpravu ovládacího prvku.

`SetRectNP`je totožný s `SetRect` členskou funkcí s tím rozdílem, že okno pro úpravu ovládacího prvku není překresleno.

Při prvním vytvoření ovládacího prvku pro úpravy je obdélník formátování stejný jako klientská oblast okna Upravit ovládací prvek. Voláním `SetRectNP` členské funkce může aplikace nastavit obdélník formátování větší nebo menší než okno pro úpravu ovládacího prvku.

Pokud ovládací prvek pro úpravy nemá žádný posuvník, text bude oříznut, nikoli zabalený, pokud je obdélník formátování vytvořen větší než okno.

Tento člen je zpracován pouze pomocí víceřádkových textových ovládacích prvků.

Další informace najdete v tématu [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit:: SetRect](#setrect).

##  <a name="setsel"></a>CEdit::SetSel

Voláním této funkce vyberete rozsah znaků v textovém ovládacím prvku.

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
Určuje počáteční pozici v aplikaci s nízkým pořadím a koncovou pozicí ve slově s vysokým pořadím. Pokud je slovo s nižším pořadím 0 a slovo s vyšším pořadím je-1, je vybrán veškerý text v ovládacím prvku pro úpravy. Pokud je slovo s nižším pořadím-1, všechny aktuální výběry budou odebrány.

*bNoScroll*<br/>
Určuje, zda má být blikající kurzor posunut do zobrazení. Při hodnotě FALSE se blikající kurzor posouvá do zobrazení. Při hodnotě TRUE se blikající kurzor neposouvá do zobrazení.

*nStartChar*<br/>
Určuje počáteční pozici. Pokud je *nStartChar* 0 a *nEndChar* je-1, je vybrán veškerý text v textovém poli. Pokud je *nStartChar* -1, všechny aktuální výběry se odeberou.

*nEndChar*<br/>
Určuje koncovou pozici.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [EM_SETSEL](/windows/win32/Controls/em-setsel) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEdit:: GetSel](#getsel).

##  <a name="settabstops"></a>CEdit::SetTabStops

Voláním této funkce nastavíte zarážky tabulátoru v víceřádkovém textovém ovládacím prvku.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Určuje, že se zarážky tabulátoru mají nastavit v každé jednotce dialogového okna *cxEachStop* .

*nTabStops*<br/>
Určuje počet zarážek tabulátorů obsažených v *rgTabStops*. Toto číslo musí být větší než 1.

*rgTabStops*<br/>
Odkazuje na pole celých čísel bez znaménka, které určují zarážky tabulátoru v jednotkách dialogových oken. Jednotka dialogového okna je vodorovná nebo svislá vzdálenost. Jedna vodorovná jednotka dialogového okna je rovna jedné čtvrtine aktuální jednotky základní šířky dialogového okna a 1 svislá jednotka dialogového okna je rovna jedné 8 aktuální jednotky základní výšky dialogového okna. Základní jednotky dialogového okna jsou vypočítány na základě výšky a šířky aktuálního systémového písma. Funkce `GetDialogBaseUnits` Windows vrátí aktuální základní jednotky dialogu v pixelech.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byly karty nastaveny; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Když je text zkopírován do víceřádkového ovládacího prvku pro úpravy, znak tabulátoru v textu způsobí, že se místo vygeneruje na další zarážku tabulátoru.

Chcete-li nastavit zarážky tabulátoru na výchozí velikost 32ch jednotek dialogu, zavolejte verzi této členské funkce bez parametrů. Chcete-li nastavit zarážky tabulátoru na jinou velikost než 32, zavolejte verzi pomocí parametru *cxEachStop* . Chcete-li nastavit zarážky tabulátoru na pole velikostí, použijte verzi se dvěma parametry.

Tato členská funkce je zpracována pouze pomocí víceřádkových textových ovládacích prvků.

`SetTabStops`automaticky nekreslí okno úprav. Pokud změníte zarážky pro text, který už je v ovládacím prvku pro úpravy, zavolejte v poli [CWnd:: InvalidateRect](cwnd-class.md#invalidaterect) , aby se změnilo okno úprav.

Další informace najdete v tématu [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) a [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) v Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CEditView:: SetTabStops](ceditview-class.md#settabstops).

##  <a name="showballoontip"></a>CEdit::ShowBalloonTip

Zobrazí Tip bubliny, který je přidružen k aktuálnímu ovládacímu prvku pro úpravy.

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
|*pEditBalloonTip*|pro Ukazatel na strukturu [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) , která popisuje Tip v bublině.|
|*lpszTitle*|pro Ukazatel na řetězec v kódování Unicode, který obsahuje název tipu bubliny.|
|*lpszText*|pro Ukazatel na řetězec v kódování Unicode, který obsahuje text tipu bubliny.|
|*ttiIcon*|pro **Int** , která určuje typ ikony k přidružení s tipem v bublině. Výchozí hodnota je TTI_NONE. Další informace naleznete v tématu `ttiIcon` člen struktury [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) .|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato funkce pošle zprávu [EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip) , která je popsána v Windows SDK. Další informace najdete v tématu makro [Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip) .

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_cedit`která se používá pro přístup k aktuálnímu ovládacímu prvku pro úpravy. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Příklad

Následující příklad kódu zobrazuje Tip pro ovládací prvek pro úpravy. Metoda [CEdit:: ShowBalloonTip](#showballoontip) Určuje název a text tipu v bublině.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

##  <a name="undo"></a>CEdit:: Undo

Voláním této funkce vrátíte poslední operaci úpravy ovládacího prvku.

```
BOOL Undo();
```

### <a name="return-value"></a>Návratová hodnota

V případě víceřádkového ovládacího prvku pro úpravy je návratová hodnota vždy nenulová. V případě víceřádkového ovládacího prvku pro úpravy je návratová hodnota nenulová, pokud je operace vrácení zpět úspěšná, nebo 0, pokud se operace vrácení nezdařila.

### <a name="remarks"></a>Poznámky

Operaci vrácení zpět lze také vrátit zpět. Odstraněné texty můžete například obnovit pomocí prvního volání `Undo`. Pokud neexistuje žádná operace úpravy, můžete text znovu odebrat druhým voláním `Undo`.

Další informace najdete v tématu [EM_UNDO](/windows/win32/Controls/em-undo) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Viz také:

[CALCDRIV Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CMNCTRL2 Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](cwnd-class.md)<br/>
[CButton – třída](cbutton-class.md)<br/>
[CComboBox – třída](ccombobox-class.md)<br/>
[CListBox – třída](clistbox-class.md)<br/>
[CScrollBar – třída](cscrollbar-class.md)<br/>
[CStatic – třída](cstatic-class.md)<br/>
[CDialog – třída](cdialog-class.md)
