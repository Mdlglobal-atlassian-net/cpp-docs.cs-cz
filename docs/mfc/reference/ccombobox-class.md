---
title: Třída CComboBox
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
ms.openlocfilehash: dc803fb4ce137b256f4197afaec7bc3327e1e85a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754832"
---
# <a name="ccombobox-class"></a>Třída CComboBox

Poskytuje funkce pole se seznamem systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CComboBox : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComboBox::CComboBox](#ccombobox)|Vytvoří `CComboBox` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComboBox::Přidat řetězec](#addstring)|Přidá řetězec na konec seznamu v seznamu pole se seznamem nebo na seřazené pozici seznamů se stylem CBS_SORT.|
|[CComboBox::Vymazat](#clear)|Odstraní (vymaže) aktuální výběr, pokud existuje, v ovládacím prvku upravit.|
|[CComboBox::Porovnatpoložku](#compareitem)|Volat rámci k určení relativní pozice nové položky seznamu v seřazené vlastníka nakreslené pole se seznamem.|
|[CComboBox::Kopírovat](#copy)|Zkopíruje aktuální výběr, pokud existuje, do schránky ve CF_TEXT formátu.|
|[CComboBox::Vytvořit](#create)|Vytvoří pole se seznamem a `CComboBox` připojí jej k objektu.|
|[CComboBox::Vyjmout](#cut)|Odstraní (vyjme) aktuální výběr, pokud existuje, v ovládacím prvku upravit a zkopíruje odstraněný text do schránky ve formátu CF_TEXT.|
|[CComboBox::DeleteItem](#deleteitem)|Volat rámci při odstranění položky seznamu z pole se seznamem nakreslené vlastníka.|
|[CComboBox::DeleteString](#deletestring)|Odstraní řetězec ze seznamu pole se seznamem.|
|[CComboBox::Dir](#dir)|Přidá seznam názvů souborů do seznamu pole se seznamem.|
|[CComboBox::DrawItem](#drawitem)|Volat rámci při změně vizuální aspekt pole se seznamem nakreslené vlastníka.|
|[CComboBox::FindString](#findstring)|Najde první řetězec, který obsahuje zadanou předponu v seznamu pole se seznamem.|
|[CComboBox::FindStringExact](#findstringexact)|Najde první řetězec seznamu (v poli se seznamem), který odpovídá zadanému řetězci.|
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|Načte informace `CComboBox` o objektu.|
|[CComboBox::GetCount](#getcount)|Načte počet položek v seznamu pole se seznamem.|
|[CComboBox::GetCueBanner](#getcuebanner)|Získá tágo text, který se zobrazí pro ovládací prvek pole se seznamem.|
|[CComboBox::GetCurSel](#getcursel)|Načte index aktuálně vybrané položky, pokud existuje, v seznamu pole se seznamem.|
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|Načte souřadnice obrazovky viditelného seznamu (vypuštěné dolů) rozevíracího pole se seznamem.|
|[CComboBox::GetDroppedState](#getdroppedstate)|Určuje, zda je seznam rozevíracího pole se seznamem viditelný (spadl dolů).|
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|Načte minimální povolenou šířku pro rozevírací seznam část pole se seznamem.|
|[CComboBox::GetEditSel](#geteditsel)|Získá počáteční a koncové pozice znaků aktuálního výběru v ovládacím prvku upravit pole se seznamem.|
|[CComboBox::GetExtendedUI](#getextendedui)|Určuje, zda pole se seznamem má výchozí uživatelské rozhraní nebo rozšířené uživatelské rozhraní.|
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|Vrátí šířku v obrazových bodech, kterou lze posouvat vodorovně v listové části pole se seznamem.|
|[CComboBox::GetItemData](#getitemdata)|Načte 32bitovou hodnotu dodanou aplikací přidruženou k zadané položce pole se seznamem.|
|[CComboBox::GetItemDataPtr](#getitemdataptr)|Načte 32bitový ukazatel dodaný aplikací, který je přidružen k zadané položce pole se seznamem.|
|[CComboBox::GetItemHeight](#getitemheight)|Načte výšku položek seznamu v poli se seznamem.|
|[CComboBox::GetLBText](#getlbtext)|Získá řetězec ze seznamu pole se seznamem.|
|[CComboBox::GetLBTextLen](#getlbtextlen)|Získá délku řetězce v seznamu pole se seznamem.|
|[CComboBox::GetLocale](#getlocale)|Načte identifikátor národního prostředí pro pole se seznamem.|
|[CComboBox::GetMinVisible](#getminvisible)|Získá minimální počet viditelných položek v rozevíracím seznamu aktuální pole se seznamem.|
|[CComboBox::GetTopIndex](#gettopindex)|Vrátí index první viditelné položky v části seznamu pole se seznamem.|
|[CComboBox::InitStorage](#initstorage)|Předalokuje bloky paměti pro položky a řetězce v části seznamu pole se seznamem.|
|[CComboBox::Vložit řetězec](#insertstring)|Vloží řetězec do seznamu pole se seznamem.|
|[CComboBox::LimitText](#limittext)|Omezuje délku textu, který může uživatel zadat do ovládacího prvku upravit pole se seznamem.|
|[CComboBox::MeasureItem](#measureitem)|Volat rámci k určení pole se seznamem rozměry při vytvoření pole se seznamem nakreslené vlastníka.|
|[CComboBox::Paste](#paste)|Vloží data ze schránky do ovládacího prvku pro úpravy v aktuální pozici kurzoru. Data se vkládají pouze v případě, že schránka obsahuje data v CF_TEXT formátu.|
|[CComboBox::ResetContent](#resetcontent)|Odebere všechny položky ze seznamu a upravit ovládací prvek pole se seznamem.|
|[CComboBox::SelectString](#selectstring)|Vyhledá řetězec v seznamu pole se seznamem a pokud je řetězec nalezen, vybere řetězec v seznamu a zkopíruje řetězec do ovládacího prvku pro úpravy.|
|[CComboBox::SetCueBanner](#setcuebanner)|Nastaví text upozornění, který se zobrazí pro ovládací prvek pole se seznamem.|
|[CComboBox::SetCurSel](#setcursel)|Vybere řetězec v seznamu pole se seznamem.|
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|Nastaví minimální povolenou šířku pro část rozevíracího seznamu pole se seznamem.|
|[CComboBox::SetEditsel](#seteditsel)|Vybere znaky v ovládacím prvku pro úpravy pole se seznamem.|
|[CComboBox::SetExtendedUI](#setextendedui)|Vybere výchozí uživatelské rozhraní nebo rozšířené uživatelské rozhraní pro pole se seznamem, které má CBS_DROPDOWN nebo CBS_DROPDOWNLIST stylu.|
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|Nastaví šířku v obrazových bodech, kterou lze posouvat vodorovně v listové části pole se seznamem.|
|[CComboBox::SetItemData](#setitemdata)|Nastaví 32bitovou hodnotu přidruženou k zadané položce v poli se seznamem.|
|[CComboBox::SetItemDataPtr](#setitemdataptr)|Nastaví 32bitový ukazatel přidružený k zadané položce v poli se seznamem.|
|[CComboBox::SetItemHeight](#setitemheight)|Nastaví výšku položek seznamu v poli se seznamem nebo výšku části ovládacího prvku pro úpravy (nebo statického textu) pole se seznamem.|
|[CComboBox::SetLocale](#setlocale)|Nastaví identifikátor národního prostředí pro pole se seznamem.|
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|Nastaví minimální počet viditelných položek v rozevíracím seznamu aktuálního pole se seznamem.|
|[CComboBox::SetTopIndex](#settopindex)|Sděluje část seznamu pole se seznamem, aby se položka se zadaným indexem v horní části zobrazila.|
|[CComboBox::ShowDropDown](#showdropdown)|Zobrazí nebo skryje seznam pole se seznamem, které má CBS_DROPDOWN nebo CBS_DROPDOWNLIST stylu.|

## <a name="remarks"></a>Poznámky

Pole se seznamem se skládá ze seznamu v kombinaci se statickým ovládacím prvkem nebo ovládacím prvkem úprav. Část ovládacího prvku v seznamu může být zobrazena vždy nebo může být rozevíraná pouze v případě, že uživatel vybere šipku rozevíracího seznamu vedle ovládacího prvku.

Aktuálně vybraná položka (pokud existuje) v seznamu je zobrazena ve statickém ovládacím prvku nebo ovládacím prvku pro úpravy. Kromě toho pokud pole se seznamem obsahuje styl rozevíracího seznamu, může uživatel zadat počáteční znak jedné z položek v seznamu a seznam, pokud je viditelný, zvýrazní další položku s tímto počátečním znakem.

Následující tabulka porovnává tři styly pole se [seznamem](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles).

|Styl|Kdy je seznam viditelný|Statický nebo upravit ovládací prvek|
|-----------|-------------------------------|-----------------------------|
|Jednoduchý|Vždy|Upravit|
|Rozevírací uzlovací|Při pádu dolů|Upravit|
|Rozevírací seznam|Při pádu dolů|Statická|

Objekt můžete `CComboBox` vytvořit buď ze šablony dialogu, nebo přímo v kódu. V obou případech nejprve `CComboBox` volání konstruktoru k vytvoření objektu; `CComboBox` pak volání [Vytvořit](#create) členská funkce vytvořit ovládací `CComboBox` prvek a připojit jej k objektu.

Pokud chcete zpracovávat zprávy s oznámením systému Windows odeslané polem `CDialog`se seznamem do nadřazené položky (obvykle třída odvozená z ), přidejte do nadřazené třídy pro každou zprávu funkci položky mapy zprávy a členské funkce obslužné rutiny zprávy.

Každá položka mapy zpráv má následující podobu:

**ON\_**_Oznámení_ **(** _id_, _memberFxn_ **)**

kde `id` určuje ID podřízeného okna ovládacího prvku se `memberFxn` seznamem, který odesílá oznámení, a je název nadřazené členské funkce, kterou jste napsali pro zpracování oznámení.

Prototyp funkce nadřazeného objektu je následující:

**afx_msg** `void` afx_msg `memberFxn` **( );**

Pořadí, ve kterém budou odeslána určitá oznámení, nelze předpovědět. Zejména může dojít k CBN_SELCHANGE oznámení před nebo po oznámení CBN_CLOSEUP.

Potenciální položky mapy zpráv jsou následující:

- ON_CBN_CLOSEUP (Windows 3.1 a novější.) Seznam pole se seznamem byl uzavřen. Tato zpráva s oznámením není odeslána pro pole se seznamem, které má [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl.

- ON_CBN_DBLCLK Uživatel poklepe na řetězec v seznamu pole se seznamem. Tato zpráva s oznámením je odeslána pouze pro pole se seznamem se stylem CBS_SIMPLE. U pole se seznamem se stylem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nemůže dojít k poklepání, protože jedno kliknutí skryje seznam.

- ON_CBN_DROPDOWN Seznam pole se seznamem se chystá rozbalit (být viditelný). Tato zpráva s oznámením může nastat pouze pro pole se seznamem se stylem CBS_DROPDOWN nebo CBS_DROPDOWNLIST.

- ON_CBN_EDITCHANGE Uživatel provedl akci, která mohla změnit text v části se seznamem pro úpravy a ovládací prvek. Na rozdíl od CBN_EDITUPDATE zprávy je tato zpráva odeslána po aktualizaci obrazovky systémem Windows. Není odeslána, pokud pole se seznamem má CBS_DROPDOWNLIST styl.

- ON_CBN_EDITUPDATE Část pole se seznamem se chystá zobrazit změněný text. Tato zpráva s oznámením je odeslána po naformátovaném textu ovládacího prvku, ale před zobrazením textu. Není odeslána, pokud pole se seznamem má CBS_DROPDOWNLIST styl.

- ON_CBN_ERRSPACE Pole se seznamem nemůže přidělit dostatek paměti pro splnění konkrétního požadavku.

- ON_CBN_SELENDCANCEL (Windows 3.1 a novější.) Označuje, že výběr uživatele by měl být zrušen. Uživatel klepne na položku a potom klepne na jiné okno nebo ovládací prvek skrýt seznam pole se seznamem. Tato zpráva s oznámením je odeslána před CBN_CLOSEUP oznámení, které označuje, že výběr uživatele by měl být ignorován. Zpráva CBN_SELENDCANCEL nebo CBN_SELENDOK oznámení je odeslána i v případě, že CBN_CLOSEUP oznámení není odeslána (jako v případě pole se seznamem s CBS_SIMPLE stylem).

- ON_CBN_SELENDOK Uživatel vybere položku a potom stiskne klávesu ENTER nebo klepne na klávesu ŠIPKA DOLŮ, aby skryl seznam pole se seznamem. Tato zpráva s oznámením je odeslána před CBN_CLOSEUP zprávu označující, že výběr uživatele by měl být považován za platný. Zpráva CBN_SELENDCANCEL nebo CBN_SELENDOK oznámení je odeslána i v případě, že CBN_CLOSEUP oznámení není odeslána (jako v případě pole se seznamem s CBS_SIMPLE stylem).

- ON_CBN_KILLFOCUS Pole se seznamem ztrácí vstupní zaostření.

- ON_CBN_SELCHANGE Výběr v seznamu pole se seznamem se chystá změnit v důsledku toho, že uživatel klikne do seznamu nebo změní výběr pomocí kláves se šipkami. Při zpracování této zprávy lze text v ovládacím prvku upravit pole `GetLBText` se seznamem načíst pouze prostřednictvím nebo jinou podobnou funkcí. `GetWindowText`nelze použít.

- ON_CBN_SETFOCUS Pole se seznamem obdrží vstupní zaostření.

Pokud vytvoříte `CComboBox` objekt v dialogovém okně (prostřednictvím prostředku dialogového okna), `CComboBox` objekt se automaticky zničí, když uživatel zavře dialogové okno.

Pokud vložíte `CComboBox` objekt do jiného objektu okna, není nutné jej zničit. Pokud vytvoříte `CComboBox` objekt v zásobníku, je automaticky zničen. Pokud vytvoříte `CComboBox` objekt na haldě pomocí **nové** funkce, musíte volat **delete** na objekt zničit při zničení pole se seznamem systému Windows.

**Poznámka:** Pokud chcete zpracovávat WM_KEYDOWN a WM_CHAR zprávy, musíte podtřídit ovládací prvky pro úpravy a seznam pole se seznamem, odvodit třídy z `CEdit` a `CListBox`a přidat obslužné rutiny pro tyto zprávy do odvozených tříd. Další informace naleznete v [tématu CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="ccomboboxaddstring"></a><a name="addstring"></a>CComboBox::Přidat řetězec

Přidá řetězec do seznamu pole se seznamem.

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*lpszString*<br/>
Odkazuje na řetězec ukončený hodnotou null, který má být přidán.

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota větší nebo rovna 0, je index založený na nule na řetězec v seznamu. Vrácená hodnota je CB_ERR pokud dojde k chybě; vrácená hodnota je CB_ERRSPACE pokud není k dispozici dostatek místa pro uložení nového řetězce.

### <a name="remarks"></a>Poznámky

Pokud seznam nebyl vytvořen s [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylem, řetězec je přidán na konec seznamu. V opačném případě je řetězec vložen do seznamu a seznam je seřazen.

> [!NOTE]
> Tato funkce není ovládacím `ComboBoxEx` prvkem systému Windows podporována. Další informace o tomto ovládacím prvku naleznete v [tématu ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) v sadě Windows SDK.

Chcete-li vložit řetězec do určitého umístění v seznamu, použijte členovou funkci [InsertString.](#insertstring)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

## <a name="ccomboboxccombobox"></a><a name="ccombobox"></a>CComboBox::CComboBox

Vytvoří `CComboBox` objekt.

```
CComboBox();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

## <a name="ccomboboxclear"></a><a name="clear"></a>CComboBox::Vymazat

Odstraní (vymaže) aktuální výběr, pokud existuje, v ovládacím prvku upravit pole se seznamem.

```cpp
void Clear();
```

### <a name="remarks"></a>Poznámky

Chcete-li odstranit aktuální výběr a umístit odstraněný obsah do schránky, použijte členskou funkci [Vyjmout.](#cut)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

## <a name="ccomboboxcompareitem"></a><a name="compareitem"></a>CComboBox::Porovnatpoložku

Volat rámci k určení relativní pozice nové položky v seznamu části seřazené vlastníka draw pole se seznamem.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parametry

*lpCompareItemStruct*<br/>
Dlouhý ukazatel na strukturu [COMPAREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-compareitemstruct)

### <a name="return-value"></a>Návratová hodnota

Označuje relativní polohu dvou položek popsaných ve `COMPAREITEMSTRUCT` struktuře. Může to být některá z následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|- 1|Položka 1 seřadí před bodem 2.|
|0|Položka 1 a položka 2 se řadí stejně.|
|1|Položka 1 seřadí za položkou 2.|

Viz [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) pro `COMPAREITEMSTRUCT`popis .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádné. Pokud vytvoříte pole se seznamem kreslení vlastníka s LBS_SORT stylu, musíte přepsat tuto členskou funkci, abyste pomohli při řazení nových položek přidaných do seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

## <a name="ccomboboxcopy"></a><a name="copy"></a>CComboBox::Kopírovat

Zkopíruje aktuální výběr, pokud existuje, v ovládacím prvku upravit pole se seznamem do schránky ve formátu CF_TEXT.

```cpp
void Copy();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

## <a name="ccomboboxcreate"></a><a name="create"></a>CComboBox::Vytvořit

Vytvoří pole se seznamem a `CComboBox` připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl pole se seznamem. Použijte libovolnou kombinaci [stylů se seznamem](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) na pole.

*Rect*<br/>
Ukazuje na polohu a velikost pole se seznamem. Může být [rect](/windows/win32/api/windef/ns-windef-rect) struktura `CRect` nebo objekt.

*pParentWnd*<br/>
Určuje nadřazené okno pole se `CDialog`seznamem (obvykle a). Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CComboBox` dvou krocích. Nejprve zavolejte konstruktoru `Create`a potom volání , který vytvoří pole `CComboBox` se seznamem systému Windows a připojí jej k objektu.

Při `Create` spuštění odesílá systém Windows [zprávy WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)a [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) do pole se seznamem.

Tyto zprávy jsou ve výchozím nastavení zpracovány členy [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)a [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) v `CWnd` základní třídě. Chcete-li rozšířit výchozí zpracování zpráv, odvodit třídu z `CComboBox`, přidejte mapu zpráv do nové třídy a přepsat předchozí funkce obsluhy zprávy. Přepište `OnCreate`, například provést potřebnou inicializaci pro novou třídu.

Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) u ovládacího prvku se seznamem. :

- WS_CHILD vždy

- WS_VISIBLE Obvykle

- WS_DISABLED Zřídka

- WS_VSCROLL Přidání svislého posouvání do seznamu v poli se seznamem

- WS_HSCROLL Přidání vodorovného posouvání pro seznam v poli se seznamem

- WS_GROUP Chcete-li seskupit ovládací prvky

- WS_TABSTOP Chcete-li zahrnout pole se seznamem v pořadí tabulátorů

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

## <a name="ccomboboxcut"></a><a name="cut"></a>CComboBox::Vyjmout

Odstraní (vyjme) aktuální výběr, pokud existuje, v ovládacím prvku úprav se seznamem a zkopíruje odstraněný text do schránky ve formátu CF_TEXT.

```cpp
void Cut();
```

### <a name="remarks"></a>Poznámky

Chcete-li odstranit aktuální výběr bez umístění odstraněného textu do schránky, zavolejte členskou funkci [Vymazat.](#clear)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

## <a name="ccomboboxdeleteitem"></a><a name="deleteitem"></a>CComboBox::DeleteItem

Volat rámci při uživatel odstraní položku z objektu kreslení `CComboBox` vlastníka nebo zničí pole se seznamem.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDeleteItemStruct*<br/>
Dlouhý ukazatel na strukturu [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) systému Windows, která obsahuje informace o odstraněné položce. Viz [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) popis této struktury.

### <a name="remarks"></a>Poznámky

Výchozí implementace této funkce neprovede žádné provádění. Přepište tuto funkci a podle potřeby překreslete pole se seznamem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

## <a name="ccomboboxdeletestring"></a><a name="deletestring"></a>CComboBox::DeleteString

Odstraní položku v pozici *nIndex* z pole se seznamem.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje index řetězce, který má být odstraněn.

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota větší nebo rovna 0, pak je počet řetězců zbývající v seznamu. Vrácená hodnota je CB_ERR pokud *nIndex* určuje index větší než počet položek v seznamu.

### <a name="remarks"></a>Poznámky

Všechny položky následující *po nIndex* nyní přesunout dolů o jednu pozici. Pokud například pole se seznamem obsahuje dvě položky, odstranění první položky způsobí, že zbývající položka bude nyní na první pozici. *nIndex*=0 pro položku na první pozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

## <a name="ccomboboxdir"></a><a name="dir"></a>CComboBox::Dir

Přidá seznam názvů souborů nebo jednotek do seznamu pole se seznamem.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parametry

*attr*<br/>
Může být libovolná kombinace hodnot **výčtu** popsaných v [CFile::GetStatus](../../mfc/reference/cfile-class.md#getstatus) nebo libovolnou kombinaci následujících hodnot:

- DDL_READWRITE soubor lze číst nebo zapisovat do.

- DDL_READONLY soubor lze číst z, ale není zapsán.

- DDL_HIDDEN soubor je skrytý a nezobrazuje se v seznamu adresářů.

- DDL_SYSTEM soubor je systémový soubor.

- DDL_DIRECTORY Název určený *lpszWildCard* určuje adresář.

- DDL_ARCHIVE soubor byl archivován.

- DDL_DRIVES Zahrnout všechny jednotky, které odpovídají názvu určenému *lpszWildCard*.

- DDL_EXCLUSIVE exkluzivní vlajka. Pokud je nastaven výhradní příznak, jsou uvedeny pouze soubory zadaného typu. V opačném případě jsou kromě "normálních" souborů uvedeny soubory zadaného typu.

*lpszDivoká karta*<br/>
Odkazuje na řetězec specifikace souboru. Řetězec může obsahovat zástupné znaky\*(například *. ).

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota větší nebo rovna 0, je index posledního názvu souboru, který byl přidán do seznamu, na základě nuly. Vrácená hodnota je CB_ERR pokud dojde k chybě; vrácená hodnota je CB_ERRSPACE, pokud není k dispozici dostatek místa pro uložení nových řetězců.

### <a name="remarks"></a>Poznámky

Tato funkce není ovládacím `ComboBoxEx` prvkem systému Windows podporována. Další informace o tomto ovládacím prvku naleznete v [tématu ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

## <a name="ccomboboxdrawitem"></a><a name="drawitem"></a>CComboBox::DrawItem

Volat rámci při změně vizuální aspekt pole se seznamem vlastníka draw.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na strukturu [DRAWITEMSTRUCT,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) která obsahuje informace o požadovaném typu výkresu.

### <a name="remarks"></a>Poznámky

Člen `itemAction` `DRAWITEMSTRUCT` struktury definuje kreslicí akci, která má být provedena. Viz [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) popis této struktury.

Ve výchozím nastavení tato členská funkce neprovede žádné. Přepsat tuto členovou funkci implementovat výkres `CComboBox` pro objekt nakreslení vlastníka. Před ukončením této členské funkce by aplikace měla obnovit všechny objekty rozhraní grafického zařízení (GDI) vybrané pro kontext zobrazení dodaný v *lpDrawItemStruct*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

## <a name="ccomboboxfindstring"></a><a name="findstring"></a>CComboBox::FindString

Najde, ale nevybere první řetězec, který obsahuje zadanou předponu v seznamu pole se seznamem.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Obsahuje nulový index položky před první položkou, která má být prohledána. Když hledání dosáhne dolní části seznamu, pokračuje od horní části seznamu zpět k položce určené *nStartAfter*. Pokud -1, celý seznam je prohledán od začátku.

*lpszString*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje předponu, kterou chcete vyhledat. Hledání je nezávislé na malých a velkých písmenech, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota větší nebo rovna 0, je index založený na nule odpovídající položky. Je CB_ERR, pokud hledání bylo neúspěšné.

### <a name="remarks"></a>Poznámky

Tato funkce není ovládacím `ComboBoxEx` prvkem systému Windows podporována. Další informace o tomto ovládacím prvku naleznete v [tématu ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

## <a name="ccomboboxfindstringexact"></a><a name="findstringexact"></a>CComboBox::FindStringExact

Volání `FindStringExact` členské funkce najít první seznam-box řetězec (v poli se seznamem), který odpovídá řetězec zadaný v *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parametry

*nIndexStart*<br/>
Určuje nulový index položky před první položkou, která má být prohledána. Když hledání dosáhne dolní části seznamu, pokračuje od horní části seznamu zpět k položce určené *nIndexStart*. Pokud *nIndexStart* je -1, celý seznam je prohledán od začátku.

*lpszNajít*<br/>
Odkazuje na řetězec ukončený hodnotou null, který má být vyhledán. Tento řetězec může obsahovat úplný název souboru, včetně přípony. Hledání není rozlišování velkých a malých písmen, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index odpovídající položky založený na nule nebo CB_ERR, pokud bylo hledání neúspěšné.

### <a name="remarks"></a>Poznámky

Pokud pole se seznamem byla vytvořena se stylem owner-draw, ale bez [CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu, `FindStringExact` pokusí se porovnat doubleword hodnotu s hodnotou *lpszFind*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

## <a name="ccomboboxgetcomboboxinfo"></a><a name="getcomboboxinfo"></a>CComboBox::GetComboBoxInfo

Načte informace `CComboBox` pro objekt.

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>Parametry

*pcbi řekl:*<br/>
Ukazatel na strukturu [COMBOBOXINFO.](/windows/win32/api/winuser/ns-winuser-comboboxinfo)

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Tato členská funkce emuluje funkce [zprávy CB_GETCOMBOBOXINFO,](/windows/win32/Controls/cb-getcomboboxinfo) jak je popsáno v sadě Windows SDK.

## <a name="ccomboboxgetcount"></a><a name="getcount"></a>CComboBox::GetCount

Volání této členské funkce načíst počet položek v seznamu část pole se seznamem.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek Vrácený počet je o jednu větší než hodnota indexu poslední položky (index je založen na nule). Je CB_ERR, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

## <a name="ccomboboxgetcuebanner"></a><a name="getcuebanner"></a>CComboBox::GetCueBanner

Získá tágo text, který se zobrazí pro ovládací prvek pole se seznamem.

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpszText*|[out] Ukazatel na vyrovnávací paměť, která obdrží text hlavičky cue.|
|*cchText*|[v] Velikost vyrovnávací paměti, na kterou odkazuje parametr *lpszText.*|

### <a name="return-value"></a>Návratová hodnota

V první přetížení [CString](../../atl-mfc-shared/using-cstring.md) objekt, který obsahuje text cue banner, pokud existuje; jinak `CString` objekt, který má nulovou délku.

-nebo-

V druhé přetížení TRUE Pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Cue text je výzva, která se zobrazí ve vstupní oblasti ovládacího prvku pole se seznamem. Cue text se zobrazí, dokud uživatel zadá vstup.

Tato metoda odešle [zprávu CB_GETCUEBANNER,](/windows/win32/Controls/cb-getcuebanner) která je popsána v sadě Windows SDK.

## <a name="ccomboboxgetcursel"></a><a name="getcursel"></a>CComboBox::GetCurSel

Volání této členské funkce k určení, která položka v poli se seznamem je vybrána.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Index aktuálně vybrané položky založený na nule v seznamu pole se seznamem nebo CB_ERR, pokud není vybrána žádná položka.

### <a name="remarks"></a>Poznámky

`GetCurSel`vrátí index do seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

## <a name="ccomboboxgetdroppedcontrolrect"></a><a name="getdroppedcontrolrect"></a>CComboBox::GetDroppedControlRect

Volání `GetDroppedControlRect` členské funkce načíst souřadnice obrazovky viditelného (vynechání) seznamu rozevíracího pole se seznamem.

```cpp
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Odkazuje na [rect strukturu,](/windows/win32/api/windef/ns-windef-rect) která má přijímat souřadnice.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

## <a name="ccomboboxgetdroppedstate"></a><a name="getdroppedstate"></a>CComboBox::GetDroppedState

Volání `GetDroppedState` členské funkce k určení, zda je zobrazen seznam seznamu rozbalovací pole (spadl dolů).

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je seznam viditelný; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

## <a name="ccomboboxgetdroppedwidth"></a><a name="getdroppedwidth"></a>CComboBox::GetDroppedWidth

Volánítéto funkce načíst minimální přípustnou šířku v pixelech seznamu pole se seznamem.

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, minimální povolená šířka v pixelech; jinak CB_ERR.

### <a name="remarks"></a>Poznámky

Tato funkce se vztahuje pouze na pole se seznamem se [stylem CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

Ve výchozím nastavení je minimální povolená šířka rozevíracího seznamu 0. Minimální přípustnou šířku lze nastavit voláním [SetDroppedWidth](#setdroppedwidth). Při zobrazení list-box pole se seznamem, jeho šířka je větší z minimální přípustné šířky nebo pole se seznamem šířky.

### <a name="example"></a>Příklad

  Viz příklad pro [SetDroppedWidth](#setdroppedwidth).

## <a name="ccomboboxgeteditsel"></a><a name="geteditsel"></a>CComboBox::GetEditSel

Získá počáteční a koncové pozice znaků aktuálního výběru v ovládacím prvku upravit pole se seznamem.

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>Návratová hodnota

32bitová hodnota, která obsahuje počáteční pozici ve slově nízkého řádu a pozici prvního nevybraného znaku po ukončení výběru ve slově nejvyššího řádu. Pokud je tato funkce použita v poli se seznamem bez ovládacího prvku pro úpravy, je vrácena CB_ERR.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

## <a name="ccomboboxgetextendedui"></a><a name="getextendedui"></a>CComboBox::GetExtendedUI

Volání `GetExtendedUI` členské funkce k určení, zda pole se seznamem má výchozí uživatelské rozhraní nebo rozšířené uživatelské rozhraní.

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má pole se seznamem rozšířené uživatelské rozhraní; jinak 0.

### <a name="remarks"></a>Poznámky

Rozšířené uživatelské rozhraní lze identifikovat následujícími způsoby:

- Klepnutím na statické ovládací prvek se zobrazí seznam pouze pro pole se seznamem se [stylem CBS_DROPDOWNLIST.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

- Stisknutím klávesy ŠIPKA DOLŮ se zobrazí seznam (F4 je zakázáno).

Posouvání ve statickém ovládacím prvku je zakázáno, pokud není seznam položek viditelný (klávesy se šipkami jsou zakázány).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

## <a name="ccomboboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CComboBox::GetHorizontalExtent

Načte z pole se seznamem šířku v obrazových bodech, o kterou lze část pole se seznamem posouvat vodorovně.

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>Návratová hodnota

Posuvná šířka části pole se seznamem v obrazových bodech.

### <a name="remarks"></a>Poznámky

To platí pouze v případě, že seznam část pole se seznamem má vodorovný posuvník.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

## <a name="ccomboboxgetitemdata"></a><a name="getitemdata"></a>CComboBox::GetItemData

Načte 32bitovou hodnotu dodanou aplikací přidruženou k zadané položce pole se seznamem.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje nulový index položky v seznamu pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

32bitová hodnota přidružená k položce nebo CB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

32bitovou hodnotu lze nastavit pomocí parametru *dwItemData* volání členské funkce [SetItemData.](#setitemdata) Členská `GetItemDataPtr` funkce použijte, pokud je 32bitová hodnota, která má být načtena,**ukazatelem** <strong>\*</strong>( void ).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

## <a name="ccomboboxgetitemdataptr"></a><a name="getitemdataptr"></a>CComboBox::GetItemDataPtr

Načte 32bitovou hodnotu dodanou aplikací přidruženou k zadané položce pole se seznamem jako ukazatel (**void** <strong>\*</strong>).

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje nulový index položky v seznamu pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Načte ukazatel nebo -1, pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

## <a name="ccomboboxgetitemheight"></a><a name="getitemheight"></a>CComboBox::GetItemHeight

Volání `GetItemHeight` členské funkce načíst výšku položek seznamu v poli se seznamem.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje součást pole se seznamem, jehož výška má být načtena. Pokud je parametr *nIndex* -1, načte se výška části ovládacího prvku pro úpravy (nebo statického textu) pole se seznamem. Pokud pole se seznamem obsahuje [styl CBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) *nIndex* určuje nulový index položky seznamu, jehož výška má být načtena. V opačném případě *nIndex* by měla být nastavena na 0.

### <a name="return-value"></a>Návratová hodnota

Výška zadané položky v obrazových bodech v poli se seznamem. Vrácená hodnota je CB_ERR pokud dojde k chybě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

## <a name="ccomboboxgetlbtext"></a><a name="getlbtext"></a>CComboBox::GetLBText

Získá řetězec ze seznamu pole se seznamem.

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
Obsahuje nulový index řetězce seznamu, který má být zkopírován.

*lpszText*<br/>
Odkazuje na vyrovnávací paměť, která má přijmout řetězec. Vyrovnávací paměť musí mít dostatek místa pro řetězec a ukončující znak null.

*rString*<br/>
Odkaz na `CString`.

### <a name="return-value"></a>Návratová hodnota

Délka (v bajtů) řetězce, s výjimkou ukončující ho znaku null. Pokud *nIndex* nezadává platný index, vrácená hodnota je CB_ERR.

### <a name="remarks"></a>Poznámky

Druhý formulář této členské funkce `CString` vyplní objekt textem položky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

## <a name="ccomboboxgetlbtextlen"></a><a name="getlbtextlen"></a>CComboBox::GetLBTextLen

Získá délku řetězce v seznamu pole se seznamem.

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje nulový index řetězce seznamu.

### <a name="return-value"></a>Návratová hodnota

Délka řetězce v bajtů, s výjimkou ukončující ho l.I. Pokud *nIndex* nezadává platný index, vrácená hodnota je CB_ERR.

### <a name="example"></a>Příklad

  Viz příklad pro [CComboBox::GetLBText](#getlbtext).

## <a name="ccomboboxgetlocale"></a><a name="getlocale"></a>CComboBox::GetLocale

Načte národní prostředí používané pole mno žepem.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota identifikátoru národního prostředí (LCID) pro řetězce v poli se seznamem.

### <a name="remarks"></a>Poznámky

Národní prostředí se používá například k určení pořadí řazení řetězců v seřazené pole se seznamem.

### <a name="example"></a>Příklad

  Viz příklad pro [CComboBox::SetLocale](#setlocale).

## <a name="ccomboboxgetminvisible"></a><a name="getminvisible"></a>CComboBox::GetMinVisible

Získá minimální počet viditelných položek v rozevíracím seznamu aktuální ovládací prvek pole se seznamem.

```
int GetMinVisible() const;
```

### <a name="return-value"></a>Návratová hodnota

Minimální počet viditelných položek v aktuálním rozevíracím seznamu.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu CB_GETMINVISIBLE,](/windows/win32/Controls/cb-setminvisible) která je popsána v sadě Windows SDK.

## <a name="ccomboboxgettopindex"></a><a name="gettopindex"></a>CComboBox::GetTopIndex

Načte index na základě nuly první viditelné položky v seznamu části pole se seznamem.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Návratová hodnota

Index první viditelné položky v seznamu v poli se seznamem, pokud je úspěšná, CB_ERR jinak.

### <a name="remarks"></a>Poznámky

Zpočátku je položka 0 v horní části seznamu, ale pokud je seznam posunut, může být nahoře jiná položka.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

## <a name="ccomboboxinitstorage"></a><a name="initstorage"></a>CComboBox::InitStorage

Přidělí paměť pro ukládání položek seznamu v části seznamu pole se seznamem.

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

Pokud je úspěšná, maximální počet položek, které seznam část pole se seznamem lze uložit před přerozdělení paměti je potřeba, jinak CB_ERRSPACE, což znamená, že není k dispozici dostatek paměti.

### <a name="remarks"></a>Poznámky

Volání této funkce před přidáním velkého počtu položek do `CComboBox`seznamu části .

Pouze systém Windows 95/98: Parametr *wParam* je omezen na 16bitové hodnoty. To znamená, že seznamy nemohou obsahovat více než 32 767 položek. Přestože je počet položek omezen, celková velikost položek v seznamu je omezena pouze dostupnou pamětí.

Tato funkce pomáhá urychlit inicializaci seznamů, které mají velký počet položek (více než 100). Předem přidělí zadané množství paměti tak, aby následné [funkce AddString](#addstring), [InsertString](#insertstring)a [Dir](#dir) zabíraly nejkratší možný čas. Můžete použít odhady pro parametry. Pokud nadhodnocujete, je přidělena některá další paměť; Pokud podceňujete, normální přidělení se používá pro položky, které překračují předpojitou částku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

## <a name="ccomboboxinsertstring"></a><a name="insertstring"></a>CComboBox::Vložit řetězec

Vloží řetězec do seznamu pole se seznamem.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index založený na nule na pozici v seznamu, který obdrží řetězec. Pokud je tento parametr -1, řetězec je přidán na konec seznamu.

*lpszString*<br/>
Odkazuje na řetězec ukončený hodnotou null, který má být vložen.

### <a name="return-value"></a>Návratová hodnota

Nula na základě indexu pozice, na které byl vložen řetězec. Vrácená hodnota je CB_ERR pokud dojde k chybě. Vrácená hodnota je CB_ERRSPACE pokud není k dispozici dostatek místa pro uložení nového řetězce.

### <a name="remarks"></a>Poznámky

Na rozdíl od členské `InsertString` funkce [AddString](#addstring) členská funkce nezpůsobí seřazení seznamu se stylem [CBS_SORT.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

> [!NOTE]
> Tato funkce není ovládacím `ComboBoxEx` prvkem systému Windows podporována. Další informace o tomto ovládacím prvku naleznete v [tématu ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

## <a name="ccomboboxlimittext"></a><a name="limittext"></a>CComboBox::LimitText

Omezuje délku textu v bajtech textu, který může uživatel zadat do ovládacího prvku úprav pole se seznamem.

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>Parametry

*nMaxChars*<br/>
Určuje délku (v bajtech) textu, který může uživatel zadat. Pokud je tento parametr 0, délka textu je nastavena na 65 535 bajtů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná. Pokud je voláno pro pole se seznamem se stylem [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo pro pole se seznamem bez ovládacího prvku úprav, vrácená hodnota je CB_ERR.

### <a name="remarks"></a>Poznámky

Pokud pole se seznamem nemá styl [CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles), nastavení limitu textu na větší než velikost ovládacího prvku úprav nebude mít žádný vliv.

`LimitText`omezuje pouze text, který může uživatel zadat. Nemá žádný vliv na žádný text, který je již v ovládacím prvku pro úpravy, když je zpráva odeslána, ani nemá vliv na délku textu zkopírovaného do ovládacího prvku pro úpravy, když je vybrán řetězec v seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

## <a name="ccomboboxmeasureitem"></a><a name="measureitem"></a>CComboBox::MeasureItem

Volat rámci při vytvoření pole se seznamem s stylem kreslení vlastníka.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Dlouhý ukazatel na strukturu [MEASUREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádné. Přepsat tuto členovou funkci `MEASUREITEMSTRUCT` a vyplňte strukturu informovat Windows o rozměrech seznamu v poli se seznamem. Pokud pole se seznamem je vytvořen s [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu, framework volá tuto členskou funkci pro každou položku v seznamu. V opačném případě se tento člen nazývá pouze jednou.

Použití CBS_OWNERDRAWFIXED stylu v poli se seznamem draw vlastníka vytvořeného `CWnd` pomocí členské funkce [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) zahrnuje další aspekty programování. Viz diskuse v [technické poznámce 14](../../mfc/tn014-custom-controls.md).

Viz [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) pro popis `MEASUREITEMSTRUCT` struktury.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

## <a name="ccomboboxpaste"></a><a name="paste"></a>CComboBox::Paste

Vloží data ze schránky do ovládacího prvku upravit pole se seznamem v aktuální pozici kurzoru.

```cpp
void Paste();
```

### <a name="remarks"></a>Poznámky

Data se vkládají pouze v případě, že schránka obsahuje data v CF_TEXT formátu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

## <a name="ccomboboxresetcontent"></a><a name="resetcontent"></a>CComboBox::ResetContent

Odebere všechny položky ze seznamu a upravit ovládací prvek pole se seznamem.

```cpp
void ResetContent();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

## <a name="ccomboboxselectstring"></a><a name="selectstring"></a>CComboBox::SelectString

Vyhledá řetězec v seznamu pole se seznamem, a pokud je řetězec nalezen, vybere řetězec v seznamu a zkopíruje jej do ovládacího prvku pro úpravy.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Obsahuje nulový index položky před první položkou, která má být prohledána. Když hledání dosáhne dolní části seznamu, pokračuje od horní části seznamu zpět k položce určené *nStartAfter*. Pokud -1, celý seznam je prohledán od začátku.

*lpszString*<br/>
Odkazuje na řetězec s ukončeným hodnotou null, který obsahuje předponu, kterou chcete vyhledat. Hledání je nezávislé na malých a velkých písmenech, takže tento řetězec může obsahovat libovolnou kombinaci velkých a malých písmen.

### <a name="return-value"></a>Návratová hodnota

Index s nulovým základem vybrané položky, pokud byl řetězec nalezen. Pokud hledání bylo neúspěšné, vrácená hodnota je CB_ERR a aktuální výběr se nezmění.

### <a name="remarks"></a>Poznámky

Řetězec je vybrán pouze v případě, že jeho počáteční znaky (od počátečního bodu) odpovídají znakům v řetězci předpony.

Všimněte `SelectString` si, že i `FindString` členské funkce `SelectString` najít řetězec, ale členské funkce také vybere řetězec.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

## <a name="ccomboboxsetcuebanner"></a><a name="setcuebanner"></a>CComboBox::SetCueBanner

Nastaví text upozornění, který se zobrazí pro ovládací prvek pole se seznamem.

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpszText*|[v] Ukazatel na vyrovnávací paměť s ukončenou hodnotou null, která obsahuje text cue.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Cue text je výzva, která se zobrazí ve vstupní oblasti ovládacího prvku pole se seznamem. Cue text se zobrazí, dokud uživatel zadá vstup.

Tato metoda odešle [zprávu CB_SETCUEBANNER,](/windows/win32/Controls/cb-setcuebanner) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou *m_combobox*, která se používá k programovému přístupu k ovládacímu prvku pole se seznamem. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Příklad

Následující příklad kódu nastaví tágo banner pro ovládací prvek pole se seznamem.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsetcursel"></a><a name="setcursel"></a>CComboBox::SetCurSel

Vybere řetězec v seznamu pole se seznamem.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parametry

*nVyberte*<br/>
Určuje nulový index řetězce, který chcete vybrat. Pokud -1, bude odebrán libovolný aktuální výběr v seznamu a ovládací prvek pro úpravy je vymazán.

### <a name="return-value"></a>Návratová hodnota

Index na základě nuly položky vybrané, pokud je zpráva úspěšná. Vrácená hodnota je CB_ERR pokud *nSelect* je větší než počet položek v seznamu nebo pokud *nSelect* je nastavena na -1, která vymaže výběr.

### <a name="remarks"></a>Poznámky

V případě potřeby se seznam posune řetězec do zobrazení (pokud je seznam viditelný). Text v ovládacím prvku upravit pole se seznamem se změní tak, aby odrážel nový výběr. Všechny předchozí výběr y v seznamu budou odebrány.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

## <a name="ccomboboxsetdroppedwidth"></a><a name="setdroppedwidth"></a>CComboBox::SetDroppedWidth

Voláním této funkce nastavte minimální přípustnou šířku v pixelech seznamu pole se seznamem.

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>Parametry

*nŠířka*<br/>
Minimální povolená šířka části pole se seznamem v pixelech.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, nová šířka seznamu, jinak CB_ERR.

### <a name="remarks"></a>Poznámky

Tato funkce se vztahuje pouze na pole se seznamem se [stylem CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

Ve výchozím nastavení je minimální povolená šířka rozevíracího seznamu 0. Při zobrazení list-box pole se seznamem, jeho šířka je větší z minimální přípustné šířky nebo pole se seznamem šířky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

## <a name="ccomboboxseteditsel"></a><a name="seteditsel"></a>CComboBox::SetEditsel

Vybere znaky v ovládacím prvku pro úpravy pole se seznamem.

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>Parametry

*nStartChar*<br/>
Určuje počáteční pozici. Pokud je počáteční pozice nastavena na -1, bude odebrán libovolný existující výběr.

*nEndChar*<br/>
Určuje koncovou pozici. Pokud je koncová pozice nastavena na -1, je vybrán veškerý text od počáteční pozice k poslednímu znaku v ovládacím prvku pro úpravy.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je členská funkce úspěšná; jinak 0. Je CB_ERR, `CComboBox` pokud má [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl nebo nemá seznam.

### <a name="remarks"></a>Poznámky

Pozice jsou od nuly. Chcete-li vybrat první znak ovládacího prvku pro úpravy, zadejte počáteční pozici 0. Koncová pozice je pro znak těsně za posledním znakem, který chcete vybrat. Chcete-li například vybrat první čtyři znaky ovládacího prvku pro úpravy, použijte počáteční pozici 0 a koncovou pozici 4.

> [!NOTE]
> Tato funkce není ovládacím `ComboBoxEx` prvkem systému Windows podporována. Další informace o tomto ovládacím prvku naleznete v [tématu ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) v sadě Windows SDK.

### <a name="example"></a>Příklad

  Viz příklad pro [CComboBox::GetEditSel](#geteditsel).

## <a name="ccomboboxsetextendedui"></a><a name="setextendedui"></a>CComboBox::SetExtendedUI

Voláním `SetExtendedUI` členské funkce vyberte výchozí uživatelské rozhraní nebo rozšířené uživatelské rozhraní pro pole se seznamem, které má [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>Parametry

*bExtended*<br/>
Určuje, zda má pole se seznamem používat rozšířené uživatelské rozhraní nebo výchozí uživatelské rozhraní. Hodnota TRUE vybere rozšířené uživatelské rozhraní; hodnota FALSE vybere standardní uživatelské rozhraní.

### <a name="return-value"></a>Návratová hodnota

CB_OKAY pokud je operace úspěšná, nebo CB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Rozšířené uživatelské rozhraní lze identifikovat následujícími způsoby:

- Klepnutím na statické ovládací prvek se zobrazí seznam pouze pro pole se seznamem se stylem CBS_DROPDOWNLIST.

- Stisknutím klávesy ŠIPKA DOLŮ se zobrazí seznam (F4 je zakázáno).

Posouvání ve statickém ovládacím prvku je zakázáno, pokud není seznam položek viditelný (klávesy se šipkami jsou zakázány).

### <a name="example"></a>Příklad

  Viz příklad pro [CComboBox::GetExtendedUI](#getextendedui).

## <a name="ccomboboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CComboBox::SetHorizontalExtent

Nastaví šířku v obrazových bodech, o kterou lze pole se seznamem posouvat vodorovně.

```cpp
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>Parametry

*nRozsah*<br/>
Určuje počet obrazových bodů, o které lze pole se seznamem posouvat vodorovně.

### <a name="remarks"></a>Poznámky

Pokud je šířka seznamu menší než tato hodnota, vodorovný posuvník bude vodorovně posouvat položky v seznamu. Pokud je šířka seznamu rovna nebo větší než tato hodnota, je vodorovný posuvník skrytý nebo, pokud má pole se seznamem [CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, je zakázán.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

## <a name="ccomboboxsetitemdata"></a><a name="setitemdata"></a>CComboBox::SetItemData

Nastaví 32bitovou hodnotu přidruženou k zadané položce v poli se seznamem.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index založený na nule pro položku, která má být nastavena.

*dwItemData*<br/>
Obsahuje novou hodnotu přidružit k položce.

### <a name="return-value"></a>Návratová hodnota

CB_ERR pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Členské `SetItemDataPtr` funkce použijte, pokud má být 32bitová položka ukazatelem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

## <a name="ccomboboxsetitemdataptr"></a><a name="setitemdataptr"></a>CComboBox::SetItemDataPtr

Nastaví 32bitovou hodnotu přidruženou k zadané položce v poli se seznamem jako zadaný ukazatel (**void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Obsahuje index založený na nule k položce.

*Pdata*<br/>
Obsahuje ukazatel, který chcete přidružit k položce.

### <a name="return-value"></a>Návratová hodnota

CB_ERR pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Tento ukazatel zůstává platný po dobu životnosti pole se seznamem, i když relativní pozice položky v poli se seznamem se může změnit při přidávání nebo odebírání položek. Proto index položky v poli můžete změnit, ale ukazatel zůstává spolehlivý.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

## <a name="ccomboboxsetitemheight"></a><a name="setitemheight"></a>CComboBox::SetItemHeight

Voláním `SetItemHeight` členské funkce nastavte výšku položek seznamu v poli se seznamem nebo výšku části ovládacího prvku pro úpravy (nebo statického textu) pole se seznamem.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje, zda je nastavena výška položek seznamu nebo výška části pole se seznamem, která se knímá ovládací prvek úpravy (nebo statický text).

Pokud pole se seznamem obsahuje [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl, *nIndex* určuje nulový index položky seznamu, jehož výška má být nastavena; v opačném případě *nIndex* musí být 0 a výška všech položek seznamu bude nastavena.

Pokud *nIndex* je -1, výška edit-control nebo static-text část pole se seznamem je třeba nastavit.

*cyItemHeight*<br/>
Určuje výšku komponenty se seznamem identifikované *nIndex*.

### <a name="return-value"></a>Návratová hodnota

CB_ERR, pokud je index nebo výška neplatná; jinak 0.

### <a name="remarks"></a>Poznámky

Výška edit-control (nebo static-text) část pole se seznamem je nastavena nezávisle na výšce položek seznamu. Aplikace musí zajistit, aby výška části ovládacího prvku pro úpravy (nebo statického textu) nebyla menší než výška určité položky seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

## <a name="ccomboboxsetlocale"></a><a name="setlocale"></a>CComboBox::SetLocale

Nastaví identifikátor národního prostředí pro toto pole se seznamem.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parametry

*nNewLocale*<br/>
Nová hodnota identifikátoru národního prostředí (LCID), která má být nastavena pro pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnota identifikátoru národního prostředí (LCID) pro toto pole se seznamem.

### <a name="remarks"></a>Poznámky

Pokud `SetLocale` není volána, výchozí národní prostředí je získán ze systému. Toto výchozí národní prostředí systému lze upravit pomocí regionální (nebo mezinárodní) aplikace Ovládacích panelů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

## <a name="ccomboboxsetminvisibleitems"></a><a name="setminvisibleitems"></a>CComboBox::SetMinVisibleItems

Nastaví minimální počet viditelných položek v rozevíracím seznamu aktuálního ovládacího prvku pole se seznamem.

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iMinVisible*|[v] Určuje minimální počet viditelných položek.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu CB_SETMINVISIBLE,](/windows/win32/Controls/cb-setminvisible) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou *m_combobox*, která se používá k programovému přístupu k ovládacímu prvku pole se seznamem. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Příklad

Následující příklad kódu vloží 20 položek do rozevíracího seznamu ovládacího prvku pole se seznamem. Pak určuje, že minimálně 10 položek se zobrazí, když uživatel stiskne šipku rozevíracího seznamu.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsettopindex"></a><a name="settopindex"></a>CComboBox::SetTopIndex

Zajišťuje, že určitá položka je viditelná v části seznamu pole se seznamem.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Určuje nulový index položky seznamu.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud je úspěšná, nebo CB_ERR, pokud dojde k chybě.

### <a name="remarks"></a>Poznámky

Systém posouvá seznam, dokud se v horní části seznamu nezobrazí položka určená *parametrem nIndex* nebo dokud nebude dosaženo maximálního rozsahu posouvání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

## <a name="ccomboboxshowdropdown"></a><a name="showdropdown"></a>CComboBox::ShowDropDown

Zobrazí nebo skryje seznam pole se seznamem, ve které je [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) nebo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.

```cpp
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>Parametry

*bShowIt*<br/>
Určuje, zda má být rozevírací seznam zobrazen nebo skrytý. Hodnota TRUE zobrazuje seznam. Hodnota FALSE skryje seznam.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení se v poli se seznamem tohoto stylu zobrazí seznam.

Tato členská funkce nemá žádný vliv na pole se seznamem vytvořené [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.

### <a name="example"></a>Příklad

  Viz příklad pro [CComboBox::GetDroppedState](#getdroppedstate).

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)<br/>
[CEdit – třída](../../mfc/reference/cedit-class.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic – třída](../../mfc/reference/cstatic-class.md)<br/>
[CDialog – třída](../../mfc/reference/cdialog-class.md)
