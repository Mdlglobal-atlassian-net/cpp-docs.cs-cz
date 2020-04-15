---
title: Třída CTabCtrl
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
ms.openlocfilehash: 7d4a478b560be686e4da6f6dea623d6058626562
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365957"
---
# <a name="ctabctrl-class"></a>Třída CTabCtrl

Poskytuje funkce ovládacího prvku běžné karty systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CTabCtrl::CTabCtrl](#ctabctrl)|Vytvoří `CTabCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CTabCtrl::AdjustRect](#adjustrect)|Vypočítá oblast zobrazení ovládacího prvku tabulátoru s obdélníkem okna nebo vypočítá obdélník okna, který by odpovídal dané oblasti zobrazení.|
|[CTabCtrl::Vytvořit](#create)|Vytvoří ovládací prvek tabulátoru a `CTabCtrl` připojí jej k instanci objektu.|
|[CTabCtrl::CreateEx](#createex)|Vytvoří ovládací prvek tabulátoru se zadanými rozšířenými styly systému Windows a připojí jej k instanci objektu. `CTabCtrl`|
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Odebere všechny položky z ovládacího prvku karta.|
|[CTabCtrl::DeleteItem](#deleteitem)|Odebere položku z ovládacího prvku karta.|
|[CTabCtrl::DeselectAll](#deselectall)|Obnoví položky v ovládacím prvku karty a vymaže všechny, které byly stisknuty.|
|[CTabCtrl::DrawItem](#drawitem)|Nakreslí zadanou položku ovládacího prvku karta.|
|[CTabCtrl::GetCurFocus](#getcurfocus)|Načte kartu s aktuálním fokusem ovládacího prvku tabulátoru.|
|[CTabCtrl::GetCurSel](#getcursel)|Určuje aktuálně vybranou kartu v ovládacím prvku karta.|
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Načte rozšířené styly, které jsou aktuálně používány pro ovládací prvek karta.|
|[CTabCtrl::GetImageList](#getimagelist)|Načte seznam obrázků přidružený k ovládacímu prvku tabulátoru.|
|[CTabCtrl::GetItem](#getitem)|Načte informace o kartě v ovládacím prvku karta.|
|[CTabCtrl::GetItemCount](#getitemcount)|Načte počet karet v ovládacím prvku karta.|
|[CTabCtrl::GetItemRect](#getitemrect)|Načte ohraničovací obdélník pro kartu v ovládacím prvku tabulátoru.|
|[CTabCtrl::GetItemState](#getitemstate)|Načte stav uvedené položky ovládacího prvku tabulátoru.|
|[CTabCtrl::GetRowCount](#getrowcount)|Načte aktuální počet řádků karet v ovládacím prvku karta.|
|[CTabCtrl::GetToolTips](#gettooltips)|Načte úchyt ovládacího prvku tip nástroje přidruženého k ovládacímu prvku tabulátoru.|
|[CTabCtrl::Zvýraznění](#highlightitem)|Nastaví stav zvýraznění položky karty.|
|[CTabCtrl::HitTest](#hittest)|Určuje, která karta, pokud existuje, je v zadané pozici obrazovky.|
|[CTabCtrl::InsertItem](#insertitem)|Vloží novou kartu do ovládacího prvku karta.|
|[CTabCtrl::RemoveImage](#removeimage)|Odebere obrázek ze seznamu obrázků ovládacího prvku karty.|
|[CTabCtrl::SetCurFocus](#setcurfocus)|Nastaví fokus na určenou kartu v ovládacím prvku tabulátoru.|
|[CTabCtrl::SetCurSel](#setcursel)|Vybere kartu v ovládacím prvku karta.|
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené styly ovládacího prvku tabulátoru.|
|[CTabCtrl::SetImageList](#setimagelist)|Přiřadí seznam obrázků ovládacímu prvku tabulátoru.|
|[CTabCtrl::SetItem](#setitem)|Nastaví některé nebo všechny atributy karty.|
|[CTabCtrl::SetItemExtra](#setitemextra)|Nastaví počet bajtů na kartu vyhrazenou pro data definovaná aplikací v ovládacím prvku tabulátoru.|
|[CTabCtrl::SetItemSize](#setitemsize)|Nastaví šířku a výšku položky.|
|[CTabCtrl::SetItemState](#setitemstate)|Nastaví stav uvedené položky ovládacího prvku tabulátoru.|
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Nastaví minimální šířku položek v ovládacím prvku tabulátoru.|
|[CTabCtrl::SetPadding](#setpadding)|Nastaví velikost místa (odsazení) kolem ikony a popisku každé karty v ovládacím prvku karty.|
|[CTabCtrl::Klávesy SetToolTips](#settooltips)|Přiřadí ovládací prvek špičky nástroje ovládacímu prvku tabulátoru.|

## <a name="remarks"></a>Poznámky

"Ovládací prvek tabulátoru" je obdobou oddělovačů v poznámkovém bloku nebo popisků v rozvaděči souborů. Pomocí ovládacího prvku tabulátoru může aplikace definovat více stránek pro stejnou oblast okna nebo dialogového okna. Každá stránka se skládá ze sady informací nebo skupiny ovládacích prvků, které aplikace zobrazí, když uživatel vybere odpovídající kartu. Speciální typ ovládacího prvku karta zobrazuje karty, které vypadají jako tlačítka. Klepnutí na tlačítko by mělo okamžitě provést příkaz namísto zobrazení stránky.

Tento ovládací prvek `CTabCtrl` (a tedy třída) je k dispozici pouze pro programy spuštěné v systémech Windows 95/98 a Windows NT verze 3.51 a novějších.

Další informace o `CTabCtrl`použití naleznete v [tématech Ovládací prvky](../../mfc/controls-mfc.md) a [Použití kláves CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="ctabctrladjustrect"></a><a name="adjustrect"></a>CTabCtrl::AdjustRect

Vypočítá oblast zobrazení ovládacího prvku tabulátoru s obdélníkem okna nebo vypočítá obdélník okna, který by odpovídal dané oblasti zobrazení.

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*bVětší*<br/>
Označuje, kterou operaci provést. Pokud je tento parametr TRUE, *lpRect* určuje obdélník zobrazení a obdrží odpovídající obdélník okna. Pokud je tento parametr FALSE, *lpRect* určuje obdélník okna a obdrží odpovídající obdélník zobrazení.

*lpRect*<br/>
Ukazatel na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu, která určuje daný obdélník a obdrží vypočtený obdélník.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

## <a name="ctabctrlcreate"></a><a name="create"></a>CTabCtrl::Vytvořit

Vytvoří ovládací prvek tabulátoru a `CTabCtrl` připojí jej k instanci objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl ovládacího prvku tabulátoru. Použijte libovolnou kombinaci [stylů ovládacích prvků tabulátorů](/windows/win32/Controls/tab-control-styles)popsanou v sadě Windows SDK. V části **Poznámky** naleznete seznam stylů oken, které můžete použít také pro ovládací prvek.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku tabulátoru. Může to být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/previous-versions/dd162897\(v=vs.85\)) struktury.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího `CDialog`prvku tabulátoru, obvykle . Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku tabulátoru.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla inicializace objektu úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CTabCtrl` dvou krocích. Nejprve zavolejte konstruktoru `Create`a potom volání , který vytvoří `CTabCtrl` ovládací prvek tabulátoru a připojí jej k objektu.

Kromě stylů ovládacích prvků tabulátorů můžete na ovládací prvek tabulátoru použít následující styly oken:

- WS_CHILD Vytvoří podřízené okno, které představuje ovládací prvek tabulátoru. Nelze použít se stylem WS_POPUP.

- WS_VISIBLE Vytvoří ovládací prvek tabulátoru, který je zpočátku viditelný.

- WS_DISABLED Vytvoří okno, které je zpočátku zakázáno.

- WS_GROUP Určuje první ovládací prvek skupiny ovládacích prvků, ve kterém může uživatel přesunout z jednoho ovládacího prvku na další pomocí kláves se šipkami. Všechny ovládací prvky definované WS_GROUP stylu po prvním ovládacím prvku patří do stejné skupiny. Další ovládací prvek se stylem WS_GROUP ukončí skupinu stylů a spustí další skupinu (to znamená, že jedna skupina končí tam, kde začíná další).

- WS_TABSTOP Určuje jeden z libovolného počtu ovládacích prvků, kterými se uživatel může pohybovat pomocí klávesy TAB. Klávesa TAB přesune uživatele na další ovládací prvek určený WS_TABSTOP stylu.

Chcete-li vytvořit ovládací prvek tabulátoru s rozšířenými `Create`styly oken, zavolejte [ctabctrl::CreateEx](#createex) místo .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

## <a name="ctabctrlcreateex"></a><a name="createex"></a>CTabCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) a `CTabCtrl` přidruží jej k objektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyl*<br/>
Určuje rozšířený styl vytvářeného ovládacího prvku. Seznam rozšířených stylů systému Windows naleznete v parametru *dwExStyle* pro [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) v sadě Windows SDK.

*dwStyl*<br/>
Určuje styl ovládacího prvku tabulátoru. Použijte libovolnou kombinaci [stylů ovládacích prvků tabulátorů](/windows/win32/Controls/tab-control-styles)popsanou v sadě Windows SDK. V části **Poznámky** [v tématu Vytvoření](#create) obsahuje seznam stylů oken, které můžete použít také na ovládací prvek.

*Rect*<br/>
Odkaz na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu popisující velikost a umístění okna, které mají být vytvořeny, v klientských souřadnicích *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládací prvek.

*Nid*<br/>
ID podřízeného okna ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná jinak 0.

### <a name="remarks"></a>Poznámky

Místo `CreateEx` funkce [Vytvořit](#create) použijte použití rozšířených stylů systému Windows určených **předmluvou**rozšířeného stylu systému Windows WS_EX_ .

`CreateEx`vytvoří ovládací prvek s rozšířenými styly systému Windows určenými *dwExStyle*. Nastavte rozšířené styly specifické pro ovládací prvek pomocí [SetExtendedStyle](#setextendedstyle). Použijte `CreateEx` například k nastavení takových stylů, `SetExtendedStyle` jako je WS_EX_CONTEXTHELP, ale slouží k nastavení takových stylů, jako je TCS_EX_FLATSEPARATORS. Další informace naleznete v tématu styly popsané v [tabulátoru rozšířené styly](/windows/win32/Controls/tab-control-extended-styles) v sadě Windows SDK.

## <a name="ctabctrlctabctrl"></a><a name="ctabctrl"></a>CTabCtrl::CTabCtrl

Vytvoří `CTabCtrl` objekt.

```
CTabCtrl();
```

## <a name="ctabctrldeleteallitems"></a><a name="deleteallitems"></a>CTabCtrl::DeleteAllItems

Odebere všechny položky z ovládacího prvku karta.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="ctabctrldeleteitem"></a><a name="deleteitem"></a>CTabCtrl::DeleteItem

Odebere zadanou položku z ovládacího prvku tabulátoru.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Parametry

*nPoložka*<br/>
Nulová hodnota položky, kterou chcete odstranit.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

## <a name="ctabctrldeselectall"></a><a name="deselectall"></a>CTabCtrl::DeselectAll

Obnoví položky v ovládacím prvku karty a vymaže všechny, které byly stisknuty.

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Parametry

*fExcludeFocus*<br/>
Příznak, který určuje rozsah deselection položky. Pokud je tento parametr nastaven na hodnotu NEPRAVDA, budou všechna tlačítka karty resetována. Pokud je nastavena na hodnotu TRUE, budou obnoveny všechny položky karty s výjimkou aktuálně vybrané karty.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32, [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall), jak je popsáno v sadě Windows SDK.

## <a name="ctabctrldrawitem"></a><a name="drawitem"></a>CTabCtrl::DrawItem

Volat rámci při změny vizuální aspekt ovládacího prvku karta vlastníka.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na [drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) strukturu popisující položku, která má být vybarvena.

### <a name="remarks"></a>Poznámky

Člen `itemAction` `DRAWITEMSTRUCT` struktury definuje kreslicí akci, která má být provedena.

Ve výchozím nastavení tato členská funkce neprovede žádné. Přepsat tuto členovou funkci implementovat výkres `CTabCtrl` pro objekt nakreslení vlastníka.

Aplikace by měla obnovit všechny objekty rozhraní grafického zařízení (GDI) vybrané pro kontext zobrazení dodaný v *lpDrawItemStruct* před ukončením této členské funkce.

## <a name="ctabctrlgetcurfocus"></a><a name="getcurfocus"></a>CTabCtrl::GetCurFocus

Načte index karty s aktuální fokus.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Návratová hodnota

Nulový index karty s aktuálním fokusem.

## <a name="ctabctrlgetcursel"></a><a name="getcursel"></a>CTabCtrl::GetCurSel

Načte aktuálně vybranou kartu v ovládacím prvku karta.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Návratová hodnota

Nulový index vybrané karty, pokud je úspěšná, nebo - 1, pokud není vybrána žádná karta.

## <a name="ctabctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CTabCtrl::GetExtendedStyle

Načte rozšířené styly, které jsou aktuálně používány pro ovládací prvek karta.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Návratová hodnota

Představuje rozšířené styly aktuálně používánpro ovládací prvek karta. Tato hodnota je kombinací [rozšířených stylů ovládacího prvku tabulátoru](/windows/win32/Controls/tab-control-extended-styles), jak je popsáno v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/tcm-getextendedstyle)Win32 TCM_GETEXTENDEDSTYLE , jak je popsáno v sadě Windows SDK.

## <a name="ctabctrlgetimagelist"></a><a name="getimagelist"></a>CTabCtrl::GetImageList

Načte seznam obrázků, který je přidružen k ovládacímu prvku karta.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na seznam obrázků ovládacího prvku karta; jinak NULL.

## <a name="ctabctrlgetitem"></a><a name="getitem"></a>CTabCtrl::GetItem

Načte informace o kartě v ovládacím prvku karta.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Parametry

*nPoložka*<br/>
Nulový index karty.

*pTabCtrlItem*<br/>
Ukazatel na strukturu [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) slouží k určení informace k načtení. Používá se také k přijímání informací o kartě. Tato struktura se `InsertItem`používá `GetItem`s `SetItem` , a členské funkce.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je úspěšná. FALSE jinak.

### <a name="remarks"></a>Poznámky

Při odeslání zprávy `mask` člen určuje, které atributy vrátit. Pokud `mask` člen určuje hodnotu TCIF_TEXT, musí `pszText` obsahovat adresu vyrovnávací paměti, která `cchTextMax` obdrží text položky, a člen musí určit velikost vyrovnávací paměti.

- `mask`

   Hodnota určující, `TCITEM` které členy struktury mají být načteny nebo nastaveny. Tento člen může být nula nebo kombinace následujících hodnot:

  - TCIF_TEXT `pszText` Člen je platný.

  - TCIF_IMAGE `iImage` Člen je platný.

  - TCIF_PARAM `lParam` Člen je platný.

  - TCIF_RTLREADING Text `pszText` se zobrazí pomocí pořadí čtení zprava doleva v hebrejských nebo arabských systémech.

  - TCIF_STATE `dwState` Člen je platný.

- `pszText`

   Ukazatel na řetězec s nulovým zakončeným obsahující text tabulátoru, pokud struktura obsahuje informace o tabulátoru. Pokud struktura přijímá informace, tento člen určuje adresu vyrovnávací paměti, která přijímá text karty.

- `cchTextMax`

   Velikost vyrovnávací paměti, `pszText`na kterou se vztahuje . Tento člen je ignorován, pokud struktura nepřijímá informace.

- `iImage`Index do seznamu obrázků ovládacího prvku karty, nebo - 1, pokud není k dispozici žádný obrázek pro kartu.

- `lParam`

   Data definovaná aplikací přidružená k kartě. Pokud existuje více než čtyři bajty dat definovaných aplikací na kartu, aplikace musí `TCITEM` definovat strukturu a použít ji namísto struktury. První člen struktury definované aplikací musí být [tcitemheader](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw)struktury. Struktura `TCITEMHEADER` je shodná `TCITEM` se strukturou, ale bez `lParam` člena. Rozdíl mezi velikostí struktury a velikostí `TCITEMHEADER` struktury by se měl rovnat počtu dalších bajtů na kartě.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

## <a name="ctabctrlgetitemcount"></a><a name="getitemcount"></a>CTabCtrl::GetItemCount

Načte počet karet v ovládacím prvku karta.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek v ovládacím prvku karta.

### <a name="example"></a>Příklad

  Viz příklad [cpropertysheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctabctrlgetitemrect"></a><a name="getitemrect"></a>CTabCtrl::GetItemRect

Načte ohraničovací obdélník pro zadanou kartu v ovládacím prvku tabulátoru.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nPoložka*<br/>
Nulový index položky karty.

*lpRect*<br/>
Ukazatel na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu, která obdrží ohraničující obdélník na kartě. Tyto souřadnice používají aktuální režim mapování výřezu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

  Viz příklad [cpropertysheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctabctrlgetitemstate"></a><a name="getitemstate"></a>CTabCtrl::GetItemState

Načte stav položky ovládacího prvku tabulátoru identifikovaného *položkou nItem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Parametry

*nPoložka*<br/>
Číslo indexu založené na nule položky, pro které chcete načíst informace o stavu.

*dwMask*<br/>
Maska určující, které z příznaků stavu položky vrátit. Seznam hodnot naleznete v členmasky [tcitem](/windows/win32/api/commctrl/ns-commctrl-tcitemw) struktury, jak je popsáno v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Odkaz na hodnotu DWORD přijímající informace o stavu. Může se na nich vyvěšovat jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Je vybrána položka ovládacího prvku tabulátoru.|
|TCIS_HIGHLIGHTED|Položka ovládacího prvku tabulátoru je zvýrazněna a karta a text jsou vykresleny pomocí aktuální barvy zvýraznění. Při použití barvy zvýraznění to bude skutečná interpolace, nikoli roztírená barva.|

### <a name="remarks"></a>Poznámky

Stav položky je určen `dwState` členem `TCITEM` struktury.

## <a name="ctabctrlgetrowcount"></a><a name="getrowcount"></a>CTabCtrl::GetRowCount

Načte aktuální počet řádků v ovládacím prvku karta.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet řádků karet v ovládacím prvku karta.

### <a name="remarks"></a>Poznámky

Pouze ovládací prvky tabulátoru, které mají TCS_MULTILINE styl, mohou mít více řádků karet.

## <a name="ctabctrlgettooltips"></a><a name="gettooltips"></a>CTabCtrl::GetToolTips

Načte úchyt ovládacího prvku tip nástroje přidruženého k ovládacímu prvku tabulátoru.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Návratová hodnota

Rukojeť ovládacího prvku hrotu nástroje, pokud je úspěšná; jinak NULL.

### <a name="remarks"></a>Poznámky

Ovládací prvek tabulátoru vytvoří ovládací prvek špičky nástroje, pokud má TCS_TOOLTIPS styl. Ovládacímu prvku tabulátoru můžete také `SetToolTips` přiřadit ovládací prvek špičky nástroje pomocí členské funkce.

## <a name="ctabctrlhighlightitem"></a><a name="highlightitem"></a>CTabCtrl::Zvýraznění

Nastaví stav zvýraznění položky karty.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Parametry

*idPoložka*<br/>
Nulový index položky ovládacího prvku tabulátoru.

*fZvýraznění*<br/>
Hodnota určující stav zvýraznění, který má být nastaven. Pokud je tato hodnota PRAVDA, karta se zvýrazní; pokud nepravda, karta je nastavena na výchozí stav.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje zprávu win32 [TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem), jak je popsáno v sadě Windows SDK.

## <a name="ctabctrlhittest"></a><a name="hittest"></a>CTabCtrl::HitTest

Určuje, která karta, pokud existuje, je v zadané pozici obrazovky.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Parametry

*pHitTestInfo*<br/>
Ukazatel na strukturu [TCHITTESTINFO,](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo) jak je popsáno v sadě Windows SDK, která určuje pozici obrazovky k testování.

### <a name="return-value"></a>Návratová hodnota

Vrátí index na základě nuly na kartě nebo - 1, pokud žádná karta není na zadané pozici.

## <a name="ctabctrlinsertitem"></a><a name="insertitem"></a>CTabCtrl::InsertItem

Vloží novou kartu do existujícího ovládacího prvku tabulátoru.

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

*nPoložka*<br/>
Nulový index nové karty.

*pTabCtrlItem*<br/>
Ukazatel na strukturu [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) která určuje atributy karty.

*lpszPoložka*<br/>
Adresa řetězce s ukončeným hodnotou null, který obsahuje text karty.

*nObrázek*<br/>
Nulový index obrázku, který chcete vložit ze seznamu obrázků.

*nMaska*<br/>
Určuje, `TCITEM` které atributy struktury mají být nastaveny. Může být nula nebo kombinace následujících hodnot:

- TCIF_TEXT `pszText` Člen je platný.

- TCIF_IMAGE `iImage` Člen je platný.

- TCIF_PARAM Člen *lParam* je platný.

- TCIF_RTLREADING Text `pszText` se zobrazí pomocí pořadí čtení zprava doleva v hebrejských nebo arabských systémech.

- TCIF_STATE Člen *dwState* je platný.

*Lparam*<br/>
Data definovaná aplikací přidružená k kartě.

*dwState*<br/>
Určuje hodnoty pro stavy položky. Další informace naleznete v [tématu TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) v sadě Windows SDK.

*dwStateMask*<br/>
Určuje, které stavy mají být nastaveny. Další informace naleznete v [tématu TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Index na základě nuly nové karty v případě úspěchu; jinak - 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

## <a name="ctabctrlremoveimage"></a><a name="removeimage"></a>CTabCtrl::RemoveImage

Odebere zadaný obrázek ze seznamu obrázků ovládacího prvku tabulátoru.

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Parametry

*nObrázek*<br/>
Nulový index obrázku, který chcete odebrat.

### <a name="remarks"></a>Poznámky

Ovládací prvek karty aktualizuje index obrázku každé karty tak, aby každá karta zůstala přidružena ke stejnému obrázku.

## <a name="ctabctrlsetcurfocus"></a><a name="setcurfocus"></a>CTabCtrl::SetCurFocus

Nastaví fokus na určenou kartu v ovládacím prvku tabulátoru.

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Parametry

*nPoložka*<br/>
Určuje index karty, která získá fokus.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/tcm-setcurfocus)Win32 TCM_SETCURFOCUS , jak je popsáno v sadě Windows SDK.

## <a name="ctabctrlsetcursel"></a><a name="setcursel"></a>CTabCtrl::SetCurSel

Vybere kartu v ovládacím prvku karta.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Parametry

*nPoložka*<br/>
Nulový index položky, která má být vybrána.

### <a name="return-value"></a>Návratová hodnota

Index na základě nuly dříve vybrané karty v případě úspěchu, jinak - 1.

### <a name="remarks"></a>Poznámky

Ovládací prvek tabulátoru neodesílá TCN_SELCHANGING nebo TCN_SELCHANGE oznámení, když je karta vybrána pomocí této funkce. Tato oznámení jsou odesílána pomocí WM_NOTIFY, když uživatel klikne nebo použije klávesnici ke změně karet.

## <a name="ctabctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CTabCtrl::SetExtendedStyle

Nastaví rozšířené styly ovládacího prvku tabulátoru.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Parametry

*dwNewStyle*<br/>
Hodnota určující kombinaci rozšířených stylů ovládacího prvku tabulátoru.

*dwExMaska*<br/>
Hodnota DWORD, která označuje, které styly v *dwNewStyle* mají být ovlivněny. Budou změněny pouze rozšířené styly v *dwExMask.* Všechny ostatní styly budou zachovány tak, jak jsou. Pokud je tento parametr nula, budou ovlivněny všechny styly v *dwNewStyle.*

### <a name="return-value"></a>Návratová hodnota

Hodnota DWORD, která obsahuje předchozí [ovládací prvek karta rozšířené styly](/windows/win32/Controls/tab-control-extended-styles), jak je popsáno v sadě Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/tcm-setextendedstyle)Win32 TCM_SETEXTENDEDSTYLE , jak je popsáno v sadě Windows SDK.

## <a name="ctabctrlsetimagelist"></a><a name="setimagelist"></a>CTabCtrl::SetImageList

Přiřadí seznam obrázků ovládacímu prvku tabulátoru.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*seznam obrázků pImage*<br/>
Ukazatel na seznam obrázků, který má být přiřazen ovládacímu prvku tabulátoru.

### <a name="return-value"></a>Návratová hodnota

Vrátí ukazatel na předchozí seznam obrázků nebo hodnotu NULL, pokud neexistuje žádný předchozí seznam obrázků.

## <a name="ctabctrlsetitem"></a><a name="setitem"></a>CTabCtrl::SetItem

Nastaví některé nebo všechny atributy karty.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Parametry

*nPoložka*<br/>
Nulový index položky.

*pTabCtrlItem*<br/>
Ukazatel na strukturu [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) která obsahuje nové atributy položky. Člen `mask` určuje, které atributy mají být nastaveny. Pokud `mask` člen určuje hodnotu TCIF_TEXT, `pszText` člen je adresa řetězce ukončeného `cchTextMax` nulou a člen je ignorován.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

  Viz příklad pro [GetItem](#getitem).

## <a name="ctabctrlsetitemextra"></a><a name="setitemextra"></a>CTabCtrl::SetItemExtra

Nastaví počet bajtů na kartu vyhrazenou pro data definovaná aplikací v ovládacím prvku tabulátoru.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Parametry

*nBajtu bajtů*<br/>
Počet dalších bajtů, které chcete nastavit.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/tcm-setitemextra)Win32 TCM_SETITEMEXTRA , jak je popsáno v sadě Windows SDK.

## <a name="ctabctrlsetitemsize"></a><a name="setitemsize"></a>CTabCtrl::SetItemSize

Nastaví šířku a výšku položek ovládacího prvku tabulátoru.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Nová šířka a výška položek ovládacího prvku tabulátoru v obrazových bodech.

### <a name="return-value"></a>Návratová hodnota

Vrátí starou šířku a výšku položek ovládacího prvku tabulátoru.

## <a name="ctabctrlsetitemstate"></a><a name="setitemstate"></a>CTabCtrl::SetItemState

Nastaví stav položky ovládacího prvku tabulátoru identifikované *položkou nItem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Parametry

*nPoložka*<br/>
Číslo indexu založené na nule položky, pro které chcete nastavit informace o stavu.

*dwMask*<br/>
Maska určující, které z příznaků stavu položky nastavit. Seznam hodnot naleznete v členmasky [tcitem](/windows/win32/api/commctrl/ns-commctrl-tcitemw) struktury, jak je popsáno v sadě Windows SDK.

*dwState*<br/>
Odkaz na hodnotu DWORD obsahující informace o stavu. Může se na nich vyvěšovat jedna z následujících hodnot:

|Hodnota|Popis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Je vybrána položka ovládacího prvku tabulátoru.|
|TCIS_HIGHLIGHTED|Položka ovládacího prvku tabulátoru je zvýrazněna a karta a text jsou vykresleny pomocí aktuální barvy zvýraznění. Při použití barvy zvýraznění to bude skutečná interpolace, nikoli roztírená barva.|

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="ctabctrlsetmintabwidth"></a><a name="setmintabwidth"></a>CTabCtrl::SetMinTabWidth

Nastaví minimální šířku položek v ovládacím prvku tabulátoru.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Parametry

*Cx*<br/>
Minimální šířka, která má být nastavena pro položku ovládacího prvku tabulátoru. Pokud je tento parametr nastaven na -1, ovládací prvek použije výchozí šířku karty.

### <a name="return-value"></a>Návratová hodnota

Předchozí minimální šířka karty.

### <a name="return-value"></a>Návratová hodnota

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/tcm-setmintabwidth)Win32 TCM_SETMINTABWIDTH , jak je popsáno v sadě Windows SDK.

## <a name="ctabctrlsetpadding"></a><a name="setpadding"></a>CTabCtrl::SetPadding

Nastaví velikost místa (odsazení) kolem ikony a popisku každé karty v ovládacím prvku karty.

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
Nastaví velikost místa (odsazení) kolem ikony a popisku každé karty v ovládacím prvku karty.

## <a name="ctabctrlsettooltips"></a><a name="settooltips"></a>CTabCtrl::Klávesy SetToolTips

Přiřadí ovládací prvek špičky nástroje ovládacímu prvku tabulátoru.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parametry

*pWndTip*<br/>
Rukojeť ovládacího prvku hrotu nástroje.

### <a name="remarks"></a>Poznámky

Ovládací prvek tip nástroje můžete získat přidružené k ovládacímu prvku karta voláním `GetToolTips`do .

### <a name="example"></a>Příklad

  Viz příklad [cpropertysheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)<br/>
[Třída CListCtrl](../../mfc/reference/clistctrl-class.md)
