---
title: Atributu CTabCtrl – třída
ms.date: 11/04/2016
f1_keywords:
- CTabCtrl
- AFXCMN/CTabCtrl
- AFXCMN/CTabCtrl::CTabCtrl
- AFXCMN/CTabCtrl::AdjustRect
- AFXCMN/CTabCtrl::Create
- AFXCMN/CTabCtrl::CreateEx
- AFXCMN/CTabCtrl::DeleteAllItems
- AFXCMN/CTabCtrl::DeleteItem
- AFXCMN/CTabCtrl::DeselectAll
- AFXCMN/CTabCtrl::DrawItem
- AFXCMN/CTabCtrl::GetCurFocus
- AFXCMN/CTabCtrl::GetCurSel
- AFXCMN/CTabCtrl::GetExtendedStyle
- AFXCMN/CTabCtrl::GetImageList
- AFXCMN/CTabCtrl::GetItem
- AFXCMN/CTabCtrl::GetItemCount
- AFXCMN/CTabCtrl::GetItemRect
- AFXCMN/CTabCtrl::GetItemState
- AFXCMN/CTabCtrl::GetRowCount
- AFXCMN/CTabCtrl::GetToolTips
- AFXCMN/CTabCtrl::HighlightItem
- AFXCMN/CTabCtrl::HitTest
- AFXCMN/CTabCtrl::InsertItem
- AFXCMN/CTabCtrl::RemoveImage
- AFXCMN/CTabCtrl::SetCurFocus
- AFXCMN/CTabCtrl::SetCurSel
- AFXCMN/CTabCtrl::SetExtendedStyle
- AFXCMN/CTabCtrl::SetImageList
- AFXCMN/CTabCtrl::SetItem
- AFXCMN/CTabCtrl::SetItemExtra
- AFXCMN/CTabCtrl::SetItemSize
- AFXCMN/CTabCtrl::SetItemState
- AFXCMN/CTabCtrl::SetMinTabWidth
- AFXCMN/CTabCtrl::SetPadding
- AFXCMN/CTabCtrl::SetToolTips
helpviewer_keywords:
- CTabCtrl [MFC], CTabCtrl
- CTabCtrl [MFC], AdjustRect
- CTabCtrl [MFC], Create
- CTabCtrl [MFC], CreateEx
- CTabCtrl [MFC], DeleteAllItems
- CTabCtrl [MFC], DeleteItem
- CTabCtrl [MFC], DeselectAll
- CTabCtrl [MFC], DrawItem
- CTabCtrl [MFC], GetCurFocus
- CTabCtrl [MFC], GetCurSel
- CTabCtrl [MFC], GetExtendedStyle
- CTabCtrl [MFC], GetImageList
- CTabCtrl [MFC], GetItem
- CTabCtrl [MFC], GetItemCount
- CTabCtrl [MFC], GetItemRect
- CTabCtrl [MFC], GetItemState
- CTabCtrl [MFC], GetRowCount
- CTabCtrl [MFC], GetToolTips
- CTabCtrl [MFC], HighlightItem
- CTabCtrl [MFC], HitTest
- CTabCtrl [MFC], InsertItem
- CTabCtrl [MFC], RemoveImage
- CTabCtrl [MFC], SetCurFocus
- CTabCtrl [MFC], SetCurSel
- CTabCtrl [MFC], SetExtendedStyle
- CTabCtrl [MFC], SetImageList
- CTabCtrl [MFC], SetItem
- CTabCtrl [MFC], SetItemExtra
- CTabCtrl [MFC], SetItemSize
- CTabCtrl [MFC], SetItemState
- CTabCtrl [MFC], SetMinTabWidth
- CTabCtrl [MFC], SetPadding
- CTabCtrl [MFC], SetToolTips
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
ms.openlocfilehash: a0ca4cbad48c420250fe39e131de5504b1ae70f3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502480"
---
# <a name="ctabctrl-class"></a>Atributu CTabCtrl – třída

Poskytuje funkce pro běžný ovládací prvek karty Windows.

