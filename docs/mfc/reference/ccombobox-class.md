---
title: CComboBox – – třída
ms.date: 11/04/2016
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
ms.openlocfilehash: b54a1913073ca0b23aeb17a57b16f589a074637b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890804"
---
# <a name="ccombobox-class"></a>CComboBox – – třída

Poskytuje funkce pole se seznamem systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CComboBox : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComboBox –:: CComboBox –](#ccombobox)|Vytvoří objekt `CComboBox`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComboBox –:: AddString](#addstring)|Přidá řetězec na konec seznamu v seznamu pole se seznamem nebo do pole seřazená pozice pro seznam se stylem CBS_SORT.|
|[CComboBox –:: Clear](#clear)|Odstraní (vymaže) aktuální výběr v ovládacím prvku pro úpravy.|
|[CComboBox –:: CompareItem](#compareitem)|Volá se rozhraním, aby se určila relativní pozice nové položky seznamu v seřazeném poli se seznamem seřazeného vlastníka.|
|[CComboBox –:: Copy](#copy)|Zkopíruje aktuální výběr, pokud existuje, do schránky ve formátu CF_TEXT.|
|[CComboBox –:: Create](#create)|Vytvoří pole se seznamem a připojí ho k objektu `CComboBox`.|
|[CComboBox –:: vyjmout](#cut)|Odstraní (vyjme) aktuální výběr (pokud existuje) v textovém poli a zkopíruje odstraněný text do schránky ve formátu CF_TEXT.|
|[CComboBox –::D eleteItem](#deleteitem)|Volá se rozhraním, když se položka seznamu odstraní z pole se seznamem vykresleného vlastníkem.|
|[CComboBox –::D eleteString](#deletestring)|Odstraní řetězec ze seznamu pole se seznamem.|
|[CComboBox –::D IR](#dir)|Přidá seznam názvů souborů do seznamu pole se seznamem.|
|[CComboBox –::D rawItem](#drawitem)|Volá se rozhraním, když se změní vizuální aspekt vlastního pole se seznamem vykresleného vlastníkem.|
|[CComboBox –:: FindString](#findstring)|Vyhledá první řetězec, který obsahuje zadanou předponu v seznamu pole se seznamem.|
|[CComboBox –:: FindStringExact](#findstringexact)|Najde první řetězec seznamu – pole (v poli se seznamem), který odpovídá zadanému řetězci.|
|[CComboBox –:: GetComboBoxInfo](#getcomboboxinfo)|Načte informace o objektu `CComboBox`.|
|[CComboBox –:: GetCount](#getcount)|Načte počet položek v seznamu pole se seznamem.|
|[CComboBox –:: GetCueBanner](#getcuebanner)|Načte startovací text, který se zobrazí pro ovládací prvek pole se seznamem.|
|[CComboBox –::](#getcursel)|Načte index aktuálně vybrané položky, pokud existuje, v seznamu pole se seznamem.|
|[CComboBox –:: GetDroppedControlRect](#getdroppedcontrolrect)|Načte souřadnice obrazovky rozevíracího seznamu (rozevíracího seznamu), který se zobrazuje v rozevíracím seznamu.|
|[CComboBox –:: GetDroppedState](#getdroppedstate)|Určuje, zda je seznam pole se seznamem rozevíracího seznamu zobrazený (vyřazený).|
|[CComboBox –:: GetDroppedWidth](#getdroppedwidth)|Načte minimální povolenou šířku pro část rozevíracího seznamu pole se seznamem.|
|[CComboBox –:: GetEditSel](#geteditsel)|Získá počáteční a koncovou pozici znaků aktuálního výběru v ovládacím prvku pole se seznamem.|
|[CComboBox –:: GetExtendedUI](#getextendedui)|Určuje, zda má pole se seznamem výchozí uživatelské rozhraní nebo Rozšířené uživatelské rozhraní.|
|[CComboBox –:: GetHorizontalExtent](#gethorizontalextent)|Vrátí šířku v pixelech, kterou lze v poli se seznamem zobrazit v části pole se seznamem vodorovně.|
|[CComboBox –:: GetItemData](#getitemdata)|Načte hodnotu 32-bit poskytnutou aplikací přidruženou k zadané položce se seznamem.|
|[CComboBox –:: GetItemDataPtr](#getitemdataptr)|Načte ukazatel 32-bit dodaný aplikací, který je spojen s určenou položkou pole se seznamem.|
|[CComboBox –:: GetItemHeight](#getitemheight)|Načte výšku položek seznamu v poli se seznamem.|
|[CComboBox –:: GetLBText](#getlbtext)|Načte řetězec ze seznamu pole se seznamem.|
|[CComboBox –:: GetLBTextLen](#getlbtextlen)|Získá délku řetězce v seznamu pole se seznamem.|
|[CComboBox –:: getLocal](#getlocale)|Načte identifikátor národního prostředí pro pole se seznamem.|
|[CComboBox –:: GetMinVisible](#getminvisible)|Získá minimální počet viditelných položek v rozevíracím seznamu aktuálního pole se seznamem.|
|[CComboBox –:: GetTopIndex](#gettopindex)|Vrátí index první viditelné položky v části seznamu pole se seznamem.|
|[CComboBox –:: InitStorage](#initstorage)|Předem přidělí bloky paměti pro položky a řetězce v části seznamu pole se seznamem.|
|[CComboBox –:: InsertString](#insertstring)|Vloží řetězec do seznamu pole se seznamem.|
|[CComboBox –:: LimitText](#limittext)|Omezí délku textu, který může uživatel zadat do ovládacího prvku pro úpravy pole se seznamem.|
|[CComboBox –:: MeasureItem](#measureitem)|Volá se rozhraním, aby se určily dimenze pole se seznamem, když se vytvoří pole se seznamem vykresleného vlastníkem.|
|[CComboBox –::P kopírovat](#paste)|Vloží data ze schránky do ovládacího prvku pro úpravy na aktuální pozici kurzoru. Data jsou vložena pouze v případě, že schránka obsahuje data ve formátu CF_TEXT.|
|[CComboBox –:: ResetContent](#resetcontent)|Odebere všechny položky ze seznamu a textového ovládacího prvku pole se seznamem.|
|[CComboBox –:: SelectString](#selectstring)|Vyhledá řetězec v seznamu pole se seznamem a v případě, že je řetězec nalezen, vybere řetězec v poli seznam a zkopíruje řetězec do ovládacího prvku pro úpravy.|
|[CComboBox –:: SetCueBanner](#setcuebanner)|Nastaví startovací text, který se zobrazí pro ovládací prvek pole se seznamem.|
|[CComboBox –:: SetCurSel](#setcursel)|Vybere řetězec v rozevíracím seznamu pole se seznamem.|
|[CComboBox –:: SetDroppedWidth](#setdroppedwidth)|Nastaví minimální povolenou šířku pro část rozevíracího seznamu pole se seznamem.|
|[CComboBox –:: SetEditSel](#seteditsel)|Vybere znaky v ovládacím prvku pole se seznamem.|
|[CComboBox –:: SetExtendedUI](#setextendedui)|Vybere buď výchozí uživatelské rozhraní, nebo Rozšířené uživatelské rozhraní pro pole se seznamem, které má styl CBS_DROPDOWN nebo CBS_DROPDOWNLIST.|
|[CComboBox –:: SetHorizontalExtent](#sethorizontalextent)|Nastaví šířku v pixelech, kterou lze v poli se seznamem zobrazit v části pole se seznamem vodorovně.|
|[CComboBox –:: SetItemData](#setitemdata)|Nastaví hodnotu 32 přidruženou k zadané položce v poli se seznamem.|
|[CComboBox –:: SetItemDataPtr](#setitemdataptr)|Nastaví 32 ukazatel, který je přidružený k zadané položce v poli se seznamem.|
|[CComboBox –:: SetItemHeight](#setitemheight)|Nastaví výšku položek seznamu v poli se seznamem nebo výšku části ovládacího prvku pro úpravy (nebo statického textu) pole se seznamem.|
|[CComboBox –:: SetLocale –](#setlocale)|Nastaví identifikátor národního prostředí pro pole se seznamem.|
|[CComboBox –:: SetMinVisibleItems](#setminvisibleitems)|Nastaví minimální počet viditelných položek v rozevíracím seznamu pro aktuální pole se seznamem.|
|[CComboBox –:: SetTopIndex](#settopindex)|Přikáže část seznamu pole se seznamem k zobrazení položky se zadaným indexem v horní části.|
|[CComboBox –:: ShowDropDown](#showdropdown)|Zobrazí nebo skryje seznam pole se seznamem, který má styl CBS_DROPDOWN nebo CBS_DROPDOWNLIST.|

## <a name="remarks"></a>Poznámky

Pole se seznamem se skládá z pole seznamu kombinovaného s ovládacím prvkem static Control nebo Edit. Část ovládacího prvku seznamu se může zobrazit ve všech časech, nebo se může vyřadit pouze v případě, že uživatel vybere šipku rozevíracího seznamu vedle ovládacího prvku.

Aktuálně vybraná položka (pokud existuje) v poli se seznamem se zobrazí v ovládacím prvku static nebo Edit. Kromě toho, pokud má pole se seznamem styl rozevíracího seznamu, může uživatel zadat počáteční znak jedné z položek v seznamu a seznam, pokud je zobrazen, zvýrazní další položku tímto počátečním znakem.

Následující tabulka porovnává tři [styly](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)pole se seznamem.

|Styl|Když je seznam viditelný|Statický nebo ovládací prvek pro úpravy|
|-----------|-------------------------------|-----------------------------|
|Jednoduchý|Vždy|Upravit|
|Rozevírací seznam|Při vyřazení dolů|Upravit|
|Rozevírací seznam|Při vyřazení dolů|Statická|

Objekt `CComboBox` můžete vytvořit buď z šablony dialogového okna, nebo přímo v kódu. V obou případech nejprve zavolejte konstruktor `CComboBox` pro vytvoření objektu `CComboBox`; Potom zavolejte funkci [vytvořit](#create) členskou funkci pro vytvoření ovládacího prvku a připojte jej k objektu `CComboBox`.

Chcete-li zpracovat oznamovací zprávy systému Windows odeslané polem se seznamem do své nadřazené položky (obvykle třída odvozená z `CDialog`), přidejte položku mapování zpráv a členskou funkci obslužné rutiny zpráv do nadřazené třídy pro každou zprávu.

Každá položka mapování zpráv má následující podobu:

**Oznámení o\_** **(** _ID_, _memberFxn_ **)**

kde `id` Určuje ID podřízeného okna ovládacího prvku pole se seznamem, který odesílá oznámení a `memberFxn` je název nadřazené členské funkce, kterou jste napsali pro zpracování oznámení.

Prototyp funkce nadřazeného objektu je následující:

**afx_msg** `void` `memberFxn` **();**

Pořadí, ve kterém budou odeslána určitá oznámení, nelze předpovědět. Oznámení CBN_SELCHANGE se může vyskytnout zejména před nebo po CBN_CLOSEUP oznámení.

Možné položky mapy zpráv jsou následující:

- ON_CBN_CLOSEUP (Windows 3,1 a novější) Seznam se zavřel v poli se seznamem. Tato zpráva oznámení není odeslána pro pole se seznamem, které má styl [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

- ON_CBN_DBLCLK uživatel dvakrát klikne na řetězec v seznamu pole se seznamem. Tato zpráva oznámení je odeslána pouze pro pole se seznamem se stylem CBS_SIMPLE. Pro pole se seznamem se stylem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nemůže dojít k dvojímu kliknutí, protože jedno kliknutí skryje seznam.

- ON_CBN_DROPDOWN seznamu pole se seznamem se chystá rozevírací seznam (bude zobrazený). Tato zpráva oznámení se může vyskytovat pouze pro pole se seznamem se stylem CBS_DROPDOWN nebo CBS_DROPDOWNLIST.

- ON_CBN_EDITCHANGE uživatel učinil akci, která mohla změnit text v části pro úpravy ovládacího prvku pole se seznamem. Na rozdíl od CBN_EDITUPDATE zprávy se tato zpráva pošle po aktualizaci obrazovky Windows. Neposílá se, pokud pole se seznamem má styl CBS_DROPDOWNLIST.

- ON_CBN_EDITUPDATE části úpravy ovládacího prvku v poli se seznamem se chystá zobrazit změněný text. Tato zpráva oznámení se odešle po formátování textu ovládacího prvku, ale před zobrazením textu. Neposílá se, pokud pole se seznamem má styl CBS_DROPDOWNLIST.

- ON_CBN_ERRSPACE pole se seznamem nemůže přidělit dostatek paměti pro splnění konkrétní žádosti.

- ON_CBN_SELENDCANCEL (Windows 3,1 a novější) Indikuje, že výběr uživatele by měl být zrušen. Uživatel klikne na položku a potom klikne na jiné okno nebo ovládací prvek, aby se skryl seznam pole se seznamem. Tato zpráva oznámení se pošle před CBN_CLOSEUP zpráva oznámení, že výběr uživatele by se měl ignorovat. Zpráva s oznámením CBN_SELENDCANCEL nebo CBN_SELENDOK se pošle i v případě, že zpráva CBN_CLOSEUP oznámení není odeslaná (jako v případě pole se seznamem se stylem CBS_SIMPLE).

- ON_CBN_SELENDOK uživatel vybere položku a pak buď stiskne klávesu ENTER, nebo klepne na klávesu šipka dolů, aby se seznam pole se seznamem skryl. Tato zpráva oznámení se odešle před CBN_CLOSEUP zprávy, která indikuje, že výběr uživatele by měl být považován za platný. Zpráva s oznámením CBN_SELENDCANCEL nebo CBN_SELENDOK se pošle i v případě, že zpráva CBN_CLOSEUP oznámení není odeslaná (jako v případě pole se seznamem se stylem CBS_SIMPLE).

- ON_CBN_KILLFOCUS pole se seznamem ztratí fokus vstupu.

- ON_CBN_SELCHANGE výběru v seznamu pole se seznamem se chystá změna v důsledku toho, že uživatel klikne na pole se seznamem, nebo změní výběr pomocí kláves se šipkami. Při zpracování této zprávy lze text v textovém ovládacím prvku pole se seznamem získat pouze prostřednictvím `GetLBText` nebo jiné podobné funkce. `GetWindowText` nelze použít.

- ON_CBN_SETFOCUS pole se seznamem obdrží fokus vstupu.

Vytvoříte-li objekt `CComboBox` v dialogovém okně (prostřednictvím prostředku dialogového okna), je objekt `CComboBox` automaticky zničen, když uživatel zavře dialogové okno.

Pokud vložíte objekt `CComboBox` do jiného objektu okna, nemusíte ho zničit. Vytvoříte-li objekt `CComboBox` v zásobníku, bude automaticky zničen. Vytvoříte-li objekt `CComboBox` na haldě pomocí **nové** funkce, je nutné volat metodu **Delete** u objektu, aby jej bylo možné zničit, když je pole se seznamem systému Windows zničeno.

**Poznámka:** Chcete-li zpracovat zprávy WM_KEYDOWN a WM_CHAR, je nutné podtřídit ovládací prvky pro úpravy a seznam v poli se seznamem, odvodit třídy z `CEdit` a `CListBox`a přidat obslužné rutiny pro tyto zprávy do odvozených tříd. Další informace naleznete v tématu [CWnd:: SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="addstring"></a>CComboBox –:: AddString

Přidá řetězec do seznamu pole se seznamem.

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*lpszString*<br/>
Odkazuje na řetězec zakončený hodnotou null, který má být přidán.

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota větší než nebo rovna 0, je index založený na nule k řetězci v poli se seznamem. Návratová hodnota je CB_ERR, pokud dojde k chybě; Návratová hodnota je CB_ERRSPACE, pokud není k dispozici dostatek místa pro uložení nového řetězce.

### <a name="remarks"></a>Poznámky

Pokud se pole seznamu nevytvořilo se stylem [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , přidá se na konec seznamu řetězec. V opačném případě je řetězec vložen do seznamu a seznam je seřazen.

> [!NOTE]
>  Tato funkce není podporována ovládacím prvkem Windows `ComboBoxEx`. Další informace o tomto ovládacím prvku naleznete v tématu [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) in the Windows SDK.

Chcete-li vložit řetězec do konkrétního umístění v rámci seznamu, použijte členskou funkci [InsertString](#insertstring) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

##  <a name="ccombobox"></a>CComboBox –:: CComboBox –

Vytvoří objekt `CComboBox`.

```
CComboBox();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

##  <a name="clear"></a>CComboBox –:: Clear

Odstraní (vymaže) aktuální výběr, pokud existuje, v ovládacím prvku pro úpravy pole se seznamem.

```
void Clear();
```

### <a name="remarks"></a>Poznámky

Chcete-li odstranit aktuální výběr a umístit odstraněný obsah do schránky, použijte funkci [Vyjmout](#cut) člen.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

##  <a name="compareitem"></a>CComboBox –:: CompareItem

Volá se rozhraním, aby se určila relativní pozice nové položky v části seznamu seřazeného pole se seznamem seřazeného vlastníka.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parametry

*lpCompareItemStruct*<br/>
Dlouhý ukazatel na strukturu [COMPAREITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-compareitemstruct) .

### <a name="return-value"></a>Návratová hodnota

Určuje relativní pozici dvou položek popsaných ve struktuře `COMPAREITEMSTRUCT`. Může to být kterákoli z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|- 1|Položka 1 se řadí před položkou 2.|
|0|Položka 1 a položka 2 mají stejný druh.|
|1|Položka 1 se řadí za položku 2.|

Popis `COMPAREITEMSTRUCT`naleznete v tématu [CWnd:: OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádnou akci. Pokud vytvoříte pole se seznamem, které je LBS_SORT součástí vlastního vlastnictví, je nutné přepsat tuto členskou funkci, aby bylo možné pomáhat rozhraní při řazení nových položek přidaných do pole se seznamem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

##  <a name="copy"></a>CComboBox –:: Copy

Zkopíruje aktuální výběr, pokud existuje, v ovládacím prvku pro úpravy pole se seznamem do schránky ve formátu CF_TEXT.

```
void Copy();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

##  <a name="create"></a>CComboBox –:: Create

Vytvoří pole se seznamem a připojí ho k objektu `CComboBox`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl pole se seznamem. Použití libovolné kombinace [stylů pole se seznamem](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) pro pole

*OBD*<br/>
Odkazuje na pozici a velikost pole se seznamem. Může být [Struktura Rect](/windows/win32/api/windef/ns-windef-rect) nebo objekt `CRect`.

*pParentWnd*<br/>
Určuje nadřazené okno pole se seznamem (obvykle `CDialog`). Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Objekt `CComboBox` vytvoříte ve dvou krocích. Nejprve zavolejte konstruktor a potom zavolejte `Create`, čímž se vytvoří pole se seznamem Windows a připojí ho k objektu `CComboBox`.

Když se `Create` spustí, Windows pošle zprávy [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)a [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) do pole se seznamem.

Tyto zprávy jsou ve výchozím nastavení zpracovávány členskými funkcemi [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [Create](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)a [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) v základní třídě `CWnd`. Chcete-li zvětšit výchozí zpracování zprávy, odvodit třídu z `CComboBox`, přidat do nové třídy mapu zprávy a přepsat předchozí funkce členů obslužné rutiny zpráv. Přepsat `OnCreate`, například k provedení potřebné inicializace pro novou třídu.

Použijte následující [Styly okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) pro ovládací prvek pole se seznamem. :

- WS_CHILD vždycky

- WS_VISIBLE obvykle

- WS_DISABLED zřídka

- WS_VSCROLL pro přidání svislého posouvání pro pole seznamu v poli se seznamem

- WS_HSCROLL pro přidání vodorovného posouvání pro pole seznamu v poli se seznamem

- WS_GROUP seskupení ovládacích prvků

- WS_TABSTOP zahrnutí pole se seznamem do pořadí procházení

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

##  <a name="cut"></a>CComboBox –:: vyjmout

Odstraní (vyjme) aktuální výběr, pokud existuje, v ovládacím prvku pro úpravy pole se seznamem a zkopíruje odstraněný text do schránky ve formátu CF_TEXT.

```
void Cut();
```

### <a name="remarks"></a>Poznámky

Chcete-li odstranit aktuální výběr bez umístění odstraněného textu do schránky, zavolejte funkci [clear](#clear) member.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

##  <a name="deleteitem"></a>CComboBox –::D eleteItem

Volá se rozhraním, když uživatel odstraní položku z objektu `CComboBox` vykresleného vlastníkem nebo zničí pole se seznamem.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDeleteItemStruct*<br/>
Dlouhý ukazatel na strukturu [DELETEITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) systému Windows, která obsahuje informace o odstraněné položce. Popis této struktury naleznete v tématu [CWnd:: OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) .

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádnou akci. Potlačením této funkce překreslete pole se seznamem podle potřeby.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

##  <a name="deletestring"></a>CComboBox –::D eleteString

Odstraní položku v umístění *nIndex* z pole se seznamem.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index pro řetězec, který má být odstraněn.

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota větší než nebo rovna 0, pak je počet řetězců zbývajících v seznamu. Návratová hodnota je CB_ERR, pokud *nIndex* určuje index větší než počet položek v seznamu.

### <a name="remarks"></a>Poznámky

Všechny položky, které následují *nIndex* , se teď přesunou o jednu pozici dolů. Například pokud pole se seznamem obsahuje dvě položky, odstranění první položky způsobí, že zbývající položka bude nyní na první pozici. *nIndex*= 0 pro položku na první pozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

##  <a name="dir"></a>CComboBox –::D IR

Přidá seznam názvů souborů nebo jednotek do seznamu pole se seznamem.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parametry

*ATTR*<br/>
Může být libovolná kombinace hodnot **výčtu** popsaná v [CFile –:: GetStatus](../../mfc/reference/cfile-class.md#getstatus) nebo libovolná kombinace následujících hodnot:

- Soubor DDL_READWRITE lze číst nebo do něj zapisovat.

- Soubor DDL_READONLY lze číst, ale nikoli zapisovat do.

- Soubor DDL_HIDDEN je skrytý a v seznamu adresářů se nezobrazí.

- Soubor DDL_SYSTEM je systémový soubor.

- DDL_DIRECTORY název určený parametrem *lpszWildCard* Určuje adresář.

- Soubor DDL_ARCHIVE byl archivován.

- DDL_DRIVES zahrnout všechny jednotky, které odpovídají názvu určenému parametrem *lpszWildCard*.

- Příznak DDL_EXCLUSIVE exkluzivní. Pokud je nastaven příznak Exclusive, jsou uvedeny pouze soubory zadaného typu. V opačném případě jsou soubory zadaného typu uvedeny vedle "normálního" souboru.

*lpszWildCard*<br/>
Odkazuje na řetězec specifikace souboru. Řetězec může obsahovat zástupné znaky (například *.\*).

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota větší než nebo rovna 0, je indexem posledního názvu souboru přidaného do seznamu index založený na nule. Návratová hodnota je CB_ERR, pokud dojde k chybě; Návratová hodnota je CB_ERRSPACE, pokud není k dispozici dostatek místa pro uložení nových řetězců.

### <a name="remarks"></a>Poznámky

Tato funkce není podporována ovládacím prvkem Windows `ComboBoxEx`. Další informace o tomto ovládacím prvku naleznete v tématu [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) in the Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

##  <a name="drawitem"></a>CComboBox –::D rawItem

Volá se rozhraním, když se změní vizuální aspekt vlastního pole se seznamem vykresleného pomocí vlastníka.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na strukturu [DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) , která obsahuje informace o požadovaném typu výkresu.

### <a name="remarks"></a>Poznámky

`itemAction` člen struktury `DRAWITEMSTRUCT` definuje akci kreslení, která má být provedena. Popis této struktury naleznete v tématu [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) .

Ve výchozím nastavení tato členská funkce neprovede žádnou akci. Přepište tuto členskou funkci pro implementaci vykreslování pro objekt `CComboBox` vykreslený vlastníkem. Před ukončením této členské funkce by aplikace měla obnovit všechny objekty GDI (Graphics Device Interface) vybrané pro kontext zobrazení zadaný v *lpDrawItemStruct*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

##  <a name="findstring"></a>CComboBox –:: FindString

Najde, ale nevybere, první řetězec, který obsahuje zadanou předponu v seznamu pole se seznamem.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Obsahuje index položky vycházející od nuly před první položkou, která má být prohledána. Když hledání dosáhne dolní části seznamu, pokračuje v horní části seznamu zpátky na položku zadanou v *nStartAfter*. Pokud je-1, bude prohledán celý seznam od začátku.

*lpszString*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje předponu, kterou chcete vyhledat. Hledání je nezávislé na velikosti písmen, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota větší než nebo rovna 0, je index odpovídající položky založený na nule. Pokud hledání neproběhlo úspěšně, je CB_ERR.

### <a name="remarks"></a>Poznámky

Tato funkce není podporována ovládacím prvkem Windows `ComboBoxEx`. Další informace o tomto ovládacím prvku naleznete v tématu [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) in the Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

##  <a name="findstringexact"></a>CComboBox –:: FindStringExact

Zavolejte členskou funkci `FindStringExact` pro nalezení prvního řetězce seznamu pole (v poli se seznamem), který odpovídá řetězci zadanému v *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parametry

*nIndexStart*<br/>
Určuje index položky vycházející od nuly před první položkou, která se má prohledat. Když hledání dosáhne dolní části seznamu, pokračuje v horní části seznamu zpátky na položku zadanou v *nIndexStart*. Pokud je *nIndexStart* -1, bude prohledán celý seznam od začátku.

*lpszFind*<br/>
Odkazuje na řetězec zakončený hodnotou null, který má být hledán. Tento řetězec může obsahovat úplný název souboru včetně rozšíření. Hledání nerozlišuje velká a malá písmena, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index se shodnou položkou založený na nule nebo CB_ERR, pokud hledání nebylo úspěšné.

### <a name="remarks"></a>Poznámky

Pokud bylo pole se seznamem vytvořeno pomocí stylu vykreslování vlastníka, ale bez stylu [CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , `FindStringExact` se pokusí porovnat hodnotu doubleword s hodnotou *lpszFind*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

##  <a name="getcomboboxinfo"></a>CComboBox –:: GetComboBoxInfo

Načte informace pro objekt `CComboBox`.

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>Parametry

*pcbi*<br/>
Ukazatel na strukturu [COMBOBOXINFO](/windows/win32/api/winuser/ns-winuser-comboboxinfo) .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [CB_GETCOMBOBOXINFO](/windows/win32/Controls/cb-getcomboboxinfo) zprávy, jak je popsáno v Windows SDK.

##  <a name="getcount"></a>CComboBox –:: GetCount

Zavolejte tuto členskou funkci pro načtení počtu položek v části seznamu pole se seznamem.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek Počet vrácených položek je větší než hodnota indexu poslední položky (index je založený na nule). Je CB_ERR, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

##  <a name="getcuebanner"></a>CComboBox –:: GetCueBanner

Načte startovací text, který se zobrazí pro ovládací prvek pole se seznamem.

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpszText*|mimo Ukazatel na vyrovnávací paměť, která obdrží text banneru hromádky.|
|*cchText*|pro Velikost vyrovnávací paměti, na kterou parametr *lpszText* odkazuje.|

### <a name="return-value"></a>Návratová hodnota

V prvním přetížení objekt [CString](../../atl-mfc-shared/using-cstring.md) , který obsahuje text banneru hromádky, pokud existuje; v opačném případě objekt `CString`, který má nulovou délku.

-nebo-

Ve druhém přetížení, TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Startovací text je výzva, která se zobrazí ve vstupní oblasti ovládacího prvku pole se seznamem. Text startovacího textu se zobrazí, dokud uživatel nezadá vstup.

Tato metoda pošle zprávu [CB_GETCUEBANNER](/windows/win32/Controls/cb-getcuebanner) , která je popsána v Windows SDK.

##  <a name="getcursel"></a>CComboBox –::

Chcete-li určit, která položka v poli se seznamem je vybrána, zavolejte tuto členskou funkci.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule aktuálně vybrané položky v seznamu pole se seznamem, nebo CB_ERR, pokud není vybrána žádná položka.

### <a name="remarks"></a>Poznámky

`GetCurSel` vrátí index do seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

##  <a name="getdroppedcontrolrect"></a>CComboBox –:: GetDroppedControlRect

Zavolejte členskou funkci `GetDroppedControlRect`, aby se načetly souřadnice obrazovky seznamu zobrazených polí rozevíracího seznamu.

```
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>Parametry

*lprect*<br/>
Odkazuje na [strukturu Rect](/windows/win32/api/windef/ns-windef-rect) , která má přijmout souřadnice.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

##  <a name="getdroppedstate"></a>CComboBox –:: GetDroppedState

Voláním členské funkce `GetDroppedState` určíte, zda je seznam pole rozevíracího seznamu zobrazený (vyřazený).

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je pole se seznamem viditelné; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

##  <a name="getdroppedwidth"></a>CComboBox –:: GetDroppedWidth

Voláním této funkce načtete minimální povolenou šířku seznamu pole se seznamem (v pixelech).

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu je minimální povolená Šířka v pixelech. v opačném případě CB_ERR.

### <a name="remarks"></a>Poznámky

Tato funkce se vztahuje pouze na pole se seznamem se stylem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

Ve výchozím nastavení je minimální povolená Šířka rozevíracího seznamu 0. Minimální povolenou šířku lze nastavit voláním [SetDroppedWidth](#setdroppedwidth). Když se zobrazí část seznamu pole se seznamem, její šířka je větší než minimální povolená šířka nebo šířka pole se seznamem.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [SetDroppedWidth](#setdroppedwidth).

##  <a name="geteditsel"></a>CComboBox –:: GetEditSel

Získá počáteční a koncovou pozici znaků aktuálního výběru v ovládacím prvku pole se seznamem.

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota 32, která obsahuje počáteční pozici v aplikaci s nízkým pořadím a pozici prvního nevybraného znaku po konci výběru v aplikaci s vysokým pořadím. Pokud se tato funkce používá v poli se seznamem bez ovládacího prvku pro úpravy, CB_ERR se vrátí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

##  <a name="getextendedui"></a>CComboBox –:: GetExtendedUI

Voláním členské funkce `GetExtendedUI` určíte, zda má pole se seznamem výchozí uživatelské rozhraní nebo Rozšířené uživatelské rozhraní.

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud pole se seznamem má rozšířené uživatelské rozhraní; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Rozšířené uživatelské rozhraní lze identifikovat následujícími způsoby:

- Kliknutím na statický ovládací prvek se zobrazí seznam pouze pro pole se seznamem se stylem [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

- Stisknutí klávesy se ŠIPKou dolů zobrazí seznam (F4 je zakázaný).

Posouvání ve statickém ovládacím prvku je zakázáno, pokud není zobrazen seznam položek (klávesy se šipkami jsou zakázány).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

##  <a name="gethorizontalextent"></a>CComboBox –:: GetHorizontalExtent

Načte se z pole se seznamem Šířka v pixelech, o kterou může být část seznamu pole se seznamem posunutá vodorovně.

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>Návratová hodnota

Rolovací šířka části seznamu pole se seznamem (v pixelech).

### <a name="remarks"></a>Poznámky

To platí pouze v případě, že část seznamu pole se seznamem má vodorovný posuvník.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

##  <a name="getitemdata"></a>CComboBox –:: GetItemData

Načte hodnotu 32-bit poskytnutou aplikací přidruženou k zadané položce se seznamem.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index položky vycházející z nuly v seznamu pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Hodnota 32, která je přidružená k položce, nebo CB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Hodnota 32-bit lze nastavit pomocí parametru *dwItemData* volání členské funkce [SetItemData](#setitemdata) . Pokud je hodnota 32, která se má načíst, je ukazatel (**void** <strong>\*</strong>), použijte `GetItemDataPtr` členskou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

##  <a name="getitemdataptr"></a>CComboBox –:: GetItemDataPtr

Načte hodnotu 32-bit poskytnutou aplikací přidruženou k zadané položce se seznamem jako ukazatel (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index položky vycházející z nuly v seznamu pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Načte ukazatel nebo-1, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

##  <a name="getitemheight"></a>CComboBox –:: GetItemHeight

Zavolejte členskou funkci `GetItemHeight`, aby se načetla Výška položek seznamu v poli se seznamem.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje komponentu pole se seznamem, jejíž výška má být načtena. Pokud je parametr *nIndex* -1, je načtena Výška části ovládacího prvku pro úpravy (nebo statického textu) pole se seznamem. Pokud pole se seznamem má styl [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , určuje *nIndex* index položky seznamu, jejichž výška má být načtena. V opačném případě by měl být *nIndex* nastaven na 0.

### <a name="return-value"></a>Návratová hodnota

Výška zadané položky v poli se seznamem (v pixelech) Návratová hodnota je CB_ERR, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

##  <a name="getlbtext"></a>CComboBox –:: GetLBText

Načte řetězec ze seznamu pole se seznamem.

```
int GetLBText(
    int nIndex,
    LPTSTR lpszText) const;

void GetLBText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index vycházející z řetězce seznamu, který se má zkopírovat.

*lpszText*<br/>
Odkazuje na vyrovnávací paměť, která přijímá řetězec. Vyrovnávací paměť musí mít dostatek místa pro řetězec a ukončující znak null.

*rString*<br/>
Odkaz na `CString`.

### <a name="return-value"></a>Návratová hodnota

Délka (v bajtech) řetězce s výjimkou ukončujícího znaku null. Pokud *nIndex* neurčuje platný index, návratová hodnota je CB_ERR.

### <a name="remarks"></a>Poznámky

Druhá forma této členské funkce vyplní objekt `CString` textem položky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

##  <a name="getlbtextlen"></a>CComboBox –:: GetLBTextLen

Získá délku řetězce v seznamu pole se seznamem.

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index založený na nule řetězce seznamu.

### <a name="return-value"></a>Návratová hodnota

Délka řetězce v bajtech s výjimkou ukončujícího znaku null. Pokud *nIndex* neurčuje platný index, návratová hodnota je CB_ERR.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CComboBox –:: GetLBText](#getlbtext).

##  <a name="getlocale"></a>CComboBox –:: getLocal

Načte národní prostředí používané polem se seznamem.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota identifikátoru národního prostředí (LCID) pro řetězce v poli se seznamem.

### <a name="remarks"></a>Poznámky

Národní prostředí se používá například k určení pořadí řazení řetězců v seřazeném poli se seznamem.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CComboBox –:: setlocale](#setlocale).

##  <a name="getminvisible"></a>CComboBox –:: GetMinVisible

Získá minimální počet viditelných položek v rozevíracím seznamu aktuálního ovládacího prvku pole se seznamem.

```
int GetMinVisible() const;
```

### <a name="return-value"></a>Návratová hodnota

Minimální počet viditelných položek v aktuálním rozevíracím seznamu.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [CB_GETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) , která je popsána v Windows SDK.

##  <a name="gettopindex"></a>CComboBox –:: GetTopIndex

Načte index první viditelné položky v seznamu pole se seznamem, který je založený na nule.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule první viditelné položky v seznamu pole se seznamem, pokud je to úspěšné, CB_ERR jinak.

### <a name="remarks"></a>Poznámky

Zpočátku je položka 0 v horní části seznamu, ale v případě, že je pole se seznamem posunuto, může být v horní části zobrazená jiná položka.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

##  <a name="initstorage"></a>CComboBox –:: InitStorage

Přidělí paměť pro ukládání položek seznamu v části seznamu pole se seznamem.

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

Pokud je to úspěšné, maximální počet položek, které může část seznamu pole se seznamem obsahovat, je možné uložit před tím, než je potřeba přerozdělení paměti, jinak CB_ERRSPACE, což znamená, že k dispozici není dostatek paměti.

### <a name="remarks"></a>Poznámky

Tuto funkci volejte před přidáním velkého počtu položek do části seznamu `CComboBox`.

Jenom Windows 95/98: parametr *wParam* je omezený na 16 bitů hodnot. To znamená, že pole se seznamem nemůžou obsahovat více než 32 767 položek. I když je počet položek omezený, celková velikost položek v poli seznamu je omezená pouze pomocí dostupné paměti.

Tato funkce pomáhá zrychlit inicializaci seznamů polí, které mají velký počet položek (více než 100). Předem alokuje zadanou velikost paměti, aby následné funkce [AddString](#addstring), [InsertString](#insertstring)a [dir](#dir) vybraly nejkratší možnou dobu. Můžete použít odhady pro parametry. Pokud dojde k přeodhadování, je přiděleno několik dalších paměťových paměti; Pokud se podceňují skutečnou, použije se pro položky, které překračují předběžně přidělené množství, normální přidělení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

##  <a name="insertstring"></a>CComboBox –:: InsertString

Vloží řetězec do seznamu pole se seznamem.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index založený na nule do pozice v poli se seznamem, který obdrží řetězec. Pokud je tento parametr-1, řetězec je přidán na konec seznamu.

*lpszString*<br/>
Odkazuje na řetězec zakončený hodnotou null, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule pozice, do které byl řetězec vložen. Návratová hodnota je CB_ERR, pokud dojde k chybě. Návratová hodnota je CB_ERRSPACE, pokud není k dispozici dostatek místa pro uložení nového řetězce.

### <a name="remarks"></a>Poznámky

Na rozdíl od [členské funkce](#addstring) `InsertString` nezpůsobí řazení seznamu [CBS_SORTho](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.

> [!NOTE]
>  Tato funkce není podporována ovládacím prvkem Windows `ComboBoxEx`. Další informace o tomto ovládacím prvku naleznete v tématu [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) in the Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

##  <a name="limittext"></a>CComboBox –:: LimitText

Omezí délku textu v bajtech, které může uživatel zadat do ovládacího prvku pro úpravy pole se seznamem.

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>Parametry

*nMaxChars*<br/>
Určuje délku (v bajtech) textu, který může uživatel zadat. Pokud je tento parametr 0, délka textu je nastavená na 65 535 bajtů.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné. Pokud je volána pro pole se seznamem se stylem [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo pole se seznamem bez ovládacího prvku pro úpravy, vrácená hodnota je CB_ERR.

### <a name="remarks"></a>Poznámky

Pokud pole se seznamem nemá [CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)stylu, nastavení limitu pro text je větší, než velikost ovládacího prvku pro úpravy nebude mít žádný efekt.

`LimitText` pouze omezuje text, který uživatel může zadat. Nemá žádný vliv na žádný text, který už je v ovládacím prvku pro úpravy při odeslání zprávy, ani nemá vliv na délku textu zkopírovaného do textového pole, když je vybraný řetězec v seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

##  <a name="measureitem"></a>CComboBox –:: MeasureItem

Volá se rozhraním, když se vytvoří pole se seznamem se stylem vykreslování vlastníka.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Dlouhý ukazatel na strukturu [MEASUREITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádnou akci. Tuto členskou funkci přepište a naplňte `MEASUREITEMSTRUCT` struktury a informujte okna o rozměrech seznamu v poli se seznamem. Pokud je pole se seznamem vytvořeno pomocí stylu [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , rozhraní volá tuto členskou funkci pro každou položku v seznamu. V opačném případě se tento člen volá jenom jednou.

Použití stylu CBS_OWNERDRAWFIXED v poli se seznamem, vykresleném vlastníkem, které bylo vytvořeno s členskou funkcí [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) `CWnd` zahrnuje další pokyny pro programování. Podívejte se na diskuzi v [technické poznámce 14](../../mfc/tn014-custom-controls.md).

Popis `MEASUREITEMSTRUCT` struktury naleznete v tématu [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

##  <a name="paste"></a>CComboBox –::P kopírovat

Vloží data ze schránky do ovládacího prvku pro úpravy pole se seznamem na aktuální pozici kurzoru.

```
void Paste();
```

### <a name="remarks"></a>Poznámky

Data jsou vložena pouze v případě, že schránka obsahuje data ve formátu CF_TEXT.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

##  <a name="resetcontent"></a>CComboBox –:: ResetContent

Odebere všechny položky ze seznamu a textového ovládacího prvku pole se seznamem.

```
void ResetContent();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

##  <a name="selectstring"></a>CComboBox –:: SelectString

Vyhledá řetězec v seznamu pole se seznamem a v případě, že je řetězec nalezen, vybere řetězec v poli seznam a zkopíruje jej do ovládacího prvku pro úpravy.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Obsahuje index položky vycházející od nuly před první položkou, která má být prohledána. Když hledání dosáhne dolní části seznamu, pokračuje v horní části seznamu zpátky na položku zadanou v *nStartAfter*. Pokud je-1, bude prohledán celý seznam od začátku.

*lpszString*<br/>
Odkazuje na řetězec zakončený hodnotou null, který obsahuje předponu, kterou chcete vyhledat. Hledání je nezávislé na velikosti písmen, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule vybrané položky, pokud byl řetězec nalezen. Pokud hledání nebylo úspěšné, vrácená hodnota je CB_ERR a aktuální výběr se nemění.

### <a name="remarks"></a>Poznámky

Je vybrán řetězec pouze v případě, že jeho počáteční znaky (z počátečního bodu) odpovídají znakům v řetězci předpony.

Všimněte si, že členské funkce `SelectString` a `FindString` oba naleznou řetězec, ale `SelectString` členská funkce také vybere řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

##  <a name="setcuebanner"></a>CComboBox –:: SetCueBanner

Nastaví startovací text, který se zobrazí pro ovládací prvek pole se seznamem.

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpszText*|pro Ukazatel na vyrovnávací paměť zakončenou hodnotou null, která obsahuje text startovacího textu.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Startovací text je výzva, která se zobrazí ve vstupní oblasti ovládacího prvku pole se seznamem. Text startovacího textu se zobrazí, dokud uživatel nezadá vstup.

Tato metoda pošle zprávu [CB_SETCUEBANNER](/windows/win32/Controls/cb-setcuebanner) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, *m_combobox*, která se používá k programovému přístupu k ovládacímu prvku pole se seznamem. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví banner hromádky pro ovládací prvek pole se seznamem.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="setcursel"></a>CComboBox –:: SetCurSel

Vybere řetězec v rozevíracím seznamu pole se seznamem.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parametry

*nVyberte*<br/>
Určuje index založený na nule řetězce, který chcete vybrat. Pokud je-1, všechny aktuální výběry v seznamu se odeberou a textové pole se vymaže.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule položky vybrané, pokud je zpráva úspěšná Návratová hodnota je CB_ERR, pokud je *nVyberte* větší než počet položek v seznamu nebo pokud je *nVyberte* nastaven na hodnotu-1, což zruší výběr.

### <a name="remarks"></a>Poznámky

V případě potřeby se v seznamu posune řetězec do zobrazení (Pokud je seznam zobrazený). Text v ovládacím prvku pro úpravy pole se seznamem se změní tak, aby odrážel nový výběr. Všechny předchozí výběry v seznamu jsou odebrány.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

##  <a name="setdroppedwidth"></a>CComboBox –:: SetDroppedWidth

Voláním této funkce nastavíte minimální povolenou šířku seznamu pole se seznamem (v pixelech).

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Minimální povolená šířka části seznamu pole se seznamem (v pixelech).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, Nová šířka pole se seznamem, jinak CB_ERR.

### <a name="remarks"></a>Poznámky

Tato funkce se vztahuje pouze na pole se seznamem se stylem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

Ve výchozím nastavení je minimální povolená Šířka rozevíracího seznamu 0. Když se zobrazí část seznamu pole se seznamem, její šířka je větší než minimální povolená šířka nebo šířka pole se seznamem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

##  <a name="seteditsel"></a>CComboBox –:: SetEditSel

Vybere znaky v ovládacím prvku pole se seznamem.

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>Parametry

*nStartChar*<br/>
Určuje počáteční pozici. Pokud je počáteční pozice nastavená na hodnotu-1, všechny existující výběry se odeberou.

*nEndChar*<br/>
Určuje koncovou pozici. Je-li koncová pozice nastavena na hodnotu-1, bude vybrán veškerý text z počáteční pozice na poslední znak v ovládacím prvku pro úpravy.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je členská funkce úspěšná; v opačném případě 0. Je CB_ERR, pokud má `CComboBox` styl [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo nemá pole se seznamem.

### <a name="remarks"></a>Poznámky

Pozice jsou počítány od nuly. Chcete-li vybrat první znak ovládacího prvku pro úpravy, zadáte počáteční pozici 0. Koncová pozice je pro znak hned za posledním znakem, který chcete vybrat. Například pro výběr prvních čtyř znaků textového ovládacího prvku byste použili počáteční pozici 0 a koncovou pozici 4.

> [!NOTE]
>  Tato funkce není podporována ovládacím prvkem Windows `ComboBoxEx`. Další informace o tomto ovládacím prvku naleznete v tématu [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) in the Windows SDK.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CComboBox –:: GetEditSel](#geteditsel).

##  <a name="setextendedui"></a>CComboBox –:: SetExtendedUI

Zavolejte členskou funkci `SetExtendedUI` a vyberte buď výchozí uživatelské rozhraní, nebo Rozšířené uživatelské rozhraní pro pole se seznamem, které má styl [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>Parametry

*bExtended*<br/>
Určuje, zda má pole se seznamem používat Rozšířené uživatelské rozhraní nebo výchozí uživatelské rozhraní. Hodnota TRUE vybere Rozšířené uživatelské rozhraní; Hodnota FALSE vybere standardní uživatelské rozhraní.

### <a name="return-value"></a>Návratová hodnota

CB_OKAY, zda je operace úspěšná, nebo CB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Rozšířené uživatelské rozhraní lze identifikovat následujícími způsoby:

- Kliknutím na statický ovládací prvek se zobrazí seznam pouze pro pole se seznamem se stylem CBS_DROPDOWNLIST.

- Stisknutí klávesy se ŠIPKou dolů zobrazí seznam (F4 je zakázaný).

Posouvání ve statickém ovládacím prvku je zakázáno, pokud seznam položek není viditelný (klávesy se šipkami jsou zakázány).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CComboBox –:: GetExtendedUI](#getextendedui).

##  <a name="sethorizontalextent"></a>CComboBox –:: SetHorizontalExtent

Nastaví šířku v pixelech, o kterou lze v poli se seznamem vodorovně posouvat část seznamu.

```
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>Parametry

*nExtent*<br/>
Určuje počet pixelů, o který lze v poli se seznamem vodorovně posouvat část seznamu.

### <a name="remarks"></a>Poznámky

Pokud je šířka pole seznamu menší než tato hodnota, vodorovný posuvník bude vodorovně posouvat položky v poli se seznamem. Pokud je šířka pole seznamu větší nebo rovna této hodnotě, je vodorovný posuvník skrytý nebo, pokud pole se seznamem má styl [Cbs_disablenoscroll](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) zakázaný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

##  <a name="setitemdata"></a>CComboBox –:: SetItemData

Nastaví hodnotu 32 přidruženou k zadané položce v poli se seznamem.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index založený na nule pro položku, kterou chcete nastavit.

*dwItemData*<br/>
Obsahuje novou hodnotu, kterou chcete přidružit k položce.

### <a name="return-value"></a>Návratová hodnota

CB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Pokud 32 položka musí být ukazatelem, použijte členskou funkci `SetItemDataPtr`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

##  <a name="setitemdataptr"></a>CComboBox –:: SetItemDataPtr

Nastaví hodnotu 32, která je přidružená k zadané položce v poli se seznamem, tak, aby byla zadaným ukazatelem (**void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index položky založený na nule.

*pData*<br/>
Obsahuje ukazatel, který se má přidružit k položce.

### <a name="return-value"></a>Návratová hodnota

CB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tento ukazatel zůstává platný po dobu života pole se seznamem, i když se relativní pozice položky v poli se seznamem může změnit při přidání nebo odebrání položek. Proto se index položky v poli může změnit, ale ukazatel zůstane spolehlivý.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

##  <a name="setitemheight"></a>CComboBox –:: SetItemHeight

Voláním členské funkce `SetItemHeight` nastavíte výšku položek seznamu v poli se seznamem nebo výšku části ovládacího prvku pro úpravy (nebo statického textu) pole se seznamem.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje, zda je nastavena Výška položek seznamu nebo Výška části ovládacího prvku pro úpravy (nebo statického textu) pole se seznamem.

Pokud má pole se seznamem [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, určuje index vycházející z položky seznamu, jejíž výška má být nastavena, hodnota *nIndex* . v opačném případě musí být *nIndex* 0 a výška všech položek seznamu bude nastavena.

Pokud je *nIndex* -1, je nastavena výška pole se seznamem pro úpravy nebo na statickou textovou část.

*cyItemHeight*<br/>
Určuje výšku komponenty pole se seznamem (v pixelech), kterou identifikuje *nIndex*.

### <a name="return-value"></a>Návratová hodnota

CB_ERR, pokud je index nebo výška neplatný; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Výška části ovládacího prvku pro úpravy (nebo statického textu) pole se seznamem je nastavena nezávisle na výšce položek seznamu. Aplikace musí zajistit, aby výška části pro úpravu ovládacího prvku (nebo statického textu) nebyla menší než výška konkrétní položky v poli se seznamem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

##  <a name="setlocale"></a>CComboBox –:: SetLocale –

Nastaví identifikátor národního prostředí pro toto pole se seznamem.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parametry

*nNewLocale*<br/>
Nová hodnota identifikátoru národního prostředí (LCID), která se má nastavit pro pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnota identifikátoru národního prostředí (LCID) pro toto pole se seznamem.

### <a name="remarks"></a>Poznámky

Pokud není volána `SetLocale`, je ze systému získáno výchozí národní prostředí. Toto výchozí národní prostředí systému lze upravit pomocí regionální (nebo mezinárodní) aplikace v Ovládacích panelech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

##  <a name="setminvisibleitems"></a>CComboBox –:: SetMinVisibleItems

Nastaví minimální počet viditelných položek v rozevíracím seznamu aktuálního ovládacího prvku pole se seznamem.

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*neviditelné*|pro Určuje minimální počet viditelných položek.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [CB_SETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, *m_combobox*, která se používá k programovému přístupu k ovládacímu prvku pole se seznamem. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Příklad

Následující příklad kódu vloží do rozevíracího seznamu ovládacího prvku pole se seznamem 20 položek. Pak určuje, že když uživatel stiskne šipku rozevíracího seznamu, zobrazí se aspoň 10 položek.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="settopindex"></a>CComboBox –:: SetTopIndex

Zajistí, že se v části seznamu pole se seznamem zobrazí konkrétní položka.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index položky seznamu na základě nuly.

### <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu nebo CB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Systém posune seznam do pole, dokud se nezobrazí položka zadaná parametrem *nIndex* v horní části seznamu nebo bylo dosaženo maximálního rozsahu posouvání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

##  <a name="showdropdown"></a>CComboBox –:: ShowDropDown

Zobrazí nebo skryje seznam pole se seznamem, který má styl [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

```
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>Parametry

*bShowIt*<br/>
Určuje, zda se má rozevírací seznam zobrazovat nebo skrývat. Hodnota TRUE zobrazí seznam. Hodnota FALSE skryje seznam.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení se pole se seznamem tohoto stylu zobrazí v seznamu.

Tato členská funkce nemá žádný vliv na pole se seznamem vytvořené pomocí stylu [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CComboBox –:: GetDroppedState](#getdroppedstate).

## <a name="see-also"></a>Viz také

[CTRLBARS Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic – třída](../../mfc/reference/cstatic-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
