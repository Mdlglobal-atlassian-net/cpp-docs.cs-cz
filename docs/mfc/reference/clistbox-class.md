---
title: Clistbox – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: ad9f945a91a96c40afe614240a847a028ba5b5d9
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178613"
---
# <a name="clistbox-class"></a>Clistbox – třída

Poskytuje funkce pro pole se seznamem Windows.

## <a name="syntax"></a>Syntaxe

```
class CListBox : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|Vytvoří `CListBox` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CListBox::AddString](#addstring)|Přidá řetězec do pole se seznamem.|
|[CListBox::CharToItem](#chartoitem)|Přepsání nastavení za účelem zadejte vlastní WM_CHAR zpracování pro seznamy vykreslené vlastníkem, které nemají řetězce.|
|[CListBox::CompareItem](#compareitem)|Volá se rozhraním lze určit pozici nové položky v seznamu seřazené vykreslené vlastníkem.|
|[CListBox::Create](#create)|Vytvoří pole se seznamem Windows a připojí ho k `CListBox` objektu.|
|[CListBox::DeleteItem](#deleteitem)|Volá se rozhraním, když uživatel odstraní položku ze seznamu vykreslené vlastníkem.|
|[CListBox::DeleteString](#deletestring)|Řetězec se odstraní ze seznamu.|
|[CListBox::Dir](#dir)|Přidá do seznamu názvy souborů, jednotek nebo obě z aktuálního adresáře.|
|[CListBox::DrawItem](#drawitem)|Volá se rozhraním při úpravě vizuálního aspektu uživatelem nakreslený seznam se změní.|
|[CListBox::FindString](#findstring)|Vyhledá řetězec v seznamu.|
|[CListBox::FindStringExact](#findstringexact)|Najde první řetězec pole se seznamem, který se shoduje se zadaným řetězcem.|
|[CListBox::GetAnchorIndex](#getanchorindex)|Načte z nuly vycházející index aktuální ukotvení položky v seznamu.|
|[CListBox::GetCaretIndex](#getcaretindex)|Určuje index položky, který má rámečku fokusu v seznamu více výběrů.|
|[CListBox::GetCount](#getcount)|Vrátí počet řetězců v seznamu.|
|[CListBox::GetCurSel](#getcursel)|Vrátí index aktuálně vybrané řetězec založený na nule v seznamu.|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Vrátí šířku v pixelech, že je vodorovně posuvný seznam.|
|[CListBox::GetItemData](#getitemdata)|Vrátí hodnotu 32-bit přidružené položky pole se seznamem.|
|[CListBox::GetItemDataPtr](#getitemdataptr)|Vrací ukazatel na pole se seznamem položek.|
|[CListBox::GetItemHeight](#getitemheight)|Určuje výšku položky v seznamu.|
|[CListBox::GetItemRect](#getitemrect)|Vrací ohraničující obdélník položky pole se seznamem, který se nyní zobrazí.|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Získá počet položek na sloupec.|
|[CListBox::GetLocale](#getlocale)|Načte identifikátor národního prostředí pro pole se seznamem.|
|[CListBox::GetSel](#getsel)|Vrátí stav výběru položky pole se seznamem.|
|[CListBox::GetSelCount](#getselcount)|Vrátí počet aktuálně vybraného v seznamu s vícenásobným výběrem pole řetězců.|
|[CListBox::GetSelItems](#getselitems)|Vrátí indexy řetězce aktuálně vybraného v seznamu.|
|[CListBox::GetText](#gettext)|Zkopíruje položky pole se seznamem do vyrovnávací paměti.|
|[CListBox::GetTextLen](#gettextlen)|Vrátí délku v bajtech položky pole se seznamem.|
|[CListBox::GetTopIndex](#gettopindex)|Vrátí index první viditelné řetězec v seznamu.|
|[CListBox::InitStorage](#initstorage)|Preallocates bloky paměti pro seznam položek pole a řetězce.|
|[CListBox::InsertString](#insertstring)|Vloží řetězec v konkrétním umístění v seznamu.|
|[CListBox::ItemFromPoint](#itemfrompoint)|Vrátí index položky pole se seznamem nejbližší bod.|
|[CListBox::MeasureItem](#measureitem)|Volá se rozhraním při vytvoření seznamu vykreslené vlastníkem. k určení rozměry pole se seznamem.|
|[CListBox::ResetContent](#resetcontent)|Vymaže všechny položky ze seznamu.|
|[CListBox::SelectString](#selectstring)|Vyhledá a vybere řetězec v seznamu jedním výběrem.|
|[CListBox::SelItemRange](#selitemrange)|Vybrat nebo zrušit výběr rozsahu řetězců v poli seznamu s vícenásobným výběrem.|
|[CListBox::SetAnchorIndex](#setanchorindex)|Nastaví ukotvení zahájíte rozšířený výběr v seznamu více výběrů.|
|[CListBox::SetCaretIndex](#setcaretindex)|Nastaví obdélník na položky v zadaném indexu v seznamu více výběrů.|
|[CListBox::SetColumnWidth](#setcolumnwidth)|Nastavuje šířku sloupce vícesloupcový seznam.|
|[CListBox::SetCurSel](#setcursel)|Vybere pole se seznamem řetězec.|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Nastavuje šířku v pixelech, že je vodorovně posuvný seznam.|
|[CListBox::SetItemData](#setitemdata)|Nastaví hodnotu 32-bit přidružené položky pole se seznamem.|
|[CListBox::SetItemDataPtr](#setitemdataptr)|Nastaví ukazatel na pole se seznamem položek.|
|[CListBox::SetItemHeight](#setitemheight)|Nastaví výšku položky v seznamu.|
|[CListBox::SetLocale](#setlocale)|Nastaví identifikátor národního prostředí pro pole se seznamem.|
|[CListBox::SetSel](#setsel)|Vybere nebo zruší výběr pole se seznamem položek v seznamu více výběrů.|
|[CListBox::SetTabStops](#settabstops)|Nastaví konec tabulátoru pozic v seznamu.|
|[CListBox::SetTopIndex](#settopindex)|Nastaví index založený na nule první řetězec, který je viditelný v seznamu.|
|[CListBox::VKeyToItem](#vkeytoitem)|Přepsání nastavení za účelem poskytnout vlastní WM_KEYDOWN zpracování pro pole se seznamem se sadou LBS_WANTKEYBOARDINPUT style.|

## <a name="remarks"></a>Poznámky

Seznamu se zobrazí seznam položek, jako jsou názvy souborů, které uživatel může zobrazit a vybrat.

V seznamu jedním výběrem může uživatel vybrat pouze jednu položku. V seznamu více výběrů je možné vybrat rozsah položek. Když uživatel vybere položku, je zvýrazněn a pole se seznamem odešle upozornění do nadřazeného okna.

Seznam můžete vytvořit z šablony dialogového okna nebo přímo v kódu. Pokud chcete vytvořit přímo, vytvořit `CListBox` objekt a potom voláním [vytvořit](#create) členskou funkci pro vytvoření ovládacího prvku pole se seznamem Windows a připojte ji k `CListBox` objektu. Použijte seznam pole v šabloně dialogu, deklaraci proměnné pole se seznamem ve vaší třídy dialogového okna a potom použijte `DDX_Control` ve třídě dialog box `DoDataExchange` funkce pro připojení členské proměnné do ovládacího prvku. (je to pro vás automaticky při přidání proměnnou ovládacího prvku do vaší třídy dialogového okna.)

Konstrukce může být jednoduchý proces ve třídě odvozené z `CListBox`. Zápis konstruktoru pro odvozenou třídu a volání `Create` z v rámci konstruktoru.

Pokud chcete zpracovávat Windows oznamující zprávy odeslal seznamu k nadřazené úloze (obvykle třída odvozená z [CDialog](../../mfc/reference/cdialog-class.md)), přidat mapu zpráv položku a obslužná rutina zprávy členskou funkci na nadřazené třídu pro každou zprávu.

Každá položka mapování zpráv má následující podobu:

`ON_Notification( id, memberFxn )`

kde `id` určuje Identifikátor podřízené okno ovládacího prvku pole se seznamem odesílání oznámení a `memberFxn` je název nadřazené členské funkce mají napsané tak, aby oznámení.

Prototyp funkce nadřazeného objektu je následujícím způsobem:

`afx_msg void memberFxn( );`

Tady je seznam možných položky mapování zpráv a popis případy, ve kterých se mají být odeslány do nadřazené:

- ON_LBN_DBLCLK uživatel dvakrát klikne řetězec v seznamu. Pouze seznam, který má [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl pošle tuto zprávu oznámení.

- Pole se seznamem ON_LBN_ERRSPACE nemůže přidělit dostatek paměti k uspokojení požadavku.

- ON_LBN_KILLFOCUS pole se seznamem je ztráta vstupního fokusu.

- ON_LBN_SELCANCEL aktuální výběr pole se seznamem se zrušila. Tato zpráva se odesílají jenom při seznamu má LBS_NOTIFY styl.

- ON_LBN_SELCHANGE výběru v rozevíracím seznamu se změnila. Toto oznámení se odesílá, pokud se změní výběr [CListBox::SetCurSel](#setcursel) členskou funkci. Toto oznámení se vztahuje pouze na seznamu, který má LBS_NOTIFY styl. Zprávy oznámení LBN_SELCHANGE přijde pro vícenásobný výběr seznamu vždy, když uživatel stiskne klávesu se šipkou i v případě, že výběr nezmění.

- Pole se seznamem ON_LBN_SETFOCUS přijímá vstupní fokus.

- ON_WM_CHARTOITEM pole se seznamem vykreslené vlastníkem, který nemá žádné závazky přijme zprávu WM_CHAR.

- Pole se seznamem A ON_WM_VKEYTOITEM stylem LBS_WANTKEYBOARDINPUT obdrží je zpráva WM_KEYDOWN.

Pokud vytvoříte `CListBox` objekt v rámci dialogového okna (prostřednictvím prostředku dialogového okna), `CListBox` objekt je zničen automaticky, když uživatel zavře dialogové okno.

Pokud jste vytvořili `CListBox` objekt v rámci časového období, možná budete muset zničit `CListBox` objektu. Pokud jste vytvořili `CListBox` objekt v zásobníku, je automaticky zničen. Pokud jste vytvořili `CListBox` objektů na haldě pomocí **nové** funkce, je nutné volat **odstranit** na objekt, který chcete zničit se při zavření nadřazeného okna.

Pokud přidělení paměti v `CListBox` objektu, přepsat `CListBox` destruktor k uvolnění přidělení.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="addstring"></a>  CListBox::AddString

Přidá řetězec do pole se seznamem.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
Odkazuje na řetězec zakončený hodnotou null, který se má přidat.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule na řetězec v poli seznamu. Vrácená hodnota je LB_ERR, pokud dojde k chybě; Vrácená hodnota je LB_ERRSPACE, pokud je k dispozici pro uložení nového řetězce není dostatek místa.

### <a name="remarks"></a>Poznámky

Pokud pole se seznamem nebylo vytvořeno pomocí [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, řetězec je přidán na konec seznamu. V opačném případě řetězec je vložen do seznamu a seznam je seřazen. Pokud byl vytvořen pole se seznamem se stylem LBS_SORT, ale ne [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, rozhraní Seřadí seznam jednoho nebo více volání `CompareItem` členskou funkci.

Použití [InsertString](#insertstring) vložit řetězec do určitého umístění v rámci pole se seznamem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

##  <a name="chartoitem"></a>  CListBox::CharToItem

Volá se rozhraním, když pole se seznamem nadřazené okno obdrží zprávu WM_CHARTOITEM ze seznamu.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nKey*<br/>
ANSI kód znaku uživatel zadal.

*nIndex*<br/>
Aktuální pozici blikajícího kurzoru pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu - 1 nebo - 2 pro žádná další akce nebo nezáporné číslo indexu pole se seznamem položek na základě které chcete provést výchozí akci pro stisknutí klávesy. Výchozí implementace vrací - 1.

### <a name="remarks"></a>Poznámky

Pole se seznamem odesílají zprávy WM_CHARTOITEM při přijetí zprávy WM_CHAR, ale pouze v případě, že pole se seznamem splňuje všechna tato kritéria:

- Je pole se seznamem vykreslené vlastníkem.

- Nemá [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu sady.

- Má alespoň jednu položku.

Měli byste nikdy volat tuto funkci sami. Přepsání této funkce můžete poskytnout vlastní vlastní zpracování zpráv týkajících se klávesnice.

V přepsání musí vracet hodnotu k informování rozhraní framework, jaké akce jste provedli. Návratová hodnota - 1 nebo - 2 označuje zpracovává všechny aspekty pak vyberete požadovanou položku a vyžaduje žádná další akce podle pole se seznamem. Před vrácením – 1 nebo - 2, vám může nastavit výběr nebo přesunutí blikající kurzor nebo obojí. Pokud chcete nastavit výběr, použijte [setcursel –](#setcursel) nebo [SetSel](#setsel). Přesune blikající kurzor, použijte [SetCaretIndex](#setcaretindex).

Vrácená hodnota 0 nebo větší Určuje index položky v seznamu a označuje, že pole se seznamem by měl provedení výchozí akce pro stisknutí klávesy na danou položku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

##  <a name="clistbox"></a>  CListBox::CListBox

Vytvoří `CListBox` objektu.

```
CListBox();
```

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CListBox` objektu ve dvou krocích. Nejprve volat konstruktor `ClistBox` a následně zavolat `Create`, která inicializuje pole se seznamem Windows a připojí ho k `CListBox`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

