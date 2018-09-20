---
title: Ctabctrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa7fd6b89ad4437397e0ff685400b7efe957eaca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421879"
---
# <a name="ctabctrl-class"></a>Ctabctrl – třída

Poskytuje funkce pro ovládací prvek běžné karty Windows.

## <a name="syntax"></a>Syntaxe

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CTabCtrl::CTabCtrl](#ctabctrl)|Vytvoří `CTabCtrl` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTabCtrl::AdjustRect](#adjustrect)|Vypočítá zadané obdélníku okna ovládacího prvku karta zobrazovanou oblast nebo vypočítá rámeček okna, která by odpovídala dané zobrazení plochy.|
|[CTabCtrl::Create](#create)|Vytvoří ovládací prvek karty a připojí ho k instanci `CTabCtrl` objektu.|
|[CTabCtrl::CreateEx](#createex)|Vytvoří ovládací prvek karty pomocí zadaného rozšířené styly Windows a připojí ho k instanci `CTabCtrl` objektu.|
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Odebere všechny položky z ovládacího prvku karta.|
|[CTabCtrl::DeleteItem](#deleteitem)|Odebere položku z karty ovládací prvek.|
|[CTabCtrl::DeselectAll](#deselectall)|Obnoví položky v ovládacím prvkem karta, zrušíte všechny, které byly zavedeny.|
|[CTabCtrl::DrawItem](#drawitem)|Vykreslí zadané položky ovládacího prvku karta.|
|[CTabCtrl::GetCurFocus](#getcurfocus)|Na kartě se zvýrazněným ovládacím prvkem karta načte.|
|[CTabCtrl::GetCurSel](#getcursel)|Určuje kartu aktuálně vybraného v ovládacím prvkem karta.|
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Rozšířené styly, které jsou právě používány pro ovládací prvek karta načte.|
|[CTabCtrl::GetImageList](#getimagelist)|Načte seznam obrázků, které jsou spojené s ovládacím prvkem karta.|
|[CTabCtrl::GetItem](#getitem)|Načte informace o kartě v ovládacím prvkem karta.|
|[CTabCtrl::GetItemCount](#getitemcount)|Získá počet karet v ovládacím prvku karty.|
|[CTabCtrl::GetItemRect](#getitemrect)|Načte ohraničující obdélník na kartě v ovládacím prvkem karta.|
|[CTabCtrl::GetItemState](#getitemstate)|Načte stav položky uvedené kartě ovládacího prvku.|
|[CTabCtrl::GetRowCount](#getrowcount)|Načte aktuální počet řádků karet v ovládacím prvkem karta.|
|[CTabCtrl::GetToolTips](#gettooltips)|Načte popisovač ovládacím prvkem popis tlačítka nástroj spojené s ovládacím prvkem karta.|
|[CTabCtrl::HighlightItem](#highlightitem)|Nastaví stav zvýraznění položky karty.|
|[CTabCtrl::HitTest](#hittest)|Určuje, které kartě, pokud existuje, je na pozici zadanou obrazovku.|
|[CTabCtrl::InsertItem](#insertitem)|Vloží na nové kartě v ovládacím prvkem karta.|
|[CTabCtrl::RemoveImage](#removeimage)|Odebere bitovou kopii ze seznamu obrázků ovládacího prvku karta.|
|[CTabCtrl::SetCurFocus](#setcurfocus)|Fokus se nastaví na zadanou kartu v ovládacím prvkem karta.|
|[CTabCtrl::SetCurSel](#setcursel)|Vybere na kartě v ovládacím prvkem karta.|
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené styly pro ovládací prvek karty.|
|[CTabCtrl::SetImageList](#setimagelist)|Seznam obrázků přiřadí ovládacím prvkem karta.|
|[CTabCtrl::SetItem](#setitem)|Nastaví některá nebo všechna na kartě atributy.|
|[CTabCtrl::SetItemExtra](#setitemextra)|Nastaví počet bajtů na kartě vyhrazené pro definovaného aplikací dat v ovládacím prvkem karta.|
|[CTabCtrl::SetItemSize](#setitemsize)|Nastaví šířku a výšku položky.|
|[CTabCtrl::SetItemState](#setitemstate)|Nastaví stav položky uvedené kartě ovládacího prvku.|
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Nastavuje minimální šířku položky v ovládacím prvkem karta.|
|[CTabCtrl::SetPadding](#setpadding)|Nastaví velikost místa (odsazení) kolem každé kartě ikona a popisek v ovládacím prvkem karta.|
|[CTabCtrl::SetToolTips](#settooltips)|Přiřadí ovládacím prvkem popis tlačítka nástroj ovládacím prvkem karta.|

## <a name="remarks"></a>Poznámky

"Ovládacím prvkem karta" je obdobou oddělovačů poznámkového bloku nebo popisky v souboru CAB. Pomocí ovládacího prvku Karta aplikace můžete definovat více stránek pro stejnou oblast okno nebo dialogového okna. Každá stránka obsahuje sadu informace nebo skupiny ovládacích prvků, které aplikace zobrazí, když uživatel vybere na odpovídající kartu. Zvláštní druh ovládací prvek karty zobrazí karty, které vypadají jako tlačítka. Kliknutím na tlačítko měli okamžitě provést příkaz místo zobrazení stránky.

Tento ovládací prvek (a tedy `CTabCtrl` třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95/98 a Windows NT verze 3.51 a vyšší.

Další informace o používání `CTabCtrl`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md) a [používání atributu CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

##  <a name="adjustrect"></a>  CTabCtrl::AdjustRect

Vypočítá zadané obdélníku okna ovládacího prvku karta zobrazovanou oblast nebo vypočítá rámeček okna, která by odpovídala dané zobrazení plochy.

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*bLarger*<br/>
Označuje, kterou operaci má provést. Pokud tento parametr má hodnotu TRUE, *lprect –* určuje zobrazovací obdélník a přijímat odpovídající rámeček okna. Pokud tento parametr má hodnotu FALSE, *lprect –* určuje rámeček okna a přijímat odpovídající zobrazovací obdélník.

*lprect –*<br/>
Ukazatel [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která určuje danou obdélník a přijímá počítaný obdélník.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

##  <a name="create"></a>  CTabCtrl::Create

Vytvoří ovládací prvek karty a připojí ho k instanci `CTabCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl ovládacího prvku karty. Použít libovolnou kombinaci [kartě – styly ovládacích prvků](/windows/desktop/Controls/tab-control-styles), které jsou popsány v sadě Windows SDK. Zobrazit **poznámky** seznam styly oken, které můžete provést také do ovládacího prvku.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku karty. Může být buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku karta, obvykle `CDialog`. Nesmí být NULL.

*nID*<br/>
Určuje ID ovládacího prvku karty.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se inicializace objektu byla úspěšná. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CTabCtrl` objektu ve dvou krocích. Nejprve volat konstruktor a poté zavolejte `Create`, což vytvoří ovládací prvek karty a připojí ho k `CTabCtrl` objektu.

Kromě – styly ovládacího prvku karta můžete použít následující styly oken do ovládacího prvku karta:

- WS_CHILD vytvoří podřízené okno, která představuje ovládací prvek karty. Nelze použít s WS_POPUP style.

- WS_VISIBLE vytvoří ovládací prvek karty, které je zpočátku viditelné.

- WS_DISABLED vytvoří okno, které je zpočátku zakázáno.

- WS_GROUP Určuje první prvek skupiny ovládacích prvků, ve kterých uživatel může přesouvat z jednoho ovládacího prvku na další pomocí kláves se šipkami. Všechny ovládací prvky definované ve stylu WS_GROUP po prvním ovládacím prvku, patří do stejné skupiny. Další ovládací prvek se stylem WS_GROUP končí skupině styl a začíná další skupinu (tedy. zakončení jedné skupiny kde začíná další).

- WS_TABSTOP Určuje jeden z několika ovládacích prvků, pomocí kterých uživatel může přecházet pomocí klávesy TAB. Klávesy TAB přesune uživatele na další ovládací prvek určený stylem WS_TABSTOP.

Chcete-li vytvořit ovládací prvek karty s rozšířené styly oken, zavolejte [CTabCtrl::CreateEx](#createex) místo `Create`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

##  <a name="createex"></a>  CTabCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ji k `CTabCtrl` objektu.

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
Určuje rozšířený styl ovládacího prvku vytváří. Seznam rozšířené styly Windows najdete v tématu *dwExStyle* parametr pro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) v sadě Windows SDK.

*dwStyle*<br/>
Určuje styl ovládacího prvku karty. Použít libovolnou kombinaci [kartě – styly ovládacích prvků](/windows/desktop/Controls/tab-control-styles), které jsou popsány v sadě Windows SDK. Zobrazit **poznámky** v [vytvořit](#create) seznam styly oken, které můžete provést také do ovládacího prvku.

*Rect*<br/>
Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující, velikost a umístění okna, které nelze v souřadnice klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, který je nadřazeného ovládacího prvku.

*nID*<br/>
ID ovládacího prvku podřízené okno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná jinak 0.

### <a name="remarks"></a>Poznámky

Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určené předponu rozšířeného stylu Windows **WS_EX_**.

`CreateEx` Vytvoří ovládací prvek s rozšířené styly Windows určené *dwExStyle*. Rozšířené styly specifické pro ovládací prvek pomocí sady [SetExtendedStyle](#setextendedstyle). Například použít `CreateEx` nastavit tyto styly jako WS_EX_CONTEXTHELP, ale použijte `SetExtendedStyle` nastavit jako tcs_ex_flatseparators – tyto styly. Další informace najdete v tématu styly podle [rozšířené styly ovládacího prvku karta](/windows/desktop/Controls/tab-control-extended-styles) v sadě Windows SDK.

##  <a name="ctabctrl"></a>  CTabCtrl::CTabCtrl

Vytvoří `CTabCtrl` objektu.

```
CTabCtrl();
```

##  <a name="deleteallitems"></a>  CTabCtrl::DeleteAllItems

Odebere všechny položky z ovládacího prvku karta.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

##  <a name="deleteitem"></a>  CTabCtrl::DeleteItem

Odebere určenou položku z karty ovládací prvek.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Založený na nule hodnoty položky k odstranění.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

##  <a name="deselectall"></a>  CTabCtrl::DeselectAll

Obnoví položky v ovládacím prvkem karta, zrušíte všechny, které byly zavedeny.

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Parametry

*fExcludeFocus*<br/>
Příznak, který určuje rozsah deselection položky. Pokud tento parametr je nastaven na hodnotu FALSE, všechna tlačítka karta se resetuje. Pokud je nastavena na hodnotu TRUE, pak všechny kartu s výjimkou je aktuálně vybrané položky se resetuje.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TCM_DESELECTALL](/windows/desktop/Controls/tcm-deselectall), jak je popsáno v sadě Windows SDK.

##  <a name="drawitem"></a>  CTabCtrl::DrawItem

Volá se rozhraním při úpravě vizuálního aspektu změn kartu ovládací prvek vykreslené vlastníkem.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel [drawitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) struktura popisující položku, který se má namalovat.

### <a name="remarks"></a>Poznámky

`itemAction` Člena `DRAWITEMSTRUCT` struktury definuje výkresu akci, která se má provést.

Tato členská funkce ve výchozím nastavení nemá žádný účinek. Přepsat tato členská funkce implementovat kreslení pro vykreslené vlastníkem `CTabCtrl` objektu.

Aplikace by měl obnovit všechny grafiky zařízení rozhraní GDI systému objekty vybrané pro zadaný kontext zobrazení v *lpDrawItemStruct* před tento člen funkce skončí.

##  <a name="getcurfocus"></a>  CTabCtrl::GetCurFocus

Načte index na kartu s aktuálním zaměřením.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule kartu s aktuálním zaměřením.

##  <a name="getcursel"></a>  CTabCtrl::GetCurSel

Načte aktuálně vybraná karta v ovládacím prvkem karta.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule vybraná karta v případě úspěchu nebo – 1, pokud je vybraná žádná karta.

##  <a name="getextendedstyle"></a>  CTabCtrl::GetExtendedStyle

Rozšířené styly, které jsou právě používány pro ovládací prvek karta načte.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Návratová hodnota

Představuje rozšířené styly aktuálně používané pro ovládací prvek karty. Tato hodnota je kombinací [kartu ovládacího prvku rozšířené styly](/windows/desktop/Controls/tab-control-extended-styles), jak je popsáno v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TCM_GETEXTENDEDSTYLE](/windows/desktop/Controls/tcm-getextendedstyle), jak je popsáno v sadě Windows SDK.

##  <a name="getimagelist"></a>  CTabCtrl::GetImageList

Načte seznam obrázků, který je spojen s ovládacím prvkem karta.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na seznam obrázků na kartě řízení; v opačném případě hodnota NULL.

##  <a name="getitem"></a>  CTabCtrl::GetItem

Načte informace o kartě v ovládacím prvkem karta.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Na kartě index založený na nule.

*pTabCtrlItem*<br/>
Ukazatel [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) struktura používá k určení informace, které se mají načíst. Umožňuje také přijímat informace o kartě. Tato struktura se používá s `InsertItem`, `GetItem`, a `SetItem` členské funkce.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; FALSE v opačném případě.

### <a name="remarks"></a>Poznámky

Při odeslání zprávy `mask` člen Určuje, jaké atributy se mají vrátit. Pokud `mask` člen Určuje hodnotu TCIF_TEXT `pszText` člen musí obsahovat adresu vyrovnávací paměti, která bude přijímat textové položky a `cchTextMax` člena nutné zadat velikost vyrovnávací paměti.

- `mask`

   Hodnotu určující, které `TCITEM` načíst nebo nastavit členy struktury. Tento člen může být nula nebo kombinaci těchto hodnot:

   - TCIF_TEXT `pszText` člena je neplatný.

   - TCIF_IMAGE `iImage` člena je neplatný.

   - TCIF_PARAM `lParam` člena je neplatný.

   - TCIF_RTLREADING text z `pszText` se zobrazí pomocí pořadí čtení zprava doleva v systémech hebrejština nebo arabštině.

   - TCIF_STATE `dwState` člena je neplatný.

- `pszText`

   Ukazatel na řetězec zakončený hodnotou null obsahující text karty, pokud struktura obsahuje informace o kartě. Pokud struktura přijímá informace, určuje tento člen Adresa vyrovnávací paměti, která přijímá textem karty.

- `cchTextMax`

   Velikost vyrovnávací paměti, na které odkazuje `pszText`. Tento člen se ignoruje, pokud strukturu, nadále nepřijímá informace.

- `iImage` Index do ovládacího prvku karta seznam obrázků nebo - 1, pokud neexistuje žádný obrázek karty.

- `lParam`

   Definované aplikací data související s kartou. Pokud existuje více než čtyři bajty dat definované aplikací na kartě, aplikace musí definovat strukturu a použít místo něj `TCITEM` struktury. Musí být prvním členem struktury definované aplikací [TCITEMHEADER](/windows/desktop/api/commctrl/ns-commctrl-tagtcitemheadera)struktury. `TCITEMHEADER` Struktura je stejné jako `TCITEM` struktury, ale bez `lParam` člena. Rozdíl mezi velikost struktury a velikost `TCITEMHEADER` struktury by se měl rovnat počtu bajtů navíc na kartu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

##  <a name="getitemcount"></a>  CTabCtrl::GetItemCount

Získá počet karet v ovládacím prvku karty.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v ovládacím prvku karty.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemrect"></a>  CTabCtrl::GetItemRect

Načte ohraničující rámeček pro zadanou kartu v ovládacím prvkem karta.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Z nuly vycházející index položky karty.

*lprect –*<br/>
Ukazatel [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která přijímá ohraničující obdélník na kartě. Tyto souřadnice režim zobrazení na aktuální mapování.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemstate"></a>  CTabCtrl::GetItemState

Načte stav položky ovládacího prvku karta identifikovaný *nItem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Založený na nule číslo indexu položky, pro které chcete načíst informace o stavu.

*dwMask*<br/>
Maska určující, které položky stavu příznaky pro vrácení. Seznam hodnot, naleznete v tématu člen maska [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) struktury, jak je popsáno v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu DWORD příjem informací o stavu. Může být jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Je vybraná položka ovládacího prvku karty.|
|TCIS_HIGHLIGHTED|Položku ovládacího prvku karta je zvýrazněn a na kartě a text jsou vykreslovány pomocí aktuální barvu zvýraznění. Při použití barvu zvýraznění, bude true umožňuje stručně popsat, tónovaná barva.|

### <a name="remarks"></a>Poznámky

Je určen stav položky `dwState` člena `TCITEM` struktury.

##  <a name="getrowcount"></a>  CTabCtrl::GetRowCount

Načte aktuální počet řádků v ovládacím prvku karty.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet řádků karet v ovládacím prvku karty.

### <a name="remarks"></a>Poznámky

Více řádků karet může mít pouze ovládací prvky karet, které TCS_MULTILINE stylu.

##  <a name="gettooltips"></a>  CTabCtrl::GetToolTips

Načte popisovač ovládacím prvkem popis tlačítka nástroj spojené s ovládacím prvkem karta.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač nástroj ovládacím prvkem popis tlačítka v případě úspěchu; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Ovládací prvek karty vytvoří ovládacím prvkem popis tlačítka nástroj, pokud má TCS_TOOLTIPS stylu. Můžete také přiřadit ovládacím prvkem popis tlačítka nástroj do ovládacího prvku karta s použitím `SetToolTips` členskou funkci.

##  <a name="highlightitem"></a>  CTabCtrl::HighlightItem

Nastaví stav zvýraznění položky karty.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Parametry

*idItem*<br/>
Z nuly vycházející index položky ovládacího prvku karty.

*fHighlight*<br/>
Hodnota, která určuje stav zvýraznění, který má být nastavena. Pokud je tato hodnota TRUE, je zvýrazněný na kartě. Pokud má hodnotu FALSE, je nastavena na kartě do výchozího stavu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje zpráva Win32 [TCM_HIGHLIGHTITEM](/windows/desktop/Controls/tcm-highlightitem), jak je popsáno v sadě Windows SDK.

##  <a name="hittest"></a>  CTabCtrl::HitTest

Určuje, které kartě, pokud existuje, je na pozici zadanou obrazovku.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Parametry

*pHitTestInfo*<br/>
Ukazatel [TCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtchittestinfo) struktury, jak je popsáno v sadě Windows SDK, která určuje umístění obrazovky k testování.

### <a name="return-value"></a>Návratová hodnota

Vrátí index o základu 0 na kartě nebo - 1, pokud žádné karta je na zadané pozici.

##  <a name="insertitem"></a>  CTabCtrl::InsertItem

Vloží na nové kartě v existující ovládací prvek karty.

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
Index založený na nule na nové kartě.

*pTabCtrlItem*<br/>
Ukazatel [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) struktura, která určuje atributy na kartu.

*lpszItem*<br/>
Adresa řetězec zakončený hodnotou null, který obsahuje text na kartě.

*nvybrán Nobrázek*<br/>
Z nuly vycházející index obrázku pro vložení ze seznamu obrázků.

*nMask*<br/>
Určuje, které `TCITEM` struktury atributy se mají nastavit. Může být nula nebo kombinaci těchto hodnot:

- TCIF_TEXT `pszText` člena je neplatný.

- TCIF_IMAGE `iImage` člena je neplatný.

- TCIF_PARAM *lParam* člena je neplatný.

- TCIF_RTLREADING text z `pszText` se zobrazí pomocí pořadí čtení zprava doleva v systémech hebrejština nebo arabštině.

- TCIF_STATE *dwState* člena je neplatný.

*lParam*<br/>
Definované aplikací data související s kartou.

*dwState*<br/>
Určuje hodnoty pro položky stavy. Další informace najdete v tématu [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) v sadě Windows SDK.

*dwStateMask*<br/>
Určuje, které stavy mají být nastaveny. Další informace najdete v tématu [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule nová karta v případě úspěchu; jinak - 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

##  <a name="removeimage"></a>  CTabCtrl::RemoveImage

Odebere zadané bitové kopie ze seznamu obrázků ovládacího prvku karta.

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Parametry

*nvybrán Nobrázek*<br/>
Z nuly vycházející index Image, který chcete odebrat.

### <a name="remarks"></a>Poznámky

Ovládací prvek karty aktualizuje index bitové kopie každé kartě tak, aby každá karta zůstane spojená se stejnou bitovou kopii.

##  <a name="setcurfocus"></a>  CTabCtrl::SetCurFocus

Fokus se nastaví na zadanou kartu v ovládacím prvkem karta.

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Určuje index kartu, která získá fokus.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TCM_SETCURFOCUS](/windows/desktop/Controls/tcm-setcurfocus), jak je popsáno v sadě Windows SDK.

##  <a name="setcursel"></a>  CTabCtrl::SetCurSel

Vybere na kartě v ovládacím prvkem karta.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Index založený na nule položka, která má být vybrán.

### <a name="return-value"></a>Návratová hodnota

Index založený na nule dříve vybraná karta v případě úspěchu, jinak - 1.

### <a name="remarks"></a>Poznámky

Ovládací prvek karty neodesílá TCN_SELCHANGING nebo TCN_SELCHANGE zprávu s oznámením při použití této funkce při vybrání karty. Tato oznámení jsou odesílána pomocí WM_NOTIFY, když uživatel klepne nebo změnit karet pomocí klávesnice.

##  <a name="setextendedstyle"></a>  CTabCtrl::SetExtendedStyle

Nastaví rozšířené styly pro ovládací prvek karty.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Parametry

*dwNewStyle*<br/>
Hodnota, která určuje kombinaci kartu řídit rozšířené styly.

*dwExMask*<br/>
Hodnotu typu DWORD určující styly, které v *dwNewStyle* se bude ovlivněná. Rozšířené styly pouze v *dwExMask* se změní. Další styly se zachová, protože je. Pokud tento parametr je nula, pak všechny styly *dwNewStyle* bude mít vliv.

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD obsahující předchozí [kartu ovládacího prvku rozšířené styly](/windows/desktop/Controls/tab-control-extended-styles), jak je popsáno v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Tato členská funkce implementuje chování zprávy Win32 [TCM_SETEXTENDEDSTYLE](/windows/desktop/Controls/tcm-setextendedstyle), jak je popsáno v sadě Windows SDK.

##  <a name="setimagelist"></a>  CTabCtrl::SetImageList

Seznam obrázků přiřadí ovládacím prvkem karta.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Ukazatel na seznam obrázků má být přiřazena k ovládací prvek karty.

### <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na předchozí seznam obrázků nebo hodnota NULL, pokud není žádná předchozí seznamu obrázků.

##  <a name="setitem"></a>  CTabCtrl::SetItem

Nastaví některá nebo všechna na kartě atributy.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Z nuly vycházející index položky.

*pTabCtrlItem*<br/>
Ukazatel [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) strukturu, která obsahuje nové atributy položky. `mask` Člen Určuje atributy, které chcete nastavit. Pokud `mask` člen Určuje hodnotu TCIF_TEXT `pszText` člen je adresa řetězec zakončený hodnotou null a `cchTextMax` členů se ignoruje.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [GetItem](#getitem).

##  <a name="setitemextra"></a>  CTabCtrl::SetItemExtra

Nastaví počet bajtů na kartě vyhrazené pro definovaného aplikací dat v ovládacím prvkem karta.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Počet bajtů navíc k nastavení.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [TCM_SETITEMEXTRA](/windows/desktop/Controls/tcm-setitemextra), jak je popsáno v sadě Windows SDK.

##  <a name="setitemsize"></a>  CTabCtrl::SetItemSize

Nastaví šířku a výšku položky ovládacího prvku karty.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Novou šířku a výšku v pixelech, položek ovládacího prvku karty.

### <a name="return-value"></a>Návratová hodnota

Vrátí původní šířka a výška ohraničení položky ovládacího prvku karty.

##  <a name="setitemstate"></a>  CTabCtrl::SetItemState

Nastaví stav položky ovládacího prvku karta identifikovaný *nItem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Založený na nule číslo indexu položky, pro kterou chcete nastavit informace o stavu.

*dwMask*<br/>
Maska určující, které položky stavu příznaky pro nastavení. Seznam hodnot, naleznete v tématu člen maska [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) struktury, jak je popsáno v sadě Windows SDK.

*dwState*<br/>
Odkaz na hodnotu DWORD obsahující informace o stavu. Může být jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Je vybraná položka ovládacího prvku karty.|
|TCIS_HIGHLIGHTED|Položku ovládacího prvku karta je zvýrazněn a na kartě a text jsou vykreslovány pomocí aktuální barvu zvýraznění. Při použití barvu zvýraznění, bude true umožňuje stručně popsat, tónovaná barva.|

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

##  <a name="setmintabwidth"></a>  CTabCtrl::SetMinTabWidth

Nastavuje minimální šířku položky v ovládacím prvkem karta.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Parametry

*CX*<br/>
Minimální šířka nastavení pro položku ovládacího prvku karty. Pokud tento parametr je nastaven na hodnotu -1, bude ovládací prvek používat výchozí šířku karty.

### <a name="return-value"></a>Návratová hodnota

Předchozí karta minimální šířka.

### <a name="return-value"></a>Návratová hodnota

Tato členská funkce implementuje chování zprávy Win32 [TCM_SETMINTABWIDTH](/windows/desktop/Controls/tcm-setmintabwidth), jak je popsáno v sadě Windows SDK.

##  <a name="setpadding"></a>  CTabCtrl::SetPadding

Nastaví velikost místa (odsazení) kolem každé kartě ikona a popisek v ovládacím prvkem karta.

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Nastaví velikost místa (odsazení) kolem každé kartě ikona a popisek v ovládacím prvkem karta.

##  <a name="settooltips"></a>  CTabCtrl::SetToolTips

Přiřadí ovládacím prvkem popis tlačítka nástroj ovládacím prvkem karta.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parametry

*pWndTip*<br/>
Popisovač ovládacím prvkem popis tlačítka nástroj.

### <a name="remarks"></a>Poznámky

Můžete získat ovládacím prvkem popis tlačítka nástroj spojené s ovládacím prvkem karta tím, že zavoláte na `GetToolTips`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl – třída](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl – třída](../../mfc/reference/clistctrl-class.md)
