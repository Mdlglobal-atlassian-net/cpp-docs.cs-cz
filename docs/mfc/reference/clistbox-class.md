---
title: "Clistbox – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: df627cbd062d2347539c0db26580360d80c3dd9a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="clistbox-class"></a>Clistbox – třída
Poskytuje funkci pole se seznamem systému Windows.  
  
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
|[CListBox::CharToItem](#chartoitem)|Přepsání za účelem poskytování vlastní `WM_CHAR` zpracování pro vykreslování vlastníka seznamy, které nemají řetězce.|  
|[CListBox::CompareItem](#compareitem)|Voláno rámcem k určení pozice novou položku v seznamu seřazené vykreslování vlastníka.|  
|[CListBox::Create](#create)|Pole se seznamem Windows vytvoří a připojí jej k `CListBox` objektu.|  
|[CListBox::DeleteItem](#deleteitem)|Voláno rámcem, když uživatel odstraní položku ze seznamu vykreslování vlastníka.|  
|[CListBox::DeleteString](#deletestring)|Řetězec se odstraní ze seznamu.|  
|[CListBox::Dir](#dir)|Přidá do pole se seznamem názvů souborů, jednotky nebo obojí z aktuálního adresáře.|  
|[CListBox::DrawItem](#drawitem)|Voláno rámcem při visual aspekt vykreslování vlastníka seznamu se změní.|  
|[CListBox::FindString](#findstring)|Vyhledá řetězec v seznamu.|  
|[CListBox::FindStringExact](#findstringexact)|Vyhledá první pole se seznamem řetězec, který odpovídá určeného řetězce.|  
|[CListBox::GetAnchorIndex](#getanchorindex)|Načte index založený na nule aktuální ukotvení položky v seznamu.|  
|[CListBox::GetCaretIndex](#getcaretindex)|Určuje index položky, která nemá rámečku fokusu v poli s vícenásobným výběrem.|  
|[CListBox::GetCount](#getcount)|Vrátí počet řetězců v seznamu.|  
|[CListBox::GetCurSel](#getcursel)|Vrátí index o základu 0 řetězce, který aktuálně vybraného v seznamu.|  
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Vrátí šířku v pixelech, vodorovně posunout pole se seznamem.|  
|[CListBox::GetItemData](#getitemdata)|Vrátí hodnotu 32-bit přidružené k položce pole se seznamem.|  
|[CListBox::GetItemDataPtr](#getitemdataptr)|Vrací ukazatel na položku pole se seznamem.|  
|[CListBox::GetItemHeight](#getitemheight)|Určuje výšku položky v seznamu.|  
|[CListBox::GetItemRect](#getitemrect)|Vrátí ohraničující obdélník položky pole se seznamem, který je aktuálně zobrazovat.|  
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Načte počet položek na sloupec.|  
|[CListBox::GetLocale](#getlocale)|Načte identifikátor národního prostředí pro pole se seznamem.|  
|[CListBox::GetSel](#getsel)|Vrátí stav výběru položky pole se seznamem.|  
|[CListBox::GetSelCount](#getselcount)|Vrátí počet aktuálně vybraného v seznamu s vícenásobným výběrem pole řetězců.|  
|[CListBox::GetSelItems](#getselitems)|Vrátí indexy řetězců v seznamu aktuálně vybranou.|  
|[CListBox::GetText](#gettext)|Zkopíruje položky pole se seznamem do vyrovnávací paměti.|  
|[CListBox::GetTextLen](#gettextlen)|Vrátí délku v bajtech položky pole se seznamem.|  
|[CListBox::GetTopIndex](#gettopindex)|Vrátí index první viditelné řetězec v seznamu.|  
|[CListBox::InitStorage](#initstorage)|Preallocates bloky paměti pro položky seznamu pole a řetězce.|  
|[CListBox::InsertString](#insertstring)|Vloží řetězec na určité místo v seznamu.|  
|[CListBox::ItemFromPoint](#itemfrompoint)|Vrátí index položky pole se seznamem nejbližší bod.|  
|[CListBox::MeasureItem](#measureitem)|Voláno rámcem při vytvoření seznamu vykreslování vlastníka k určení rozměry pole se seznamem.|  
|[CListBox::ResetContent](#resetcontent)|Vymaže všechny položky ze seznamu.|  
|[CListBox::SelectString](#selectstring)|Vyhledá a vybere řetězec v seznamu jedním výběrem.|  
|[CListBox::SelItemRange](#selitemrange)|Vybere nebo zruší výběr řadu řetězců v seznamu vícenásobného výběru.|  
|[CListBox::SetAnchorIndex](#setanchorindex)|Nastaví ukotvení v poli seznamu s vícenásobným výběrem zahájíte rozšířené výběr.|  
|[CListBox::SetCaretIndex](#setcaretindex)|Nastaví rámečku fokusu položek v zadaném indexu v seznamu vícenásobného výběru.|  
|[CListBox::SetColumnWidth](#setcolumnwidth)|Nastaví šířku pole se seznamem více sloupců.|  
|[CListBox::SetCurSel](#setcursel)|Vybere pole se seznamem řetězec.|  
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Nastaví šířku v pixelech, vodorovně posunout pole se seznamem.|  
|[CListBox::SetItemData](#setitemdata)|Nastaví hodnotu 32-bit přidružené k položce pole se seznamem.|  
|[CListBox::SetItemDataPtr](#setitemdataptr)|Nastaví ukazatel na položku pole se seznamem.|  
|[CListBox::SetItemHeight](#setitemheight)|Nastaví výšku položky v seznamu.|  
|[CListBox::SetLocale](#setlocale)|Nastaví identifikátor národního prostředí pro pole se seznamem.|  
|[CListBox::SetSel](#setsel)|Vybere nebo zruší výběr pole se seznamem položku v seznamu vícenásobného výběru.|  
|[CListBox::SetTabStops](#settabstops)|Nastaví zarážek pozice v seznamu.|  
|[CListBox::SetTopIndex](#settopindex)|Nastaví index založený na nule řetězce první viditelné v seznamu.|  
|[CListBox::VKeyToItem](#vkeytoitem)|Přepsání za účelem poskytování vlastní `WM_KEYDOWN` zpracování pro seznamy s **lbs_wantkeyboardinput –** styl sady.|  
  
## <a name="remarks"></a>Poznámky  
 Pole se seznamem zobrazí seznam položek, jako jsou názvy souborů, který uživatel může zobrazit a vybrat.  
  
 V seznamu jedním výběrem kterého uživatel může vybrat jen jednu položku. V seznamu s vícenásobným výběrem pole lze vybrat rozsah položky. Když uživatel vybere položku, je označený a pole se seznamem odešle upozornění do nadřazeného okna.  
  
 Pole se seznamem můžete vytvořit buď z šablony dialogového okna, nebo přímo v kódu. Pokud chcete vytvořit přímo, vytvořit `CListBox` objekt a potom volání [vytvořit](#create) členské funkce ovládacího prvku pole se seznamem Windows a vytvořte jej do `CListBox` objektu. Použijte seznam pole v šablony dialogového okna, deklarovat proměnnou pole se seznamem ve vaší třídy dialogového okna a potom použijte `DDX_Control` ve vlastní pole třídy dialogového okna `DoDataExchange` funkce pro připojení členské proměnné do ovládacího prvku. (to se provádí pro vás automaticky při přidání proměnné ovládacího prvku do vaší třídy dialogového okna.)  
  
 Konstrukce může být jednoduchý proces v třídy odvozené od `CListBox`. Zápis konstruktoru odvozené třídy a volání **vytvořit** z v konstruktoru.  
  
 Pokud chcete pro zpracování zpráv s oznámením Windows posílá nadřazené pole se seznamem (obvykle třída odvozená z [CDialog](../../mfc/reference/cdialog-class.md)), přidejte map zpráv položku a obslužné rutiny zpráv členské funkce do nadřazené třídy pro každou zprávu.  
  
 Každá položka mapování zpráv má následující podobu:  
  
 `ON_Notification( id, memberFxn )`  
  
 kde `id` Určuje ID podřízené okno ovládacího prvku pole se seznamem odesílání oznámení a `memberFxn` je název nadřazeného člena funkce napsané pro zpracování oznámení.  
  
 Prototyp funkce nadřazeného objektu je následující:  
  
 `afx_msg void memberFxn( );`  
  
 Následuje seznam možných položkách map zpráv a popis v případech, ve kterých se mají být odeslány do nadřazené:  
  
- **ON_LBN_DBLCLK** poklepání řetězec v seznamu. Pouze seznam, který má [lbs_notify –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl odešle tuto zprávu oznámení.  
  
- **ON_LBN_ERRSPACE** pole se seznamem nemůže přidělit dostatek paměti ke splnění žádosti.  
  
- **ON_LBN_KILLFOCUS** pole se seznamem je ztráty zaměření pro vstup.  
  
- **ON_LBN_SELCANCEL** aktuální výběr pole se seznamem je zrušená. Tato zpráva je odeslán, pouze pokud má pole se seznamem **lbs_notify –** stylu.  
  
- **ON_LBN_SELCHANGE** došlo ke změně výběr v seznamu. Toto oznámení nejsou odesílány, pokud je výběr změnit [CListBox::SetCurSel](#setcursel) – členská funkce. Toto oznámení se vztahuje pouze na pole se seznamem, který má **lbs_notify –** stylu. **LBN_SELCHANGE** oznámení je odeslána zpráva pro pole se seznamem vícenásobného výběru vždy, když uživatel stiskne klávesu se šipkou i v případě, že výběr se nemění.  
  
- **ON_LBN_SETFOCUS** pole se seznamem přijímá zaměření pro vstup.  
  
- **ON_WM_CHARTOITEM** obdrží seznam vykreslování vlastníka, který nemá žádné řetězce `WM_CHAR` zprávy.  
  
- **ON_WM_VKEYTOITEM** pole se seznamem **lbs_wantkeyboardinput –** styl obdrží `WM_KEYDOWN` zprávy.  
  
 Pokud vytvoříte `CListBox` objekt v rámci dialogového okna (prostřednictvím prostředku dialogového okna), `CListBox` objekt zničen automaticky při zavření dialogu.  
  
 Pokud vytvoříte `CListBox` objekt v rámci časového období, budete muset destroy `CListBox` objektu. Pokud vytvoříte `CListBox` objektu v zásobníku, byla automaticky. Pokud vytvoříte `CListBox` objektu v haldě pomocí **nové** funkce, musí volat **odstranit** na objekt, který má zničte, jakmile uživatel nezavře nadřazeného okna.  
  
 Pokud přidělíte libovolná paměť v `CListBox` objektu, přepsat `CListBox` destruktor k uvolnění přidělení.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListBox`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="addstring"></a>CListBox::AddString  
 Přidá řetězec do pole se seznamem.  
  
```  
int AddString(LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszItem`  
 Body řetězce ukončené hodnotou null, který má být přidán.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index o základu 0 pro řetězec v seznamu. Vrácená hodnota je **LB_ERR** Pokud dojde k chybě; vrácená hodnota je **LB_ERRSPACE** Pokud je k dispozici pro uložení nového řetězce není dostatek místa.  
  
### <a name="remarks"></a>Poznámky  
 Pokud pole se seznamem nebyla vytvořena pomocí [lbs_sort –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, řetězec se přidá na konec seznamu. Jinak řetězec vložíte do seznamu, a tento seznam je řazen. Pokud pole se seznamem byl vytvořen s **lbs_sort –** styl ale není [lbs_hasstrings –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl rozhraní Seřadí seznam ve jeden nebo více volání `CompareItem` – členská funkce.  
  
 Použití [InsertString](#insertstring) vložení řetězec do určitého umístění v rámci pole se seznamem.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]  
  
##  <a name="chartoitem"></a>CListBox::CharToItem  
 Voláno rámcem přijetí nadřazeného okna pole se seznamem `WM_CHARTOITEM` zpráv ze seznamu.  
  
```  
virtual int CharToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nKey`  
 ANSI kód znaku uživatel zadal.  
  
 `nIndex`  
 Aktuální umístění pomocí pole se seznamem kurzoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu - 1 nebo - 2 pro žádná další akce nebo zadejte index položky pole se seznamem, na které se má provést výchozí akci pro klávesu nezáporné číslo. Výchozí implementace vrátí hodnotu - 1.  
  
### <a name="remarks"></a>Poznámky  
 `WM_CHARTOITEM` Odesílají zprávy pole se seznamem při přijetí `WM_CHAR` zprávy, ale pouze pokud pole se seznamem splňuje všechny tato kritéria:  
  
-   Je vykreslování vlastníka pole se seznamem.  
  
-   Nemá [lbs_hasstrings –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl sady.  
  
-   Má alespoň jednu položku.  
  
 Měli byste nikdy volat tuto funkci sami. Přepsání této funkce můžete poskytnout vlastní vlastní zpracování zpráv klávesnice.  
  
 V přepsání musí vrátit hodnotu říct rozhraní, jaké akce, které jste provedli. Návratová hodnota - 1 nebo - 2 určuje zpracovává všechny aspekty výběrem položky a vyžaduje žádná další akce podle pole se seznamem. Před vrácením - 1 nebo - 2, můžete nastavení výběru nebo přesunout vsuvka nebo obojí. Pokud chcete nastavit výběr, použijte [setcursel –](#setcursel) nebo [SetSel](#setsel). Chcete-li přesunout znak, použijte [SetCaretIndex](#setcaretindex).  
  
 Vrácená hodnota 0 nebo větší Určuje index položky v seznamu a označuje, že pole se seznamem by měl výchozí akce pro klávesu na danou položku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]  
  
##  <a name="clistbox"></a>CListBox::CListBox  
 Vytvoří `CListBox` objektu.  
  
```  
CListBox();
```  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CListBox` objektu ve dvou krocích. Nejprve volat konstruktor **clistbox –** a pak zavolají **vytvořit**, která inicializuje pole se seznamem Windows a připojí jej k `CListBox`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]  
  
##  <a name="compareitem"></a>CListBox::CompareItem  
 Voláno rámcem určit relativní umístění novou položku v seznamu seřazené vykreslování vlastníka.  
  
```  
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpCompareItemStruct`  
 Dlouhé ukazatel `COMPAREITEMSTRUCT` struktura.  
  
### <a name="return-value"></a>Návratová hodnota  
 Určuje relativní pozici dvě položky, které jsou popsané v [compareitemstruct –](../../mfc/reference/compareitemstruct-structure.md) struktura. Může to být žádný z následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|-1|Položka 1 seřadí před položka 2.|  
|0|Položka 1 a 2 položky řadit stejné.|  
|1|Položka 1 seřadí po položka 2.|  
  
 V tématu [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) popis `COMPAREITEMSTRUCT` struktura.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato funkce člen neprovede žádnou akci. Pokud vytvoříte seznam vykreslování vlastníka s **lbs_sort –** styl, je nutné přepsat tuto členskou funkci rozhraní jako pomůcku při řazení nové položky, které jsou přidány do seznamu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]  
  
##  <a name="create"></a>CListBox::Create  
 Pole se seznamem Windows vytvoří a připojí jej k `CListBox` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl pole se seznamem. Použít libovolnou kombinaci [styly seznamů](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) do pole.  
  
 `rect`  
 Určuje velikost pole se seznamem a umístění. Může být buď `CRect` objekt nebo `RECT` struktury.  
  
 `pParentWnd`  
 Určuje pole se seznamem nadřazeného okna (obvykle `CDialog` objekt). Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku pole se seznamem  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CListBox` objektu ve dvou krocích. Nejprve volat konstruktor a pak zavolají **vytvořit**, která inicializuje pole se seznamem Windows a připojí jej k `CListBox` objektu.  
  
 Když **vytvořit** provede, odešle Windows [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), a [WM_ GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) zprávy do ovládacího prvku pole se seznamem.  
  
 Tyto zprávy jsou zpracovávány ve výchozím nastavení [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), a [ongetminmaxinfo –](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) členské funkce v `CWnd` základní třídy. Rozšíření zpracování zpráv výchozí, odvození třídy z `CListBox`, přidejte mapy zpráv do nové třídy a přepsat předchozí členské funkce obslužné rutiny zpráv. Přepsání `OnCreate`, například k provedení potřebných inicializace pro novou třídu.  
  
 Použít následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) do ovládacího prvku pole se seznamem.  
  
- **Ws_child –** vždy  
  
- **Ws_visible –** obvykle  
  
- **Ws_disabled –** zřídka  
  
- **Ws_vscroll –** přidat svislý posuvník  
  
- **Ws_hscroll –** přidat vodorovného posuvníku  
  
- **Ws_group –** k seskupování ovládacích prvků  
  
- **Ws_tabstop –** umožňující pomocí klávesy tabulátor do tohoto ovládacího prvku  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]  
  
##  <a name="deleteitem"></a>CListBox::DeleteItem  
 Voláno rámcem, když uživatel odstraní položku z kreslení vlastníka `CListBox` objektu nebo zničí pole se seznamem.  
  
```  
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDeleteItemStruct`  
 Dlouhé ukazatel na Windows [deleteitemstruct –](../../mfc/reference/deleteitemstruct-structure.md) struktura, která obsahuje informace o odstraněné položky.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace této funkce neprovede žádnou akci. Přepsání této funkci můžete ho překreslit pole se seznamem vykreslování vlastníka podle potřeby.  
  
 V tématu [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) popis `DELETEITEMSTRUCT` struktura.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]  
  
##  <a name="deletestring"></a>CListBox::DeleteString  
 Odstraní položky v pozici `nIndex` z pole se seznamem.  
  
```  
int DeleteString(UINT nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index založený na nule řetězce, který má být odstraněn.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet zbývajících v seznamu řetězců. Vrácená hodnota je **LB_ERR** Pokud `nIndex` Určuje indexu větší než počet položek v seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Všechny položky následující `nIndex` nyní přesunout o jednu pozici dolů. Například pokud seznam obsahuje dvě položky, odstranění první položka způsobí, že zbývající položka, která má být nyní v první pozici. `nIndex`= 0 pro položky v první pozici.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]  
  
##  <a name="dir"></a>CListBox::Dir  
 Přidá seznam názvů souborů, disky nebo obojího pole se seznamem.  
  
```  
int Dir(
    UINT attr,  
    LPCTSTR lpszWildCard);
```  
  
### <a name="parameters"></a>Parametry  
 `attr`  
 Může být libovolnou kombinací `enum` hodnoty popsané v **CFile::GetStatu**[s](../../mfc/reference/cfile-class.md#getstatus), nebo libovolnou kombinaci těchto hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|0x0000|Soubor může číst nebo zapisovat do.|  
|0x0001|Soubor můžete číst z ale nezapíše se do.|  
|0x0002|Soubor je skrytá a v seznamu adresářů nezobrazí.|  
|0x0004|Soubor je soubor systému.|  
|0x0010|Název zadaný `lpszWildCard` Určuje adresář.|  
|0x0020|Soubor byl archivován.|  
|0x4000|Zahrnout všechny disky, které odpovídají názvu určeného `lpszWildCard`.|  
|0x8000|Výhradní příznak. Pokud je nastavený příznak výhradní, jsou uvedeny pouze soubory zadaného typu. Soubory zadaného typu, jinak, jsou uvedené kromě "normální" souborů.|  
  
 `lpszWildCard`  
 Odkazuje na řetězec specifikaci souboru. Řetězec může obsahovat zástupné znaky (například *.\*).  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule poslední názvu souboru do seznamu přidat. Vrácená hodnota je **LB_ERR** Pokud dojde k chybě; vrácená hodnota je **LB_ERRSPACE** Pokud je k dispozici pro uložení nových řetězců není dostatek místa.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]  
  
##  <a name="drawitem"></a>CListBox::DrawItem  
 Voláno rámcem při visual aspekt vykreslování vlastníka seznamu se změní.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Dlouhé ukazatel [drawitemstruct –](../../mfc/reference/drawitemstruct-structure.md) struktura, která obsahuje informace o typu kreslení vyžaduje.  
  
### <a name="remarks"></a>Poznámky  
 **ItemAction** a **itemState** členy `DRAWITEMSTRUCT` struktura definovat kreslení akci, která má být provedena.  
  
 Ve výchozím nastavení tato funkce člen neprovede žádnou akci. Člen funkci implementovat kreslení pro kreslení vlastníka přepsat `CListBox` objektu. Aplikace by měla obnovit všechny grafiky zařízení rozhraní GDI objekty vybrané pro zadaný kontext zobrazení v `lpDrawItemStruct` před tento člen funkce ukončí.  
  
 V tématu [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) popis `DRAWITEMSTRUCT` struktura.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]  
  
##  <a name="findstring"></a>CListBox::FindString  
 Najde první řetězec v seznamu, který obsahuje zadanou předponu beze změny výběru pole se seznamem.  
  
```  
int FindString(
    int nStartAfter,  
    LPCTSTR lpszItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nStartAfter`  
 Obsahuje index položky před první má proběhnout založený na nule. Při hledání dosáhne spodní části pole se seznamem, pokračuje z horní části seznamu zpátky k položce určeného `nStartAfter`. Pokud `nStartAfter` je -1, prohledají se celý seznam od začátku.  
  
 `lpszItem`  
 Body řetězce ukončené hodnotou null, který obsahuje předpona, kterou chcete vyhledat. Hledání je případ nezávislé, takže tento řetězec může obsahovat libovolnou kombinaci velkých a velkých písmen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule odpovídající položky nebo **LB_ERR** Pokud vyhledávání nebylo úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Použití [SelectString](#selectstring) – členská funkce k vyhledávání a vyberte řetězec.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]  
  
##  <a name="findstringexact"></a>CListBox::FindStringExact  
 Najde první pole se seznamem řetězec, který odpovídá řetězec zadaný v `lpszFind`.  
  
```  
int FindStringExact(
    int nIndexStart,  
    LPCTSTR lpszFind) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndexStart`  
 Určuje index položky před první má proběhnout založený na nule. Při hledání dosáhne spodní části pole se seznamem, pokračuje z horní části seznamu zpátky k položce určeného `nIndexStart`. Pokud `nIndexStart` je -1, prohledají se celý seznam od začátku.  
  
 `lpszFind`  
 Odkazuje na hledaný řetězec ukončené hodnotou null. Tento řetězec může obsahovat úplný název souboru, včetně přípony. Hledání není velká a malá písmena, takže řetězec může obsahovat libovolnou kombinaci velkých a velkých písmen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index odpovídající položky nebo **LB_ERR** Pokud vyhledávání nebylo úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud pole se seznamem byl vytvořen s styl vykreslování vlastníka, ale bez [lbs_hasstrings –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, `FindStringExact` – členská funkce pokusí odpovídají hodnotě doubleword s hodnotou `lpszFind`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]  
  
##  <a name="getanchorindex"></a>CListBox::GetAnchorIndex  
 Načte index založený na nule aktuální ukotvení položky v seznamu.  
  
```  
int GetAnchorIndex() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index aktuální položky anchor, v případě úspěšného; v opačném případě **LB_ERR**.  
  
### <a name="remarks"></a>Poznámky  
 V dialogovém okně vícenásobným výběrem ukotvení položka je první nebo poslední položku v bloku souvislý vybrané položky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CListBox::SetAnchorIndex](#setanchorindex).  
  
##  <a name="getcaretindex"></a>CListBox::GetCaretIndex  
 Určuje index položky, která nemá rámečku fokusu v poli s vícenásobným výběrem.  
  
```  
int GetCaretIndex() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule položky, kterou má rámečku fokusu v seznamu. Pokud pole se seznamem je pole se seznamem jedním výběrem, vrácená hodnota je index položky, kterou vyberete, pokud existuje.  
  
### <a name="remarks"></a>Poznámky  
 Může nebo nemusí být vybrané položky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CListBox::SetCaretIndex](#setcaretindex).  
  
##  <a name="getcount"></a>CListBox::GetCount  
 Načte počet položek v seznamu.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek v seznamu, nebo **LB_ERR** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Vrácený počet je větší než hodnota indexu poslední položky (index je počítáno od nuly).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]  
  
##  <a name="getcursel"></a>CListBox::GetCurSel  
 Načte index založený na nule aktuálně vybrané položky, pokud existuje, v poli seznamu jedním výběrem.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule aktuálně vybrané položky. Pokud je pole se seznamem jedním výběrem. Je `LB_ERR` Pokud aktuálně není vybrána žádná položka.  
  
 V seznamu s vícenásobným výběrem pole index položky, který je aktivní.  
  
### <a name="remarks"></a>Poznámky  
 Nevolejte `GetCurSel` pro pole se seznamem vícenásobného výběru. Použití [CListBox::GetSelItems](#getselitems) místo.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]  
  
##  <a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent  
 Načte z pole se seznamem šířku v pixelech, které ho vodorovně posunout.  
  
```  
int GetHorizontalExtent() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Posuvný šířka pole se seznamem, v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tuto možnost lze použít pouze v případě pole se seznamem vodorovného posuvníku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]  
  
##  <a name="getitemdata"></a>CListBox::GetItemData  
 Načte hodnotu doubleword zadané aplikace přidružené k položce zadaného seznamu.  
  
```  
DWORD_PTR GetItemData(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index založený na nule položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 32-bit hodnotu přidruženou položku, nebo **LB_ERR** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota doubleword byla `dwItemData` parametr [setitemdata –](#setitemdata) volání.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]  
  
##  <a name="getitemdataptr"></a>CListBox::GetItemDataPtr  
 Načte 32bitové hodnotu zadané aplikace přidružené k položce zadaný seznam jako ukazatel ( **void\***).  
  
```  
void* GetItemDataPtr(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index založený na nule položky v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Načte ukazatel nebo -1, pokud dojde k chybě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]  
  
##  <a name="getitemheight"></a>CListBox::GetItemHeight  
 Určuje výšku položky v seznamu.  
  
```  
int GetItemHeight(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index založený na nule položky v seznamu. Tento parametr se používá pouze v případě, že má pole se seznamem **lbs_ownerdrawvariable –** styl; jinak, by měla být nastavena na hodnotu 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška v pixelech, položky v seznamu. Pokud má pole se seznamem [lbs_ownerdrawvariable –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) je návratovou hodnotu styl, výška položky určeného `nIndex`. Pokud dojde k chybě, je vrácenou hodnotu **LB_ERR**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]  
  
##  <a name="getitemrect"></a>CListBox::GetItemRect  
 Načte dimenze rámeček daná položka rozsah – pole se seznamem, jako je aktuálně zobrazený v okně pole se seznamem.  
  
```  
int GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index položky založený na nule.  
  
 `lpRect`  
 Určuje dlouho ukazatel [Rect – struktura](../../mfc/reference/rect-structure1.md) která přijme souřadnice klienta pole se seznamem položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 **LB_ERR** Pokud dojde k chybě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]  
  
##  <a name="getlistboxinfo"></a>CListBox::GetListBoxInfo  
 Načte počet položek na sloupec.  
  
```  
DWORD GetListBoxInfo() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek na sloupec `CListBox` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce [LB_GETLISTBOXINFO](http://msdn.microsoft.com/library/windows/desktop/bb775208) zprávy, jak je popsáno v sadě Windows SDK.  
  
##  <a name="getlocale"></a>CListBox::GetLocale  
 Načte národní prostředí používané pole se seznamem.  
  
```  
LCID GetLocale() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota identifikátoru (LCID) národního prostředí pro řetězce v rozevíracím seznamu.  
  
### <a name="remarks"></a>Poznámky  
 Národní prostředí se používá, například k určení pořadí řazení řetězců v seřazený seznam.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CListBox::SetLocale](#setlocale).  
  
##  <a name="getsel"></a>CListBox::GetSel  
 Načte stav výběru položky.  
  
```  
int GetSel(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index položky založený na nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Kladné číslo. Pokud je zadaná položka vybrána; v opačném případě je 0. Vrácená hodnota je `LB_ERR` Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce pracuje s oba seznamy výběr jednoho a víc.  
  
 Pro načtení index položku aktuálně vybraném seznamu, použijte [CListBox::GetCurSel](#getcursel).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]  
  
##  <a name="getselcount"></a>CListBox::GetSelCount  
 Načte celkový počet vybraných položek v seznamu vícenásobného výběru.  
  
```  
int GetSelCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet vybraných položek v seznamu. Pokud pole se seznamem je seznam s jedním výběrem pole, je vrácenou hodnotu **LB_ERR**.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CListBox::GetSelItems](#getselitems).  
  
##  <a name="getselitems"></a>CListBox::GetSelItems  
 Vyrovnávací paměť vyplní pole celých čísel, které určuje položku čísla vybrané položky v seznamu vícenásobného výběru.  
  
```  
int GetSelItems(
    int nMaxItems,  
    LPINT rgIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nMaxItems`  
 Určuje maximální počet vybraných položek, jejichž čísla položek mají být umístěny ve vyrovnávací paměti.  
  
 `rgIndex`  
 Určuje ukazatel na dostatečně velký počet celých čísel určeného `nMaxItems`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Skutečný počet položek, které jsou umístěny ve vyrovnávací paměti. Pokud pole se seznamem je seznam s jedním výběrem pole, je vrácenou hodnotu `LB_ERR`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]  
  
##  <a name="gettext"></a>CListBox::GetText  
 Získá řetězec, ze seznamu.  
  
```  
int GetText(
    int nIndex,  
    LPTSTR lpszBuffer) const;  
  
void GetText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index založený na nule řetězce, který má být načtena.  
  
 `lpszBuffer`  
 Body do vyrovnávací paměti, která přijímá řetězec. Vyrovnávací paměti musí být dost místa pro řetězce a znak ukončující null. Velikost řetězce, který se dá určit předem voláním `GetTextLen` – členská funkce.  
  
 `rString`  
 Odkaz na `CString` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka řetězce, s výjimkou ukončující znak hodnoty null (v bajtech). Pokud `nIndex` neurčuje platný index, je vrácenou hodnotou **LB_ERR**.  
  
### <a name="remarks"></a>Poznámky  
 Druhý formulář člen funkce výplněmi `CString` objekt s textový řetězec.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]  
  
##  <a name="gettextlen"></a>CListBox::GetTextLen  
 Získá délku řetězce v položce pole se seznamem.  
  
```  
int GetTextLen(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index založený na nule řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka řetězce ve znacích, s výjimkou ukončující znak hodnoty null. Pokud `nIndex` neurčuje platný index, je vrácenou hodnotou **LB_ERR**.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CListBox::GetText](#gettext).  
  
##  <a name="gettopindex"></a>CListBox::GetTopIndex  
 Načte index založený na nule první zobrazené položky v seznamu.  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule první zobrazené položky v seznamu, pokud bylo úspěšné, **LB_ERR** jinak.  
  
### <a name="remarks"></a>Poznámky  
 Na začátku položka 0 je v horní části seznamu, ale pokud přesunut pole se seznamem oblasti jiné položky může být v horní části.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]  
  
##  <a name="initstorage"></a>CListBox::InitStorage  
 Přidělí paměť pro ukládání položky pole se seznamem.  
  
```  
int InitStorage(
    int nItems,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 `nItems`  
 Určuje počet položek, které chcete přidat.  
  
 `nBytes`  
 Určuje velikost paměti, v bajtech, přidělit pro položku řetězce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, maximální počet položek, které pole se seznamem můžete uložit, než je potřeba opakované přidělení paměti, v opačném případě **LB_ERRSPACE**, což znamená, není dost paměti je k dispozici.  
  
### <a name="remarks"></a>Poznámky  
 Před přidáním velké množství položek k volání této funkce `CListBox`.  
  
 Tato funkce pomáhá zrychlit inicializace seznamy, které mají velký počet položek (více než 100). Ho preallocates zadaného množství paměti, že následné [addstring –](#addstring), [InsertString](#insertstring), a [Dir](#dir) funkce přebírat co nejdříve. Odhadne můžete použít pro parametry. Pokud jste overestimate, se přidělí některé další paměť; Pokud jste příliš nízko, použije se normální přidělení pro položky, které překračují předběžně přidělená velikost.  
  
 Systém Windows 95/98 pouze: `nItems` je omezený na 16bitové hodnoty parametru. To znamená, že seznamy nesmí obsahovat víc než 32 767 položky. I když počet položek, které je s omezeným přístupem, celková velikost položky v seznamu je omezena pouze dostupné paměti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]  
  
##  <a name="insertstring"></a>CListBox::InsertString  
 Řetězec se vloží do pole se seznamem.  
  
```  
int InsertString(
    int nIndex,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index pozice tím řetězec vložíte založený na nule. Pokud má parametr hodnotu -1, řetězec se přidá na konec seznamu.  
  
 `lpszItem`  
 Body řetězce ukončené hodnotou null, který chcete vložit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule pozice, kdy byl vložen řetězec. Vrácená hodnota je **LB_ERR** Pokud dojde k chybě; vrácená hodnota je **LB_ERRSPACE** Pokud je k dispozici pro uložení nového řetězce není dostatek místa.  
  
### <a name="remarks"></a>Poznámky  
 Na rozdíl od [addstring –](#addstring) – členská funkce `InsertString` nezpůsobí seznam s [lbs_sort –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, který se má seřadit.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]  
  
##  <a name="itemfrompoint"></a>CListBox::ItemFromPoint  
 Určuje položky pole se seznamem nejbližší bod uvedený v `pt`.  
  
```  
UINT ItemFromPoint(
    CPoint pt,  
    BOOL& bOutside) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 Bod, pro které chcete najít nejbližší položky určen ve vztahu k levého horního rohu klientské oblasti pole se seznamem.  
  
 `bOutside`  
 Odkaz na `BOOL` proměnné, která bude nastavena pro `TRUE` Pokud `pt` je mimo oblast klienta nejbližší položku seznamu, `FALSE` Pokud `pt` je uvnitř oblasti klienta nejbližší položku seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index nejbližší položky na bod uvedený v `pt`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci můžete použít k určení, která pole se seznamem položka myší přesune přes.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CListBox::SetAnchorIndex](#setanchorindex).  
  
##  <a name="measureitem"></a>CListBox::MeasureItem  
 Voláno rámcem, když je vytvořen seznam s styl vykreslování vlastníka.  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpMeasureItemStruct`  
 Dlouhé ukazatel [measureitemstruct –](../../mfc/reference/measureitemstruct-structure.md) struktura.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení tato funkce člen neprovede žádnou akci. Funkci člena přepsat a vyplňte `MEASUREITEMSTRUCT` struktura k informování Windows pole se seznamem dimenzí. Pokud pole se seznamem je vytvořen s [lbs_ownerdrawvariable –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) volá framework styl, tato funkce člena pro každou položku v seznamu. Tento člen, jinak je volat pouze jednou.  
  
 Další informace o používání [lbs_ownerdrawfixed –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl v seznamu vykreslování vlastníka, vytvořené pomocí `SubclassDlgItem` členské funkce `CWnd`, viz popis v [Technická poznámka 14](../../mfc/tn014-custom-controls.md).  
  
 V tématu [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) popis `MEASUREITEMSTRUCT` struktura **.**  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]  
  
##  <a name="resetcontent"></a>CListBox::ResetContent  
 Odebere všechny položky ze seznamu.  
  
```  
void ResetContent();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]  
  
##  <a name="selectstring"></a>CListBox::SelectString  
 Hledání položky pole se seznamem, který odpovídá zadaným řetězcem, a pokud najde odpovídající položku, vybere položka.  
  
```  
int SelectString(
    int nStartAfter,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nStartAfter`  
 Obsahuje index položky před první má proběhnout založený na nule. Při hledání dosáhne spodní části pole se seznamem, pokračuje z horní části seznamu zpátky k položce určeného `nStartAfter`. Pokud `nStartAfter` je -1, prohledají se celý seznam od začátku.  
  
 `lpszItem`  
 Body řetězce ukončené hodnotou null, který obsahuje předpona, kterou chcete vyhledat. Hledání je případ nezávislé, takže tento řetězec může obsahovat libovolnou kombinaci velkých a velkých písmen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index vybrané položky. Pokud vyhledávání byl úspěšný. Pokud hledání nebylo úspěšné, je vrácenou hodnotu **LB_ERR** a aktuální výběr se nezmění.  
  
### <a name="remarks"></a>Poznámky  
 Pole se seznamem je přesunut oblasti, pokud je to nezbytné, aby se tím, že vybrané položky do zobrazení.  
  
 Tato funkce člena nelze použít s pole se seznamem, který má [lbs_multiplesel –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu.  
  
 Je položka vybrána pouze v případě, že jeho počáteční znaky (od počátečního bodu) odpovídat znakům řetězec určený `lpszItem`.  
  
 Použití `FindString` – členská funkce najít řetězec bez výběru položky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]  
  
##  <a name="selitemrange"></a>CListBox::SelItemRange  
 Vybere více po sobě jdoucích položek v seznamu vícenásobného výběru.  
  
```  
int SelItemRange(
    BOOL bSelect,  
    int nFirstItem,  
    int nLastItem);
```  
  
### <a name="parameters"></a>Parametry  
 `bSelect`  
 Určuje, jak nastavit výběr. Pokud `bSelect` je **TRUE**, řetězec nebude vybrána a zvýrazní; Pokud **FALSE**, je odebrán zvýraznění a řetězec je již vybrána.  
  
 `nFirstItem`  
 Určuje index založený na nule první položky nastavení.  
  
 `nLastItem`  
 Určuje index založený na nule poslední položky nastavení.  
  
### <a name="return-value"></a>Návratová hodnota  
 **LB_ERR** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce člen pouze s vícenásobným výběrem seznamy. Pokud je nutné vybrat jen jednu položku v poli seznamu s vícenásobným výběrem – to znamená, pokud `nFirstItem` rovná `nLastItem` – volání [SetSel](#setsel) členské funkce místo.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]  
  
##  <a name="setanchorindex"></a>CListBox::SetAnchorIndex  
 Nastaví ukotvení v poli seznamu s vícenásobným výběrem zahájíte rozšířené výběr.  
  
```  
void SetAnchorIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index založený na nule položky pole se seznamem, který bude ukotvení.  
  
### <a name="remarks"></a>Poznámky  
 V dialogovém okně vícenásobným výběrem ukotvení položka je první nebo poslední položku v bloku souvislý vybrané položky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]  
  
##  <a name="setcaretindex"></a>CListBox::SetCaretIndex  
 Nastaví rámečku fokusu položek v zadaném indexu v seznamu vícenásobného výběru.  
  
```  
int SetCaretIndex(
    int nIndex,  
    BOOL bScroll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index založený na nule položky přijímat rámečku fokusu v rozevíracím seznamu.  
  
 *bScroll*  
 Pokud tato hodnota je 0, je přesunut položka oblasti, dokud nebude plně viditelné. Pokud není tato hodnota 0, položka je přešli, dokud se aspoň částečně nezobrazí.  
  
### <a name="return-value"></a>Návratová hodnota  
 **LB_ERR** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud položka není viditelná, je přesunut do oblasti zobrazení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]  
  
##  <a name="setcolumnwidth"></a>CListBox::SetColumnWidth  
 Nastaví šířku v pixelech všechny sloupce v seznamu více sloupců (vytvořené pomocí [lbs_multicolumn –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl).  
  
```  
void SetColumnWidth(int cxWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `cxWidth`  
 Určuje šířku v pixelech všechny sloupce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]  
  
##  <a name="setcursel"></a>CListBox::SetCurSel  
 Vybere řetězec a posune do zobrazení, v případě potřeby.  
  
```  
int SetCurSel(int nSelect);
```  
  
### <a name="parameters"></a>Parametry  
 `nSelect`  
 Určuje řetězec, který má být vybrán index na nule. Pokud `nSelect` je -1, pole se seznamem nastavena tak, aby měl žádný výběr.  
  
### <a name="return-value"></a>Návratová hodnota  
 `LB_ERR`Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je vybraný nový řetězec, pole se seznamem Odebere zvýraznění z dříve vybrané řetězce.  
  
 Pomocí této funkce člen jenom s jedním výběrem seznamy.  
  
 Chcete-li nastavit nebo odebrat výběr v seznamu s vícenásobným výběrem pole, použijte [CListBox::SetSel](#setsel).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]  
  
##  <a name="sethorizontalextent"></a>CListBox::SetHorizontalExtent  
 Nastaví šířku v pixelech, podle kterých pole se seznamem vodorovně posunout.  
  
```  
void SetHorizontalExtent(int cxExtent);
```  
  
### <a name="parameters"></a>Parametry  
 *cxExtent*  
 Určuje počet pixelů, podle kterých pole se seznamem vodorovně posunout.  
  
### <a name="remarks"></a>Poznámky  
 Pokud velikost pole se seznamem je menší než tato hodnota, bude vodorovného posuvníku přejděte vodorovně položky v seznamu. Pokud pole se seznamem je stejně velké nebo větší než tato hodnota, je skrytý vodorovného posuvníku.  
  
 Reagovat na volání `SetHorizontalExtent`, pole se seznamem musí být definována s [ws_hscroll –](../../mfc/reference/styles-used-by-mfc.md#window-styles) stylu.  
  
 Tato funkce člen není vhodný pro více sloupců seznamy. U polí s více sloupci seznamu volání `SetColumnWidth` – členská funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]  
  
##  <a name="setitemdata"></a>CListBox::SetItemData  
 Nastaví hodnotu 32-bit přidružené zadaná položka v seznamu.  
  
```  
int SetItemData(
    int nIndex,  
    DWORD_PTR dwItemData);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index položky založený na nule.  
  
 `dwItemData`  
 Určuje, že hodnota je přidružená k položce.  
  
### <a name="return-value"></a>Návratová hodnota  
 **LB_ERR** Pokud dojde k chybě.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]  
  
##  <a name="setitemdataptr"></a>CListBox::SetItemDataPtr  
 Nastaví hodnotu 32-bit přidružené zadaná položka v seznamu jako zadaný ukazatele ( **void\***).  
  
```  
int SetItemDataPtr(
    int nIndex,  
    void* pData);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index položky založený na nule.  
  
 `pData`  
 Určuje má ukazatel na být přidružená k položce.  
  
### <a name="return-value"></a>Návratová hodnota  
 **LB_ERR** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Tento ukazatel zůstane platný po dobu trvání pole se seznamem, i když položky relativní pozici v rámci pole se seznamem může změnit, protože přidání nebo odebrání položky. Proto můžete změnit index položky v rámci pole, ale ukazatel zůstane spolehlivé.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]  
  
##  <a name="setitemheight"></a>CListBox::SetItemHeight  
 Nastaví výšku položky v seznamu.  
  
```  
int SetItemHeight(
    int nIndex,  
    UINT cyItemHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index založený na nule položky v seznamu. Tento parametr se používá pouze v případě, že má pole se seznamem **lbs_ownerdrawvariable –** styl; jinak, by měla být nastavena na hodnotu 0.  
  
 `cyItemHeight`  
 Určuje výšku v pixelech položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 **LB_ERR** Pokud index nebo výšky je neplatný.  
  
### <a name="remarks"></a>Poznámky  
 Pokud má pole se seznamem [lbs_ownerdrawvariable –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, tato funkce nastaví výšku položky určeného `nIndex`. Tato funkce jinak, nastaví výšku všechny položky v seznamu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]  
  
##  <a name="setlocale"></a>CListBox::SetLocale  
 Nastaví identifikátor národního prostředí pro toto pole se seznamem.  
  
```  
LCID SetLocale(LCID nNewLocale);
```  
  
### <a name="parameters"></a>Parametry  
 `nNewLocale`  
 Nová hodnota národního prostředí identifikátor (LCID) pro pole se seznamem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí hodnotu národního prostředí (LCID) identifikátor pro toto pole se seznamem.  
  
### <a name="remarks"></a>Poznámky  
 Pokud **SetLocale** není volán výchozí národní prostředí se získávají z systému. Tato výchozí národní prostředí systému můžete upravit pomocí ovládacích panelů místní (nebo mezinárodní) aplikace.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]  
  
##  <a name="setsel"></a>CListBox::SetSel  
 Vybere řetězec v seznamu vícenásobného výběru.  
  
```  
int SetSel(
    int nIndex,  
    BOOL bSelect = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Obsahuje index řetězec, který má být nastavena na nule. Pokud -1, výběr je přidat nebo odebrat ze všech řetězce, v závislosti na hodnotě `bSelect`.  
  
 `bSelect`  
 Určuje, jak nastavit výběr. Pokud `bSelect` je `TRUE`, řetězec nebude vybrána a zvýrazní; Pokud `FALSE`, je odebrán zvýraznění a řetězec je již vybrána. Zadaný řetězec je vybraná a zvýrazní ve výchozím nastavení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `LB_ERR`Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce člen pouze s vícenásobným výběrem seznamy.  
  
 Chcete-li vybrat položku z pole se seznamem jedním výběrem, použijte [CListBox::SetCurSel](#setcursel).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]  
  
##  <a name="settabstops"></a>CListBox::SetTabStops  
 Nastaví zarážek pozice v seznamu.  
  
```  
void SetTabStops();  
BOOL SetTabStops(const int& cxEachStop);

 
BOOL SetTabStops(
    int nTabStops,  
    LPINT rgTabStops);
```  
  
### <a name="parameters"></a>Parametry  
 `cxEachStop`  
 Zarážek jsou nastaveny v každé `cxEachStop` jednotky dialogu. V tématu *rgTabStops* popis jednotky dialogu.  
  
 `nTabStops`  
 Určuje počet zarážek tak, aby měl v rozevíracím seznamu.  
  
 `rgTabStops`  
 Bodů na první prvek pole obsahující pozic zarážek v jednotky dialogu celých čísel. Jednotky dialogu je vzdálenost vodorovně nebo svisle. Jednu jednotku vodorovné dialogové okno je rovna jedné čtvrtý aktuální základní šířka jednotky dialogu a jednu jednotku svislých dialogové okno se rovná osmina aktuální základní výška jednotky dialogu. Základní jednotky dialogu se vypočítávají podle výšky a šířky aktuálním písmem systému. **GetDialogBaseUnits** funkce systému Windows vrátí dialogu aktuální základní jednotky v pixelech. Zarážek tabulátoru musí být seřazeny ve vzestupném pořadí; back karty nejsou povoleny.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byly nastavené všechny karty; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 K nastavení zarážek tabulátoru na výchozí velikost 2 jednotky dialogu, volání bez parametrů verze této funkce člen. Chcete-li nastavení zarážek velikost než 2, volejte verzi s `cxEachStop` argument.  
  
 Nastavení zarážek na pole velikosti, použijte verzi pomocí `rgTabStops` a `nTabStops` argumenty. Nastaví se zarážku pro každou hodnotu v `rgTabStops`, až číslo zadané parametrem `nTabStops`.  
  
 Reagovat na volání `SetTabStops` – členská funkce pole se seznamem musí být vytvořen s [lbs_usetabstops –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]  
  
##  <a name="settopindex"></a>CListBox::SetTopIndex  
 Zajišťuje, že konkrétní seznam položky viditelné.  
  
```  
int SetTopIndex(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Určuje index položky pole se seznamem založený na nule.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu nebo **LB_ERR** Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Systém se posouvá společně pole se seznamem dokud položka určeného `nIndex` se zobrazí v horní části seznamu bylo dosaženo pole nebo rozsah maximální scroll.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]  
  
##  <a name="vkeytoitem"></a>CListBox::VKeyToItem  
 Voláno rámcem přijetí nadřazeného okna pole se seznamem `WM_VKEYTOITEM` zpráv ze seznamu.  
  
```  
virtual int VKeyToItem(
    UINT nKey,  
    UINT nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nKey`  
 Virtuální kód klíče uživatele stisknutí tlačítka. Seznam kódů standardní virtuální klíče naleznete v části winuser  
  
 `nIndex`  
 Aktuální umístění pomocí pole se seznamem kurzoru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací - 2 pro žádné další akce, - 1 pro výchozí akci nebo zadejte index položky seznamu pole na které se má provést výchozí akci pro klávesu nezáporné číslo.  
  
### <a name="remarks"></a>Poznámky  
 `WM_VKEYTOITEM` Odesílají zprávy pole se seznamem při přijetí `WM_KEYDOWN` zprávy, ale pouze pokud pole se seznamem splňuje obě z následujících akcí:  
  
-   Má [lbs_wantkeyboardinput –](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl sady.  
  
-   Má alespoň jednu položku.  
  
 Měli byste nikdy volat tuto funkci sami. Přepsání této funkce můžete poskytnout vlastní vlastní zpracování zpráv klávesnice.  
  
 Musí vrátit hodnotu říct rozhraní, jaké akce provést přepsání. Návratová hodnota - 2 označuje, že aplikace zpracovává všechny aspekty výběrem položky a vyžaduje žádná další akce podle pole se seznamem. Před vrácením - 2, můžete nastavení výběru nebo přesunout vsuvka nebo obojí. Pokud chcete nastavit výběr, použijte [setcursel –](#setcursel) nebo [SetSel](#setsel). Chcete-li přesunout znak, použijte [SetCaretIndex](#setcaretindex).  
  
 Návratová hodnota - 1 označuje, že pole se seznamem by měl výchozí akci v reakci klávesu. Výchozí implementace vrátí hodnotu - 1.  
  
 Vrácená hodnota 0 nebo větší Určuje index položky v seznamu a označuje, že pole se seznamem by měl výchozí akce pro klávesu na danou položku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CTRLTEST](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CButton – třída](../../mfc/reference/cbutton-class.md)   
 [CComboBox – třída](../../mfc/reference/ccombobox-class.md)   
 [CEdit – třída](../../mfc/reference/cedit-class.md)   
 [CScrollBar – třída](../../mfc/reference/cscrollbar-class.md)   
 [CStatic – třída](../../mfc/reference/cstatic-class.md)