##  <a name="compareitem"></a>  CListBox::CompareItem

Volá se rozhraním pro určení relativní pozice nové položky v seznamu seřazené vykreslené vlastníkem.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parametry

*lpCompareItemStruct*<br/>
Dlouhým ukazatelem na `COMPAREITEMSTRUCT` struktury.

### <a name="return-value"></a>Návratová hodnota

Označuje relativní polohu dvě položky podle [compareitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagcompareitemstruct) struktury. To může být libovolná z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|-1|Položka 1 se řadí před položkou 2.|
|0|Položka 1 a položka 2 seřadí hodnoty stejné.|
|1|Položka 1 se řadí po položce 2.|

Zobrazit [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) popis `COMPAREITEMSTRUCT` struktury.

### <a name="remarks"></a>Poznámky

Tato členská funkce ve výchozím nastavení nemá žádný účinek. Pokud vytvoříte do uživatelem nakreslený seznam pole se stylem LBS_SORT, je nutné přepsat tato členská funkce, které pomáhají rozhraní framework při řazení nové položky přidané do seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

##  <a name="create"></a>  CListBox::Create

Vytvoří pole se seznamem Windows a připojí ho k `CListBox` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl pole se seznamem. Použít libovolnou kombinaci [styly seznamů](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) do pole.

