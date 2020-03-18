---
title: CListBox – – třída
description: Popis třídy CListBox – knihovny MFC a jejích členských funkcí.
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
ms.openlocfilehash: 5c3337641dcfc720a5f9fbccf5bb0614e97c3b54
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420335"
---
# <a name="clistbox-class"></a>CListBox – – třída

Poskytuje funkce seznamu systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CListBox : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CListBox –:: CListBox –](#clistbox)|Vytvoří objekt `CListBox`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CListBox –:: AddString](#addstring)|Přidá řetězec do pole se seznamem.|
|[CListBox –:: CharToItem](#chartoitem)|Přepište, abyste poskytovali vlastní zpracování WM_CHAR pro seznamy, které nemají řetězce.|
|[CListBox –:: CompareItem](#compareitem)|Volá se rozhraním, aby se určila pozice nové položky v poli seznamu seřazeného vlastníka.|
|[CListBox –:: Create](#create)|Vytvoří seznam Windows a připojí ho k objektu `CListBox`.|
|[CListBox –::D eleteItem](#deleteitem)|Volá se rozhraním, když uživatel odstraní položku ze seznamu vykresleného vlastníkem.|
|[CListBox –::D eleteString](#deletestring)|Odstraní řetězec z pole seznamu.|
|[CListBox –::D IR](#dir)|Přidá do seznamu názvy souborů, jednotky nebo obojí z aktuálního adresáře.|
|[CListBox –::D rawItem](#drawitem)|Volá se rozhraním, když se změní vizuální aspekt seznamu vykreslování vlastníka.|
|[CListBox –:: FindString](#findstring)|Vyhledá řetězec v poli se seznamem.|
|[CListBox –:: FindStringExact](#findstringexact)|Najde první řetězec seznamu – pole, který odpovídá zadanému řetězci.|
|[CListBox –:: GetAnchorIndex](#getanchorindex)|Načte index aktuální položky kotvy založený na nule v seznamu.|
|[CListBox –:: GetCaretIndex](#getcaretindex)|Určuje index položky, která má obdélník výběru v seznamu vícenásobného výběru.|
|[CListBox –:: GetCount](#getcount)|Vrátí počet řetězců v poli se seznamem.|
|[CListBox –::](#getcursel)|Vrátí index aktuálně vybraného řetězce v seznamu s nulovým základem.|
|[CListBox –:: GetHorizontalExtent](#gethorizontalextent)|Vrátí šířku v pixelech, kterou může být seznam zobrazen vodorovně.|
|[CListBox –:: GetItemData](#getitemdata)|Vrátí hodnotu přidruženou k položce se seznamem.|
|[CListBox –:: GetItemDataPtr](#getitemdataptr)|Vrátí ukazatel na položku rozevíracího seznamu.|
|[CListBox –:: GetItemHeight](#getitemheight)|Určuje výšku položek v poli se seznamem.|
|[CListBox –:: GetItemRect](#getitemrect)|Vrátí ohraničující obdélník položky seznamu, jak je aktuálně zobrazen.|
|[CListBox –:: GetListBoxInfo](#getlistboxinfo)|Načte počet položek na sloupec.|
|[CListBox –:: getLocal](#getlocale)|Načte identifikátor národního prostředí pro pole seznamu.|
|[CListBox –:: GetSel](#getsel)|Vrátí stav výběru položky v poli se seznamem.|
|[CListBox –:: GetSelCount](#getselcount)|Vrátí počet aktuálně vybraných řetězců v seznamu vícenásobného výběru.|
|[CListBox –:: GetSelItems](#getselitems)|Vrátí indexy aktuálně vybraných řetězců v seznamu.|
|[CListBox –:: GetText](#gettext)|Zkopíruje položku seznamu se seznamem do vyrovnávací paměti.|
|[CListBox –:: GetTextLen](#gettextlen)|Vrátí délku položky pole seznamu v bajtech.|
|[CListBox –:: GetTopIndex](#gettopindex)|Vrátí index prvního viditelného řetězce v seznamu.|
|[CListBox –:: InitStorage](#initstorage)|Předem přidělí bloky paměti pro položky seznamu a řetězce.|
|[CListBox –:: InsertString](#insertstring)|Vloží řetězec do konkrétního umístění v seznamu.|
|[CListBox –:: ItemFromPoint](#itemfrompoint)|Vrátí index položky rozevíracího seznamu nejbližšího bodu.|
|[CListBox –:: MeasureItem](#measureitem)|Volá se rozhraním, když se vytvoří seznam pro vykreslení vlastníka, který určí rozměry seznamu.|
|[CListBox –:: ResetContent](#resetcontent)|Vymaže všechny položky ze seznamu.|
|[CListBox –:: SelectString](#selectstring)|Vyhledá a vybere řetězec v seznamu s jedním výběrem.|
|[CListBox –:: SelItemRange](#selitemrange)|Vybere nebo odškrtne rozsah řetězců v seznamu vícenásobného výběru.|
|[CListBox –:: SetAnchorIndex](#setanchorindex)|Nastaví kotvu do pole se seznamem vícenásobného výběru, aby se začaly rozšířit výběr.|
|[CListBox –:: SetCaretIndex](#setcaretindex)|Nastaví v poli se seznamem vícenásobného výběru rámeček fokusu na položku na zadaném indexu.|
|[CListBox –:: SetColumnWidth](#setcolumnwidth)|Nastaví šířku sloupce seznamu s více sloupci.|
|[CListBox –:: SetCurSel](#setcursel)|Vybere řetězec seznamu se seznamem.|
|[CListBox –:: SetHorizontalExtent](#sethorizontalextent)|Nastaví šířku v pixelech, kterou může být seznam zobrazen vodorovně.|
|[CListBox –:: SetItemData](#setitemdata)|Nastaví hodnotu přidruženou k položce seznamu.|
|[CListBox –:: SetItemDataPtr](#setitemdataptr)|Nastaví ukazatel na položku rozevíracího seznamu.|
|[CListBox –:: SetItemHeight](#setitemheight)|Nastaví výšku položek v poli se seznamem.|
|[CListBox –:: SetLocale –](#setlocale)|Nastaví identifikátor národního prostředí pro seznam.|
|[CListBox –:: SetSel](#setsel)|Vybere nebo odškrtne položku seznamu v seznamu vícenásobného výběru.|
|[CListBox –:: SetTabStops](#settabstops)|Nastaví pozice zarážky tabulátoru v seznamu.|
|[CListBox –:: SetTopIndex](#settopindex)|Nastaví index založený na nule prvního viditelného řetězce v seznamu.|
|[CListBox –:: VKeyToItem](#vkeytoitem)|Přepište k poskytnutí vlastního WM_KEYDOWN manipulace se seznamy se sadou stylů LBS_WANTKEYBOARDINPUT.|

## <a name="remarks"></a>Poznámky

V seznamu se zobrazí seznam položek, jako jsou například názvy souborů, které může uživatel zobrazit a vybrat.

V poli se seznamem s jedním výběrem může uživatel vybrat pouze jednu položku. V poli se seznamem vícenásobného výběru lze vybrat rozsah položek. Když uživatel vybere položku, zvýrazní se a pole se seznamem pošle zprávu s oznámením do nadřazeného okna.

Můžete vytvořit seznam buď ze šablony dialogového okna, nebo přímo v kódu. Chcete-li vytvořit přímo, Sestavte objekt `CListBox` a potom zavolejte funkci [vytvořit](#create) členskou funkci pro vytvoření ovládacího prvku seznamu Windows a připojte ho k objektu `CListBox`. Chcete-li použít seznam v šabloně dialogového okna, deklarujte proměnnou pole seznamu ve třídě dialogového okna a pak použijte `DDX_Control` ve `DoDataExchange` funkce třídy dialogového okna pro připojení členské proměnné k ovládacímu prvku. (to se provádí automaticky při přidání proměnné ovládacího prvku do vaší třídy dialogového okna.)

Konstrukce může být proces jednoho kroku ve třídě odvozené z `CListBox`. Napište konstruktor pro odvozenou třídu a zavolejte `Create` z konstruktoru.

Chcete-li zpracovat oznamovací zprávy systému Windows odesílané seznamem do své nadřazené položky (obvykle třída odvozená z [CDialog](../../mfc/reference/cdialog-class.md)), přidejte položku mapování zpráv a členskou funkci obslužné rutiny zpráv do nadřazené třídy pro každou zprávu.

Každá položka mapování zpráv má následující podobu:

`ON_Notification( id, memberFxn )`

kde `id` Určuje ID podřízeného okna ovládacího prvku seznamu, který odesílá oznámení a `memberFxn` je název nadřazené členské funkce, kterou jste napsali pro zpracování oznámení.

Prototyp funkce nadřazeného objektu je následující:

`afx_msg void memberFxn( );`

Následuje seznam možných položek map zpráv a popis případů, ve kterých by se odesílaly do nadřazeného objektu:

- ON_LBN_DBLCLK uživatel dvakrát klikne na řetězec v seznamu. Tuto zprávu oznámení pošle jenom seznam, který má styl [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

- ON_LBN_ERRSPACE seznamu nelze přidělit dostatek paměti pro splnění požadavku.

- ON_LBN_KILLFOCUS rozevírací seznam ztratí fokus vstupu.

- ON_LBN_SELCANCEL se zruší výběr aktuálního seznamu. Tato zpráva se odešle jenom v případě, že má seznam LBS_NOTIFY styl.

- ON_LBN_SELCHANGE výběr v poli se seznamem se změnil. Toto oznámení není odesláno, pokud je změněn výběr pomocí členské funkce [CListBox –:: SetCurSel](#setcursel) . Toto oznámení se vztahuje pouze na seznam, který má styl LBS_NOTIFY. Zpráva s oznámením LBN_SELCHANGE je odeslána pro seznam vícenásobného výběru vždy, když uživatel stiskne klávesu šipka, a to i v případě, že se výběr nemění.

- ON_LBN_SETFOCUS rozevíracího seznamu přijímá vstupní fokus.

- ON_WM_CHARTOITEM seznamu pro vykreslování vlastníka, který nemá žádné řetězce, obdrží zprávu WM_CHAR.

- ON_WM_VKEYTOITEM seznamu s LBS_WANTKEYBOARDINPUT stylu obdrží zprávu WM_KEYDOWN.

Vytvoříte-li objekt `CListBox` v dialogovém okně (prostřednictvím prostředku dialogového okna), je objekt `CListBox` automaticky zničen, když uživatel zavře dialogové okno.

Vytvoříte-li objekt `CListBox` v rámci okna, bude pravděpodobně nutné zničit objekt `CListBox`. Vytvoříte-li objekt `CListBox` v zásobníku, bude automaticky zničen. Vytvoříte-li objekt `CListBox` na haldě pomocí **nové** funkce, je nutné volat metodu **Delete** u objektu, aby jej bylo možné zničit, když uživatel zavře nadřazené okno.

Pokud přidělíte jakoukoli paměť v objektu `CListBox`, přepište destruktoru `CListBox`, aby se odstranilo přidělení.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="addstring"></a>CListBox –:: AddString

Přidá řetězec do pole se seznamem.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
Odkazuje na řetězec zakončený hodnotou null, který má být přidán.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule do řetězce v poli se seznamem. Návratová hodnota je LB_ERR, pokud dojde k chybě; Návratová hodnota je LB_ERRSPACE, pokud není k dispozici dostatek místa pro uložení nového řetězce.

### <a name="remarks"></a>Poznámky

Pokud se pole seznamu nevytvořilo se stylem [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , přidá se na konec seznamu řetězec. V opačném případě je řetězec vložen do seznamu a seznam je seřazen. Pokud byl seznam vytvořen se stylem LBS_SORT, ale nikoli stylem [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , rozhraní seřadí seznam podle jednoho nebo více volání členské funkce `CompareItem`.

Pomocí [InsertString](#insertstring) vložte řetězec do konkrétního umístění v rámci seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

##  <a name="chartoitem"></a>CListBox –:: CharToItem

Volá se rozhraním, když nadřazené okno seznamu obdrží zprávu WM_CHARTOITEM ze seznamu.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nKey*<br/>
Kód ANSI znaku, který uživatel zadal.

*nIndex*<br/>
Aktuální pozice blikajícího kurzoru seznamu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu-1 nebo-2 pro žádnou další akci nebo nezáporné číslo pro určení indexu položky seznamu, na které má být provedena výchozí akce pro klávesovou zkratku. Výchozí implementace vrátí hodnotu-1.

### <a name="remarks"></a>Poznámky

Zpráva WM_CHARTOITEM se pošle seznamem, když obdrží zprávu WM_CHAR, ale jenom v případě, že seznam splňuje všechna tato kritéria:

- Je seznam pro vykreslování vlastníka.

- Nemá sadu stylů [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

- Má alespoň jednu položku.

Tuto funkci byste nikdy neměli volat sami. Tuto funkci můžete přepsat tak, aby poskytovala vlastní zpracování zpráv klávesnice.

V přepsání je nutné vrátit hodnotu, abyste informovali, jakou akci jste provedli. Návratová hodnota-1 nebo-2 znamená, že jste pomohli všechny aspekty výběru položky a nevyžadují žádnou další akci seznamu. Před vrácením – 1 nebo-2 můžete nastavit výběr nebo přesunout blikající kurzor nebo obojí. Chcete-li nastavit výběr, použijte [SetCurSel](#setcursel) nebo [SetSel](#setsel). Chcete-li přesunout blikající kurzor, použijte [SetCaretIndex](#setcaretindex).

Návratová hodnota 0 nebo vyšší určuje index položky v seznamu a označuje, že pole seznam by mělo pro klávesu s příslušnou položkou provést výchozí akci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

##  <a name="clistbox"></a>CListBox –:: CListBox –

Vytvoří objekt `CListBox`.

```
CListBox();
```

### <a name="remarks"></a>Poznámky

Objekt `CListBox` vytvoříte ve dvou krocích. Nejdřív zavolejte konstruktor `ClistBox` a potom zavolejte `Create`, která inicializuje seznam Windows a připojí ho k `CListBox`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

##  <a name="compareitem"></a>CListBox –:: CompareItem

Volá se rozhraním, aby se určila relativní pozice nové položky v setříděném seznamu vykreslování vlastníka.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parametry

*lpCompareItemStruct*<br/>
Dlouhý ukazatel na strukturu `COMPAREITEMSTRUCT`.

### <a name="return-value"></a>Návratová hodnota

Označuje relativní pozici dvou položek popsaných ve struktuře [COMPAREITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-compareitemstruct) . Může to být kterákoli z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|-1|Položka 1 se řadí před položkou 2.|
|0|Položka 1 a položka 2 mají stejný druh.|
|1|Položka 1 se řadí za položku 2.|

Popis `COMPAREITEMSTRUCT` struktury naleznete v tématu [CWnd:: OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádnou akci. Pokud vytvoříte seznam pro vykreslení vlastníka se stylem LBS_SORT, je nutné přepsat tuto členskou funkci, aby bylo možné v rámci řazení nových položek přidaných do seznamu do něj pomáhat rozhraní.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

##  <a name="create"></a>CListBox –:: Create

Vytvoří seznam Windows a připojí ho k objektu `CListBox`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl pole seznamu. Použití libovolné kombinace [stylů seznamů](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) na poli

*OBD*<br/>
Určuje velikost a umístění seznamu. Může být buď objekt `CRect`, nebo struktura `RECT`.

*pParentWnd*<br/>
Určuje nadřazené okno seznamu (obvykle objekt `CDialog`). Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku pole seznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Objekt `CListBox` vytvoříte ve dvou krocích. Nejprve zavolejte konstruktor a potom zavolejte `Create`, který inicializuje seznam Windows a připojí ho k objektu `CListBox`.

Když se `Create` spustí, Windows pošle zprávy [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)a [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) do ovládacího prvku seznam.

Tyto zprávy jsou ve výchozím nastavení zpracovávány členskými funkcemi [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [Create](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)a [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) v základní třídě `CWnd`. Chcete-li zvětšit výchozí zpracování zprávy, odvodit třídu z `CListBox`, přidat do nové třídy mapu zprávy a přepsat předchozí funkce členů obslužné rutiny zpráv. Přepsat `OnCreate`, například k provedení potřebné inicializace pro novou třídu.

Použijte následující [Styly okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) pro ovládací prvek seznamu.

- WS_CHILD vždycky

- WS_VISIBLE obvykle

- WS_DISABLED zřídka

- WS_VSCROLL pro přidání svislého posuvníku

- WS_HSCROLL pro přidání vodorovného posuvníku

- WS_GROUP seskupení ovládacích prvků

- WS_TABSTOP pro povolení procházení klávesy s tímto ovládacím prvkem

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

##  <a name="deleteitem"></a>CListBox –::D eleteItem

Volá se rozhraním, když uživatel odstraní položku z objektu `CListBox`ho vykreslování vlastníka nebo zničí pole seznamu.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDeleteItemStruct*<br/>
Dlouhý ukazatel na strukturu [DELETEITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) systému Windows, která obsahuje informace o odstraněné položce.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádnou akci. Potlačením této funkce překreslete podle potřeby seznam vykresleného vlastníka.

Popis `DELETEITEMSTRUCT` struktury naleznete v tématu [CWnd:: OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

##  <a name="deletestring"></a>CListBox –::D eleteString

Odstraní položku v umístění *nIndex* ze seznamu.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule řetězce, který se má odstranit.

### <a name="return-value"></a>Návratová hodnota

Počet řetězců zbývajících v seznamu. Návratová hodnota je LB_ERR, pokud *nIndex* určuje index větší než počet položek v seznamu.

### <a name="remarks"></a>Poznámky

Všechny položky, které následují *nIndex* , se teď přesunou o jednu pozici dolů. Například pokud pole se seznamem obsahuje dvě položky, odstranění první položky způsobí, že zbývající položka bude nyní na první pozici. *nIndex*= 0 pro položku na první pozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

##  <a name="dir"></a>CListBox –::D IR

Přidá do seznamu seznam názvů souborů, jednotek nebo obojího.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parametry

*ATTR*<br/>
Může být libovolná kombinace hodnot **výčtu** popsaná v `CFile::GetStatu`[s](../../mfc/reference/cfile-class.md#getstatus)nebo libovolná kombinace následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|0x0000|Soubor je možné číst nebo do něj zapisovat.|
|0x0001|Soubor lze číst, ale nikoli zapisovat do.|
|0x0002|Soubor je skrytý a v seznamu adresářů se nezobrazí.|
|0x0004|Soubor je systémový soubor.|
|0x0010|Název určený parametrem *lpszWildCard* Určuje adresář.|
|0x0020|Soubor byl archivován.|
|0x4000|Zahrňte všechny jednotky, které odpovídají názvu určenému parametrem *lpszWildCard*.|
|0x8000|Příznak Exclusive. Pokud je nastaven příznak Exclusive, jsou uvedeny pouze soubory zadaného typu. V opačném případě jsou soubory zadaného typu uvedeny vedle "normálního" souboru.|

*lpszWildCard*<br/>
Odkazuje na řetězec specifikace souboru. Řetězec může obsahovat zástupné znaky (například *.\*).

### <a name="return-value"></a>Návratová hodnota

Index založený na nule posledního názvu souboru přidaného do seznamu. Návratová hodnota je LB_ERR, pokud dojde k chybě; Návratová hodnota je LB_ERRSPACE, pokud není k dispozici dostatek místa pro uložení nových řetězců.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

##  <a name="drawitem"></a>CListBox –::D rawItem

Volá se rozhraním, když se změní vizuální aspekt seznamu vykreslování vlastníka.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhý ukazatel na strukturu [DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) , která obsahuje informace o typu požadované kresby.

### <a name="remarks"></a>Poznámky

`itemAction` a `itemState` členů struktury `DRAWITEMSTRUCT` definují akci kreslení, která má být provedena.

Ve výchozím nastavení tato členská funkce neprovede žádnou akci. Přepište tuto členskou funkci pro implementaci vykreslování pro objekt `CListBox` vykreslený vlastníkem. Aplikace by měla obnovit všechny objekty GDI (Graphic Device Interface) vybrané pro kontext zobrazení zadaný v *lpDrawItemStruct* před ukončením této členské funkce.

Popis `DRAWITEMSTRUCT` struktury naleznete v tématu [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

##  <a name="findstring"></a>CListBox –:: FindString

Vyhledá první řetězec v seznamu, který obsahuje zadanou předponu, aniž by bylo nutné měnit výběr seznamu.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Obsahuje index položky vycházející od nuly před první položkou, která má být prohledána. Když hledání dosáhne dolní části seznamu, pokračuje v horní části seznamu zpátky na položku zadanou v *nStartAfter*. Pokud je *nStartAfter* -1, bude prohledán celý seznam od začátku.

*lpszItem*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje předponu, kterou chcete vyhledat. Hledání je nezávislé na velikosti písmen, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index se shodnou položkou založený na nule nebo LB_ERR, pokud hledání nebylo úspěšné.

### <a name="remarks"></a>Poznámky

Použijte členskou funkci [SelectString](#selectstring) pro hledání a výběr řetězce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

##  <a name="findstringexact"></a>CListBox –:: FindStringExact

Najde první řetězec seznamu, který odpovídá řetězci zadanému v *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parametry

*nIndexStart*<br/>
Určuje index položky vycházející od nuly před první položkou, která se má prohledat. Když hledání dosáhne dolní části seznamu, pokračuje v horní části seznamu zpátky na položku zadanou v *nIndexStart*. Pokud je *nIndexStart* -1, bude prohledán celý seznam od začátku.

*lpszFind*<br/>
Odkazuje na řetězec zakončený hodnotou null, který má být hledán. Tento řetězec může obsahovat úplný název souboru včetně rozšíření. Hledání nerozlišuje velká a malá písmena, takže řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index pro shodnou položku nebo LB_ERR, pokud hledání nebylo úspěšné.

### <a name="remarks"></a>Poznámky

Pokud byl seznam vytvořen pomocí stylu vykresleného vlastníkem, ale bez stylu [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , `FindStringExact` členská funkce se pokusí porovnat hodnotu doubleword s hodnotou *lpszFind*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

##  <a name="getanchorindex"></a>CListBox –:: GetAnchorIndex

Načte index aktuální položky kotvy založený na nule v poli se seznamem.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index aktuální položky ukotvení, pokud je úspěšný; jinak LB_ERR.

### <a name="remarks"></a>Poznámky

V poli se seznamem vícenásobného výběru je položka ukotvení první nebo poslední položka v bloku souvislých vybraných položek.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox –:: SetAnchorIndex](#setanchorindex).

##  <a name="getcaretindex"></a>CListBox –:: GetCaretIndex

Určuje index položky, která má obdélník výběru v seznamu vícenásobného výběru.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule položky, která má v seznamu pole obdélník výběru. Pokud je seznam jedním výběrem, návratová hodnota je index položky, která je vybrána, pokud existuje.

### <a name="remarks"></a>Poznámky

Položka může nebo nemusí být vybraná.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox –:: SetCaretIndex](#setcaretindex).

##  <a name="getcount"></a>CListBox –:: GetCount

Načte počet položek v poli se seznamem.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v poli se seznamem, nebo LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Počet vrácených položek je větší než hodnota indexu poslední položky (index je založený na nule).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

##  <a name="getcursel"></a>CListBox –::

Načte index založený na nule aktuálně vybrané položky, pokud existuje, v seznamu s jedním výběrem.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule aktuálně vybrané položky, pokud se jedná o seznam s jedním výběrem. Je LB_ERR, pokud není aktuálně vybrána žádná položka.

V poli se seznamem vícenásobného výběru index položky, která má fokus.

### <a name="remarks"></a>Poznámky

Nevolejte `GetCurSel` pro seznam vícenásobného výběru. Místo toho použijte [CListBox –:: GetSelItems](#getselitems) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

##  <a name="gethorizontalextent"></a>CListBox –:: GetHorizontalExtent

Načte ze seznamu šířku v pixelech, o kterou se dá vodorovně posouvat.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Návratová hodnota

Posunutí šířky pole seznamu (v pixelech)

### <a name="remarks"></a>Poznámky

To platí pouze v případě, že je v seznamu vodorovný posuvník.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

##  <a name="getitemdata"></a>CListBox –:: GetItemData

Načte hodnotu doubleword zadanou aplikací přidruženou k zadané položce seznamu.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Hodnota přidružená k položce nebo LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Hodnota doubleword byla parametrem *dwItemData* volání [SetItemData](#setitemdata) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

##  <a name="getitemdataptr"></a>CListBox –:: GetItemDataPtr

Načte hodnotu 32-bit poskytnutou aplikací spojenou s určenou položkou seznamu jako ukazatel (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Načte ukazatel nebo-1, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

##  <a name="getitemheight"></a>CListBox –:: GetItemHeight

Určuje výšku položek v poli se seznamem.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule položky v seznamu. Tento parametr se používá pouze v případě, že má seznam LBS_OWNERDRAWVARIABLE styl. v opačném případě by měl být nastaven na hodnotu 0.

### <a name="return-value"></a>Návratová hodnota

Výška položek v poli se seznamem (v pixelech). Pokud má pole se seznamem styl [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , návratová hodnota je výška položky určené parametrem *nIndex*. Pokud dojde k chybě, návratová hodnota je LB_ERR.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

##  <a name="getitemrect"></a>CListBox –:: GetItemRect

Načte rozměry obdélníku, který je ohraničen položkou seznamu, protože je aktuálně zobrazen v okně seznamu.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index položky vycházející z nuly.

*lpRect*<br/>
Určuje dlouhý ukazatel na [strukturu Rect](/windows/win32/api/windef/ns-windef-rect) , která přijímá souřadnice klienta seznamu.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

##  <a name="getlistboxinfo"></a>CListBox –:: GetListBoxInfo

Načte počet položek na sloupec.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek na sloupec objektu `CListBox`

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo) zprávy, jak je popsáno v Windows SDK.

##  <a name="getlocale"></a>CListBox –:: getLocal

Načte národní prostředí používané seznamem.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota identifikátoru národního prostředí (LCID) pro řetězce v poli se seznamem.

### <a name="remarks"></a>Poznámky

Národní prostředí se používá například k určení pořadí řazení řetězců v seřazeném seznamu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox –:: setlocale](#setlocale).

##  <a name="getsel"></a>CListBox –:: GetSel

Načte stav výběru položky.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index položky vycházející z nuly.

### <a name="return-value"></a>Návratová hodnota

Kladné číslo, pokud je vybrána zadaná položka; v opačném případě je 0. Návratová hodnota je LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tato členská funkce pracuje se seznamem s jedním i vícenásobným výběrem.

Chcete-li načíst index položky aktuálně vybraného seznamu, použijte [CListBox –::](#getcursel)proitem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

##  <a name="getselcount"></a>CListBox –:: GetSelCount

Načte celkový počet vybraných položek v seznamu vícenásobného výběru.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet vybraných položek v poli se seznamem. Pokud je seznam jedním výběrem, návratová hodnota je LB_ERR.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox –:: GetSelItems](#getselitems).

##  <a name="getselitems"></a>CListBox –:: GetSelItems

Vyplní vyrovnávací paměť polem celých čísel, která určují čísla položek vybraných položek v seznamu vícenásobného výběru.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Parametry

*nMaxItems*<br/>
Určuje maximální počet vybraných položek, jejichž čísla položek se mají umístit do vyrovnávací paměti.

*rgIndex*<br/>
Určuje ukazatel na vyrovnávací paměť, která je dostatečně velká pro počet celých čísel určených parametrem *nMaxItems*.

### <a name="return-value"></a>Návratová hodnota

Skutečný počet položek umístěných ve vyrovnávací paměti. Pokud je seznam jedním výběrem, návratová hodnota je `LB_ERR`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

##  <a name="gettext"></a>CListBox –:: GetText

Načte řetězec z pole seznamu.

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
Určuje index založený na nule řetězce, který se má načíst.

*lpszBuffer*<br/>
Odkazuje na vyrovnávací paměť, která přijímá řetězec. Vyrovnávací paměť musí mít dostatek místa pro řetězec a ukončující znak null. Velikost řetězce lze určit před časem voláním členské funkce `GetTextLen`.

*rString*<br/>
Odkaz na objekt `CString`.

### <a name="return-value"></a>Návratová hodnota

Délka (v bajtech) řetězce s výjimkou ukončujícího znaku null. Pokud *nIndex* neurčuje platný index, návratová hodnota je LB_ERR.

### <a name="remarks"></a>Poznámky

Druhá forma této členské funkce vyplní objekt `CString` textem řetězce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

##  <a name="gettextlen"></a>CListBox –:: GetTextLen

Získá délku řetězce v položce seznamu.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule řetězce.

### <a name="return-value"></a>Návratová hodnota

Délka řetězce ve znacích, s výjimkou ukončujícího znaku null. Pokud *nIndex* neurčuje platný index, návratová hodnota je LB_ERR.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox –:: GetText](#gettext).

##  <a name="gettopindex"></a>CListBox –:: GetTopIndex

Načte index první viditelné položky v seznamu na základě nuly.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule první viditelné položky v seznamu v případě úspěchu LB_ERR jinak.

### <a name="remarks"></a>Poznámky

Zpočátku je položka 0 v horní části seznamu, ale v případě, že je pole se seznamem posunuto, může být v horní části zobrazená jiná položka.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

##  <a name="initstorage"></a>CListBox –:: InitStorage

Přidělí paměť pro ukládání položek seznamu box.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Parametry

*nItems*<br/>
Určuje počet položek, které se mají přidat.

*nBytes*<br/>
Určuje množství paměti (v bajtech), které se má přidělit pro řetězce položek.

### <a name="return-value"></a>Návratová hodnota

Pokud je to úspěšné, maximální počet položek, které může seznam ukládat, než bude potřeba přerozdělení paměti, jinak LB_ERRSPACE, což znamená, že k dispozici není dostatek paměti.

### <a name="remarks"></a>Poznámky

Před přidáním velkého počtu položek do `CListBox`volejte tuto funkci.

Tato funkce pomáhá zrychlit inicializaci seznamů polí, které mají velký počet položek (více než 100). Předem alokuje zadanou velikost paměti, aby následné funkce [AddString](#addstring), [InsertString](#insertstring)a [dir](#dir) vybraly nejkratší možnou dobu. Můžete použít odhady pro parametry. Pokud dojde k přeodhadování, je přiděleno několik dalších paměťových paměti; Pokud se podceňují skutečnou, použije se pro položky, které překračují předběžně přidělené množství, normální přidělení.

Jenom Windows 95/98: parametr *nItems* je omezený na 16 bitů hodnot. To znamená, že pole se seznamem nemůžou obsahovat více než 32 767 položek. I když je počet položek omezený, celková velikost položek v poli seznamu je omezená pouze pomocí dostupné paměti.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

##  <a name="insertstring"></a>CListBox –:: InsertString

Vloží řetězec do pole se seznamem.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule pozice pro vložení řetězce. Pokud je tento parametr-1, řetězec je přidán na konec seznamu.

*lpszItem*<br/>
Odkazuje na řetězec zakončený hodnotou null, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule pozice, do které byl řetězec vložen. Návratová hodnota je LB_ERR, pokud dojde k chybě; Návratová hodnota je LB_ERRSPACE, pokud není k dispozici dostatek místa pro uložení nového řetězce.

### <a name="remarks"></a>Poznámky

Na rozdíl od členské funkce [AddString](#addstring) `InsertString` nezpůsobí řazení seznamu se stylem [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

##  <a name="itemfrompoint"></a>CListBox –:: ItemFromPoint

Určuje položku seznamu, která je nejbližší bodu určenému v *PT*.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Parametry

*bodů*<br/>
Bod, pro který chcete najít nejbližší položku určenou vzhledem k levému hornímu rohu klientské oblasti seznamu.

*bOutside*<br/>
Odkaz na proměnnou BOOL, která bude nastavena na hodnotu TRUE, pokud je *bod PT* mimo klientskou oblast seznamu, false, pokud je *bod PT* uvnitř klientské oblasti seznamu.

### <a name="return-value"></a>Návratová hodnota

Index nejbližší položky v bodě určeném v *PT*

### <a name="remarks"></a>Poznámky

Pomocí této funkce lze určit, která položka rozevíracího seznamu se přesune na ukazatel myši.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox –:: SetAnchorIndex](#setanchorindex).

##  <a name="measureitem"></a>CListBox –:: MeasureItem

Volá se rozhraním, když se vytvoří seznam se stylem vykreslování vlastníka.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Dlouhý ukazatel na strukturu [MEASUREITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádnou akci. Tuto členskou funkci přepište a naplňte `MEASUREITEMSTRUCT` struktury a informujte okna o dimenzích seznamu. Pokud je pole se seznamem vytvořeno pomocí stylu [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , rozhraní volá tuto členskou funkci pro každou položku v seznamu. V opačném případě se tento člen volá jenom jednou.

Další informace o použití stylu [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) v poli se seznamem pro vykreslení vlastníka vytvořeném pomocí členské funkce `SubclassDlgItem` `CWnd`naleznete v diskuzi v [technickém poznámce 14](../../mfc/tn014-custom-controls.md).

Popis `MEASUREITEMSTRUCT` struktury naleznete v tématu [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

##  <a name="resetcontent"></a>CListBox –:: ResetContent

Odebere všechny položky ze seznamu.

```
void ResetContent();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

##  <a name="selectstring"></a>CListBox –:: SelectString

Vyhledá položku rozevíracího seznamu, která odpovídá zadanému řetězci, a pokud je nalezena odpovídající položka, vybere položku.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Obsahuje index položky vycházející od nuly před první položkou, která má být prohledána. Když hledání dosáhne dolní části seznamu, pokračuje v horní části seznamu zpátky na položku zadanou v *nStartAfter*. Pokud je *nStartAfter* -1, bude prohledán celý seznam od začátku.

*lpszItem*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje předponu, kterou chcete vyhledat. Hledání je nezávislé na velikosti písmen, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index vybrané položky, pokud bylo hledání úspěšné. Pokud hledání nebylo úspěšné, vrácená hodnota je LB_ERR a aktuální výběr se nemění.

### <a name="remarks"></a>Poznámky

V případě potřeby se seznam posuňte, pokud je to nutné, aby se vybraná položka zobrazila.

Tuto členskou funkci nelze použít se seznamem, který má styl [LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

Položka je vybrána pouze v případě, že počáteční znaky (z počátečního bodu) odpovídají znakům v řetězci určeném parametrem *lpszItem*.

K vyhledání řetězce bez výběru položky použijte členskou funkci `FindString`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

##  <a name="selitemrange"></a>CListBox –:: SelItemRange

Vybere více po sobě jdoucích položek v seznamu vícenásobného výběru.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Parametry

*bSelect*<br/>
Určuje způsob nastavení výběru. Pokud má *bSelect* hodnotu true, je vybraný a zvýrazněný řetězec; Pokud je hodnota FALSE, zvýraznění se odebere a řetězec už není vybraný.

*nFirstItem*<br/>
Určuje index založený na nule první položky, která se má nastavit.

*nLastItem*<br/>
Určuje index založený na nule poslední položky, která se má nastavit.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci použijte pouze v seznamech s vícenásobným výběrem. Pokud potřebujete vybrat pouze jednu položku v seznamu vícenásobného výběru – to znamená, že pokud je *nFirstItem* rovno *nLastItem* , zavolejte místo toho členskou funkci [SetSel](#setsel) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

##  <a name="setanchorindex"></a>CListBox –:: SetAnchorIndex

Nastaví kotvu do pole se seznamem vícenásobného výběru, aby se začaly rozšířit výběr.

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule položky rozevíracího seznamu, která bude ukotvena.

### <a name="remarks"></a>Poznámky

V poli se seznamem vícenásobného výběru je položka ukotvení první nebo poslední položka v bloku souvislých vybraných položek.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

##  <a name="setcaretindex"></a>CListBox –:: SetCaretIndex

Nastaví v poli se seznamem vícenásobného výběru rámeček fokusu na položku na zadaném indexu.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index položky vycházející z nuly, který získá obdélník výběru v poli se seznamem.

*bScroll*<br/>
Pokud je tato hodnota 0, přesune se položka, dokud není plně viditelná. Pokud není tato hodnota 0, bude položka posunuta, dokud není alespoň částečně viditelná.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Pokud položka není viditelná, přejde do zobrazení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

##  <a name="setcolumnwidth"></a>CListBox –:: SetColumnWidth

Nastaví šířku v pixelech všech sloupců v seznamu s více sloupci (vytvořené pomocí stylu [LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) ).

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Parametry

*cxWidth*<br/>
Určuje šířku všech sloupců v pixelech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

##  <a name="setcursel"></a>CListBox –:: SetCurSel

Vybere řetězec a v případě potřeby ho posune do zobrazení.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parametry

*nVyberte*<br/>
Určuje index založený na nule řetězce, který má být vybrán. Pokud je *nVyberte* -1, pole se seznamem je nastaveno na možnost bez výběru.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Po výběru nového řetězce se v seznamu odebere zvýraznění z dříve vybraného řetězce.

Tuto členskou funkci lze použít pouze v seznamu polí s jedním výběrem.

Chcete-li nastavit nebo odebrat výběr v poli se seznamem vícenásobného výběru, použijte [CListBox –:: SetSel](#setsel).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

##  <a name="sethorizontalextent"></a>CListBox –:: SetHorizontalExtent

Nastaví šířku v pixelech, o kterou může být seznam zobrazen vodorovně.

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Parametry

*cxExtent*<br/>
Určuje počet pixelů, o které se může seznam vodorovně posunout.

### <a name="remarks"></a>Poznámky

Pokud je velikost pole seznamu menší než tato hodnota, vodorovný posuvník bude vodorovně posouvat položky v poli se seznamem. Pokud je seznam velký nebo větší než tato hodnota, je vodorovný posuvník skrytý.

Chcete-li reagovat na volání `SetHorizontalExtent`, pole seznamu musí být definováno se stylem [WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles) .

Tato členská funkce není užitečná pro pole se seznamem s více sloupci. Pro pole se seznamem s více sloupci Zavolejte členskou funkci `SetColumnWidth`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

##  <a name="setitemdata"></a>CListBox –:: SetItemData

Nastaví hodnotu přidruženou k zadané položce v seznamu.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index položky vycházející z nuly.

*dwItemData*<br/>
Určuje hodnotu, která má být přidružena k položce.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

##  <a name="setitemdataptr"></a>CListBox –:: SetItemDataPtr

Nastaví hodnotu 32, která je přidružená k zadané položce v seznamu, aby byla zadaným ukazatelem ( **void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index položky vycházející z nuly.

*pData*<br/>
Určuje ukazatel, který se má přidružit k položce.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tento ukazatel zůstává platný po dobu života seznamu, a to i v případě, že se přidávají nebo odebírají položky relativní pozice položky v seznamu. Proto se index položky v poli může změnit, ale ukazatel zůstane spolehlivý.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

##  <a name="setitemheight"></a>CListBox –:: SetItemHeight

Nastaví výšku položek v poli se seznamem.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule položky v seznamu. Tento parametr se používá pouze v případě, že má seznam LBS_OWNERDRAWVARIABLE styl. v opačném případě by měl být nastaven na hodnotu 0.

*cyItemHeight*<br/>
Určuje výšku položky v pixelech.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud je index nebo výška neplatný.

### <a name="remarks"></a>Poznámky

Pokud má pole se seznamem styl [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , tato funkce nastaví výšku položky určené parametrem *nIndex*. V opačném případě tato funkce nastaví výšku všech položek v seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

##  <a name="setlocale"></a>CListBox –:: SetLocale –

Nastaví identifikátor národního prostředí pro tento seznam.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parametry

*nNewLocale*<br/>
Nová hodnota identifikátoru národního prostředí (LCID), která se má nastavit pro pole seznamu.

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnota identifikátoru národního prostředí (LCID) pro tento seznam.

### <a name="remarks"></a>Poznámky

Pokud není volána `SetLocale`, je ze systému získáno výchozí národní prostředí. Toto výchozí národní prostředí systému lze upravit pomocí regionální (nebo mezinárodní) aplikace v Ovládacích panelech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

##  <a name="setsel"></a>CListBox –:: SetSel

Vybere řetězec v seznamu vícenásobného výběru.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index založený na nule řetězce, který má být nastaven. Pokud-1, výběr se přidá nebo odebere ze všech řetězců v závislosti na hodnotě *bSelect*.

*bSelect*<br/>
Určuje způsob nastavení výběru. Pokud má *bSelect* hodnotu true, je vybraný a zvýrazněný řetězec; Pokud je hodnota FALSE, zvýraznění se odebere a řetězec už není vybraný. Zadaný řetězec je vybraný a ve výchozím nastavení zvýrazněný.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tuto členskou funkci použijte pouze v seznamech s vícenásobným výběrem.

Chcete-li vybrat položku ze seznamu jednoho výběru, použijte [CListBox –:: SetCurSel](#setcursel).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

##  <a name="settabstops"></a>CListBox –:: SetTabStops

Nastaví pozice zarážky tabulátoru v seznamu.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Zarážky tabulátoru se nastavují v každé jednotce dialogového okna *cxEachStop* . Popis jednotky dialogového okna naleznete v tématu *rgTabStops* .

*nTabStops*<br/>
Určuje počet zarážek tabulátorů v seznamu.

*rgTabStops*<br/>
Odkazuje na prvního člena pole celých čísel obsahující pozice zarážky tabulátorem v jednotkách dialogových oken. Jednotka dialogového okna je vodorovná nebo svislá vzdálenost. Jedna vodorovná jednotka dialogového okna se rovná jedné čtvrté jednotky základní šířky a jedna svislá jednotka dialogového okna je rovna jedné 8 aktuální jednotky základní výšky dialogového okna. Základní jednotky dialogového okna jsou vypočítány na základě výšky a šířky aktuálního systémového písma. Funkce `GetDialogBaseUnits` systému Windows vrátí aktuální základní jednotky dialogu v pixelech. Zarážky tabulátoru musí být seřazeny ve vzestupném pořadí; Zpětná ouška nejsou povolena.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byly nastaveny všechny karty; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pro nastavení zarážky tabulátoru na výchozí velikost 2 jednotky dialogového okna volejte verzi bez parametrů této členské funkce. Chcete-li nastavit zarážky tabulátoru na jinou velikost než 2, zavolejte verzi pomocí argumentu *cxEachStop* .

K nastavení zarážek tabulátoru na pole velikostí použijte verzi s argumenty *rgTabStops* a *nTabStops* . Pro každou hodnotu v *rgTabStops*se nastaví zarážka tabulátoru až do čísla zadaného parametrem *nTabStops*.

Chcete-li reagovat na volání členské funkce `SetTabStops`, musí být seznam vytvořen se stylem [LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

##  <a name="settopindex"></a>CListBox –:: SetTopIndex

Zajistí, že se zobrazí konkrétní položka seznamu.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index položky seznamu na základě nuly.

### <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu nebo LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Systém posune seznam do pole, dokud se nezobrazí položka zadaná parametrem *nIndex* v horní části seznamu nebo bylo dosaženo maximálního rozsahu posouvání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

##  <a name="vkeytoitem"></a>CListBox –:: VKeyToItem

Volá se rozhraním, když nadřazené okno seznamu obdrží zprávu WM_VKEYTOITEM ze seznamu.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nKey*<br/>
Kód virtuálního klíče, který uživatel stiskne. Seznam standardních kódů virtuálních klíčů naleznete v tématu Winuser. h.

*nIndex*<br/>
Aktuální pozice blikajícího kurzoru seznamu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu-2 pro žádnou další akci,-1 pro výchozí akci nebo nezáporné číslo pro určení indexu položky seznamu, na které má být provedena výchozí akce pro klávesovou zkratku.

### <a name="remarks"></a>Poznámky

WM_VKEYTOITEM zpráva je odeslána seznamem, když obdrží zprávu WM_KEYDOWN, ale pouze v případě, že seznam splňuje obě následující:

- Má sadu stylů [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

- Má alespoň jednu položku.

Tuto funkci byste nikdy neměli volat sami. Tuto funkci můžete přepsat tak, aby poskytovala vlastní zpracování zpráv klávesnice.

Je nutné vrátit hodnotu a sdělit rozhraní, jaké akci vaše přepsání provedla. Návratová hodnota-2 znamená, že aplikace zpracovává všechny aspekty výběru položky a nevyžaduje žádné další akce v seznamu. Před vrácením – 2 můžete nastavit výběr nebo přesunout blikající kurzor nebo obojí. Chcete-li nastavit výběr, použijte [SetCurSel](#setcursel) nebo [SetSel](#setsel). Chcete-li přesunout blikající kurzor, použijte [SetCaretIndex](#setcaretindex).

Návratová hodnota-1 označuje, že pole seznamu by mělo provést výchozí akci v reakci na klávesovou zkratku. Výchozí implementace vrátí hodnotu-1.

Návratová hodnota 0 nebo vyšší určuje index položky v seznamu a označuje, že pole seznam by mělo pro klávesu s příslušnou položkou provést výchozí akci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Viz také

[CTRLTEST Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox – třída](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic – třída](../../mfc/reference/cstatic-class.md)
