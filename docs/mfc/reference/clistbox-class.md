---
title: CListBox – třída
description: Popis třídy CListBox knihovny MFC a jejích členských funkcí.
ms.date: 01/22/2020
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
helpviewer_keywords:
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
ms.openlocfilehash: 171038ebaaed815aa687c200fe3210bde8000be3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753588"
---
# <a name="clistbox-class"></a>CListBox – třída

Poskytuje funkce seznamu systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CListBox : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|Vytvoří `CListBox` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CListBox::Přidat řetězec](#addstring)|Přidá řetězec do seznamu.|
|[CListBox::chartoitem](#chartoitem)|Přepsat poskytnout vlastní WM_CHAR zpracování pro seznamy losování vlastníka, které nemají řetězce.|
|[CListBox::Porovnatpoložku](#compareitem)|Volat rámci k určení pozice nové položky v seřazené vlastníka losování seznamu.|
|[CListBox::Vytvořit](#create)|Vytvoří seznam systému Windows a `CListBox` připojí jej k objektu.|
|[CListBox::DeleteItem](#deleteitem)|Volat rámci při uživatel odstraní položku ze seznamu vlastníka losování.|
|[CListBox::DeleteString](#deletestring)|Odstraní řetězec ze seznamu.|
|[CListBox::D](#dir)|Přidá názvy souborů, jednotky nebo obojí z aktuálního adresáře do seznamu.|
|[CListBox::DrawItem](#drawitem)|Volat rámci při změně vizuální aspekt seznamu vlastníka kreslit.|
|[CListBox::FindString](#findstring)|Vyhledá řetězec v seznamu.|
|[CListBox::FindStringExact](#findstringexact)|Vyhledá první řetězec seznamu, který odpovídá zadanému řetězci.|
|[CListBox::GetAnchorIndex](#getanchorindex)|Načte index na základě nuly aktuální kotevní položky v seznamu.|
|[CListBox::GetCaretIndex](#getcaretindex)|Určuje index položky, která má obdélník fokusu v seznamu s více výběry.|
|[CListBox::GetCount](#getcount)|Vrátí počet řetězců v seznamu.|
|[CListBox::GetCurSel](#getcursel)|Vrátí index aktuálně vybraného řetězce v seznamu založený na nule.|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Vrátí šířku v obrazových bodech, po které lze seznam posouvat vodorovně.|
|[CListBox::GetItemData](#getitemdata)|Vrátí hodnotu přidruženou k položce seznamu.|
|[CListBox::GetItemDataPtr](#getitemdataptr)|Vrátí ukazatel na položku seznamu.|
|[CListBox::GetItemHeight](#getitemheight)|Určuje výšku položek v seznamu.|
|[CListBox::GetItemRect](#getitemrect)|Vrátí ohraničovací obdélník položky seznamu tak, jak je aktuálně zobrazena.|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Načte počet položek na sloupec.|
|[CListBox::GetLocale](#getlocale)|Načte identifikátor národního prostředí pro seznam.|
|[CListBox::GetSel](#getsel)|Vrátí stav výběru položky seznamu.|
|[CListBox::GetSelCount](#getselcount)|Vrátí počet řetězců aktuálně vybraných v seznamu s více násobným výběrem.|
|[CListBox::GetSelItems](#getselitems)|Vrátí indexy řetězců aktuálně vybraných v seznamu.|
|[CListBox::GetText](#gettext)|Zkopíruje položku seznamu do vyrovnávací paměti.|
|[CListBox::GetTextLen](#gettextlen)|Vrátí délku položky seznamu v bajtech.|
|[CListBox::GettopIndex](#gettopindex)|Vrátí index prvního viditelného řetězce v seznamu.|
|[CListBox::InitStorage](#initstorage)|Předem přidělí bloky paměti pro položky seznamu a řetězce.|
|[CListBox::Vložit řetězec](#insertstring)|Vloží řetězec do určitého umístění v seznamu.|
|[CListBox::ItemFromPoint](#itemfrompoint)|Vrátí index položky seznamu, která je nejblíže bodu.|
|[CListBox::MeasureItem](#measureitem)|Volat rámci při vytvoření seznamu vlastníka čerpat k určení dimenze seznamu.|
|[CListBox::ResetContent](#resetcontent)|Vymaže všechny položky ze seznamu.|
|[CListBox::SelectString](#selectstring)|Vyhledá a vybere řetězec v seznamu s jedním výběrem.|
|[CListBox::SelItemRange](#selitemrange)|Vybere nebo zruší výběr řady řetězců v seznamu s více výběry.|
|[CListBox::SetAnchorIndex](#setanchorindex)|Nastaví kotvu v seznamu s více násobným výběrem tak, aby začínala rozšířený výběr.|
|[CListBox::SetCaretIndex](#setcaretindex)|Nastaví obdélník fokusu na položku v zadaném indexu v seznamu s více násobným výběrem.|
|[CListBox::SetColumnWidth](#setcolumnwidth)|Nastaví šířku sloupce seznamu s více sloupci.|
|[CListBox::SetCurSel](#setcursel)|Vybere řetězec seznamu.|
|[CListBox::Nastavitvodorovný rozsah](#sethorizontalextent)|Nastaví šířku v obrazových bodech, po které lze seznam posouvat vodorovně.|
|[CListBox::SetItemData](#setitemdata)|Nastaví hodnotu přidruženou k položce seznamu.|
|[CListBox::SetItemDataPtr](#setitemdataptr)|Nastaví ukazatel na položku seznamu.|
|[CListBox::SetItemHeight](#setitemheight)|Nastaví výšku položek v seznamu.|
|[CListBox::SetLocale](#setlocale)|Nastaví identifikátor národního prostředí pro seznam.|
|[CListBox::SetSel](#setsel)|Vybere nebo zruší výběr položky seznamu v seznamu s více výběry.|
|[CListBox::SetTabstops](#settabstops)|Nastaví pozice zastavovacího místa v seznamu.|
|[CListBox::SettopIndex](#settopindex)|Nastaví nulový index prvního viditelného řetězce v seznamu.|
|[CListBox::VKeyToItem](#vkeytoitem)|Přepsáníposkytuje vlastní WM_KEYDOWN zpracování seznamů se sadou stylů LBS_WANTKEYBOARDINPUT.|

## <a name="remarks"></a>Poznámky

V seznamu se zobrazí seznam položek, například názvů souborů, které může uživatel zobrazit a vybrat.

V seznamu s jedním výběrem může uživatel vybrat pouze jednu položku. V seznamu s více násobným výběrem lze vybrat rozsah položek. Když uživatel vybere položku, je zvýrazněna a seznam odešle oznámení do nadřazeného okna.

Seznam můžete vytvořit buď ze šablony dialogového okna, nebo přímo v kódu. Chcete-li jej vytvořit `CListBox` přímo, vytvořte objekt a pak zavolejte členovou funkci `CListBox` [Vytvořit](#create) a vytvořte ovládací prvek seznamu systému Windows a připojte jej k objektu. Chcete-li použít seznam v šabloně dialogového okna, deklarujte `DDX_Control` proměnnou seznamu ve `DoDataExchange` třídě dialogového okna a potom použijte ve funkci třídy dialogového okna pro připojení členské proměnné k ovládacímu prvku. (To se provádí automaticky, když přidáte řídicí proměnnou do třídy dialogového okna.)

Konstrukce může být jednostupňový proces ve `CListBox`třídě odvozené z . Napište konstruktor pro odvozené `Create` třídy a volání z uvnitř konstruktoru.

Pokud chcete zpracovat zprávy oznámení systému Windows odeslané seznamem jeho nadřazené (obvykle třídy odvozené z [CDialog](../../mfc/reference/cdialog-class.md)), přidejte položku mapy zprávy a členskou funkci obslužné rutiny zprávy do nadřazené třídy pro každou zprávu.

Každá položka mapy zpráv má následující podobu:

`ON_Notification( id, memberFxn )`

kde `id` určuje ID podřízeného okna ovládacího prvku `memberFxn` seznamu odesílajícího oznámení a je název nadřazené členské funkce, kterou jste napsali pro zpracování oznámení.

Prototyp funkce nadřazeného objektu je následující:

`afx_msg void memberFxn( );`

Následuje seznam možných položek mapy zpráv a popis případů, ve kterých by byly odeslány nadřazenému:

- ON_LBN_DBLCLK Uživatel poklepe na řetězec v seznamu. Tuto oznámení odešle pouze seznam, ve které je [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu.

- ON_LBN_ERRSPACE Seznam nemůže přidělit dostatek paměti pro splnění požadavku.

- ON_LBN_KILLFOCUS Seznam ztrácí vstupní fokus.

- ON_LBN_SELCANCEL Aktuální výběr seznamu je zrušen. Tato zpráva je odeslána pouze v případě, že seznam obsahuje LBS_NOTIFY styl.

- ON_LBN_SELCHANGE Výběr v seznamu se změnil. Toto oznámení není odeslána, pokud je výběr změněn člennou funkcí [CListBox::SetCurSel.](#setcursel) Toto oznámení se vztahuje pouze na seznam, který má LBS_NOTIFY stylu. Zpráva LBN_SELCHANGE oznámení je odeslána pro seznam více násobných výběrů vždy, když uživatel stiskne klávesu se šipkou, i když se výběr nezmění.

- ON_LBN_SETFOCUS Do seznamu se přijímá vstupní fokus.

- ON_WM_CHARTOITEM Seznam draw vlastníka, který nemá žádné řetězce, obdrží WM_CHAR zprávu.

- ON_WM_VKEYTOITEM: V seznamu se stylem LBS_WANTKEYBOARDINPUT se zobrazí WM_KEYDOWN zpráva.

Pokud vytvoříte `CListBox` objekt v dialogovém okně (prostřednictvím prostředku dialogového okna), `CListBox` objekt se automaticky zničí, když uživatel zavře dialogové okno.

Pokud vytvoříte `CListBox` objekt v okně, bude pravděpodobně `CListBox` nutné zničit objekt. Pokud vytvoříte `CListBox` objekt v zásobníku, je automaticky zničen. Pokud vytvoříte `CListBox` objekt na haldě pomocí **nové** funkce, musíte volat **delete** na objekt zničit, když uživatel zavře nadřazené okno.

Pokud přidělíte všechny `CListBox` paměti v `CListBox` objektu, přepsat destruktor k vyřazení přidělení.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="clistboxaddstring"></a><a name="addstring"></a>CListBox::Přidat řetězec

Přidá řetězec do seznamu.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*lpszPoložka*<br/>
Odkazuje na řetězec ukončený hodnotou null, který má být přidán.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule na řetězec v seznamu. Vrácená hodnota je LB_ERR, pokud dojde k chybě; vrácená hodnota je LB_ERRSPACE, pokud není k dispozici dostatek místa pro uložení nového řetězce.

### <a name="remarks"></a>Poznámky

Pokud seznam nebyl vytvořen s [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylem, řetězec je přidán na konec seznamu. V opačném případě je řetězec vložen do seznamu a seznam je seřazen. Pokud byl seznam vytvořen s LBS_SORT stylem, ale nikoli [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylem, framework `CompareItem` seřadí seznam podle jednoho nebo více volání členské funkce.

Pomocí [funkce InsertString](#insertstring) vložte řetězec do určitého umístění v seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

## <a name="clistboxchartoitem"></a><a name="chartoitem"></a>CListBox::chartoitem

Volat rámci při nadřazené okno seznamu obdrží zprávu WM_CHARTOITEM ze seznamu.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nKlíč*<br/>
Kód ANSI znaku, který uživatel zadali.

*nIndex*<br/>
Aktuální pozice stříšky seznamu.

### <a name="return-value"></a>Návratová hodnota

Vrátí - 1 nebo - 2 pro žádnou další akci nebo nezáporné číslo pro určení indexu položky seznamu, na které chcete provést výchozí akci pro stisknutí klávesy. Výchozí implementace vrátí - 1.

### <a name="remarks"></a>Poznámky

Zpráva WM_CHARTOITEM je odeslána seznamem, když obdrží zprávu WM_CHAR, ale pouze v případě, že seznam splňuje všechna tato kritéria:

- Je seznam vlastníků a losování.

- Nemá sadu [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu.

- Má alespoň jednu položku.

Nikdy byste neměli volat tuto funkci sami. Přepsat tuto funkci poskytnout vlastní zpracování zpráv klávesnice.

V přepsání je nutné vrátit hodnotu sdělit rámci, jaké akce jste provedli. Vrácená hodnota - 1 nebo - 2 označuje, že jste zvládli všechny aspekty výběru položky a nevyžaduje žádnou další akci v seznamu. Před návratem - 1 nebo - 2, můžete nastavit výběr nebo přesunout stříška nebo obojí. Chcete-li nastavit výběr, použijte [SetCurSel](#setcursel) nebo [SetSel](#setsel). Chcete-li přesunout stříšku, použijte [SetCaretIndex](#setcaretindex).

Vrácená hodnota 0 nebo vyšší určuje index položky v seznamu a označuje, že seznam by měl provést výchozí akci pro stisknutí klávesy na dané položce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

## <a name="clistboxclistbox"></a><a name="clistbox"></a>CListBox::CListBox

Vytvoří `CListBox` objekt.

```
CListBox();
```

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CListBox` dvou krocích. Nejprve zavolejte `ClistBox` konstruktoru `Create`a potom volání , který inicializuje `CListBox`seznam systému Windows a připojí jej k .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

## <a name="clistboxcompareitem"></a><a name="compareitem"></a>CListBox::Porovnatpoložku

Volat rámci k určení relativní pozice nové položky v seřazené vlastníka losování seznamu.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parametry

*lpCompareItemStruct*<br/>
Dlouhý ukazatel na `COMPAREITEMSTRUCT` strukturu.

### <a name="return-value"></a>Návratová hodnota

Označuje relativní pozici dvou položek popsaných ve struktuře [COMPAREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-compareitemstruct) Může se jedná o některou z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|-1|Položka 1 seřadí před bodem 2.|
|0|Položka 1 a položka 2 se řadí stejně.|
|1|Položka 1 seřadí za položkou 2.|

Viz [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) popis `COMPAREITEMSTRUCT` struktury.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádné. Pokud vytvoříte seznam losování vlastníka se stylem LBS_SORT, musíte přepsat tuto členskou funkci, abyste pomohli při řazení nových položek přidaných do seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

## <a name="clistboxcreate"></a><a name="create"></a>CListBox::Vytvořit

Vytvoří seznam systému Windows a `CListBox` připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl seznamu. Použijte libovolnou kombinaci [stylů seznamu](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) na pole.

*Rect*<br/>
Určuje velikost a umístění seznamu. Může být `CRect` objekt nebo `RECT` struktura.

*pParentWnd*<br/>
Určuje nadřazené okno seznamu `CDialog` (obvykle objekt). Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku seznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CListBox` dvou krocích. Nejprve zavolejte konstruktoru `Create`a potom volání , který inicializuje `CListBox` seznam systému Windows a připojí jej k objektu.

Při `Create` spuštění systémWindows odešle [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)a [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) zprávy do ovládacího prvku seznamu.

Tyto zprávy jsou ve výchozím nastavení zpracovány členy [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)a [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) v `CWnd` základní třídě. Chcete-li rozšířit výchozí zpracování zpráv, odvodit třídu z `CListBox`, přidejte mapu zpráv do nové třídy a přepsat předchozí funkce obsluhy zprávy. Přepište `OnCreate`, například provést potřebnou inicializaci pro novou třídu.

Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) u ovládacího prvku seznamu.

- WS_CHILD vždy

- WS_VISIBLE Obvykle

- WS_DISABLED Zřídka

- WS_VSCROLL Přidání svislého posuvníku

- WS_HSCROLL Přidání vodorovného posuvníku

- WS_GROUP Chcete-li seskupit ovládací prvky

- WS_TABSTOP Povolení tabulátoru k tomuto ovládacímu prvku

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

## <a name="clistboxdeleteitem"></a><a name="deleteitem"></a>CListBox::DeleteItem

Volat rámci při uživatel odstraní položku z objektu kreslení `CListBox` vlastníka nebo zničí seznam.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDeleteItemStruct*<br/>
Dlouhý ukazatel na strukturu [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) systému Windows, která obsahuje informace o odstraněné položce.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádné provádění. Přepište tuto funkci a podle potřeby překreslte seznam losování vlastníka.

Viz [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) popis `DELETEITEMSTRUCT` struktury.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

## <a name="clistboxdeletestring"></a><a name="deletestring"></a>CListBox::DeleteString

Odstraní položku v pozici *nIndex* ze seznamu.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index řetězce, který má být odstraněn.

### <a name="return-value"></a>Návratová hodnota

Počet řetězců zbývajících v seznamu. Vrácená hodnota je LB_ERR pokud *nIndex* určuje index větší než počet položek v seznamu.

### <a name="remarks"></a>Poznámky

Všechny položky následující *po nIndex* nyní přesunout dolů o jednu pozici. Pokud například seznam obsahuje dvě položky, odstranění první položky způsobí, že zbývající položka bude nyní na první pozici. *nIndex*=0 pro položku na první pozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

## <a name="clistboxdir"></a><a name="dir"></a>CListBox::D

Přidá seznam názvů souborů, jednotek nebo obojího do seznamu.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parametry

*attr*<br/>
Může být libovolná kombinace **výčtových** hodnot popsaných v `CFile::GetStatu` [s](../../mfc/reference/cfile-class.md#getstatus), nebo libovolná kombinace následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|0x0000|Soubor lze číst nebo zapisovat do.|
|0x0001|Soubor lze číst z, ale není zapsán.|
|0x0002|Soubor je skrytý a nezobrazuje se v seznamu adresářů.|
|0x0004|Soubor je systémový soubor.|
|0x0010|Název určený *lpszWildCard* určuje adresář.|
|0x0020|Soubor byl archivován.|
|0x4000|Zahrnout všechny jednotky, které odpovídají názvu určenému *lpszWildCard*.|
|0x8000|Exkluzivní vlajka. Pokud je nastaven výhradní příznak, jsou uvedeny pouze soubory zadaného typu. V opačném případě jsou kromě "normálních" souborů uvedeny soubory zadaného typu.|

*lpszDivoká karta*<br/>
Odkazuje na řetězec specifikace souboru. Řetězec může obsahovat zástupné znaky\*(například *. ).

### <a name="return-value"></a>Návratová hodnota

Index posledního názvu souboru, který byl přidán do seznamu, založený na nule. Vrácená hodnota je LB_ERR, pokud dojde k chybě; vrácená hodnota je LB_ERRSPACE, pokud není k dispozici dostatek místa pro uložení nových řetězců.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

## <a name="clistboxdrawitem"></a><a name="drawitem"></a>CListBox::DrawItem

Volat rámci při změně vizuální aspekt seznamu vlastníka kreslit.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhý ukazatel na strukturu [DRAWITEMSTRUCT,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) která obsahuje informace o požadovaném typu výkresu.

### <a name="remarks"></a>Poznámky

A `itemAction` `itemState` členové `DRAWITEMSTRUCT` struktury definují akci kreslení, která má být provedena.

Ve výchozím nastavení tato členská funkce neprovede žádné. Přepsat tuto členovou funkci implementovat výkres `CListBox` pro objekt nakreslení vlastníka. Aplikace by měla obnovit všechny objekty rozhraní grafického zařízení (GDI) vybrané pro kontext zobrazení dodaný v *lpDrawItemStruct* před ukončením této členské funkce.

Viz [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) popis `DRAWITEMSTRUCT` struktury.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

## <a name="clistboxfindstring"></a><a name="findstring"></a>CListBox::FindString

Najde první řetězec v seznamu, který obsahuje zadanou předponu bez evidencí se změnou výběru seznamu.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Obsahuje nulový index položky před první položkou, která má být prohledána. Když hledání dosáhne dolní části seznamu, pokračuje od horní části seznamu zpět k položce určené *nStartAfter*. Pokud *nStartAfter* je -1, celý seznam je prohledán od začátku.

*lpszPoložka*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje předponu, kterou chcete vyhledat. Hledání je nezávislé na malých a velkých písmenech, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index odpovídající položky založený na nule nebo LB_ERR, pokud bylo hledání neúspěšné.

### <a name="remarks"></a>Poznámky

Pomocí členské funkce [SelectString](#selectstring) můžete najít i vybrat řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

## <a name="clistboxfindstringexact"></a><a name="findstringexact"></a>CListBox::FindStringExact

Vyhledá první řetězec seznamu, který odpovídá řetězci zadanému v *souboru lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parametry

*nIndexStart*<br/>
Určuje nulový index položky před první položkou, která má být prohledána. Když hledání dosáhne dolní části seznamu, pokračuje od horní části seznamu zpět k položce určené *nIndexStart*. Pokud *nIndexStart* je -1, celý seznam je prohledán od začátku.

*lpszNajít*<br/>
Odkazuje na řetězec ukončený hodnotou null, který má být vyhledán. Tento řetězec může obsahovat úplný název souboru, včetně přípony. Hledání není rozlišování velkých a malých písmen, takže řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index odpovídající položky nebo LB_ERR, pokud hledání bylo neúspěšné.

### <a name="remarks"></a>Poznámky

Pokud byl seznam vytvořen se stylem kreslení [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) vlastníka, `FindStringExact` ale bez LBS_HASSTRINGS stylu, členské funkce se pokusí porovnat hodnotu doubleword s hodnotou *lpszFind*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

## <a name="clistboxgetanchorindex"></a><a name="getanchorindex"></a>CListBox::GetAnchorIndex

Načte index na základě nuly aktuální položky ukotvení v seznamu.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index aktuální kotevní položky, pokud je úspěšná; jinak LB_ERR.

### <a name="remarks"></a>Poznámky

V seznamu s více násobným výběrem je kotevní položka první nebo poslední položkou v bloku sousedících vybraných položek.

### <a name="example"></a>Příklad

  Viz příklad pro [CListBox::SetAnchorIndex](#setanchorindex).

## <a name="clistboxgetcaretindex"></a><a name="getcaretindex"></a>CListBox::GetCaretIndex

Určuje index položky, která má obdélník fokusu v seznamu s více výběry.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Nula na základě indexu položky, která má obdélník fokusu v seznamu. Pokud je seznam seznam emitovaného, vrátí se hodnota indexu vybrané položky, pokud existuje.

### <a name="remarks"></a>Poznámky

Položka může nebo nemusí být vybrána.

### <a name="example"></a>Příklad

  Viz příklad pro [CListBox::SetCaretIndex](#setcaretindex).

## <a name="clistboxgetcount"></a><a name="getcount"></a>CListBox::GetCount

Načte počet položek v seznamu.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu nebo LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Vrácený počet je o jednu větší než hodnota indexu poslední položky (index je založen na nule).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

## <a name="clistboxgetcursel"></a><a name="getcursel"></a>CListBox::GetCurSel

Načte index aktuálně vybrané položky založený na nule, pokud existuje, v seznamu s jedním výběrem.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Index aktuálně vybrané položky založený na nule, pokud se jedná o seznam s jedním výběrem. Je LB_ERR, pokud není aktuálně vybrána žádná položka.

V seznamu s více násobným výběrem je index položky, která má fokus.

### <a name="remarks"></a>Poznámky

Nevolejte `GetCurSel` seznam s více násobným výběrem. Místo toho použijte [CListBox::GetSelItems.](#getselitems)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

## <a name="clistboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent

Načte ze seznamu šířku v obrazových bodech, o kterou ji lze posouvat vodorovně.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Návratová hodnota

Posuvná šířka seznamu v obrazových bodech.

### <a name="remarks"></a>Poznámky

To platí pouze v případě, že seznam obsahuje vodorovný posuvník.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

## <a name="clistboxgetitemdata"></a><a name="getitemdata"></a>CListBox::GetItemData

Načte hodnotu doubleword dodanou aplikací přidruženou k zadané položce seznamu.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Hodnota přidružená k položce nebo LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Hodnota doubleword byla parametrem *dwItemData* volání [SetItemData.](#setitemdata)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

## <a name="clistboxgetitemdataptr"></a><a name="getitemdataptr"></a>CListBox::GetItemDataPtr

Načte 32bitovou hodnotu dodanou aplikací přidruženou k zadané položce seznamu jako ukazatel (**void** <strong>\*</strong>).

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Načte ukazatel nebo -1, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

## <a name="clistboxgetitemheight"></a><a name="getitemheight"></a>CListBox::GetItemHeight

Určuje výšku položek v seznamu.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky v seznamu. Tento parametr se používá pouze v případě, že seznam obsahuje LBS_OWNERDRAWVARIABLE styl; v opačném případě by měla být nastavena na 0.

### <a name="return-value"></a>Návratová hodnota

Výška položek v seznamu v obrazových bodech. Pokud seznam obsahuje [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, vrácená hodnota je výška položky určené *nIndex*. Pokud dojde k chybě, vrácená hodnota je LB_ERR.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

## <a name="clistboxgetitemrect"></a><a name="getitemrect"></a>CListBox::GetItemRect

Načte rozměry obdélníku, který ohraničuje položku seznamu tak, jak je aktuálně zobrazena v okně seznamu.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky.

*lpRect*<br/>
Určuje dlouhý ukazatel na [strukturu RECT,](/windows/win32/api/windef/ns-windef-rect) která přijímá souřadnice klienta seznamu položky.

### <a name="return-value"></a>Návratová hodnota

LB_ERR pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

## <a name="clistboxgetlistboxinfo"></a><a name="getlistboxinfo"></a>CListBox::GetListBoxInfo

Načte počet položek na sloupec.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek na sloupec `CListBox` objektu.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo) zprávy, jak je popsáno v sadě Windows SDK.

## <a name="clistboxgetlocale"></a><a name="getlocale"></a>CListBox::GetLocale

Načte národní prostředí používané v seznamu.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota identifikátoru národního prostředí (LCID) pro řetězce v seznamu.

### <a name="remarks"></a>Poznámky

Národní prostředí se používá například k určení pořadí řazení řetězců v seřazené seznamu.

### <a name="example"></a>Příklad

  Viz příklad pro [CListBox::SetLocale](#setlocale).

## <a name="clistboxgetsel"></a><a name="getsel"></a>CListBox::GetSel

Načte stav výběru položky.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky.

### <a name="return-value"></a>Návratová hodnota

Kladné číslo, pokud je vybrána zadaná položka; jinak je 0. Vrácená hodnota je LB_ERR pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tato členská funkce pracuje se seznamy s jedním i více výběry.

Chcete-li načíst index aktuálně vybrané položky seznamu, použijte [CListBox::GetCurSel](#getcursel).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

## <a name="clistboxgetselcount"></a><a name="getselcount"></a>CListBox::GetSelCount

Načte celkový počet vybraných položek v seznamu s více násobným výběrem.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet vybraných položek v seznamu. Pokud je seznam seznam emitovaného, vrátí se vrácená hodnota LB_ERR.

### <a name="example"></a>Příklad

  Viz příklad pro [CListBox::GetSelItems](#getselitems).

## <a name="clistboxgetselitems"></a><a name="getselitems"></a>CListBox::GetSelItems

Vyplní vyrovnávací paměť polem s celočíselnými čísly, která určují počet položek vybraných položek v seznamu s více násobným výběrem.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Parametry

*nPoložky MaxItems*<br/>
Určuje maximální počet vybraných položek, jejichž čísla položek mají být umístěna do vyrovnávací paměti.

*rgIndex*<br/>
Určuje ukazatel na vyrovnávací paměť, která je dostatečně velká pro počet celá čísla určená *parametrem nMaxItems*.

### <a name="return-value"></a>Návratová hodnota

Skutečný počet položek umístěných do vyrovnávací paměti. Pokud je seznam seznam emitovaného, vrátí `LB_ERR`se vrácená hodnota .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

## <a name="clistboxgettext"></a><a name="gettext"></a>CListBox::GetText

Získá řetězec ze seznamu.

```
int GetText(
    int nIndex,
    LPTSTR lpszBuffer) const;

void GetText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index řetězce, který má být načten.

*lpszBuffer*<br/>
Odkazuje na vyrovnávací paměť, která obdrží řetězec. Vyrovnávací paměť musí mít dostatek místa pro řetězec a ukončující znak null. Velikost řetězce lze určit předem voláním `GetTextLen` členské funkce.

*rString*<br/>
Odkaz na `CString` objekt.

### <a name="return-value"></a>Návratová hodnota

Délka (v bajtů) řetězce, s výjimkou ukončující ho znaku null. Pokud *nIndex* nezadává platný index, vrácená hodnota je LB_ERR.

### <a name="remarks"></a>Poznámky

Druhý formulář této členské funkce `CString` vyplní objekt textem řetězce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

## <a name="clistboxgettextlen"></a><a name="gettextlen"></a>CListBox::GetTextLen

Získá délku řetězce v položce seznamu.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index řetězce.

### <a name="return-value"></a>Návratová hodnota

Délka řetězce ve znacích, s výjimkou ukončujícího znaku null. Pokud *nIndex* nezadává platný index, vrácená hodnota je LB_ERR.

### <a name="example"></a>Příklad

  Viz příklad pro [CListBox::GetText](#gettext).

## <a name="clistboxgettopindex"></a><a name="gettopindex"></a>CListBox::GettopIndex

Načte index na základě nuly první viditelné položky v seznamu.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index první viditelné položky v seznamu založený na nule, LB_ERR jinak.

### <a name="remarks"></a>Poznámky

Zpočátku je položka 0 v horní části seznamu, ale pokud je seznam posunut, může být nahoře jiná položka.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

## <a name="clistboxinitstorage"></a><a name="initstorage"></a>CListBox::InitStorage

Přidělí paměť pro ukládání položek seznamu.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Parametry

*nPoložky*<br/>
Určuje počet položek, které mají být přidejte.

*nBajtu bajtů*<br/>
Určuje velikost paměti v bajtech, která má být přidělena pro řetězce položek.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, maximální počet položek, které lze uložit seznam před je potřeba přerozdělení paměti, jinak LB_ERRSPACE, což znamená, že není k dispozici dostatek paměti.

### <a name="remarks"></a>Poznámky

Volání této funkce před přidáním velkého `CListBox`počtu položek do .

Tato funkce pomáhá urychlit inicializaci seznamů, které mají velký počet položek (více než 100). Předem přidělí zadané množství paměti tak, aby následné [funkce AddString](#addstring), [InsertString](#insertstring)a [Dir](#dir) zabíraly nejkratší možný čas. Můžete použít odhady pro parametry. Pokud nadhodnocujete, je přidělena některá další paměť; Pokud podceňujete, normální přidělení se používá pro položky, které překračují předpojitou částku.

Pouze systém Windows 95/98: Parametr *nItems* je omezen na 16bitové hodnoty. To znamená, že seznamy nemohou obsahovat více než 32 767 položek. Přestože je počet položek omezen, celková velikost položek v seznamu je omezena pouze dostupnou pamětí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

## <a name="clistboxinsertstring"></a><a name="insertstring"></a>CListBox::Vložit řetězec

Vloží řetězec do seznamu.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index pozice pro vložení řetězce. Pokud je tento parametr -1, řetězec je přidán na konec seznamu.

*lpszPoložka*<br/>
Odkazuje na řetězec ukončený hodnotou null, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Nula na základě indexu pozice, na které byl vložen řetězec. Vrácená hodnota je LB_ERR, pokud dojde k chybě; vrácená hodnota je LB_ERRSPACE, pokud není k dispozici dostatek místa pro uložení nového řetězce.

### <a name="remarks"></a>Poznámky

Na rozdíl od členské `InsertString` funkce [AddString](#addstring) nezpůsobí seřazení seznamu se stylem [LBS_SORT.](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

## <a name="clistboxitemfrompoint"></a><a name="itemfrompoint"></a>CListBox::ItemFromPoint

Určuje položku seznamu nejbližší bodu určenému v *bodě pt*.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Bod, pro který chcete najít nejbližší položku, zadanou vzhledem k levému hornímu rohu klientské oblasti seznamu.

*b Mimo*<br/>
Odkaz na proměnnou BOOL, která bude nastavena na HODNOTU *TRUE,* pokud je pt mimo klientskou oblast seznamu, FALSE, pokud je *pt* uvnitř klientské oblasti seznamu.

### <a name="return-value"></a>Návratová hodnota

Index nejbližší položky k bodu určenému v *bodě pt*.

### <a name="remarks"></a>Poznámky

Pomocí této funkce můžete určit, kterou položku seznamu se kurzor myši přesune.

### <a name="example"></a>Příklad

  Viz příklad pro [CListBox::SetAnchorIndex](#setanchorindex).

## <a name="clistboxmeasureitem"></a><a name="measureitem"></a>CListBox::MeasureItem

Volat rámci při vytvoření seznamu se stylem kreslení vlastníka.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Dlouhý ukazatel na strukturu [MEASUREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádné. Přepsat tuto členovou funkci `MEASUREITEMSTRUCT` a vyplnit strukturu informovat Windows o rozměrech seznamu. Pokud je seznam vytvořen pomocí [stylu LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) framework volá tuto členskou funkci pro každou položku v seznamu. V opačném případě se tento člen nazývá pouze jednou.

Další informace o použití [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu v seznamu losování `SubclassDlgItem` vlastníka `CWnd`vytvořeném pomocí členské funkce aplikace naleznete v technické [poznámce 14](../../mfc/tn014-custom-controls.md).

Viz [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) pro popis `MEASUREITEMSTRUCT` struktury.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

## <a name="clistboxresetcontent"></a><a name="resetcontent"></a>CListBox::ResetContent

Odebere všechny položky ze seznamu.

```cpp
void ResetContent();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

## <a name="clistboxselectstring"></a><a name="selectstring"></a>CListBox::SelectString

Vyhledá položku seznamu, která odpovídá zadanému řetězci, a pokud je nalezena odpovídající položka, vybere položku.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Obsahuje nulový index položky před první položkou, která má být prohledána. Když hledání dosáhne dolní části seznamu, pokračuje od horní části seznamu zpět k položce určené *nStartAfter*. Pokud *nStartAfter* je -1, celý seznam je prohledán od začátku.

*lpszPoložka*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje předponu, kterou chcete vyhledat. Hledání je nezávislé na malých a velkých písmenech, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index vybrané položky, pokud bylo hledání úspěšné. Pokud hledání bylo neúspěšné, vrácená hodnota je LB_ERR a aktuální výběr se nezmění.

### <a name="remarks"></a>Poznámky

Seznam se v případě potřeby posune, aby se vybraná položka zobrazila do zobrazení.

Tuto členskou funkci nelze použít se seznamem, který má [LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl.

Položka je vybrána pouze v případě, že její počáteční znaky (od počátečního bodu) odpovídají znakům v řetězci určeném *lpszItem*.

Pomocí `FindString` členské funkce vyhledejte řetězec bez výběru položky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

## <a name="clistboxselitemrange"></a><a name="selitemrange"></a>CListBox::SelItemRange

Vybere více po sobě jdoucích položek v seznamu s více násobným výběrem.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Parametry

*bVybrat*<br/>
Určuje způsob nastavení výběru. Pokud *je bSelect* TRUE, řetězec je vybrán a zvýrazněn; pokud nepravda, zvýraznění je odebráno a řetězec již není vybrán.

*nFirstItem*<br/>
Určuje nulový index první položky, která má být nastavena.

*nLastItem*<br/>
Určuje nulový index poslední položky, která má být nastavena.

### <a name="return-value"></a>Návratová hodnota

LB_ERR pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tuto členská funkci používejte pouze se seznamy s více výběry. Pokud potřebujete vybrat pouze jednu položku v seznamu s více násobným výběrem – to znamená, že pokud *nFirstItem* se rovná *nLastItem* – místo toho zavolejte členskou funkci [SetSel.](#setsel)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

## <a name="clistboxsetanchorindex"></a><a name="setanchorindex"></a>CListBox::SetAnchorIndex

Nastaví kotvu v seznamu s více násobným výběrem tak, aby začínala rozšířený výběr.

```cpp
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky seznamu, která bude ukotvena.

### <a name="remarks"></a>Poznámky

V seznamu s více násobným výběrem je kotevní položka první nebo poslední položkou v bloku sousedících vybraných položek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

## <a name="clistboxsetcaretindex"></a><a name="setcaretindex"></a>CListBox::SetCaretIndex

Nastaví obdélník fokusu na položku v zadaném indexu v seznamu s více násobným výběrem.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky, která má obdržet obdélník fokusu v seznamu.

*bPosunnutí*<br/>
Pokud je tato hodnota 0, položka se posouvá, dokud není plně viditelná. Pokud tato hodnota není 0, položka se posouvá, dokud není alespoň částečně viditelné.

### <a name="return-value"></a>Návratová hodnota

LB_ERR pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Pokud položka není viditelná, je posunuta do zobrazení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

## <a name="clistboxsetcolumnwidth"></a><a name="setcolumnwidth"></a>CListBox::SetColumnWidth

Nastaví šířku všech sloupců v obrazových bodech [LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) v seznamu s více sloupci (vytvořeného LBS_MULTICOLUMN stylem).

```cpp
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Parametry

*cxWidth*<br/>
Určuje šířku všech sloupců v obrazových bodech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

## <a name="clistboxsetcursel"></a><a name="setcursel"></a>CListBox::SetCurSel

Vybere řetězec a v případě potřeby jej posune do zobrazení.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parametry

*nVyberte*<br/>
Určuje index řetězce, který má být vybrán na základě nuly. Pokud *nSelect* je -1, je seznam nastaven tak, aby neměl žádný výběr.

### <a name="return-value"></a>Návratová hodnota

LB_ERR pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Když je vybrán nový řetězec, seznam odstraní zvýraznění z dříve vybraného řetězce.

Tuto člennou funkci používejte pouze u seznamů s jedním výběrem.

Chcete-li nastavit nebo odebrat výběr v seznamu s více násobným výběrem, použijte [CListBox::SetSel](#setsel).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

## <a name="clistboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CListBox::Nastavitvodorovný rozsah

Nastaví šířku v obrazových bodech, o kterou lze seznam posouvat vodorovně.

```cpp
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Parametry

*cxRozsah*<br/>
Určuje počet obrazových bodů, o které lze seznam posouvat vodorovně.

### <a name="remarks"></a>Poznámky

Pokud je velikost seznamu menší než tato hodnota, vodorovný posuvník bude vodorovně posouvat položky v seznamu. Pokud je seznam stejně velký nebo větší než tato hodnota, vodorovný posuvník je skrytý.

Chcete-li odpovědět `SetHorizontalExtent`na volání , musí být seznam definován [stylem WS_HSCROLL.](../../mfc/reference/styles-used-by-mfc.md#window-styles)

Tato členská funkce není užitečná pro seznamy se více sloupci. Pro seznamy se více `SetColumnWidth` sloupci volejte členovou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

## <a name="clistboxsetitemdata"></a><a name="setitemdata"></a>CListBox::SetItemData

Nastaví hodnotu přidruženou k zadané položce v seznamu.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky.

*dwItemData*<br/>
Určuje hodnotu, která má být přidružena k položce.

### <a name="return-value"></a>Návratová hodnota

LB_ERR pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

## <a name="clistboxsetitemdataptr"></a><a name="setitemdataptr"></a>CListBox::SetItemDataPtr

Nastaví 32bitovou hodnotu přidruženou k zadané položce v seznamu jako zadaný ukazatel ( **void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky.

*Pdata*<br/>
Určuje ukazatel, který má být přidružen k položce.

### <a name="return-value"></a>Návratová hodnota

LB_ERR pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tento ukazatel zůstává platný po dobu životnosti seznamu, i když relativní pozice položky v seznamu může změnit jako položky jsou přidány nebo odebrány. Proto index položky v poli můžete změnit, ale ukazatel zůstává spolehlivý.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

## <a name="clistboxsetitemheight"></a><a name="setitemheight"></a>CListBox::SetItemHeight

Nastaví výšku položek v seznamu.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky v seznamu. Tento parametr se používá pouze v případě, že seznam obsahuje LBS_OWNERDRAWVARIABLE styl; v opačném případě by měla být nastavena na 0.

*cyItemHeight*<br/>
Určuje výšku položky v obrazových bodech.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud je index nebo výška neplatná.

### <a name="remarks"></a>Poznámky

Pokud seznam obsahuje [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, tato funkce nastaví výšku položky určené *nIndex*. V opačném případě tato funkce nastaví výšku všech položek v seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

## <a name="clistboxsetlocale"></a><a name="setlocale"></a>CListBox::SetLocale

Nastaví identifikátor národního prostředí pro tento seznam.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parametry

*nNewLocale*<br/>
Nová hodnota identifikátoru národního prostředí (LCID), která má být nastavena pro seznam.

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnota identifikátoru národního prostředí (LCID) pro tento seznam.

### <a name="remarks"></a>Poznámky

Pokud `SetLocale` není volána, výchozí národní prostředí je získán ze systému. Toto výchozí národní prostředí systému lze upravit pomocí regionální (nebo mezinárodní) aplikace Ovládacích panelů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

## <a name="clistboxsetsel"></a><a name="setsel"></a>CListBox::SetSel

Vybere řetězec v seznamu s více násobným výběrem.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje nulový index řetězce, který má být nastaven. Pokud -1, výběr je přidán nebo odebrán ze všech řetězců, v závislosti na hodnotě *bSelect*.

*bVybrat*<br/>
Určuje způsob nastavení výběru. Pokud *je bSelect* TRUE, řetězec je vybrán a zvýrazněn; pokud nepravda, zvýraznění je odebráno a řetězec již není vybrán. Zadaný řetězec je vybrán a ve výchozím nastavení zvýrazněn.

### <a name="return-value"></a>Návratová hodnota

LB_ERR pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tuto členská funkci používejte pouze se seznamy s více výběry.

Chcete-li vybrat položku ze seznamu s jedním výběrem, použijte [CListBox::SetCurSel](#setcursel).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

## <a name="clistboxsettabstops"></a><a name="settabstops"></a>CListBox::SetTabstops

Nastaví pozice zastavovacího místa v seznamu.

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Zarážky tabulátoru jsou nastaveny na každé jednotky dialogového okna *cxEachStop.* Viz *rgTabStops* pro popis jednotky dialogu.

*nTabStops*<br/>
Určuje počet zarážek tabulátoru, které mají být v seznamu.

*rgTabStops*<br/>
Odkazuje na prvníčlen pole celá čísla obsahující pozice zarážky v dialogových jednotkách. Jednotka dialogu je vodorovná nebo svislá vzdálenost. Jedna vodorovná jednotka dialogu se rovná jedné čtvrtině aktuální jednotky základní šířky dialogu a jedna svislá jednotka dialogu se rovná jedné osmině aktuální jednotky základní výšky dialogu. Základní jednotky dialogu se počítají na základě výšky a šířky aktuálního systémového písma. Funkce `GetDialogBaseUnits` Systému Windows vrátí aktuální základní jednotky dialogového okna v obrazových bodech. Zarážky tabulátoru musí být seřazeny ve vzestupném pořadí; zadní karty nejsou povoleny.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byly nastaveny všechny karty; jinak 0.

### <a name="remarks"></a>Poznámky

Chcete-li nastavit zarážky tabulátoru na výchozí velikost 2 jednotek dialogu, zavolejte bezparametrovou verzi této členské funkce. Chcete-li nastavit zarážky tabulátoru na jinou velikost než 2, zavolejte verzi s argumentem *cxEachStop.*

Chcete-li nastavit zarážky tabulátoru na pole velikostí, použijte verzi s argumenty *rgTabStops* a *nTabStops.* Pro každou hodnotu v *rgTabStops*bude nastavena zarážka tabulátoru až do počtu určeného *nTabStops*.

Chcete-li odpovědět na `SetTabStops` volání členské funkce, musí být seznam vytvořen s [LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

## <a name="clistboxsettopindex"></a><a name="settopindex"></a>CListBox::SettopIndex

Zajišťuje, že je viditelná určitá položka seznamu.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky seznamu.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud je úspěšná, nebo LB_ERR pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Systém posouvá seznam, dokud se v horní části seznamu nezobrazí položka určená *parametrem nIndex* nebo dokud nebude dosaženo maximálního rozsahu posouvání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

## <a name="clistboxvkeytoitem"></a><a name="vkeytoitem"></a>CListBox::VKeyToItem

Volat rámci při nadřazené okno seznamu obdrží zprávu WM_VKEYTOITEM ze seznamu.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nKlíč*<br/>
Kód virtuálního klíče klávesy, kterou uživatel stiskl. Seznam standardních virtuálních kódů klíčů naleznete v tématu Winuser.h

*nIndex*<br/>
Aktuální pozice stříšky seznamu.

### <a name="return-value"></a>Návratová hodnota

Vrátí - 2 pro žádnou další akci, - 1 pro výchozí akci nebo nezáporné číslo pro určení indexu položky seznamu, na kterém má být pro stisknutí klávesy provedení výchozí akce.

### <a name="remarks"></a>Poznámky

Zpráva WM_VKEYTOITEM je odeslána seznamem, když obdrží zprávu WM_KEYDOWN, ale pouze v případě, že seznam splňuje obě následující požadavky:

- Má [nastavený LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl.

- Má alespoň jednu položku.

Nikdy byste neměli volat tuto funkci sami. Přepsat tuto funkci poskytnout vlastní zpracování zpráv klávesnice.

Je nutné vrátit hodnotu sdělit rámci, jaké akce přepsání provedl. Vrácená hodnota - 2 označuje, že aplikace zpracovala všechny aspekty výběru položky a nevyžaduje žádnou další akci v seznamu. Před návratem - 2, můžete nastavit výběr nebo přesunout stříška nebo obojí. Chcete-li nastavit výběr, použijte [SetCurSel](#setcursel) nebo [SetSel](#setsel). Chcete-li přesunout stříšku, použijte [SetCaretIndex](#setcaretindex).

Vrácená hodnota - 1 označuje, že seznam by měl provést výchozí akci v reakci na stisknutí klávesy. Výchozí implementace vrátí - 1.

Vrácená hodnota 0 nebo vyšší určuje index položky v seznamu a označuje, že seznam by měl provést výchozí akci pro stisknutí klávesy na dané položce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[Třída CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic – třída](../../mfc/reference/cstatic-class.md)