*Rect*<br/>
Určuje velikost pole se seznamem a umístění. Může být buď `CRect` objektu nebo `RECT` struktury.

*pParentWnd*<br/>
Určuje pole se seznamem nadřazené okno (obvykle `CDialog` objekt). Nesmí být NULL.

*nID*<br/>
Určuje ID ovládacího prvku pole se seznamem

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CListBox` objektu ve dvou krocích. Nejprve volat konstruktor a následně zavolat `Create`, která inicializuje pole se seznamem Windows a připojí ho k `CListBox` objektu.

Když `Create` spustí, odešle Windows [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), a [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) zprávy do ovládacího prvku pole se seznamem.

Tyto zprávy jsou zpracovány ve výchozím nastavení [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), a [ongetminmaxinfo –](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) členské funkce v `CWnd` základní třídy. Pokud chcete rozšířit výchozí zpracování zpráv, odvoďte třídu z `CListBox`, přidání mapy zpráv do nové třídy a přepsat předchozí členské funkce obslužná rutina zprávy. Přepsat `OnCreate`, například k provedení potřebných inicializace pro novou třídu.

Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) do ovládacího prvku pole se seznamem.

- WS_CHILD vždy

- WS_VISIBLE obvykle

- WS_DISABLED jen zřídka

- WS_VSCROLL k přidání svislý posuvník

- WS_HSCROLL k přidání vodorovný posuvník

- WS_GROUP k seskupování ovládacích prvků

- WS_TABSTOP k povolení procházení tabulátorem na tento ovládací prvek

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

##  <a name="deleteitem"></a>  CListBox::DeleteItem

Volá se rozhraním, když uživatel odstraní položku ze vykreslené vlastníkem `CListBox` objektu nebo odstraní pole se seznamem.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDeleteItemStruct*<br/>
Dlouhým ukazatelem na Windows [deleteitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagdeleteitemstruct) strukturu, která obsahuje informace o odstraněné položky.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce nemá žádný účinek. Tuto funkci pro překreslení do seznamu pole vykreslené vlastníkem. podle potřeby přepište.

Zobrazit [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) popis `DELETEITEMSTRUCT` struktury.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

##  <a name="deletestring"></a>  CListBox::DeleteString

Odstraní položku na pozici *nIndex* ze seznamu.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule řetězec, který má být odstraněna.

### <a name="return-value"></a>Návratová hodnota

Počet zbývajících v seznamu řetězců. Vrácená hodnota je LB_ERR Pokud *nIndex* Určuje index větší než počet položek v seznamu.

### <a name="remarks"></a>Poznámky

Všechny položky následující *nIndex* teď přejít o jednu pozici dolů. Například pokud seznam obsahuje dvě položky, odstranění první položky způsobí zbývající položky, která má být nyní na první pozici. *nIndex*= 0 pro položku na první pozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

##  <a name="dir"></a>  CListBox::Dir

Přidá seznam názvů souborů, disků nebo obojí do seznamu.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parametry

*attr*<br/>
Může být libovolná kombinace **výčtu** podle hodnoty `CFile::GetStatu` [s](../../mfc/reference/cfile-class.md#getstatus), nebo libovolnou kombinaci následujícího:

|Hodnota|Význam|
|-----------|-------------|
|0x0000|Soubor může číst nebo zapisovat do.|
|0x0001|Soubor můžete číst z ale nezapíše se do.|
|0x0002|Soubor je skrytá a se nezobrazí v seznamu adresářů.|
|0x0004|Soubor je systémový soubor.|
|0x0010|Název zadaný v *lpszWildCard* Určuje adresář.|
|0x0020|Soubor byl archivován.|
|0x4000|Zahrnout všechny jednotky, které odpovídají názvu určeného *lpszWildCard*.|
|0x8000|Příznak Exclusive. Pokud je nastavený příznak exclusive, jsou uvedeny pouze soubory zadaného typu. Jinak jsou kromě "normální" soubory uvedené soubory zadaného typu.|

*lpszWildCard*<br/>
Odkazuje na řetězec specifikace souboru. Řetězec může obsahovat zástupné znaky (například *.\*).

### <a name="return-value"></a>Návratová hodnota

Index založený na nule poslední název souboru přidán do seznamu. Vrácená hodnota je LB_ERR, pokud dojde k chybě; Vrácená hodnota je LB_ERRSPACE, pokud je k dispozici pro uložení nového řetězce není dostatek místa.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

##  <a name="drawitem"></a>  CListBox::DrawItem

Volá se rozhraním při úpravě vizuálního aspektu uživatelem nakreslený seznam se změní.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhým ukazatelem na [drawitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) strukturu, která obsahuje informace o typu kreslení vyžaduje.

### <a name="remarks"></a>Poznámky

`itemAction` a `itemState` členy `DRAWITEMSTRUCT` struktura definovat výkresu akci, která se má provést.

Tato členská funkce ve výchozím nastavení nemá žádný účinek. Přepsat tato členská funkce implementovat kreslení pro vykreslené vlastníkem `CListBox` objektu. Aplikace by měl obnovit všechny grafiky zařízení rozhraní GDI systému objekty vybrané pro zadaný kontext zobrazení v *lpDrawItemStruct* před tento člen funkce skončí.

Zobrazit [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) popis `DRAWITEMSTRUCT` struktury.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

##  <a name="findstring"></a>  CListBox::FindString

Najde první řetězec v seznamu, který obsahuje zadanou předponu beze změny seznamů výběru.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Obsahuje položku před první položky, které chcete prohledat index založený na nule. Dolní části seznamu dosáhne hledání pokračuje od horního okraje pole se seznamem zpět položku určenou na základě *nStartAfter*. Pokud *nStartAfter* se -1, je prohledána celý seznam od začátku.

*lpszItem*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje předpona, kterou chcete vyhledat. Vyhledávání je případ nezávislé, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule odpovídající položka nebo LB_ERR Pokud vyhledávání nebylo úspěšné.

### <a name="remarks"></a>Poznámky

Použití [SelectString](#selectstring) členskou funkci, jak najít a vybrat řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

##  <a name="findstringexact"></a>  CListBox::FindStringExact

Najde první řetězec pole se seznamem, který odpovídá řetězci zadanému v *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parametry

*nIndexStart*<br/>
Určuje index založený na nule položku před první položky, které chcete prohledat. Dolní části seznamu dosáhne hledání pokračuje od horního okraje pole se seznamem zpět položku určenou na základě *nIndexStart*. Pokud *nIndexStart* se -1, je prohledána celý seznam od začátku.

*lpszFind*<br/>
Odkazuje na hledaný řetězec zakončený hodnotou null. Tento řetězec může obsahovat úplný název souboru, včetně přípony. Hledání není velká a malá písmena, takže řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index odpovídající položka nebo LB_ERR Pokud vyhledávání nebylo úspěšné.

### <a name="remarks"></a>Poznámky

Pokud se pole se seznamem vytvořil stylem vykreslené vlastníkem. ale bez [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, `FindStringExact` členská funkce se pokusí porovnat hodnoty doubleword s hodnotu *lpszFind*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

##  <a name="getanchorindex"></a>  CListBox::GetAnchorIndex

Načte z nuly vycházející index aktuální ukotvení položky v seznamu.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index aktuální položky ukotvení, v případě úspěchu; jinak LB_ERR.

### <a name="remarks"></a>Poznámky

Položka ukotvení v vícenásobný výběr seznamu je první nebo poslední položku v blok souvislé vybrané položky.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox::SetAnchorIndex](#setanchorindex).

##  <a name="getcaretindex"></a>  CListBox::GetCaretIndex

Určuje index položky, který má rámečku fokusu v seznamu více výběrů.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule, který má rámečku fokusu v seznamu položku. Pokud pole se seznamem je jedním výběrem seznamu, vrácená hodnota je index položky, který je vybrán, pokud existuje.

### <a name="remarks"></a>Poznámky

Položka může nebo nemusí být vybrané.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox::SetCaretIndex](#setcaretindex).

##  <a name="getcount"></a>  CListBox::GetCount

Získá počet položek v seznamu.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v seznamu nebo LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Vrácený počet je větší než hodnota indexu na poslední položku (index je založený na nule).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

##  <a name="getcursel"></a>  CListBox::GetCurSel

Načte z nuly vycházející index aktuálně vybrané položky, pokud existuje, v seznamu jedním výběrem.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule aktuálně vybrané položky, pokud je seznam jedním výběrem. Jedná se LB_ERR, pokud je aktuálně vybrána žádná položka.

V rozevíracím seznamu s vícenásobným výběrem index položky, která má fokus.

### <a name="remarks"></a>Poznámky

Nevolejte `GetCurSel` pro vícenásobný výběr seznamu. Použití [CListBox::GetSelItems](#getselitems) místo.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

##  <a name="gethorizontalextent"></a>  CListBox::GetHorizontalExtent

Načte ze seznamu požadovanou šířku v pixelech, které jej lze seznam vodorovně posunout.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Návratová hodnota

Posuvný šířka pole seznamu, v pixelech.

### <a name="remarks"></a>Poznámky

To platí jenom v případě, že pole se seznamem má vodorovný posuvník.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

##  <a name="getitemdata"></a>  CListBox::GetItemData

Načte hodnotu poskytované aplikací doubleword přidružené položky zadaného seznamu.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje z nuly vycházející index položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

32bitová hodnota přidružené položky nebo LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Byla zadána hodnota doubleword *dwItemData* parametr [setitemdata –](#setitemdata) volání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

##  <a name="getitemdataptr"></a>  CListBox::GetItemDataPtr

Načte 32bitovou hodnotu poskytované aplikací přidružených k položce zadaný seznam jako ukazatel (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje z nuly vycházející index položky v seznamu.

### <a name="return-value"></a>Návratová hodnota

Načte ukazatel nebo -1, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

##  <a name="getitemheight"></a>  CListBox::GetItemHeight

Určuje výšku položky v seznamu.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje z nuly vycházející index položky v seznamu. Tento parametr se používá jenom v případě, že pole se seznamem má LBS_OWNERDRAWVARIABLE styl; v opačném případě je třeba nastavit na hodnotu 0.

### <a name="return-value"></a>Návratová hodnota

Výška v pixelech položek v seznamu. Pokud má pole se seznamem [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, vrácená hodnota je výška položku určenou na základě *nIndex*. Pokud dojde k chybě, vrácená hodnota je LB_ERR.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

##  <a name="getitemrect"></a>  CListBox::GetItemRect

Načte rozměry obdélníku danou položku rozsah – pole se seznamem, který se nyní zobrazí v okně pole se seznamem.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule položky.

*lprect –*<br/>
Určuje dlouhým ukazatelem na [Rect – struktura](/windows/desktop/api/windef/ns-windef-tagrect) , který přijímá pole se seznamem klienta souřadnice položky.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

##  <a name="getlistboxinfo"></a>  CListBox::GetListBoxInfo

Získá počet položek na sloupec.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek na sloupec `CListBox` objektu.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkčnost [LB_GETLISTBOXINFO](/windows/desktop/Controls/lb-getlistboxinfo) zprávu, jak je popsáno v sadě Windows SDK.

##  <a name="getlocale"></a>  CListBox::GetLocale

Načte národního prostředí používaného pole se seznamem.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota identifikátoru LCID národního prostředí pro řetězce v poli seznamu.

### <a name="remarks"></a>Poznámky

Národní prostředí, které se používá, například k určení pořadí řazení řetězců v seřazeném seznamu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox::SetLocale](#setlocale).

##  <a name="getsel"></a>  CListBox::GetSel

Načte stav výběru položky.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule položky.

### <a name="return-value"></a>Návratová hodnota

Kladné číslo, pokud zadaná položka je zaškrtnuto. v opačném případě je 0. Vrácená hodnota je LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tato členská funkce pracuje s obě pole se seznamem výběru jednoho a víc.

Pokud chcete načíst index aktuálně vybrané pole Položka, použijte [CListBox::GetCurSel](#getcursel).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

##  <a name="getselcount"></a>  CListBox::GetSelCount

Načte celkový počet vybraných položek v seznamu více výběrů.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet vybraných položek v seznamu. Pokud pole se seznamem je jedním výběrem seznamu, vrácená hodnota je LB_ERR.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox::GetSelItems](#getselitems).

##  <a name="getselitems"></a>  CListBox::GetSelItems

Pole celých čísel, které určuje položku čísla vybrané položky do seznamu s vícenásobným výběrem pole vyplní vyrovnávací paměti.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Parametry

*nMaxItems*<br/>
Určuje maximální počet vybraných položek, jejichž čísla jsou umístěny ve vyrovnávací paměti.

*rgIndex*<br/>
Určuje ukazatel dostatečně velký počet celých čísel určená vyrovnávací paměť *nMaxItems*.

### <a name="return-value"></a>Návratová hodnota

Skutečný počet položek, které jsou umístěny ve vyrovnávací paměti. Pokud pole se seznamem je jedním výběrem seznamu, vrácená hodnota je `LB_ERR`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

##  <a name="gettext"></a>  CListBox::GetText

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
Určuje index založený na nule řetězec, který se má načíst.

*lpszBuffer*<br/>
Body do vyrovnávací paměti, která přijímá řetězec. Vyrovnávací paměť musí mít dostatek místa pro řetězce a ukončujícího znaku null. Velikost řetězce můžete určit předem voláním `GetTextLen` členskou funkci.

*rString*<br/>
Odkaz na `CString` objektu.

### <a name="return-value"></a>Návratová hodnota

Délka řetězce, s výjimkou ukončujícího znaku null (v bajtech). Pokud *nIndex* neurčuje platný index, vrácená hodnota je LB_ERR.

### <a name="remarks"></a>Poznámky

Tedy o druhou podobu této členské funkce výplně `CString` objekt s text řetězce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

##  <a name="gettextlen"></a>  CListBox::GetTextLen

Získá délku řetězce v položce seznamu.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index o základu 0 řetězce.

### <a name="return-value"></a>Návratová hodnota

Délka řetězce ve znacích, s výjimkou ukončujícího znaku null. Pokud *nIndex* neurčuje platný index, vrácená hodnota je LB_ERR.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox::GetText](#gettext).

##  <a name="gettopindex"></a>  CListBox::GetTopIndex

Načte z nuly vycházející index první viditelné položky v seznamu.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Z nuly vycházející index první viditelné položky v seznamu, pokud je úspěšná, jinak LB_ERR.

### <a name="remarks"></a>Poznámky

Na začátku položka 0 je v horní části seznamu, ale pokud je pole se seznamem posunul, jiná položka může být v horní části.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

##  <a name="initstorage"></a>  CListBox::InitStorage

Přiděluje paměť pro ukládání položky pole se seznamem.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Parametry

*nItems*<br/>
Určuje počet položek, které chcete přidat.

*nBytes*<br/>
Určuje velikost paměti, v bajtech pro přidělení pro položku řetězce.

### <a name="return-value"></a>Návratová hodnota

Pokud úspěšné, maximální počet položek, které pole se seznamem můžete uložit před realokace paměti je zapotřebí, jinak LB_ERRSPACE, není to znamená, je k dispozici dostatek paměti.

### <a name="remarks"></a>Poznámky

Voláním této funkce před přidáním velký počet položek, které chcete `CListBox`.

Tato funkce pomáhá zrychlit inicializace pole se seznamem, které mají velký počet položek (více než 100). Preallocates zadaného množství paměti, takže to následné [addstring –](#addstring), [InsertString](#insertstring), a [Dir](#dir) funkce přijímají nejkratší možné době. Odhad můžete použít pro parametry. Pokud jste overestimate, je přidělen některé další paměť. Pokud jste příliš nízko, normální rozdělení se používá pro položky, které překračují předběžně přidělená velikost.

Windows 95/98 pouze: *NItems* je omezená na 16bitové hodnoty parametru. To znamená, že pole se seznamem nemůže obsahovat více než 32 767 položky. I když je počet položek, které s omezeným přístupem, celková velikost položky v seznamu je omezen pouze dostupnou paměť.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

##  <a name="insertstring"></a>  CListBox::InsertString

Řetězec se vloží do pole se seznamem.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje pozici tím řetězec vložíte index založený na nule. Pokud tento parametr hodnotu -1, řetězec je přidána na konec seznamu.

*lpszItem*<br/>
Odkazuje na řetězec zakončený hodnotou null, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Z nuly vycházející index pozice vložený řetězec. Vrácená hodnota je LB_ERR, pokud dojde k chybě; Vrácená hodnota je LB_ERRSPACE, pokud je k dispozici pro uložení nového řetězce není dostatek místa.

### <a name="remarks"></a>Poznámky

Na rozdíl od [addstring –](#addstring) členskou funkci `InsertString` nezpůsobí seznam [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, který se má seřadit.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

##  <a name="itemfrompoint"></a>  CListBox::ItemFromPoint

Určuje položky pole se seznamem nejbližší bod uvedený v *pt*.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Parametry

*PT*<br/>
Bod, pro kterou se má vyhledat nejbližší položky určen ve vztahu k levého horního rohu klientské oblasti pole se seznamem.

*bOutside*<br/>
Odkaz na proměnnou typu BOOL, která bude nastavena na hodnotu TRUE, pokud *pt* je mimo oblasti klienta nejbližší položky seznamu, FALSE v případě *pt* se nachází uvnitř oblasti klienta nejbližší položku seznamu.

### <a name="return-value"></a>Návratová hodnota

Index položky nejbližší bod uvedený v *pt*.

### <a name="remarks"></a>Poznámky

Tuto funkci můžete použít k určení, která pole se seznamem položka přesune ukazatel myši.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CListBox::SetAnchorIndex](#setanchorindex).

##  <a name="measureitem"></a>  CListBox::MeasureItem

Volá se rozhraním, když se vytvoří pole se seznamem stylem vykreslené vlastníkem.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Dlouhým ukazatelem na [measureitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagmeasureitemstruct) struktury.

### <a name="remarks"></a>Poznámky

Tato členská funkce ve výchozím nastavení nemá žádný účinek. Tato členská funkce přepsání a vyplňte `MEASUREITEMSTRUCT` struktura informovat Windows rozměry pole se seznamem. Pokud pole se seznamem se vytvoří s [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, rozhraní volá tuto funkci člena pro každou položku v seznamu. V opačném případě tento člen je volána pouze jednou.

Další informace o používání [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl do uživatelem nakreslený seznam pole vytvořené pomocí `SubclassDlgItem` členskou funkci `CWnd`, viz diskuze v [Technická poznámka 14](../../mfc/tn014-custom-controls.md).

Zobrazit [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) popis `MEASUREITEMSTRUCT` struktury.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

##  <a name="resetcontent"></a>  CListBox::ResetContent

Odebere všechny položky ze seznamu.

```
void ResetContent();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

