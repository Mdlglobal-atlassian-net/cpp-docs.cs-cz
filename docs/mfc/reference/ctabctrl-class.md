---
title: "CTabCtrl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e9720d407fb13b5a87335da08eb40c2886fdcdb3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctabctrl-class"></a>CTabCtrl – třída
Poskytuje funkce Windows běžné ovládacího prvku karta.  
  
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
|[CTabCtrl::AdjustRect](#adjustrect)|Vypočítá zadané okno obdélníku oblasti zobrazení ovládacího prvku karta nebo vypočítá okno obdélníku, která odpovídá dané zobrazení oblasti.|  
|[CTabCtrl::Create](#create)|Vytvoří ovládacího prvku karta a připojí k instanci `CTabCtrl` objektu.|  
|[CTabCtrl::CreateEx](#createex)|Vytvoří zadaný Windows rozšířené styly ovládacího prvku karta a připojí k instanci `CTabCtrl` objektu.|  
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Odebere všechny položky z ovládacího prvku karta.|  
|[CTabCtrl::DeleteItem](#deleteitem)|Odebere položku z ovládacího prvku karta.|  
|[CTabCtrl::DeselectAll](#deselectall)|Obnoví položky v ovládacím prvku karta vymazání všechny, které byly stisknutí tlačítka.|  
|[CTabCtrl::DrawItem](#drawitem)|Nakreslí zadanou položku ovládacího prvku karta.|  
|[CTabCtrl::GetCurFocus](#getcurfocus)|Načte na kartě s aktuální fokus ovládacího prvku karta.|  
|[CTabCtrl::GetCurSel](#getcursel)|Určuje kartě aktuálně vybraný v ovládacím prvkem karta.|  
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Načte rozšířené styly, které jsou právě používány pro ovládací prvek karty.|  
|[CTabCtrl::GetImageList](#getimagelist)|Načte seznam obrázků spojené s ovládacím prvkem karta.|  
|[CTabCtrl::GetItem](#getitem)|Načte informace o kartě v ovládacím prvkem karta.|  
|[CTabCtrl::GetItemCount](#getitemcount)|Načte počet karet do ovládacího prvku karta.|  
|[CTabCtrl::GetItemRect](#getitemrect)|Načte ohraničující obdélník karta v ovládacím prvkem karta.|  
|[CTabCtrl::GetItemState](#getitemstate)|Načte stav položky ovládacího prvku karta uvedené.|  
|[CTabCtrl::GetRowCount](#getrowcount)|Načte aktuální počet řádků v ovládacím prvkem karta karty.|  
|[CTabCtrl::GetToolTips](#gettooltips)|Načte popisovač spojené s ovládacím prvkem karta ovládacím prvkem popis tlačítka.|  
|[CTabCtrl::HighlightItem](#highlightitem)|Nastaví stav zvýraznění položka tabulátoru.|  
|[CTabCtrl::HitTest](#hittest)|Určuje, které kartě, pokud existuje, je na pozici zadanou obrazovky.|  
|[CTabCtrl::InsertItem](#insertitem)|Vloží novou kartu ovládacího prvku karta.|  
|[CTabCtrl::RemoveImage](#removeimage)|Odebere ze seznamu obrázků ovládacího prvku karta bitovou kopii.|  
|[CTabCtrl::SetCurFocus](#setcurfocus)|Nastaví fokus na zadanou kartu v ovládacím prvkem karta.|  
|[CTabCtrl::SetCurSel](#setcursel)|Vyberte na kartě v ovládacím prvkem karta.|  
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené styly pro ovládací prvek karty.|  
|[CTabCtrl::SetImageList](#setimagelist)|Přiřadí seznamu obrázků do ovládacího prvku karta.|  
|[CTabCtrl::SetItem](#setitem)|Nastaví některé nebo všechny na kartě atributy.|  
|[CTabCtrl::SetItemExtra](#setitemextra)|Nastaví počet bajtů za karta vyhrazené pro definované aplikací dat v ovládacím prvkem karta.|  
|[CTabCtrl::SetItemSize](#setitemsize)|Nastaví šířku a výšku položky.|  
|[CTabCtrl::SetItemState](#setitemstate)|Nastaví stav položky ovládacího prvku karta uvedené.|  
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Nastaví minimální šířku položky v ovládacím prvkem karta.|  
|[CTabCtrl::SetPadding](#setpadding)|Nastaví množství místa (odsazení) kolem ikona a popisek v ovládacím prvkem karta každé kartě.|  
|[CTabCtrl::SetToolTips](#settooltips)|Přiřadí prvkem popis tlačítka do ovládacího prvku karta.|  
  
## <a name="remarks"></a>Poznámky  
 "Ovládacího prvku karta" je obdobou rozdělení v poznámkovém bloku nebo popisky v souboru CAB. Pomocí ovládacího prvku Karta aplikace můžete definovat více stránek pro stejné oblasti okno nebo dialogové okno. Každé stránce se skládá ze sady informace nebo skupinu ovládacích prvků, které aplikace se zobrazí, když uživatel vybere odpovídající kartě. Speciální typ ovládacího prvku karta zobrazí karty, které vypadají podobně jako tlačítka. Kliknutím na tlačítko okamžitě proveďte příkaz namísto zobrazení stránky.  
  
 Tento ovládací prvek (a proto `CTabCtrl` třída) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95/98 a systému Windows NT 3.51 a novějším.  
  
 Další informace o používání `CTabCtrl`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md) a [pomocí CTabCtrl](../../mfc/using-ctabctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTabCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="adjustrect"></a>CTabCtrl::AdjustRect  
 Vypočítá zadané okno obdélníku oblasti zobrazení ovládacího prvku karta nebo vypočítá okno obdélníku, která odpovídá dané zobrazení oblasti.  
  
```  
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `bLarger`  
 Určuje, kterou operaci provést. Pokud tento parametr je **TRUE**, `lpRect` určuje obdélníku zobrazení a získá odpovídající obdélníku okna. Pokud tento parametr je **FALSE**, `lpRect` určuje obdélníku okno a získá odpovídající obdélník zobrazení.  
  
 `lpRect`  
 Ukazatel na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která určuje dané rámeček a přijímá počítaný obdélník.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]  
  
##  <a name="create"></a>CTabCtrl::Create  
 Vytvoří ovládacího prvku karta a připojí k instanci `CTabCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl ovládacího prvku karta. Použít libovolnou kombinaci [kartě styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb760549), které jsou popsány v sadě Windows SDK. V tématu **poznámky** seznam styly oken, které můžete provést také do ovládacího prvku.  
  
 `rect`  
 Určuje velikost a umístění ovládacího prvku karta. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura.  
  
 `pParentWnd`  
 Určuje nadřazeného ovládacího prvku karta okna, obvykle `CDialog`. Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku karta.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud inicializace objektu byla úspěšná, jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CTabCtrl` objektu ve dvou krocích. Nejprve volat konstruktor a pak zavolají **vytvořit**, který vytvoří ovládacího prvku karta a připojí jej k `CTabCtrl` objektu.  
  
 Kromě styly ovládacího prvku karta můžete použít následující styly oken do ovládacího prvku karta:  
  
- **Ws_child –** vytvoří podřízeného okna, který představuje ovládacího prvku karta. Nelze použít s `WS_POPUP` stylu.  
  
- **Ws_visible –** vytvoří ovládacího prvku karta, která původně viditelná.  
  
- **Ws_disabled –** vytvoří okno, které je původně zakázána.  
  
- **Ws_group –** Určuje první prvek skupiny ovládacích prvků, ve kterých může uživatel přesunout z jednoho ovládacího prvku na další pomocí klávesy se šipkami. Všechny ovládací prvky, které jsou definované pomocí **ws_group –** styl po první prvek patří do stejné skupiny. Na další ovládací prvek s **ws_group –** styl končí skupinu stylů a spustí na další skupinu (to znamená, jedna skupina elementy end kde začíná další).  
  
- **Ws_tabstop –** určuje jedné z několika ovládacích prvků, pomocí kterých může uživatel přesunout pomocí klávesy TAB. Klávesy TAB přesune na další ovládací prvek určeného uživatele **ws_tabstop –** stylu.  
  
 Chcete-li vytvořit ovládacího prvku karta s rozšířené styly oken, volejte [CTabCtrl::CreateEx](#createex) místo **vytvořit**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]  
  
##  <a name="createex"></a>CTabCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízeného okna) a přidruží ji s `CTabCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Určuje styl rozšířené vytváří ovládacího prvku. Seznam rozšířené styly Windows najdete v tématu `dwExStyle` parametr pro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
 `dwStyle`  
 Určuje styl ovládacího prvku karta. Použít libovolnou kombinaci [kartě styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb760549), které jsou popsány v sadě Windows SDK. V tématu **poznámky** v [vytvořit](#create) seznam styly oken, které můžete provést také do ovládacího prvku.  
  
 `rect`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující velikost a umístění okna byly vytvořeny v souřadnice klienta `pParentWnd`.  
  
 `pParentWnd`  
 Ukazatel na okně, které je nadřazeného ovládacího prvku.  
  
 `nID`  
 ID ovládacího prvku podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určeného předponu rozšířené styl Windows **WS_EX_**.  
  
 `CreateEx`Vytvoří ovládacího prvku rozšířené styly Windows určeného `dwExStyle`. Rozšířené styly specifické pro ovládací prvek pomocí sady [SetExtendedStyle](#setextendedstyle). Například použít `CreateEx` nastavit tyto styly jako **ws_ex_contexthelp –**, ale použít `SetExtendedStyle` nastavit tyto styly jako **tcs_ex_flatseparators –**. Další informace najdete v tématu styly popsané v [rozšířené styly ovládacího prvku karta](http://msdn.microsoft.com/library/windows/desktop/bb760546) ve Windows SDK.  
  
##  <a name="ctabctrl"></a>CTabCtrl::CTabCtrl  
 Vytvoří `CTabCtrl` objektu.  
  
```  
CTabCtrl();
```  
  
##  <a name="deleteallitems"></a>CTabCtrl::DeleteAllItems  
 Odebere všechny položky z ovládacího prvku karta.  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
##  <a name="deleteitem"></a>CTabCtrl::DeleteItem  
 Odebere zadanou položku z ovládacího prvku karta.  
  
```  
BOOL DeleteItem(int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Hodnoty s nulovým základem položky odstranit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]  
  
##  <a name="deselectall"></a>CTabCtrl::DeselectAll  
 Obnoví položky v ovládacím prvku karta vymazání všechny, které byly stisknutí tlačítka.  
  
```  
void DeselectAll(BOOL fExcludeFocus);
```  
  
### <a name="parameters"></a>Parametry  
 *fExcludeFocus*  
 Příznak, který určuje rozsah deselection položky. Pokud tento parametr je nastaven na **FALSE**, všechny tlačítka karta se resetuje. Pokud je nastaven na hodnotu **TRUE**, pak všechny položky karta s výjimkou aktuálně vybraného se resetuje.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování Win32 zprávy, [TCM_DESELECTALL](http://msdn.microsoft.com/library/windows/desktop/bb760579), jak je popsáno v sadě Windows SDK.  
  
##  <a name="drawitem"></a>CTabCtrl::DrawItem  
 Voláno rámcem při visual aspekt vykreslování vlastníka karty řízení změn.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Ukazatel [drawitemstruct –](http://msdn.microsoft.com/library/windows/desktop/bb775802) struktura popisující položka, která má být vykresluje.  
  
### <a name="remarks"></a>Poznámky  
 **ItemAction** členem `DRAWITEMSTRUCT` struktura definuje kreslení akci, která má být provedena.  
  
 Ve výchozím nastavení tato funkce člen neprovede žádnou akci. Člen funkci implementovat kreslení pro kreslení vlastníka přepsat `CTabCtrl` objektu.  
  
 Aplikace by měla obnovit všechny grafiky zařízení rozhraní GDI objekty vybrané pro zadaný kontext zobrazení v `lpDrawItemStruct` před tento člen funkce ukončí.  
  
##  <a name="getcurfocus"></a>CTabCtrl::GetCurFocus  
 Načte index na kartě s aktuální fokus.  
  
```  
int GetCurFocus() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule na kartě s aktuální fokus.  
  
##  <a name="getcursel"></a>CTabCtrl::GetCurSel  
 Načte aktuálně vybraná karta v ovládacím prvkem karta.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index vybraná karta, v případě úspěchu nebo - 1, pokud je vybrána žádná karta nule.  
  
##  <a name="getextendedstyle"></a>CTabCtrl::GetExtendedStyle  
 Načte rozšířené styly, které jsou právě používány pro ovládací prvek karty.  
  
```  
DWORD GetExtendedStyle();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Představuje rozšířené styly aktuálně používán pro ovládací prvek karty. Tato hodnota je kombinací [kartě řízení extended styly](http://msdn.microsoft.com/library/windows/desktop/bb760546), jak je popsáno v sadě Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TCM_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb760585), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getimagelist"></a>CTabCtrl::GetImageList  
 Načte seznam obrázků, který je spojen s ovládacím prvkem karta.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného ukazatel na seznamu obrázků na kartě řízení; v opačném **NULL**.  
  
##  <a name="getitem"></a>CTabCtrl::GetItem  
 Načte informace o kartě v ovládacím prvkem karta.  
  
```  
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Na kartě index počítaný od nuly.  
  
 `pTabCtrlItem`  
 Ukazatel na [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) struktura, umožňuje zadat informace pro načtení. Používá se také získat informace o kartě. Tato struktura se používá s `InsertItem`, `GetItem`, a `SetItem` členské funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěšného; **FALSE** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Při odeslání zprávy **maska** člen Určuje atributy, které vrátit. Pokud **maska** určuje člena `TCIF_TEXT` hodnota, **pszText** člen musí obsahovat adresu vyrovnávací paměti, která přijímá text položky a **cchTextMax** člen musíte zadat velikost vyrovnávací paměti.  
  
 **Maska**  
 Hodnota, která určuje, které `TCITEM` struktury členy načíst nebo nastavit. Tento člen může být nula nebo kombinaci těchto hodnot:  
  
- `TCIF_TEXT`**PszText** člena je neplatný.  
  
- `TCIF_IMAGE``iImage` Člena je neplatný.  
  
- `TCIF_PARAM`**LParam** člena je neplatný.  
  
- `TCIF_RTLREADING`Text **pszText** se zobrazí v hebrejštině nebo arabské systému pomocí pořadí čtení zprava doleva.  
  
- `TCIF_STATE`**DwState** člena je neplatný.  
  
 **pszText**  
 Ukazatel na obsahující text kartě, pokud struktura obsahuje informace o kartě řetězce ukončené hodnotou null. Pokud strukturu přijímá informace, určuje tento člen adresu vyrovnávací paměti, která přijímá text karty.  
  
 **cchTextMax**  
 Velikost vyrovnávací paměti, na kterou odkazuje **pszText**. Tento člen je ignorována, pokud strukturu nepřijímá informace.  
  
 `iImage`  
 Index do ovládacího prvku karta seznamu obrázků, nebo - 1, pokud neexistuje žádný obrázek karty.  
  
 **lParam**  
 Definované aplikací data přidružená k kartě. Pokud existuje více než čtyři bajtů dat aplikace definované na kartě, aplikace musí definovat strukturu a použít místo `TCITEM` struktura. Musí být prvním členem struktury definované aplikací [TCITEMHEADER](http://msdn.microsoft.com/library/windows/desktop/bb760556)struktury. **TCITEMHEADER** struktura je stejný jako `TCITEM` struktury, ale bez **lParam** člen. Rozdíl mezi velikost strukturu a velikost **TCITEMHEADER** struktury musí být roven počtu bajtů navíc na kartě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]  
  
##  <a name="getitemcount"></a>CTabCtrl::GetItemCount  
 Načte počet karet do ovládacího prvku karta.  
  
```  
int GetItemCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v ovládacím prvku karta.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="getitemrect"></a>CTabCtrl::GetItemRect  
 Načte ohraničující obdélník zadaný karty v ovládacím prvkem karta.  
  
```  
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Index položky karta nule.  
  
 `lpRect`  
 Ukazatel na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která přijímá ohraničující obdélník na kartě. Tyto souřadnice používat aktuální režim mapování zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="getitemstate"></a>CTabCtrl::GetItemState  
 Načte stav položky ovládacího prvku karta identifikovaný `nItem`.  
  
```  
DWORD GetItemState(
    int nItem,  
    DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Číslo od nuly index položky, pro které chcete načíst informace o stavu.  
  
 `dwMask`  
 Maska určující, které položky stavu flags vrátit. Seznam hodnot najdete v tématu členem maska [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) struktury, jak je popsáno v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `DWORD` hodnota přijetí informace o stavu. Může být jedna z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|**TCIS_BUTTONPRESSED**|Je vybrána položka ovládacího prvku karta.|  
|**TCIS_HIGHLIGHTED**|Položky ovládacího prvku karta je zvýrazněna a karta a text jsou vykreslovány pomocí aktuální barva zvýraznění. Pokud používáte barva zvýraznění, bude hodnota true, interpolace, tónovaná barva.|  
  
### <a name="remarks"></a>Poznámky  
 Je zadána stav položky **dwState** členem `TCITEM` struktura.  
  
##  <a name="getrowcount"></a>CTabCtrl::GetRowCount  
 Načte aktuální počet řádků v ovládacím prvkem karta.  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet řádků v ovládacím prvku karta karet.  
  
### <a name="remarks"></a>Poznámky  
 Pouze kartě ovládací prvky, které mají **TCS_MULTILINE** styl může mít více řádků karty.  
  
##  <a name="gettooltips"></a>CTabCtrl::GetToolTips  
 Načte popisovač spojené s ovládacím prvkem karta ovládacím prvkem popis tlačítka.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač ovládacím prvkem popis tlačítka v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Ovládacího prvku karta vytvoří prvkem popis tlačítka, pokud má **TCS_TOOLTIPS** stylu. Můžete také přiřadit prvkem popis tlačítka do ovládacího prvku karta pomocí `SetToolTips` – členská funkce.  
  
##  <a name="highlightitem"></a>CTabCtrl::HighlightItem  
 Nastaví stav zvýraznění položka tabulátoru.  
  
```  
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `idItem`  
 Index položky ovládacího prvku karta nule.  
  
 `fHighlight`  
 Hodnota, která určuje nastavení stavu zvýraznění. Pokud je tato hodnota **TRUE**, je označený na kartě; Pokud **FALSE**, je nastaven na kartě do výchozího stavu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje zpráva Win32 [TCM_HIGHLIGHTITEM](http://msdn.microsoft.com/library/windows/desktop/bb760602), jak je popsáno v sadě Windows SDK.  
  
##  <a name="hittest"></a>CTabCtrl::HitTest  
 Určuje, které kartě, pokud existuje, je na pozici zadanou obrazovky.  
  
```  
int HitTest(TCHITTESTINFO* pHitTestInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pHitTestInfo`  
 Ukazatel na [TCHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb760553) struktury, jak je popsáno v sadě Windows SDK, která určuje pozici obrazovky pro testování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí index o základu 0 kartě nebo - 1, pokud žádné karta je na zadané pozici.  
  
##  <a name="insertitem"></a>CTabCtrl::InsertItem  
 Vloží novou kartu existujícího ovládacího prvku karta.  
  
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
 `nItem`  
 Index počítaný od nuly novou kartu.  
  
 `pTabCtrlItem`  
 Ukazatel na [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) struktura, která určuje atributy karty.  
  
 `lpszItem`  
 Adresa řetězce ukončené hodnotou null, který obsahuje text, na kartě.  
  
 `nImage`  
 Index založený na nule bitové kopie k vložení ze seznamu obrázků.  
  
 `nMask`  
 Určuje, které `TCITEM` struktury atributy k nastavení. Může být nula nebo kombinaci těchto hodnot:  
  
- `TCIF_TEXT`**PszText** člena je neplatný.  
  
- `TCIF_IMAGE``iImage` Člena je neplatný.  
  
- `TCIF_PARAM`**LParam** člena je neplatný.  
  
- `TCIF_RTLREADING`Text **pszText** se zobrazí v hebrejštině nebo arabské systému pomocí pořadí čtení zprava doleva.  
  
- `TCIF_STATE`**DwState** člena je neplatný.  
  
 `lParam`  
 Definované aplikací data přidružená k kartě.  
  
 `dwState`  
 Určuje hodnoty pro položky stavy. Další informace najdete v tématu [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) ve Windows SDK.  
  
 *dwStateMask*  
 Určuje, jaké stavy jsou nastavení. Další informace najdete v tématu [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index nule na nové kartě v případě úspěšného; jinak - 1.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]  
  
##  <a name="removeimage"></a>CTabCtrl::RemoveImage  
 Odebere zadanou bitovou kopii z ovládacího prvku karta seznamu obrázků.  
  
```  
void RemoveImage(int nImage);
```  
  
### <a name="parameters"></a>Parametry  
 `nImage`  
 Index bitové kopie k odebrání nule.  
  
### <a name="remarks"></a>Poznámky  
 Ovládacího prvku karta aktualizuje index bitové kopie každé kartě tak, aby zůstal přidružené stejnou bitovou kopii každé kartě.  
  
##  <a name="setcurfocus"></a>CTabCtrl::SetCurFocus  
 Nastaví fokus na zadanou kartu v ovládacím prvkem karta.  
  
```  
void SetCurFocus(int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Určuje index na kartě, který získá fokus.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TCM_SETCURFOCUS](http://msdn.microsoft.com/library/windows/desktop/bb760610), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setcursel"></a>CTabCtrl::SetCurSel  
 Vyberte na kartě v ovládacím prvkem karta.  
  
```  
int SetCurSel(int nItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Index založený na nule položky, aby byl vybrán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index nule dříve vybrané kartě, pokud bylo úspěšné, jinak hodnota - 1.  
  
### <a name="remarks"></a>Poznámky  
 Ovládacího prvku karta neodesílá **TCN_SELCHANGING** nebo **TCN_SELCHANGE** oznámení, pokud je vybrána na kartě, použití této funkce. Tato oznámení se odesílají, pomocí **wm_notify –**, když uživatel klikne na tlačítko nebo změnit karet pomocí klávesnice.  
  
##  <a name="setextendedstyle"></a>CTabCtrl::SetExtendedStyle  
 Nastaví rozšířené styly pro ovládací prvek karty.  
  
```  
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `dwNewStyle`  
 Hodnota, která určuje kombinaci karta řídit rozšířené styly.  
  
 `dwExMask`  
 A `DWORD` hodnotu, která určuje, jaké styly v `dwNewStyle` mají mít vliv. Rozšířené styly pouze v `dwExMask` se změní. Všechny ostatní styly se zachová, jako je. Pokud má parametr hodnotu nula, pak všechny styly v `dwNewStyle` bude mít vliv.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `DWORD` hodnotu, která obsahuje předchozí [kartě řízení extended styly](http://msdn.microsoft.com/library/windows/desktop/bb760546), jak je popsáno v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato funkce člen implementuje chování zprávy Win32 [TCM_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb760627), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setimagelist"></a>CTabCtrl::SetImageList  
 Přiřadí seznamu obrázků do ovládacího prvku karta.  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `pImageList`  
 Ukazatel na seznamu obrázků přiřazení ovládacího prvku karta.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na předchozí seznamu obrázků nebo **NULL** Pokud není žádná předchozí seznamu obrázků.  
  
##  <a name="setitem"></a>CTabCtrl::SetItem  
 Nastaví některé nebo všechny na kartě atributy.  
  
```  
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Index položky nule.  
  
 `pTabCtrlItem`  
 Ukazatel na [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) struktura, která obsahuje nové atributy položek. **Maska** člen Určuje atributy, které chcete nastavit. Pokud **maska** určuje člen `TCIF_TEXT` hodnotu, **pszText** člen je adresa řetězce ukončené hodnotou null a **cchTextMax** člen se ignoruje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [GetItem](#getitem).  
  
##  <a name="setitemextra"></a>CTabCtrl::SetItemExtra  
 Nastaví počet bajtů za karta vyhrazené pro definované aplikací dat v ovládacím prvkem karta.  
  
```  
BOOL SetItemExtra(int nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Počet bajtů navíc k nastavení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TCM_SETITEMEXTRA](http://msdn.microsoft.com/library/windows/desktop/bb760633), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setitemsize"></a>CTabCtrl::SetItemSize  
 Nastaví šířku a výšku položek ovládacího prvku karta.  
  
```  
CSize SetItemSize(CSize size);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Nové šířka a výška v pixelech položek ovládacího prvku karta.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí původní šířka a výška položky ovládacího prvku karta.  
  
##  <a name="setitemstate"></a>CTabCtrl::SetItemState  
 Nastaví stav položky ovládacího prvku karta identifikovaný `nItem`.  
  
```  
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```  
  
### <a name="parameters"></a>Parametry  
 `nItem`  
 Číslo od nuly index položky, pro kterou chcete nastavit informace o stavu.  
  
 `dwMask`  
 Maska určující, které položky stavu flags nastavit. Seznam hodnot najdete v tématu členem maska [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) struktury, jak je popsáno v sadě Windows SDK.  
  
 `dwState`  
 Odkaz na `DWORD` hodnotu obsahující informace o stavu. Může být jedna z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|**TCIS_BUTTONPRESSED**|Je vybrána položka ovládacího prvku karta.|  
|**TCIS_HIGHLIGHTED**|Položky ovládacího prvku karta je zvýrazněna a karta a text jsou vykreslovány pomocí aktuální barva zvýraznění. Pokud používáte barva zvýraznění, bude hodnota true, interpolace, tónovaná barva.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
##  <a name="setmintabwidth"></a>CTabCtrl::SetMinTabWidth  
 Nastaví minimální šířku položky v ovládacím prvkem karta.  
  
```  
int SetMinTabWidth(int cx);
```  
  
### <a name="parameters"></a>Parametry  
 `cx`  
 Minimální šířka, jež bude nastavena pro položku ovládacího prvku karta. Pokud tento parametr je nastaven na hodnotu -1, ovládacího prvku použije výchozí kartě šířku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí šířka minimální kartě.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato funkce člen implementuje chování zprávy Win32 [TCM_SETMINTABWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760637), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setpadding"></a>CTabCtrl::SetPadding  
 Nastaví množství místa (odsazení) kolem ikona a popisek v ovládacím prvkem karta každé kartě.  
  
```  
void SetPadding(CSize size);
```  
  
### <a name="parameters"></a>Parametry  
 `size`  
 Nastaví množství místa (odsazení) kolem ikona a popisek v ovládacím prvkem karta každé kartě.  
  
##  <a name="settooltips"></a>CTabCtrl::SetToolTips  
 Přiřadí prvkem popis tlačítka do ovládacího prvku karta.  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndTip`  
 Popisovač ovládacím prvkem popis tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Můžete získat ovládacím prvkem popis tlačítka spojené s ovládacím prvkem karta tím, že zavoláte na `GetToolTips`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CHeaderCtrl – třída](../../mfc/reference/cheaderctrl-class.md)   
 [CListCtrl – třída](../../mfc/reference/clistctrl-class.md)