## <a name="syntax"></a>Syntaxe

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CTabCtrl::CTabCtrl](#ctabctrl)|`CTabCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CTabCtrl::AdjustRect](#adjustrect)|Vypočítá oblast zobrazení ovládacího prvku karta s daným obdélníkem okna nebo vypočítá obdélník okna, který odpovídá dané oblasti zobrazení.|
|[CTabCtrl::Create](#create)|Vytvoří ovládací prvek karta a připojí ho k instanci `CTabCtrl` objektu.|
|[CTabCtrl::CreateEx](#createex)|Vytvoří ovládací prvek karta se zadanými rozšířenými styly Windows a připojí ho k instanci `CTabCtrl` objektu.|
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Odebere všechny položky z ovládacího prvku karta.|
|[CTabCtrl::DeleteItem](#deleteitem)|Odebere položku z ovládacího prvku karta.|
|[CTabCtrl::DeselectAll](#deselectall)|Zruší nastavení položek v ovládacím prvku karta, což vymaže všechny, které byly stisknuty.|
|[CTabCtrl::DrawItem](#drawitem)|Nakreslí určenou položku ovládacího prvku karta.|
|[CTabCtrl::GetCurFocus](#getcurfocus)|Načte kartu s aktuálním fokusem ovládacího prvku karta.|
|[CTabCtrl::GetCurSel](#getcursel)|Určuje aktuálně vybranou kartu v ovládacím prvku karta.|
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Načte rozšířené styly, které jsou aktuálně používány pro ovládací prvek karta.|
|[CTabCtrl::GetImageList](#getimagelist)|Načte seznam obrázků přidružený k ovládacímu prvku karta.|
|[CTabCtrl::GetItem](#getitem)|Načte informace o kartě v ovládacím prvku karta.|
|[CTabCtrl::GetItemCount](#getitemcount)|Načte počet karet v ovládacím prvku karta.|
|[CTabCtrl::GetItemRect](#getitemrect)|Načte ohraničující obdélník pro kartu v ovládacím prvku karta.|
|[CTabCtrl::GetItemState](#getitemstate)|Načte stav označené položky ovládacího prvku karta.|
|[CTabCtrl::GetRowCount](#getrowcount)|Načte aktuální počet řádků karet v ovládacím prvku karta.|
|[CTabCtrl::GetToolTips](#gettooltips)|Načte popisovač ovládacího prvku popisu tlačítka přidruženého k ovládacímu prvku karta.|
|[CTabCtrl::HighlightItem](#highlightitem)|Nastaví zvýrazněný stav položky karty.|
|[CTabCtrl::HitTest](#hittest)|Určuje, která karta se zobrazí na zadané pozici obrazovky.|
|[CTabCtrl::InsertItem](#insertitem)|Vloží novou kartu do ovládacího prvku karta.|
|[CTabCtrl::RemoveImage](#removeimage)|Odebere obrázek ze seznamu obrázků ovládacího prvku karta.|
|[CTabCtrl::SetCurFocus](#setcurfocus)|Nastaví fokus na určenou kartu v ovládacím prvku karta.|
|[CTabCtrl::SetCurSel](#setcursel)|Vybere kartu v ovládacím prvku karta.|
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené styly pro ovládací prvek karta.|
|[CTabCtrl::SetImageList](#setimagelist)|Přiřadí seznam obrázků k ovládacímu prvku karta.|
|[CTabCtrl::SetItem](#setitem)|Nastaví některé nebo všechny atributy karty.|
|[CTabCtrl::SetItemExtra](#setitemextra)|Nastaví počet bajtů na kartu rezervovanou pro data definovaná aplikací v ovládacím prvku karta.|
|[CTabCtrl::SetItemSize](#setitemsize)|Nastaví šířku a výšku položky.|
|[CTabCtrl::SetItemState](#setitemstate)|Nastaví stav označené položky ovládacího prvku karta.|
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Nastaví minimální šířku položek v ovládacím prvku karta.|
|[CTabCtrl::SetPadding](#setpadding)|Nastaví velikost prostoru (odsazení) kolem ikony a popisku každé karty v ovládacím prvku karta.|
|[CTabCtrl::SetToolTips](#settooltips)|Přiřadí ovládacímu prvku karta ovládací prvek popis tlačítka.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek na kartě" je podobný oddělovačům v poznámkovém bloku nebo jmenovkám v souboru CAB. Pomocí ovládacího prvku karta může aplikace definovat více stránek pro stejnou oblast okna nebo dialogového okna. Každá stránka se skládá ze sady informací nebo skupiny ovládacích prvků, které aplikace zobrazí, když uživatel vybere odpovídající kartu. Speciální typ ovládacího prvku karta zobrazuje karty, které vypadají jako tlačítka. Po kliknutí na tlačítko by se místo zobrazení stránky měl okamžitě provést příkaz.

Tento ovládací prvek (a `CTabCtrl` třída) je k dispozici pouze pro programy, které jsou spuštěny v systémech Windows 95/98 a Windows NT verze 3,51 a novější.

Další informace o použití `CTabCtrl`naleznete v tématu [Controls](../../mfc/controls-mfc.md) and [using atributu CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="adjustrect"></a>Atributu CTabCtrl:: AdjustRect

Vypočítá oblast zobrazení ovládacího prvku karta s daným obdélníkem okna nebo vypočítá obdélník okna, který odpovídá dané oblasti zobrazení.

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*bLarger*<br/>
Určuje, která operace se má provést. Pokud má tento parametr hodnotu TRUE, *lpRect* určuje obdélník zobrazení a získá odpovídající rámeček okna. Pokud má tento parametr hodnotu FALSE, *lpRect* určuje obdélník okna a získá odpovídající obdélník zobrazení.

*lpRect*<br/>
Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která určuje daný obdélník a získá počítaný obdélník.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

##  <a name="create"></a>Atributu CTabCtrl:: Create

Vytvoří ovládací prvek karta a připojí ho k instanci `CTabCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl ovládacího prvku karta. Použití libovolné kombinace [stylů ovládacího prvku karta](/windows/win32/Controls/tab-control-styles), které jsou popsány v Windows SDK. Seznam stylů oken, které lze také použít pro ovládací prvek, naleznete v části **poznámky** .

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku karta. Může to být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo struktura [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku karta, obvykle a `CDialog`. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku karta.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byla inicializace objektu úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

`CTabCtrl` Vytvoříte objekt ve dvou krocích. Nejprve volejte konstruktor a potom zavolejte `Create`, čímž se vytvoří ovládací prvek karta a připojí se `CTabCtrl` k objektu.

Kromě stylů ovládacího prvku karta můžete použít následující styly okna pro ovládací prvek karta:

- WS_CHILD vytvoří podřízené okno, které představuje ovládací prvek karta. Nelze použít se stylem WS_POPUP.

- WS_VISIBLE vytvoří ovládací prvek karta, který je zpočátku viditelný.

- WS_DISABLED vytvoří okno, které je zpočátku zakázané.

- WS_GROUP Určuje první ovládací prvek skupiny ovládacích prvků, ve kterém může uživatel přejít z jednoho ovládacího prvku na další pomocí kláves se šipkami. Všechny ovládací prvky definované pomocí stylu WS_GROUP po prvním ovládacím prvku patří do stejné skupiny. Následující ovládací prvek se stylem WS_GROUP ukončí skupinu stylů a spustí další skupinu (to znamená, že jedna skupina končí, kde začíná další).

- WS_TABSTOP Určuje jeden z libovolných ovládacích prvků, pomocí nichž může uživatel přesunout pomocí klávesy TAB. Klávesa TAB přesune uživatele k dalšímu ovládacímu prvku určenému stylem WS_TABSTOP.

Chcete-li vytvořit ovládací prvek karta se rozšířenými styly oken, zavolejte [atributu CTabCtrl:: CreateEx](#createex) namísto `Create`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

##  <a name="createex"></a>Atributu CTabCtrl:: CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ho k `CTabCtrl` objektu.

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
Určuje styl ovládacího prvku karta. Použití libovolné kombinace [stylů ovládacího prvku karta](/windows/win32/Controls/tab-control-styles), které jsou popsány v Windows SDK. Seznam stylů oken, které lze použít také pro ovládací prvek, naleznete v části **poznámky** v tématu [Vytvoření](#create) .

*OBD*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) popisující velikost a umístění okna, které má být vytvořeno, v souřadnicích klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládacímu prvku.

*nID*<br/>
ID podřízeného okna ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné v opačném případě 0.

### <a name="remarks"></a>Poznámky

Použijte `CreateEx` místo příkaz [vytvořit](#create) pro použití rozšířených stylů Windows, které jsou určené **WS_EX_** rozšířeným stylem Windows.

`CreateEx`Vytvoří ovládací prvek s rozšířenými styly Windows specifikovanými pomocí *dwExStyle*. Nastavte rozšířené styly specifické pro ovládací prvek pomocí [SetExtendedStyle](#setextendedstyle). Například použijte `CreateEx` k nastavení takových stylů jako WS_EX_CONTEXTHELP, ale použijte `SetExtendedStyle` k nastavení takových stylů jako TCS_EX_FLATSEPARATORS. Další informace naleznete v tématu styly popsané v [ovládacím prvku karta rozšířené styly](/windows/win32/Controls/tab-control-extended-styles) v Windows SDK.

##  <a name="ctabctrl"></a>  CTabCtrl::CTabCtrl

`CTabCtrl` Vytvoří objekt.

```
CTabCtrl();
```

##  <a name="deleteallitems"></a>  CTabCtrl::DeleteAllItems

Odebere všechny položky z ovládacího prvku karta.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

##  <a name="deleteitem"></a>  CTabCtrl::DeleteItem

Odebere zadanou položku z ovládacího prvku karta.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Nulová hodnota položky, která se má odstranit

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

##  <a name="deselectall"></a>  CTabCtrl::DeselectAll

Zruší nastavení položek v ovládacím prvku karta, což vymaže všechny, které byly stisknuty.

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Parametry

*fExcludeFocus*<br/>
Příznak, který určuje rozsah odvýběru položky. Je-li tento parametr nastaven na hodnotu FALSE, budou vynulována všechna tlačítka karet. Pokud je nastavená na hodnotu TRUE, resetují se všechny položky karty s výjimkou aktuálně vybraného.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall), jak je popsáno v Windows SDK.

##  <a name="drawitem"></a>Atributu CTabCtrl::D rawItem

Volá se rozhraním, když se změní vizuální aspekt ovládacího prvku karty s vykreslováním vlastníka.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na strukturu [DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) popisující položku, která se má vykreslit.

### <a name="remarks"></a>Poznámky

`itemAction` Člen`DRAWITEMSTRUCT` struktury definuje akci kreslení, která má být provedena.

Ve výchozím nastavení tato členská funkce neprovede žádnou akci. Přepište tuto členskou funkci pro implementaci vykreslování pro objekt vykreslený `CTabCtrl` vlastníkem.

Aplikace by měla obnovit všechny objekty GDI (Graphic Device Interface) vybrané pro kontext zobrazení zadaný v *lpDrawItemStruct* před ukončením této členské funkce.

##  <a name="getcurfocus"></a>Atributu CTabCtrl:: GetCurFocus

Načte index karty s aktuálním fokusem.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Návratová hodnota

Index karty založený na nule s aktuálním fokusem.

##  <a name="getcursel"></a>  CTabCtrl::GetCurSel

Načte aktuálně vybranou kartu v ovládacím prvku karta.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule vybrané karty, pokud je to úspěšné, nebo-1, pokud není vybraná žádná karta

##  <a name="getextendedstyle"></a>Atributu CTabCtrl:: GetExtendedStyle

Načte rozšířené styly, které jsou aktuálně používány pro ovládací prvek karta.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Návratová hodnota

Představuje rozšířené styly, které se aktuálně používají pro ovládací prvek karta. Tato hodnota je kombinací rozšířených [stylů ovládacího prvku karta](/windows/win32/Controls/tab-control-extended-styles), jak je popsáno v Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle), jak je popsáno v Windows SDK.

##  <a name="getimagelist"></a>  CTabCtrl::GetImageList

Načte seznam obrázků, který je přidružený k ovládacímu prvku karta.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na seznam obrázků ovládacího prvku karta; v opačném případě hodnota NULL.

##  <a name="getitem"></a>Atributu CTabCtrl:: GetItem

Načte informace o kartě v ovládacím prvku karta.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Index karty založený na nule.

*pTabCtrlItem*<br/>
Ukazatel na strukturu [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , která slouží k zadání informací, které se mají načíst. Slouží také k získání informací o kartě. Tato struktura je použita s `InsertItem`členskými funkcemi, `GetItem`a `SetItem` .

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je úspěšná; V opačném případě NEPRAVDA.

### <a name="remarks"></a>Poznámky

Po odeslání zprávy `mask` člen Určuje, které atributy se mají vrátit. Pokud člen Určuje hodnotu TCIF_TEXT `pszText` , člen musí obsahovat adresu vyrovnávací paměti, která obdrží text položky, a `cchTextMax` člen musí určit velikost vyrovnávací paměti. `mask`

- `mask`

   Hodnota určující, `TCITEM` které členy struktury mají být načteny nebo nastaveny. Tento člen může být nula nebo kombinace následujících hodnot:

   - `pszText` TCIF_TEXT člen je platný.

   - `iImage` TCIF_IMAGE člen je platný.

   - `lParam` TCIF_PARAM člen je platný.

   - TCIF_RTLREADING text `pszText` je zobrazený pomocí pořadí čtení zprava doleva v systémech hebrejštiny a arabského textu.

   - `dwState` TCIF_STATE člen je platný.

- `pszText`

   Ukazatel na řetězec zakončený hodnotou null obsahující text karty, pokud struktura obsahuje informace o kartě. Pokud struktura přijímá informace, určuje tento člen adresu vyrovnávací paměti, která obdrží text karty.

- `cchTextMax`

   Velikost vyrovnávací paměti, na `pszText`kterou ukazuje. Tento člen je ignorován, pokud struktura nepřijímá informace.

- `iImage`Index do seznamu obrázků ovládacího prvku karta nebo-1, pokud není k dispozici žádný obrázek pro kartu.

- `lParam`

   Data definovaná aplikací přidružená k kartě Pokud je na kartě více než čtyři bajty dat definovaných aplikací, musí aplikace definovat strukturu a použít ji místo `TCITEM` struktury. Prvním členem struktury definované aplikací musí být struktura [TCITEMHEADER](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw). Struktura je shodná `TCITEM` se`lParam` strukturou, ale bez členu. `TCITEMHEADER` Rozdíl mezi velikostí struktury a velikostí `TCITEMHEADER` struktury by měl být stejný jako počet nadbytečných bajtů na jednu kartu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

##  <a name="getitemcount"></a>  CTabCtrl::GetItemCount

Načte počet karet v ovládacím prvku karta.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v ovládacím prvku karta.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertySheet –:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemrect"></a>Atributu CTabCtrl:: GetItemRect

Načte ohraničující obdélník pro určenou kartu v ovládacím prvku karta.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Index vycházející z položky karty od nuly

*lpRect*<br/>
Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která přijímá ohraničující obdélník karty. Tyto souřadnice používají aktuální režim mapování zobrazení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertySheet –:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemstate"></a>Atributu CTabCtrl:: GetItemState

Načte stav položky ovládacího prvku karta identifikované pomocí *nItem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Číslo indexu vycházející z nuly položky, pro kterou chcete načíst informace o stavu.

*dwMask*<br/>
Maska určující, který z příznaků stavu položky má být vrácen. Seznam hodnot naleznete v tématu maska člen struktury [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , jak je popsáno v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu DWORD, která přijímá informace o stavu. Může to být jedna z následujících hodnot:

|Value|Popis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Je vybrána položka ovládacího prvku karta.|
|TCIS_HIGHLIGHTED|Položka ovládacího prvku karta je zvýrazněna a karta a text jsou vykresleny pomocí aktuální barvy zvýraznění. Při použití zvýraznění barvy se jedná o skutečnou interpolaci, nikoli o barevnou barvu.|

### <a name="remarks"></a>Poznámky

Stav položky je určen `dwState` členem `TCITEM` struktury.

##  <a name="getrowcount"></a>  CTabCtrl::GetRowCount

Načte aktuální počet řádků v ovládacím prvku karta.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet řádků karet v ovládacím prvku karta.

### <a name="remarks"></a>Poznámky

Pouze ovládací prvky karty, které mají styl TCS_MULTILINE, mohou mít více řádků karet.

##  <a name="gettooltips"></a>Atributu CTabCtrl:: GetToolTips

Načte popisovač ovládacího prvku popisu tlačítka přidruženého k ovládacímu prvku karta.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač ovládacího prvku popis tlačítka, pokud je úspěšný; jinak NULL.

### <a name="remarks"></a>Poznámky

Ovládací prvek karta vytvoří ovládací prvek popis tlačítka, pokud má styl TCS_TOOLTIPS. Ovládací prvek popis tlačítka lze také přiřadit ovládacímu prvku karta pomocí `SetToolTips` členské funkce.

##  <a name="highlightitem"></a>Atributu CTabCtrl:: HighlightItem

Nastaví zvýrazněný stav položky karty.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Parametry

*idItem*<br/>
Index vycházející z položky ovládacího prvku karta od nuly

*fHighlight*<br/>
Hodnota určující stav zvýraznění, který má být nastaven. Pokud je tato hodnota TRUE, karta se zvýrazní. Pokud má hodnotu FALSE, karta se nastaví na výchozí stav.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje [TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem)zprávy Win32, jak je popsáno v Windows SDK.

##  <a name="hittest"></a>Atributu CTabCtrl:: HitTest

Určuje, která karta se nachází na zadané pozici obrazovky.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Parametry

*pHitTestInfo*<br/>
Ukazatel na strukturu [TCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo) , jak je popsáno v Windows SDK, která určuje umístění obrazovky, které se má testovat.

### <a name="return-value"></a>Návratová hodnota

Vrátí index na kartě od nuly nebo hodnotu-1, pokud na zadané pozici není karta.

##  <a name="insertitem"></a>Atributu CTabCtrl:: InsertItem

Vloží novou kartu do existujícího ovládacího prvku karta.

```
LONG InsertItem(
    int nItem,
    TCITEM* pTabCtrlItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem,
    int nImage);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam,
    DWORD dwState,
    DWORD dwStateMask);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Index nové karty založený na nule.

*pTabCtrlItem*<br/>
Ukazatel na strukturu [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , která určuje atributy karty.

*lpszItem*<br/>
Adresa řetězce zakončeného hodnotou null, který obsahuje text karty

*nImage*<br/>
Index založený na nule obrázku, který má být vložen ze seznamu obrázků.

*nMask*<br/>
Určuje, `TCITEM` které atributy struktury se mají nastavit. Může být nula nebo kombinace následujících hodnot:

- `pszText` TCIF_TEXT člen je platný.

- `iImage` TCIF_IMAGE člen je platný.

- TCIF_PARAM člen *lParam* je platný.

- TCIF_RTLREADING text `pszText` je zobrazený pomocí pořadí čtení zprava doleva v systémech hebrejštiny a arabského textu.

- TCIF_STATE člen *dwState* je platný.

*lParam*<br/>
Data definovaná aplikací přidružená k kartě

*dwState*<br/>
Určuje hodnoty pro stavy položky. Další informace najdete v tématu [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) v Windows SDK.

*dwStateMask*<br/>
Určuje, které stavy mají být nastaveny. Další informace najdete v tématu [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Index nové karty založený na nule, pokud je úspěšný; v opačném případě-1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

##  <a name="removeimage"></a>  CTabCtrl::RemoveImage

Odebere zadaný obrázek ze seznamu obrázků ovládacího prvku karta.

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Parametry

*nImage*<br/>
Index s nulovým základem obrázku, který má být odebrán.

### <a name="remarks"></a>Poznámky

Ovládací prvek karta aktualizuje index obrázku každé karty, takže každá karta zůstane přidružená ke stejné imagi.

##  <a name="setcurfocus"></a>Atributu CTabCtrl:: SetCurFocus

Nastaví fokus na určenou kartu v ovládacím prvku karta.

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Určuje index karty, která získá fokus.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus), jak je popsáno v Windows SDK.

##  <a name="setcursel"></a>  CTabCtrl::SetCurSel

Vybere kartu v ovládacím prvku karta.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Index vycházející z položky, která má být vybrána.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule dříve vybrané karty v případě úspěchu, jinak – 1.

### <a name="remarks"></a>Poznámky

Ovládací prvek karta neposílá zprávu oznámení TCN_SELCHANGING nebo TCN_SELCHANGE, pokud je vybrána karta pomocí této funkce. Tato oznámení se odesílají pomocí WM_NOTIFY, když uživatel klikne nebo použije klávesnici ke změně karet.

##  <a name="setextendedstyle"></a>Atributu CTabCtrl:: SetExtendedStyle

Nastaví rozšířené styly pro ovládací prvek karta.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Parametry

*dwNewStyle*<br/>
Hodnota, která určuje kombinaci rozšířených stylů ovládacího prvku karta

*dwExMask*<br/>
Hodnota DWORD, která určuje, které styly v *dwNewStyle* mají být ovlivněny. Budou změněny pouze rozšířené styly v *dwExMask* . Všechny ostatní styly budou udržovány tak, jak jsou. Pokud má tento parametr hodnotu nula, bude to mít vliv na všechny styly v *dwNewStyle* .

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD obsahující předchozí [Rozšířené styly ovládacího prvku karta](/windows/win32/Controls/tab-control-extended-styles), jak je popsáno v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Tato členská funkce implementuje chování zprávy Win32 [TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle), jak je popsáno v Windows SDK.

##  <a name="setimagelist"></a>Atributu CTabCtrl:: SetImageList

Přiřadí seznam obrázků k ovládacímu prvku karta.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Ukazatel na seznam obrázků, který má být přiřazen ovládacímu prvku karta.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na předchozí seznam obrázků nebo hodnotu NULL, pokud neexistuje žádný předchozí seznam obrázků.

##  <a name="setitem"></a>Atributu CTabCtrl:: SetItem

Nastaví některé nebo všechny atributy karty.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Index položky založený na nule.

*pTabCtrlItem*<br/>
Ukazatel na strukturu [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , která obsahuje atributy nové položky. `mask` Člen Určuje, které atributy se mají nastavit. Pokud člen Určuje hodnotu TCIF_TEXT `pszText` , je členem adresa řetězce zakončeného hodnotou null a `cchTextMax` člen je ignorován. `mask`

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [GetItem](#getitem).

##  <a name="setitemextra"></a>Atributu CTabCtrl:: SetItemExtra

Nastaví počet bajtů na kartu rezervovanou pro data definovaná aplikací v ovládacím prvku karta.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Počet nadbytečných bajtů, které mají být nastaveny.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra), jak je popsáno v Windows SDK.

##  <a name="setitemsize"></a>Atributu CTabCtrl:: SetItemSize

Nastaví šířku a výšku položek ovládacího prvku karta.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Nová šířka a výška (v pixelech) položek ovládacího prvku karta.

### <a name="return-value"></a>Návratová hodnota

Vrátí starou šířku a výšku položek ovládacího prvku karta.

##  <a name="setitemstate"></a>Atributu CTabCtrl:: SetItemState

Nastaví stav položky ovládacího prvku karta, kterou identifikuje *nItem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Číslo indexu vycházející z nuly položky, pro kterou chcete nastavit informace o stavu.

*dwMask*<br/>
Maska určující, který příznak stavu položky má být nastaven. Seznam hodnot naleznete v tématu maska člen struktury [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , jak je popsáno v Windows SDK.

*dwState*<br/>
Odkaz na hodnotu DWORD obsahující informace o stavu. Může to být jedna z následujících hodnot:

|Value|Popis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Je vybrána položka ovládacího prvku karta.|
|TCIS_HIGHLIGHTED|Položka ovládacího prvku karta je zvýrazněna a karta a text jsou vykresleny pomocí aktuální barvy zvýraznění. Při použití zvýraznění barvy se jedná o skutečnou interpolaci, nikoli o barevnou barvu.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

##  <a name="setmintabwidth"></a>Atributu CTabCtrl:: SetMinTabWidth

Nastaví minimální šířku položek v ovládacím prvku karta.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Parametry

*cx*<br/>
Minimální šířka, která se má nastavit pro položku ovládacího prvku karta Pokud je tento parametr nastaven na hodnotu-1, bude ovládací prvek používat výchozí šířku tabulátoru.

### <a name="return-value"></a>Návratová hodnota

Předchozí Šířka karty minima

### <a name="return-value"></a>Návratová hodnota

Tato členská funkce implementuje chování zprávy Win32 [TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth), jak je popsáno v Windows SDK.

##  <a name="setpadding"></a>Atributu CTabCtrl:: SetPadding

Nastaví velikost prostoru (odsazení) kolem ikony a popisku každé karty v ovládacím prvku karta.

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
Nastaví velikost prostoru (odsazení) kolem ikony a popisku každé karty v ovládacím prvku karta.

##  <a name="settooltips"></a>Atributu CTabCtrl:: SetToolTips

Přiřadí ovládacímu prvku karta ovládací prvek popis tlačítka.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parametry

*pWndTip*<br/>
Popisovač ovládacího prvku popisu tlačítka

### <a name="remarks"></a>Poznámky

Můžete získat ovládací prvek popis tlačítka přidružený k ovládacímu prvku karta tím, že zavoláte `GetToolTips`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertySheet –:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl – třída](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl – třída](../../mfc/reference/clistctrl-class.md)