##  <a name="selectstring"></a>  CListBox::SelectString

Hledání položky pole se seznamem, který odpovídá určitému řetězci, a pokud je nalezena odpovídající položka, vybere položku.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Obsahuje položku před první položky, které chcete prohledat index založený na nule. Dolní části seznamu dosáhne hledání pokračuje od horního okraje pole se seznamem zpět položku určenou na základě *nStartAfter*. Pokud *nStartAfter* se -1, je prohledána celý seznam od začátku.

*lpszItem*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje předpona, kterou chcete vyhledat. Vyhledávání je případ nezávislé, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index vybrané položky, pokud bylo hledání úspěšné. Pokud se vyhledávání nebylo úspěšné, vrácená hodnota je LB_ERR a se změní aktuální výběr.

### <a name="remarks"></a>Poznámky

Pole se seznamem je posunul, v případě potřeby, aby vybrané položky do zobrazení.

Tato členská funkce nemohou být součástí seznamu, který má [LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style.

Je položka vybrána pouze v případě, že jeho počáteční znaky (od počátečního bodu) odpovídat znakům v řetězci určené *lpszItem*.

Použití `FindString` členská funkce k vyhledání řetězce bez výběru položky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

##  <a name="selitemrange"></a>  CListBox::SelItemRange

Vybere více po sobě následující položky v seznamu vícenásobného výběru.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Parametry

*bSelect*<br/>
Určuje, jak nastavit výběr. Pokud *bSelect* má hodnotu TRUE, řetězec je vybraná a zvýrazní; Pokud je hodnota FALSE, zvýraznění se odebere a řetězec je už vybraná.

*nFirstItem*<br/>
Určuje index založený na nule první položka určená k nastavení.

*nLastItem*<br/>
Určuje index založený na nule poslední položky nastavení.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tuto funkci člena můžete používejte pouze s pole se seznamem vícenásobného výběru. Pokud je nutné vybrat pouze jednu položku v seznamu více výběrů – to znamená, pokud *nFirstItem* rovná *nLastItem* – volání [SetSel](#setsel) členské funkce místo.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

##  <a name="setanchorindex"></a>  CListBox::SetAnchorIndex

Nastaví ukotvení zahájíte rozšířený výběr v seznamu více výběrů.

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule, který bude ukotvení položky pole se seznamem.

### <a name="remarks"></a>Poznámky

Položka ukotvení v vícenásobný výběr seznamu je první nebo poslední položku v blok souvislé vybrané položky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

##  <a name="setcaretindex"></a>  CListBox::SetCaretIndex

Nastaví obdélník na položky v zadaném indexu v seznamu více výběrů.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule položky pro příjem rámečku fokusu v seznamu.

*bScroll*<br/>
Pokud tato hodnota je 0, položky je posunul, dokud je plně viditelný. Pokud tato hodnota je 0, položka je posunul, dokud se aspoň částečně nezobrazí.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Pokud položka není viditelná, je přechod do zobrazení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

##  <a name="setcolumnwidth"></a>  CListBox::SetColumnWidth

Nastavuje šířku v pixelech všechny sloupce ve vícesloupcovém objektu seznamu (vytvořené pomocí [LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style).

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Parametry

*cxWidth*<br/>
Určuje šířku v pixelech všechny sloupce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

##  <a name="setcursel"></a>  CListBox::SetCurSel

Vybere řetězec a posune do zobrazení, v případě potřeby.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parametry

*nVyberte*<br/>
Určuje řetězec, který má být vybrán index založený na nule. Pokud *nVyberte* se -1, pole se seznamem je nastavena na mít žádný výběr.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Když je vybraný nový řetězec, pole se seznamem Odebere zvýraznění z dříve vybrané řetězce.

Tuto funkci člena můžete používejte pouze s jedním výběrem seznamy.

Chcete-li nastavit nebo odebrat výběr v seznamu více výběrů, použijte [CListBox::SetSel](#setsel).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

##  <a name="sethorizontalextent"></a>  CListBox::SetHorizontalExtent

Nastaví šířku v pixelech, podle kterých můžete vodorovně posuvný seznam.

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Parametry

*cxExtent*<br/>
Určuje počet pixelů, podle kterých pole se seznamem lze seznam vodorovně posunout.

### <a name="remarks"></a>Poznámky

Pokud je velikost seznamu menší než tato hodnota, bude vodorovný posuvník vodorovně posouvat položky v seznamu. Pokud pole se seznamem je stejně velké nebo větší než tato hodnota, je skrytý vodorovný posuvník.

Reakce na volání `SetHorizontalExtent`, pole se seznamem musí být definována s [WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles) style.

Tato členská funkce není užitečná pro pole se seznamem vícesloupcovém objektu. U polí s vícesloupcový seznam, zavolejte `SetColumnWidth` členskou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

##  <a name="setitemdata"></a>  CListBox::SetItemData

Nastaví hodnotu 32-bit přidružené k zadané položky seznamu.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule položky.

*dwItemData*<br/>
Určuje hodnota, která má být přidružená k položce.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

##  <a name="setitemdataptr"></a>  CListBox::SetItemDataPtr

Nastaví hodnotu 32-bit přidruženou k zadané položky seznamu jako zadaný ukazatel ( **void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule položky.

*pData*<br/>
Určuje ukazatel na být přidružená k položce.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

This – ukazatel zůstane platný po celou dobu životnosti seznamu i v případě, že položky relativní pozici v rámci pole se seznamem může změnit, protože položky jsou přidány nebo odebrány. Proto můžete změnit index položky v poli, ale ukazatel zůstane spolehlivé.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

##  <a name="setitemheight"></a>  CListBox::SetItemHeight

Nastaví výšku položky v seznamu.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje z nuly vycházející index položky v seznamu. Tento parametr se používá jenom v případě, že pole se seznamem má LBS_OWNERDRAWVARIABLE styl; v opačném případě je třeba nastavit na hodnotu 0.

*cyItemHeight*<br/>
Určuje výšku v pixelech položky.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud je neplatný index nebo výšku.

### <a name="remarks"></a>Poznámky

Pokud má pole se seznamem [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, tato funkce nastaví výšku položku určenou na základě *nIndex*. V opačném případě tato funkce nastaví výšku všech položek v seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

##  <a name="setlocale"></a>  CListBox::SetLocale

Nastaví identifikátor národního prostředí pro toto pole se seznamem.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parametry

*nNewLocale*<br/>
Nová hodnota národního prostředí identifikátor (LCID) pro pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnota identifikátoru LCID národního prostředí pro toto pole se seznamem.

### <a name="remarks"></a>Poznámky

Pokud `SetLocale` nevolá výchozí národní prostředí je získané ze systému. Tento výchozí národní prostředí systému lze upravit pomocí ovládacích panelů aplikace místní (nebo mezinárodní).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

##  <a name="setsel"></a>  CListBox::SetSel

Vybere řetězec v poli seznamu s vícenásobným výběrem.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index založený na nule řetězec, který má být nastavena. Pokud hodnotu -1, výběr je přidán či odebrán z všechny řetězce, závisí na hodnotě *bSelect*.

*bSelect*<br/>
Určuje, jak nastavit výběr. Pokud *bSelect* má hodnotu TRUE, řetězec je vybraná a zvýrazní; Pokud je hodnota FALSE, zvýraznění se odebere a řetězec je už vybraná. Zadaný řetězec je vybraná a zvýrazněn ve výchozím nastavení.

### <a name="return-value"></a>Návratová hodnota

LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tuto funkci člena můžete používejte pouze s pole se seznamem vícenásobného výběru.

Chcete-li vybrat položku ze seznamu jedním výběrem, použijte [CListBox::SetCurSel](#setcursel).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

##  <a name="settabstops"></a>  CListBox::SetTabStops

Nastaví konec tabulátoru pozic v seznamu.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Zarážky nastavené v každé *cxEachStop* jednotkách dialogového okna. Zobrazit *rgTabStops* popis jednotky dialogu.

*nTabStops*<br/>
Určuje počet tabulátoru v seznamu.

*rgTabStops*<br/>
Odkazuje na první prvek pole celých čísel, který obsahuje konec tabulátoru pozic v jednotkách dialogového okna. Dialogové okno jednotka je vodorovném nebo svislém distance. 1 jednotka vodorovné dialogového okna je rovna čtvrtinu aktuální jednotku základní šířky dialogového okna a jedna jednotka na svislé dialogového okna je rovna 28 jedním z aktuální jednotky pro základní výška dialogové okno. Dialogové okno základní jednotky se vypočítávají na základě výšku a šířku aktuální systémové písmo. `GetDialogBaseUnits` Windows funkce vrátí aktuální dialogové okno základní jednotky v pixelech. Zarážky musí být seřazeny vzestupně v pořadí. nejsou povoleny zpětné karty.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byly nastavené všechny karty; jinak 0.

### <a name="remarks"></a>Poznámky

K nastavení zarážek na výchozí velikost 2 jednotky dialogu, volání bez parametrů verze tuto členskou funkci. Chcete-li nastavení zarážek na velikost než 2, zavolejte verze s *cxEachStop* argument.

K nastavení zarážek na celou řadu velikostí, použijte verzi s *rgTabStops* a *nTabStops* argumenty. Nastaví zarážku pro každou hodnotu v *rgTabStops*, až na číslo určené atributem *nTabStops*.

Reakce na volání `SetTabStops` členská funkce seznamu musí být vytvořen s [LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

##  <a name="settopindex"></a>  CListBox::SetTopIndex

Zajišťuje, že konkrétní – pole se seznamem položek je viditelná.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index založený na nule položky pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, nebo LB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Systém posune pole se seznamem do položku určenou na základě *nIndex* se zobrazí v horní části seznamu bylo dosaženo maximální posuvníku rozsahu nebo pole.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

##  <a name="vkeytoitem"></a>  CListBox::VKeyToItem

Volá se rozhraním, když pole se seznamem nadřazené okno dostane zprávy WM_VKEYTOITEM ze seznamu.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nKey*<br/>
Virtuální kód klíče uživatel stiskl. Seznam kódů standardní virtuální klíče najdete v tématu winuser

*nIndex*<br/>
Aktuální pozici blikajícího kurzoru pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu - 2 pro žádná další akce, - 1 pro výchozí akce nebo nezáporné číslo indexu položky seznamu na základě které chcete provést výchozí akci pro stisknutí klávesy.

### <a name="remarks"></a>Poznámky

Pole se seznamem odesílají zprávy WM_VKEYTOITEM při přijetí je zpráva WM_KEYDOWN, ale pouze v případě, že pole se seznamem splňuje obě z následujících akcí:

- Má [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu sady.

- Má alespoň jednu položku.

Měli byste nikdy volat tuto funkci sami. Přepsání této funkce můžete poskytnout vlastní vlastní zpracování zpráv týkajících se klávesnice.

Musí vracet hodnotu k informování rozhraní framework akci provádí přepsání. Vrácená hodnota - 2 označuje, že aplikace zpracovává všechny aspekty pak vyberete požadovanou položku a vyžaduje žádná další akce podle pole se seznamem. Před vrácením - 2, můžete nastavit výběr nebo přesunutí blikající kurzor nebo obojí. Pokud chcete nastavit výběr, použijte [setcursel –](#setcursel) nebo [SetSel](#setsel). Přesune blikající kurzor, použijte [SetCaretIndex](#setcaretindex).

Návratová hodnota – 1 označuje, že pole se seznamem by měl provést výchozí akci v reakci stisknutí kláves. Výchozí implementace vrací - 1.

Vrácená hodnota 0 nebo větší Určuje index položky v seznamu a označuje, že pole se seznamem by měl provedení výchozí akce pro stisknutí klávesy na danou položku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC CTRLTEST](../../visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox – třída](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic – třída](../../mfc/reference/cstatic-class.md)
