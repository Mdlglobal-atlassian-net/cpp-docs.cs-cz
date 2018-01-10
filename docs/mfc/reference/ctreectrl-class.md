---
title: "CTreeCtrl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTreeCtrl
- AFXCMN/CTreeCtrl
- AFXCMN/CTreeCtrl::CTreeCtrl
- AFXCMN/CTreeCtrl::Create
- AFXCMN/CTreeCtrl::CreateDragImage
- AFXCMN/CTreeCtrl::CreateEx
- AFXCMN/CTreeCtrl::DeleteAllItems
- AFXCMN/CTreeCtrl::DeleteItem
- AFXCMN/CTreeCtrl::EditLabel
- AFXCMN/CTreeCtrl::EndEditLabelNow
- AFXCMN/CTreeCtrl::EnsureVisible
- AFXCMN/CTreeCtrl::Expand
- AFXCMN/CTreeCtrl::GetBkColor
- AFXCMN/CTreeCtrl::GetCheck
- AFXCMN/CTreeCtrl::GetChildItem
- AFXCMN/CTreeCtrl::GetCount
- AFXCMN/CTreeCtrl::GetDropHilightItem
- AFXCMN/CTreeCtrl::GetEditControl
- AFXCMN/CTreeCtrl::GetExtendedStyle
- AFXCMN/CTreeCtrl::GetFirstVisibleItem
- AFXCMN/CTreeCtrl::GetImageList
- AFXCMN/CTreeCtrl::GetIndent
- AFXCMN/CTreeCtrl::GetInsertMarkColor
- AFXCMN/CTreeCtrl::GetItem
- AFXCMN/CTreeCtrl::GetItemData
- AFXCMN/CTreeCtrl::GetItemExpandedImageIndex
- AFXCMN/CTreeCtrl::GetItemHeight
- AFXCMN/CTreeCtrl::GetItemImage
- AFXCMN/CTreeCtrl::GetItemPartRect
- AFXCMN/CTreeCtrl::GetItemRect
- AFXCMN/CTreeCtrl::GetItemState
- AFXCMN/CTreeCtrl::GetItemStateEx
- AFXCMN/CTreeCtrl::GetItemText
- AFXCMN/CTreeCtrl::GetLastVisibleItem
- AFXCMN/CTreeCtrl::GetLineColor
- AFXCMN/CTreeCtrl::GetNextItem
- AFXCMN/CTreeCtrl::GetNextSiblingItem
- AFXCMN/CTreeCtrl::GetNextVisibleItem
- AFXCMN/CTreeCtrl::GetParentItem
- AFXCMN/CTreeCtrl::GetPrevSiblingItem
- AFXCMN/CTreeCtrl::GetPrevVisibleItem
- AFXCMN/CTreeCtrl::GetRootItem
- AFXCMN/CTreeCtrl::GetScrollTime
- AFXCMN/CTreeCtrl::GetSelectedCount
- AFXCMN/CTreeCtrl::GetSelectedItem
- AFXCMN/CTreeCtrl::GetTextColor
- AFXCMN/CTreeCtrl::GetToolTips
- AFXCMN/CTreeCtrl::GetVisibleCount
- AFXCMN/CTreeCtrl::HitTest
- AFXCMN/CTreeCtrl::InsertItem
- AFXCMN/CTreeCtrl::ItemHasChildren
- AFXCMN/CTreeCtrl::MapAccIdToItem
- AFXCMN/CTreeCtrl::MapItemToAccID
- AFXCMN/CTreeCtrl::Select
- AFXCMN/CTreeCtrl::SelectDropTarget
- AFXCMN/CTreeCtrl::SelectItem
- AFXCMN/CTreeCtrl::SelectSetFirstVisible
- AFXCMN/CTreeCtrl::SetAutoscrollInfo
- AFXCMN/CTreeCtrl::SetBkColor
- AFXCMN/CTreeCtrl::SetCheck
- AFXCMN/CTreeCtrl::SetExtendedStyle
- AFXCMN/CTreeCtrl::SetImageList
- AFXCMN/CTreeCtrl::SetIndent
- AFXCMN/CTreeCtrl::SetInsertMark
- AFXCMN/CTreeCtrl::SetInsertMarkColor
- AFXCMN/CTreeCtrl::SetItem
- AFXCMN/CTreeCtrl::SetItemData
- AFXCMN/CTreeCtrl::SetItemExpandedImageIndex
- AFXCMN/CTreeCtrl::SetItemHeight
- AFXCMN/CTreeCtrl::SetItemImage
- AFXCMN/CTreeCtrl::SetItemState
- AFXCMN/CTreeCtrl::SetItemStateEx
- AFXCMN/CTreeCtrl::SetItemText
- AFXCMN/CTreeCtrl::SetLineColor
- AFXCMN/CTreeCtrl::SetScrollTime
- AFXCMN/CTreeCtrl::SetTextColor
- AFXCMN/CTreeCtrl::SetToolTips
- AFXCMN/CTreeCtrl::ShowInfoTip
- AFXCMN/CTreeCtrl::SortChildren
- AFXCMN/CTreeCtrl::SortChildrenCB
dev_langs: C++
helpviewer_keywords:
- CTreeCtrl [MFC], CTreeCtrl
- CTreeCtrl [MFC], Create
- CTreeCtrl [MFC], CreateDragImage
- CTreeCtrl [MFC], CreateEx
- CTreeCtrl [MFC], DeleteAllItems
- CTreeCtrl [MFC], DeleteItem
- CTreeCtrl [MFC], EditLabel
- CTreeCtrl [MFC], EndEditLabelNow
- CTreeCtrl [MFC], EnsureVisible
- CTreeCtrl [MFC], Expand
- CTreeCtrl [MFC], GetBkColor
- CTreeCtrl [MFC], GetCheck
- CTreeCtrl [MFC], GetChildItem
- CTreeCtrl [MFC], GetCount
- CTreeCtrl [MFC], GetDropHilightItem
- CTreeCtrl [MFC], GetEditControl
- CTreeCtrl [MFC], GetExtendedStyle
- CTreeCtrl [MFC], GetFirstVisibleItem
- CTreeCtrl [MFC], GetImageList
- CTreeCtrl [MFC], GetIndent
- CTreeCtrl [MFC], GetInsertMarkColor
- CTreeCtrl [MFC], GetItem
- CTreeCtrl [MFC], GetItemData
- CTreeCtrl [MFC], GetItemExpandedImageIndex
- CTreeCtrl [MFC], GetItemHeight
- CTreeCtrl [MFC], GetItemImage
- CTreeCtrl [MFC], GetItemPartRect
- CTreeCtrl [MFC], GetItemRect
- CTreeCtrl [MFC], GetItemState
- CTreeCtrl [MFC], GetItemStateEx
- CTreeCtrl [MFC], GetItemText
- CTreeCtrl [MFC], GetLastVisibleItem
- CTreeCtrl [MFC], GetLineColor
- CTreeCtrl [MFC], GetNextItem
- CTreeCtrl [MFC], GetNextSiblingItem
- CTreeCtrl [MFC], GetNextVisibleItem
- CTreeCtrl [MFC], GetParentItem
- CTreeCtrl [MFC], GetPrevSiblingItem
- CTreeCtrl [MFC], GetPrevVisibleItem
- CTreeCtrl [MFC], GetRootItem
- CTreeCtrl [MFC], GetScrollTime
- CTreeCtrl [MFC], GetSelectedCount
- CTreeCtrl [MFC], GetSelectedItem
- CTreeCtrl [MFC], GetTextColor
- CTreeCtrl [MFC], GetToolTips
- CTreeCtrl [MFC], GetVisibleCount
- CTreeCtrl [MFC], HitTest
- CTreeCtrl [MFC], InsertItem
- CTreeCtrl [MFC], ItemHasChildren
- CTreeCtrl [MFC], MapAccIdToItem
- CTreeCtrl [MFC], MapItemToAccID
- CTreeCtrl [MFC], Select
- CTreeCtrl [MFC], SelectDropTarget
- CTreeCtrl [MFC], SelectItem
- CTreeCtrl [MFC], SelectSetFirstVisible
- CTreeCtrl [MFC], SetAutoscrollInfo
- CTreeCtrl [MFC], SetBkColor
- CTreeCtrl [MFC], SetCheck
- CTreeCtrl [MFC], SetExtendedStyle
- CTreeCtrl [MFC], SetImageList
- CTreeCtrl [MFC], SetIndent
- CTreeCtrl [MFC], SetInsertMark
- CTreeCtrl [MFC], SetInsertMarkColor
- CTreeCtrl [MFC], SetItem
- CTreeCtrl [MFC], SetItemData
- CTreeCtrl [MFC], SetItemExpandedImageIndex
- CTreeCtrl [MFC], SetItemHeight
- CTreeCtrl [MFC], SetItemImage
- CTreeCtrl [MFC], SetItemState
- CTreeCtrl [MFC], SetItemStateEx
- CTreeCtrl [MFC], SetItemText
- CTreeCtrl [MFC], SetLineColor
- CTreeCtrl [MFC], SetScrollTime
- CTreeCtrl [MFC], SetTextColor
- CTreeCtrl [MFC], SetToolTips
- CTreeCtrl [MFC], ShowInfoTip
- CTreeCtrl [MFC], SortChildren
- CTreeCtrl [MFC], SortChildrenCB
ms.assetid: 96e20031-6161-4143-8c12-8d1816c66d90
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 573b81ce8d78cde67b63579caa5ed96bbe557ae3
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="ctreectrl-class"></a>CTreeCtrl – třída
Poskytuje funkci běžné stromové zobrazení ovládacího prvku Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CTreeCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CTreeCtrl::CTreeCtrl](#ctreectrl)|Vytvoří `CTreeCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTreeCtrl::Create](#create)|Vytvoří zobrazení ovládacího prvku strom a připojí jej k `CTreeCtrl` objektu.|  
|[CTreeCtrl::CreateDragImage](#createdragimage)|Vytvoří přetahování rastrový obrázek položky stromové zobrazení.|  
|[CTreeCtrl::CreateEx](#createex)|Vytvoří ovládacím prvkem strom s zadaný Windows rozšířené styly a připojí jej k `CTreeCtrl` objektu.|  
|[CTreeCtrl::DeleteAllItems](#deleteallitems)|Odstraní všechny položky v ovládacím prvku stromu zobrazení.|  
|[CTreeCtrl::DeleteItem](#deleteitem)|Odstraní novou položku ve stromovém zobrazení.|  
|[CTreeCtrl::EditLabel](#editlabel)|Upraví stromové zobrazení položky místní.|  
|[CTreeCtrl::EndEditLabelNow](#endeditlabelnow)|Zruší operace upravování na popisek položky zobrazení stromu v ovládacím prvku aktuální zobrazení stromu.|  
|[CTreeCtrl::EnsureVisible](#ensurevisible)|Zajišťuje, že položku zobrazení stromu viditelné v ovládacím prvku jeho stromu zobrazení.|  
|[CTreeCtrl::Expand](#expand)|Rozbalí či sbalí, podřízené položky stromové zobrazení položky.|  
|[CTreeCtrl::GetBkColor](#getbkcolor)|Načte aktuální barvu pozadí ovládacího prvku.|  
|[CTreeCtrl::GetCheck](#getcheck)|Načte stav zkontrolujte položky ovládacího prvku strom.|  
|[CTreeCtrl::GetChildItem](#getchilditem)|Načte podřízené položky stromové zobrazení.|  
|[CTreeCtrl::GetCount](#getcount)|Načte počet položek stromu spojené s ovládacím prvkem strom zobrazení.|  
|[CTreeCtrl::GetDropHilightItem](#getdrophilightitem)|Načte cíl operace přetažení myší.|  
|[CTreeCtrl::GetEditControl](#geteditcontrol)|Načte popisovač ovládacích prvků pro úpravy používaný pro úpravu položky stromové zobrazení.|  
|[CTreeCtrl::GetExtendedStyle](#getextendedstyle)|Načte rozšířené styly, které používá aktuální ovládacího prvku zobrazení stromu.|  
|[CTreeCtrl::GetFirstVisibleItem](#getfirstvisibleitem)|Načte první položky zobrazené položky stromové zobrazení.|  
|[CTreeCtrl::GetImageList](#getimagelist)|Načte popisovač seznamu obrázků spojené s ovládacím prvkem strom zobrazení.|  
|[CTreeCtrl::GetIndent](#getindent)|Načte z nadřazené položky zobrazení stromu posun (v pixelech).|  
|[CTreeCtrl::GetInsertMarkColor](#getinsertmarkcolor)|Načte barvu použitou k vykreslení značky vložení pro zobrazení stromu.|  
|[CTreeCtrl::GetItem](#getitem)|Načte atributy stromové zobrazení položky.|  
|[CTreeCtrl::GetItemData](#getitemdata)|Vrátí hodnotu 32-bit specifické pro aplikace přidružené položce.|  
|[CTreeCtrl::GetItemExpandedImageIndex](#getitemexpandedimageindex)|Načte index bitovou kopii k zobrazení, pokud zadaná položka aktuální zobrazení stromu ovládacího prvku v rozšířené stavu.|  
|[CTreeCtrl::GetItemHeight](#getitemheight)|Načte aktuální výšku položky zobrazení stromu.|  
|[CTreeCtrl::GetItemImage](#getitemimage)|Načte bitové kopie přidružený k položce.|  
|[CTreeCtrl::GetItemPartRect](#getitempartrect)|Načte ohraničující obdélník pro zadanou součást zadaná položka v ovládacím prvku aktuální zobrazení stromu.|  
|[CTreeCtrl::GetItemRect](#getitemrect)|Načte ohraničující obdélník položku zobrazení stromu.|  
|[CTreeCtrl::GetItemState](#getitemstate)|Vrátí stav položky.|  
|[CTreeCtrl::GetItemStateEx](#getitemstateex)|Načte stav rozšířené zadané položky v ovládacím prvku aktuální zobrazení stromu.|  
|[CTreeCtrl::GetItemText](#getitemtext)|Vrátí text položky.|  
|[CTreeCtrl::GetLastVisibleItem](#getlastvisibleitem)|Načte poslední rozbalené položky v ovládacím prvku aktuální zobrazení stromu.|  
|[CTreeCtrl::GetLineColor](#getlinecolor)|Načte aktuální barvu čáry pro ovládací prvek zobrazení stromu.|  
|[CTreeCtrl::GetNextItem](#getnextitem)|Načte další položky zobrazení stromu, který odpovídá zadané relaci.|  
|[CTreeCtrl::GetNextSiblingItem](#getnextsiblingitem)|Načte další na stejné úrovni jako položky stromové zobrazení.|  
|[CTreeCtrl::GetNextVisibleItem](#getnextvisibleitem)|Načte další položky zobrazené položky stromové zobrazení.|  
|[CTreeCtrl::GetParentItem](#getparentitem)|Načte nadřazené položky stromové zobrazení.|  
|[CTreeCtrl::GetPrevSiblingItem](#getprevsiblingitem)|Načte předchozí na stejné úrovni jako položky stromové zobrazení.|  
|[CTreeCtrl::GetPrevVisibleItem](#getprevvisibleitem)|Načte předchozí položky zobrazené položky stromové zobrazení.|  
|[CTreeCtrl::GetRootItem](#getrootitem)|Načte kořenové položky stromové zobrazení.|  
|[CTreeCtrl::GetScrollTime](#getscrolltime)|Načte maximální scroll čas pro ovládací prvek zobrazení stromu.|  
|[CTreeCtrl::GetSelectedCount](#getselectedcount)|Načte počet vybraných položek v ovládacím prvku aktuální zobrazení stromu.|  
|[CTreeCtrl::GetSelectedItem](#getselecteditem)|Načte aktuálně vybraná položka zobrazení.|  
|[CTreeCtrl::GetTextColor](#gettextcolor)|Načte aktuální barvy ovládacího prvku.|  
|[CTreeCtrl::GetToolTips](#gettooltips)|Načte popisovač podřízený ovládací prvek popisek používaný v ovládacím prvkem strom zobrazení.|  
|[CTreeCtrl::GetVisibleCount](#getvisiblecount)|Načte počet položek viditelné stromu spojené s ovládacím prvkem strom zobrazení.|  
|[CTreeCtrl::HitTest](#hittest)|Vrátí aktuální pozice kurzoru související s `CTreeCtrl` objektu.|  
|[CTreeCtrl::InsertItem](#insertitem)|Vloží novou položku ve stromovém zobrazení.|  
|[CTreeCtrl::ItemHasChildren](#itemhaschildren)|Vrátí nenulové hodnoty, pokud zadaná položka obsahuje podřízené položky.|  
|[CTreeCtrl::MapAccIdToItem](#mapaccidtoitem)|Mapuje zadané usnadnění identifikátor popisovač položku zobrazení stromu v ovládacím prvku aktuální zobrazení stromu.|  
|[CTreeCtrl::MapItemToAccID](#mapitemtoaccid)|Zadaný popisovač se mapuje na položku zobrazení stromu v ovládacím prvku aktuální zobrazení stromu k usnadnění identifikátor.|  
|[CTreeCtrl::Select](#select)|Vybere, posune do zobrazení nebo ho překreslí položku stromové zobrazení.|  
|[CTreeCtrl::SelectDropTarget](#selectdroptarget)|Položka stromu překreslí jako cíl operací přetažení myší.|  
|[CTreeCtrl::SelectItem](#selectitem)|Vybere položku stromové zobrazení.|  
|[CTreeCtrl::SelectSetFirstVisible](#selectsetfirstvisible)|Jako první položky zobrazené vybere položku stromové zobrazení.|  
|[CTreeCtrl::SetAutoscrollInfo](#setautoscrollinfo)|Nastaví počet nadřazená aktuální ovládacího prvku zobrazení stromu.|  
|[CTreeCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí ovládacího prvku.|  
|[CTreeCtrl::SetCheck](#setcheck)|Nastaví stav zkontrolujte položky ovládacího prvku strom.|  
|[CTreeCtrl::SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené styly pro ovládací prvek aktuální zobrazení stromu.|  
|[CTreeCtrl::SetImageList](#setimagelist)|Nastaví popisovač seznamu obrázků spojené s ovládacím prvkem strom zobrazení.|  
|[CTreeCtrl::SetIndent](#setindent)|Nastaví posunutí (v pixelech) položky zobrazení stromu z nadřazené.|  
|[CTreeCtrl::SetInsertMark](#setinsertmark)|Nastaví značky vložení v ovládacím prvku stromu zobrazení.|  
|[CTreeCtrl::SetInsertMarkColor](#setinsertmarkcolor)|Nastaví barvu použitou k vykreslení značky vložení pro zobrazení stromu.|  
|[CTreeCtrl::SetItem](#setitem)|Nastaví atributy stromové zobrazení položky.|  
|[CTreeCtrl::SetItemData](#setitemdata)|Nastaví hodnotu 32-bit specifické pro aplikace přidružené položce.|  
|[CTreeCtrl::SetItemExpandedImageIndex](#setitemexpandedimageindex)|Nastaví index bitovou kopii k zobrazení, pokud zadaná položka aktuální zobrazení stromu ovládacího prvku v rozšířené stavu.|  
|[CTreeCtrl::SetItemHeight](#setitemheight)|Nastaví výšku stromu zobrazit položky.|  
|[CTreeCtrl::SetItemImage](#setitemimage)|Přidruží položku bitové kopie.|  
|[CTreeCtrl::SetItemState](#setitemstate)|Nastaví stav položky.|  
|[CTreeCtrl::SetItemStateEx](#setitemstateex)|Nastaví stav rozšířené zadané položky v ovládacím prvku aktuální zobrazení stromu.|  
|[CTreeCtrl::SetItemText](#setitemtext)|Nastaví text položky.|  
|[CTreeCtrl::SetLineColor](#setlinecolor)|Nastaví aktuální barvu čáry pro ovládací prvek zobrazení stromu.|  
|[CTreeCtrl::SetScrollTime](#setscrolltime)|Nastaví maximální scroll čas pro ovládací prvek zobrazení stromu.|  
|[CTreeCtrl::SetTextColor](#settextcolor)|Nastaví barvu textu ovládacího prvku.|  
|[CTreeCtrl::SetToolTips](#settooltips)|Nastaví ovládací prvek popisek podřízeného ovládacího prvku zobrazení stromu.|  
|[CTreeCtrl::ShowInfoTip](#showinfotip)|Zobrazí informační tip pro zadanou položku v ovládacím prvku aktuální zobrazení stromu.|  
|[CTreeCtrl::SortChildren](#sortchildren)|Seřadí podřízené objekty daného nadřazené položky.|  
|[CTreeCtrl::SortChildrenCB](#sortchildrencb)|Seřadí podřízené objekty daného nadřazené položky pomocí funkce definované aplikací řazení.|  
  
## <a name="remarks"></a>Poznámky  
 "Zobrazení ovládacím prvkem strom" je okno, které zobrazí hierarchické seznam položek, například záhlaví v dokumentu, položky v indexu, nebo soubory a adresáře na disku. Každá položka se skládá z štítek a volitelné rastrové bitovou kopii, a každá položka může mít seznam podřízených položek s ním spojená. Uživatel kliknutím na položku, můžete rozbalit nebo sbalit přidružené seznam podřízených položek.  
  
 Tento ovládací prvek (a proto `CTreeCtrl` třída) je k dispozici pouze pro aplikace spuštěné v systému Windows 98 a systému Windows NT verze 4 a novější.  
  
 Další informace o používání `CTreeCtrl`, najdete v části:  
  
- [Ovládací prvky](../../mfc/controls-mfc.md)  
  
- [Používání atributu CTreeCtrl](../../mfc/using-ctreectrl.md)  
  
- [Stromové zobrazení ovládacího prvku odkaz](http://msdn.microsoft.com/library/windows/desktop/bb759988) ve Windows SDK.  
  
-   Článek znalostní báze Knowledge Base Q222905: postupy: zobrazení z kontextové nabídky pro CTreeCtrl  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTreeCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="create"></a>CTreeCtrl::Create  
 Pokud zadáte v poli šablony dialogového okna Ovládací prvek stromu, nebo pokud používáte [CTreeView](../../mfc/reference/ctreeview-class.md), vaše ovládací prvek stromu se vytvoří automaticky při vytvoření dialogového nebo zobrazení.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl ovládací prvek zobrazení stromu. Použít styly oken, popsané v [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)a libovolnou kombinaci [stromové zobrazení – styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb760013) jak je popsáno v sadě Windows SDK.  
  
 `rect`  
 Určuje velikost a umístění ovládacího prvku zobrazení stromu. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura.  
  
 `pParentWnd`  
 Určuje nadřazeného okna pro ovládací prvek zobrazení stromu, obvykle `CDialog`. Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku zobrazení stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se inicializace byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete vytvořit ovládací prvek stromu jako podřízeného okna Další okna, použijte **vytvořit** – členská funkce. Pokud vytvoříte pomocí ovládacího prvku strom **vytvořit**, je nutné předat **ws_visible –**, kromě jiných stylů zobrazení stromu.  
  
 Můžete vytvořit `CTreeCtrl` ve dvou krocích. První volání konstruktoru, pak zavolají **vytvořit**, který vytvoří zobrazení ovládacího prvku strom a připojí jej k `CTreeCtrl` objektu.  
  
 Chcete-li vytvořit ovládacím prvkem strom s rozšířené styly oken, volejte [CreateEx](#createex) místo **vytvořit**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_1.cpp)]  
  
##  <a name="createex"></a>CTreeCtrl::CreateEx  
 Volání této funkce vytvoření ovládacího prvku (podřízeného okna) a její přidružení `CTreeCtrl` objektu.  
  
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
 Určuje styl ovládací prvek zobrazení stromu. Použít styly oken, popsané v [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)a libovolnou kombinaci [stromové zobrazení – styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb760013) jak je popsáno v sadě Windows SDK.  
  
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
  
##  <a name="createdragimage"></a>CTreeCtrl::CreateDragImage  
 Volání této funkce k vytvoření přetahování rastrového obrázku pro danou položku v ovládacím prvku stromu zobrazení, vytvořte seznam obrázků pro bitovou mapu a přidejte do seznamu obrázků bitové mapy.  
  
```  
CImageList* CreateDragImage(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Položka stromu přetáhnout popisovač.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na seznamu obrázků, do které jste přidali přetahování rastrového obrázku, v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Aplikace používá funkce seznamu obrázků pro zobrazení bitovou kopii při přetažení položky.  
  
 `CImageList` Objektu je trvalá a, musíte jej po dokončení odstranit. Příklad:  
  
 [!code-cpp[NVC_MFC_CTreeCtrl#2](../../mfc/reference/codesnippet/cpp/ctreectrl-class_2.cpp)]  
  
##  <a name="ctreectrl"></a>CTreeCtrl::CTreeCtrl  
 Vytvoří `CTreeCtrl` objektu.  
  
```  
CTreeCtrl();
```  
  
##  <a name="deleteallitems"></a>CTreeCtrl::DeleteAllItems  
 Volání této funkce se odstranit všechny položky z ovládacího prvku zobrazení stromu.  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#3](../../mfc/reference/codesnippet/cpp/ctreectrl-class_3.cpp)]  
  
##  <a name="deleteitem"></a>CTreeCtrl::DeleteItem  
 Volání této funkce se odstranit položku z ovládacího prvku zobrazení stromu.  
  
```  
BOOL DeleteItem(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Obslužná rutina stromu položky pro odstranění. Pokud *: hitem* má **TVI_ROOT** hodnotu, se odstraní všechny položky z ovládacího prvku zobrazení stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#4](../../mfc/reference/codesnippet/cpp/ctreectrl-class_4.cpp)]  
  
##  <a name="editlabel"></a>CTreeCtrl::EditLabel  
 Volání této funkce zahájíte úpravy textu zadanou položku na místě.  
  
```  
CEdit* EditLabel(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Obslužná rutina stromu položky k provádění úprav.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného ukazatel `CEdit` objekt, který se používá ke upravit text položky; jinak hodnota **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Úpravu provádí nahrazení textu položky s ovládacím prvkem upravit jeden řádek obsahující hledaný text.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#5](../../mfc/reference/codesnippet/cpp/ctreectrl-class_5.cpp)]  
  
##  <a name="endeditlabelnow"></a>CTreeCtrl::EndEditLabelNow  
 Ukončí operaci upravit na popisek položky zobrazení stromu v ovládacím prvku aktuální zobrazení stromu.  
  
```  
BOOL EndEditLabelNow(BOOL fCancelWithoutSave);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`fCancelWithoutSave`|`true`Zahodit změny položky zobrazení stromu před uzavřením operace upravování nebo `false` se uložit změny do položky zobrazení stromu před uzavřením operaci.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TVM_ENDEDITLABELNOW](http://msdn.microsoft.com/library/windows/desktop/bb773564) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="ensurevisible"></a>CTreeCtrl::EnsureVisible  
 Volání této funkce pro zajištění viditelné položku zobrazení stromu.  
  
```  
BOOL EnsureVisible(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu prováděné viditelné.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** Pokud systému přesunut oblasti položky v ovládacím prvku zobrazení stromu zajistit, aby zadaná položka je viditelná. Jinak hodnota vrácená hodnota je **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 V případě potřeby funkce rozšíří nadřazené položky nebo posune stromové zobrazení tak, aby položka.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#6](../../mfc/reference/codesnippet/cpp/ctreectrl-class_6.cpp)]  
  
##  <a name="expand"></a>CTreeCtrl::Expand  
 Volání této funkce můžete rozbalit nebo sbalit seznam podřízené položky, pokud existuje, spojené s danou nadřazené položky.  
  
```  
BOOL Expand(
    HTREEITEM hItem,  
    UINT nCode);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Položka stromu rozbalovanou popisovač.  
  
 `nCode`  
 Příznak, který udává typ akce, které mají být provedeny. Tento příznak může mít jednu z následujících hodnot:  
  
- `TVE_COLLAPSE`Sbalí seznamu.  
  
- `TVE_COLLAPSERESET`Sbalí seznamu a odebere podřízené položky. **TVIS_EXPANDEDONCE** příznak stavu je obnovit. Tento příznak se musí používat s `TVE_COLLAPSE` příznak.  
  
- `TVE_EXPAND`Rozbalí seznam.  
  
- `TVE_TOGGLE`Sbalí seznamu, pokud je aktuálně rozšířit nebo ho rozšíří, pokud je sbalená.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::EnsureVisible](#ensurevisible).  
  
##  <a name="getbkcolor"></a>CTreeCtrl::GetBkColor  
 Tato funkce člen implementuje chování zprávy Win32 [TVM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773570), jak je popsáno v sadě Windows SDK.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COLORREF** hodnotu, která představuje aktuální barva pozadí okna pro ovládací prvek. Pokud tato hodnota -1, je pomocí ovládacího prvku okno barvy systému. V takovém případě můžete použít `::GetSysColor(COLOR_WINDOW)` získat aktuální systému barvu, která je pomocí ovládacího prvku.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::SetTextColor](#settextcolor).  
  
##  <a name="getcheck"></a>CTreeCtrl::GetCheck  
 Volání této funkce člen načíst položku na kontrolu stavu.  
  
```  
BOOL GetCheck(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 **HTREEITEM** o tom, které pro příjem informace o stavu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je zaškrtnuta možnost Položka ovládací prvek stromu; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::SetCheck](#setcheck).  
  
##  <a name="getchilditem"></a>CTreeCtrl::GetChildItem  
 Volání této funkce načtení stromu zobrazení položek je podřízená položka určeného `hItem`.  
  
```  
HTREEITEM GetChildItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač podřízenou položku v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#7](../../mfc/reference/codesnippet/cpp/ctreectrl-class_7.cpp)]  
  
##  <a name="getcount"></a>CTreeCtrl::GetCount  
 Volání této funkce se načíst počet položek v ovládacím prvkem strom zobrazení.  
  
```  
UINT GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet položek ve stromovém zobrazení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#8](../../mfc/reference/codesnippet/cpp/ctreectrl-class_8.cpp)]  
  
##  <a name="getdrophilightitem"></a>CTreeCtrl::GetDropHilightItem  
 Volejte tuto funkci k získání položky, která je cílem operací přetažení myší.  
  
```  
HTREEITEM GetDropHilightItem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač položky vyřadit v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#9](../../mfc/reference/codesnippet/cpp/ctreectrl-class_9.cpp)]  
  
##  <a name="geteditcontrol"></a>CTreeCtrl::GetEditControl  
 Volání této funkce pro načtení popisovače ovládacích prvků pro úpravy používá upravit text položky zobrazení stromu.  
  
```  
CEdit* GetEditControl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na ovládací prvek upravit používaný pro úpravu text položky v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#10](../../mfc/reference/codesnippet/cpp/ctreectrl-class_10.cpp)]  
  
##  <a name="getextendedstyle"></a>CTreeCtrl::GetExtendedStyle  
 Načte rozšířené styly, které používá aktuální ovládacího prvku zobrazení stromu.  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu, která obsahuje bitovou kombinaci (nebo) aktuální ovládacího prvku zobrazení stromu je rozšířené styly. Další informace najdete v tématu [– styly ovládacího prvku rozšířené zobrazení stromu](http://msdn.microsoft.com/library/windows/desktop/bb759981).  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TVM_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb773580) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getfirstvisibleitem"></a>CTreeCtrl::GetFirstVisibleItem  
 Volání této funkce načíst první položky zobrazené stromové zobrazení.  
  
```  
HTREEITEM GetFirstVisibleItem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač první položky zobrazené; v opačném případě **NULL**.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::SetCheck](#setcheck).  
  
##  <a name="getimagelist"></a>CTreeCtrl::GetImageList  
 Volání této funkce můžete získat popisovač normální nebo seznamu obrázků stavu přidruženého k ovládacímu prvku zobrazení stromu.  
  
```  
CImageList* GetImageList(UINT nImageList) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nImageList`  
 Typ seznamu obrázků pro načtení. Seznam obrázků může být jedna z následujících hodnot:  
  
- `TVSIL_NORMAL`Načte seznam normální bitové kopie, který obsahuje vybrané a nevybrané bitových kopií pro položky zobrazení stromu.  
  
- `TVSIL_STATE`Načte seznamu obrázků stavu, který obsahuje Image pro strom zobrazit položky, které jsou ve stavu, uživatelem definované.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na ovládací prvek seznamu obrázků v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Každá položka v ovládacím prvku stromu zobrazení může mít pár rastrových obrázků s ním spojená. Jednu image se zobrazí, když je položka vybrána, a druhé se zobrazí, pokud není vybrána položka. Například může položky zobrazit, otevřít složku, pokud je vybrána a uzavřené složku Pokud není vybraná.  
  
 Další informace o seznamech obrázků, najdete v článku [CImageList](../../mfc/reference/cimagelist-class.md) třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#11](../../mfc/reference/codesnippet/cpp/ctreectrl-class_11.cpp)]  
  
##  <a name="getindent"></a>CTreeCtrl::GetIndent  
 Volání této funkce načíst velikost, v pixelech, že podřízené položky odsazeny vzhledem k jejich nadřazené položky.  
  
```  
UINT GetIndent() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost odsazení měřená v pixelech.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#12](../../mfc/reference/codesnippet/cpp/ctreectrl-class_12.cpp)]  
  
##  <a name="getinsertmarkcolor"></a>CTreeCtrl::GetInsertMarkColor  
 Tato funkce člen implementuje chování zprávy Win32 [TVM_GETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773590), jak je popsáno v sadě Windows SDK.  
  
```  
COLORREF GetInsertMarkColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COLORREF** hodnotu, která obsahuje aktuální barvu značky vložení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#13](../../mfc/reference/codesnippet/cpp/ctreectrl-class_13.cpp)]  
  
##  <a name="getitem"></a>CTreeCtrl::GetItem  
 Volání této funkce načíst atributy položky stromové zobrazení.  
  
```  
BOOL GetItem(TVITEM* pItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Ukazatel [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) struktury, jak je popsáno v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::DeleteItem](#deleteitem).  
  
##  <a name="getitemdata"></a>CTreeCtrl::GetItemData  
 Volání této funkce můžete načíst hodnotu 32-bit specifické pro aplikace přidružené k zadané položky.  
  
```  
DWORD_PTR GetItemData(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Obslužná rutina položky, jejichž data se mají být načteny.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnotu 32-bit specifické pro aplikace přidružené k položce určeného `hItem`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#14](../../mfc/reference/codesnippet/cpp/ctreectrl-class_14.cpp)]  
  
##  <a name="getitemexpandedimageindex"></a>CTreeCtrl::GetItemExpandedImageIndex  
 Načte index bitovou kopii k zobrazení, pokud zadaná položka aktuální zobrazení stromu ovládacího prvku v rozšířené stavu.  
  
```  
int GetItemExpandedImageIndex(HTREEITEM hItem)const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`hItem`|Zpracování položky ovládacího prvku zobrazení stromu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Index bitové kopie k zobrazení, pokud zadaná položka v rozšířené stavu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TVM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773596) zprávy, která je popsána v sadě Windows SDK. Který zprávy vrátí [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) načte struktura, která popisuje položky ovládacího prvku zobrazení stromu a pak tato metoda `iExpandedImage` člena z této struktury.  
  
##  <a name="getitemheight"></a>CTreeCtrl::GetItemHeight  
 Tato funkce člen implementuje chování zprávy Win32 [TVM_GETITEMHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb773599), jak je popsáno v sadě Windows SDK.  
  
```  
SHORT GetItemHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška položky v pixelech.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#15](../../mfc/reference/codesnippet/cpp/ctreectrl-class_15.cpp)]  
  
##  <a name="getitemimage"></a>CTreeCtrl::GetItemImage  
 Každá položka v ovládacím prvku stromu zobrazení může mít pár rastrových obrázků s ním spojená.  
  
```  
BOOL GetItemImage(
    HTREEITEM hItem,  
    int& nImage,  
    int& nSelectedImage) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položek, jejichž image je mají být načteny.  
  
 `nImage`  
 Celé číslo, které obdrží index obrázku položky v seznamu obrázků v ovládacím prvku zobrazení stromu.  
  
 `nSelectedImage`  
 Celé číslo, které obdrží index image vybrané položky v seznamu obrázků v ovládacím prvku zobrazení stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Bitové kopie se zobrazí na levé straně popisku položky. Jednu image se zobrazí, když je položka vybrána, a druhé se zobrazí, pokud není vybrána položka. Například může položky zobrazit, otevřít složku, pokud je vybrána a uzavřené složku Pokud není vybraná.  
  
 Volání této funkce načíst index položky obrázku a jeho vybrané image v seznamu obrázků v ovládacím prvku zobrazení stromu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#16](../../mfc/reference/codesnippet/cpp/ctreectrl-class_16.cpp)]  
  
##  <a name="getitempartrect"></a>CTreeCtrl::GetItemPartRect  
 Načte ohraničující obdélník pro zadanou součást zadaná položka v ovládacím prvku aktuální zobrazení stromu.  
  
```  
BOOL GetItemPartRect(
    HTREEITEM hItem,   
    int nPart,   
    LPRECT lpRect)const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`hItem`|Zpracování položky ovládacího prvku zobrazení stromu.|  
|[v]`nPart`|Identifikátor pro část. musí být nastavena na `TVGIPR_BUTTON`.|  
|[out]`lpRect`|Ukazatel na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura. Pokud tato metoda je úspěšné, struktura obdrží obdélníku souřadnice část určeného `hItem` a `nPart`.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Každá položka ovládací prvek stromu ohraničená obdélníku grafiky. Vždy, když po kliknutí na bod v obdélníku, položka se říká, že *dosáhl*. Tato metoda vrátí největší rámeček tak, že když bod v obdélníku po kliknutí na položku identifikovaný `hItem` parametr je přístupů.  
  
 Tato metoda odesílá `TVM_GETITEMPARTRECT` zprávy, která je popsána v sadě Windows SDK. Další informace najdete v tématu [TreeView_GetItemPartRect](http://msdn.microsoft.com/library/windows/desktop/bb773847) makro.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_treeCtrl`, který používá pro přístup k aktuální ovládacího prvku zobrazení stromu. Příklad kódu také definuje několik HTREEITEM proměnné a celé číslo bez znaménka. Tyto proměnné se používají v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu používá identifikátor usnadnění a [CTreeCtrl::MapAccIdToItem](#mapaccidtoitem) metoda pro načtení popisovač pro kořenovou položku zobrazení stromu. V příkladu se použije popisovač a [CTreeCtrl::GetItemPartRect](#getitempartrect) metoda 3D obdélník kolem této položky. V předcházející části příklad kódu, který není zobrazený, jsme vytvořili stromové zobrazení, která se skládá z kořenového uzlu země nebo oblast pro Spojené státy americké, podřízených uzlů stavů Velká Británie a Washington a položkami stromu pro města v těchto stavů. Použili jsme [CTreeCtrl::MapItemToAccID](#mapitemtoaccid) metoda, jak přidružit kořenovou položku zobrazení stromu s identifikátorem usnadnění.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/ctreectrl-class_18.cpp)]  
  
##  <a name="getitemrect"></a>CTreeCtrl::GetItemRect  
 Volání této funkce načíst ohraničující obdélník pro `hItem` a zjistit, zda je viditelná nebo ne.  
  
```  
BOOL GetItemRect(
    HTREEITEM hItem,  
    LPRECT lpRect,  
    BOOL bTextOnly) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položky ovládacího prvku zobrazení stromu.  
  
 `lpRect`  
 Ukazatel na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která přijímá ohraničující obdélník. Souřadnice jsou relativní vzhledem k levém horním rohu zobrazení stromové struktury.  
  
 *bTextOnly*  
 Pokud tento parametr je nenulové, ohraničující obdélník obsahuje pouze text položky. V opačném případě obsahuje celý řádek, který bude zabírat položky ve stromovém zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je položka viditelná, s ohraničující obdélník obsažené v `lpRect`. Jinak hodnota 0 s `lpRect` Neinicializovaný.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#17](../../mfc/reference/codesnippet/cpp/ctreectrl-class_19.cpp)]  
  
##  <a name="getitemstate"></a>CTreeCtrl::GetItemState  
 Vrátí stav položky určeného `hItem`.  
  
```  
UINT GetItemState(
    HTREEITEM hItem,  
    UINT nStateMask) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Obslužná rutina položky, jejichž stav je mají být načteny.  
  
 `nStateMask`  
 Maska, která určuje jeden nebo více stavy, které mají být načteny. Další informace o možných hodnot pro `nStateMask`, přečtěte si diskuzi o **stavu** a **stateMask** členy [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) struktura ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **Celé_číslo** kterém jsou uložena bitová hodnota OR hodnoty zadané ve nStateMask. Informace o možných hodnot najdete v tématu [CTreeCtrl::GetItem](#getitem). Najít hodnotu pro určitý stav, provedení bitové operace AND hodnotu stavu a návratové hodnoty, jak je znázorněno v následujícím příkladu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#18](../../mfc/reference/codesnippet/cpp/ctreectrl-class_20.cpp)]  
  
##  <a name="getitemstateex"></a>CTreeCtrl::GetItemStateEx  
 Načte stav rozšířené zadané položky v ovládacím prvku aktuální zobrazení stromu.  
  
```  
UINT GetItemStateEx(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`hItem`|Zpracování položky ovládacího prvku zobrazení stromu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Rozšířené stavové položky. Další informace najdete v tématu `uStateEx` členem [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) struktury.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TVM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773596) zprávy, která je popsána v sadě Windows SDK. Který zprávy vrátí [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) načte struktura, která popisuje položky ovládacího prvku zobrazení stromu, přičemž tuto metodu `uStateEx` člena z této struktury.  
  
##  <a name="getitemtext"></a>CTreeCtrl::GetItemText  
 Vrátí text položky určeného `hItem`.  
  
```  
CString GetItemText(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Obslužná rutina položky, jejíž text je mají být načteny.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` objekt obsahující text položky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::GetNextItem](#getnextitem).  
  
##  <a name="getlastvisibleitem"></a>CTreeCtrl::GetLastVisibleItem  
 Načte poslední unexpanded uzlu položky v ovládacím prvku aktuální zobrazení stromu.  
  
```  
HTREEITEM GetLastVisibleItem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač poslední položky unexpanded uzlu, pokud je metoda úspěšná. v opačném `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TVM_GETNEXTITEM](http://msdn.microsoft.com/library/windows/desktop/bb773622) zprávy, která je popsána v sadě Windows SDK. Další informace najdete v tématu `TVGN_LASTVISIBLE` příznak v `flag` parametr této zprávy.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_treeCtrl`, který používá pro přístup k aktuální ovládacího prvku zobrazení stromu. Příklad kódu také definuje několik HTREEITEM proměnné a celé číslo bez znaménka. Jeden nebo více těchto proměnných se používají v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu načte popisovač pro poslední položky uzlu unexpanded zobrazení stromu a pak nevykresluje 3D obdélníku kolem této položky. V předcházející části příklad kódu, který není zobrazený, jsme vytvořili stromové zobrazení, která se skládá z kořenového uzlu země nebo oblast pro Spojené státy americké, podřízených uzlů stavů Velká Británie a Washington a položkami stromu pro města v těchto stavů.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctreectrl-class_21.cpp)]  
  
##  <a name="getlinecolor"></a>CTreeCtrl::GetLineColor  
 Tato funkce člen implementuje chování zprávy win32 [TVM_GETLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773619), jak je popsáno v sadě Windows SDK.  
  
```  
COLORREF GetLineColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální barvu čáry.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#19](../../mfc/reference/codesnippet/cpp/ctreectrl-class_22.cpp)]  
  
##  <a name="getnextitem"></a>CTreeCtrl::GetNextItem  
 Volání této funkce načtení stromu zobrazit položky, má zadaný vztah, uvedené `nCode` parametr, do `hItem`.  
  
```  
HTREEITEM GetNextItem(
    HTREEITEM hItem,  
    UINT nCode) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu.  
  
 `nCode`  
 Příznak, který udává typ vztahu k `hItem`. Tento příznak může být jedna z následujících hodnot:  
  
- `TVGN_CARET`Načte aktuálně vybrané položky.  
  
- `TVGN_CHILD`Načte první položka podřízené položky určeného `hItem` parametr.  
  
- `TVGN_DROPHILITE`Načte položku, která je cílem operací přetažení myší.  
  
- `TVGN_FIRSTVISIBLE`Načte první položky zobrazené.  
  
- `TVGN_LASTVISIBLE`Načte poslední rozbalené položky ve stromové struktuře. Není to načíst poslední položky viditelné v okně zobrazení stromu.  
  
- `TVGN_NEXT`Načte další položky na stejné úrovni.  
  
- `TVGN_NEXTVISIBLE`Načte další položky zobrazené, který následuje zadanou položku.  
  
- `TVGN_PARENT`Načte nadřazené zadané položky.  
  
- `TVGN_PREVIOUS`Načte předchozí položky na stejné úrovni.  
  
- `TVGN_PREVIOUSVISIBLE`Načte první položky zobrazené předcházejícího zadanou položku.  
  
- `TVGN_ROOT`Načte první položce kořenové položky, které zadaná položka je součástí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač další položky v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vrací **NULL** Pokud byla položka načítány kořenový uzel stromu. Například pokud použijete tuto zprávu s `TVGN_PARENT` příznak na podřízenou první úrovně stromové zobrazení kořenový uzel, vrátí zprávu **NULL**.  
  
### <a name="example"></a>Příklad  
 Příklad použití `GetNextItem` ve smyčce, najdete v části [CTreeCtrl::DeleteItem](#deleteitem).  
  
 [!code-cpp[NVC_MFC_CTreeCtrl#20](../../mfc/reference/codesnippet/cpp/ctreectrl-class_23.cpp)]  
  
##  <a name="getnextsiblingitem"></a>CTreeCtrl::GetNextSiblingItem  
 Volání této funkce pro načtení další úrovni `hItem`.  
  
```  
HTREEITEM GetNextSiblingItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač další položky na stejné úrovni; v opačném případě **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#21](../../mfc/reference/codesnippet/cpp/ctreectrl-class_24.cpp)]  
  
##  <a name="getnextvisibleitem"></a>CTreeCtrl::GetNextVisibleItem  
 Volání této funkce pro načtení další viditelné položce `hItem`.  
  
```  
HTREEITEM GetNextVisibleItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač další položky zobrazené; v opačném případě **NULL**.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::SetCheck](#setcheck).  
  
##  <a name="getparentitem"></a>CTreeCtrl::GetParentItem  
 Volání této funkce načíst nadřazeného `hItem`.  
  
```  
HTREEITEM GetParentItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač nadřazené položky; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce vrací **NULL** Pokud nadřazený zadané položky je kořenový uzel stromu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::EnsureVisible](#ensurevisible).  
  
##  <a name="getprevsiblingitem"></a>CTreeCtrl::GetPrevSiblingItem  
 Volání této funkce načíst předchozí úrovni `hItem`.  
  
```  
HTREEITEM GetPrevSiblingItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač předchozí na stejné úrovni; v opačném případě **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#22](../../mfc/reference/codesnippet/cpp/ctreectrl-class_25.cpp)]  
  
##  <a name="getprevvisibleitem"></a>CTreeCtrl::GetPrevVisibleItem  
 Volání této funkce načíst předchozí položce viditelné `hItem`.  
  
```  
HTREEITEM GetPrevVisibleItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač předchozí položky zobrazené; v opačném případě **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#23](../../mfc/reference/codesnippet/cpp/ctreectrl-class_26.cpp)]  
  
##  <a name="getrootitem"></a>CTreeCtrl::GetRootItem  
 Volání této funkce načíst kořenovou položku ovládacího prvku zobrazení stromu.  
  
```  
HTREEITEM GetRootItem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač kořenovou položku; v opačném případě **NULL**.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::EditLabel](#editlabel).  
  
##  <a name="getscrolltime"></a>CTreeCtrl::GetScrollTime  
 Volání této funkce člen k načtení času maximální posuňte zobrazení ovládacího prvku strom.  
  
```  
UINT GetScrollTime() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Posuv maximální dobu v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy win32 [TVM_GETSCROLLTIME](http://msdn.microsoft.com/library/windows/desktop/bb773625), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getselectedcount"></a>CTreeCtrl::GetSelectedCount  
 Načte počet vybraných položek v ovládacím prvku aktuální zobrazení stromu.  
  
```  
UINT GetSelectedCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet vybraných položek.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TVM_GETSELECTEDCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb773629) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getselecteditem"></a>CTreeCtrl::GetSelectedItem  
 Volání této funkce načíst aktuálně vybrané položky ovládacího prvku zobrazení stromu.  
  
```  
HTREEITEM GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač vybrané položce. v opačném případě **NULL**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#24](../../mfc/reference/codesnippet/cpp/ctreectrl-class_27.cpp)]  
  
##  <a name="gettextcolor"></a>CTreeCtrl::GetTextColor  
 Tato funkce člen implementuje chování zprávy Win32 [TVM_GETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773633), jak je popsáno v sadě Windows SDK.  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COLORREF** hodnotu, která představuje aktuální barvy. Pokud je tato hodnota -1, používá ovládací prvek barvy systému pro barvu textu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::SetTextColor](#settextcolor).  
  
##  <a name="gettooltips"></a>CTreeCtrl::GetToolTips  
 Tato funkce člen implementuje chování zprávy Win32 [TVM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb773729), jak je popsáno v sadě Windows SDK.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objekt, který chcete používat ovládací prvek stromu. Pokud [vytvořit](#create) – členská funkce používá styl **TVS_NOTOOLTIPS**, žádné popisy tlačítek se používají, a **NULL** je vrácen.  
  
### <a name="remarks"></a>Poznámky  
 Implementace MFC `GetToolTips` vrátí `CToolTipCtrl` objekt, který je používán ovládací prvek stromu, nikoli popisovač pro ovládací prvek popis tlačítka.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#25](../../mfc/reference/codesnippet/cpp/ctreectrl-class_28.cpp)]  
  
##  <a name="getvisiblecount"></a>CTreeCtrl::GetVisibleCount  
 Volání této funkce se načíst počet viditelné položky v ovládacím prvku stromu zobrazení.  
  
```  
UINT GetVisibleCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo zobrazené položky v ovládacím prvku stromu zobrazení; jinak - 1.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::SetCheck](#setcheck).  
  
##  <a name="hittest"></a>CTreeCtrl::HitTest  
 Volání této funkce k určení umístění zadaná bodu relativně k klientské oblasti zobrazení ovládacího prvku strom.  
  
```  
HTREEITEM HitTest(
    CPoint pt,  
    UINT* pFlags = NULL) const;  
  
HTREEITEM HitTest(TVHITTESTINFO* pHitTestInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 Souřadnice klienta bodu k testování.  
  
 `pFlags`  
 Ukazatel na celé číslo, které obdrží informace o výsledcích přístupů testu. Může mít jednu nebo více hodnot uvedený v seznamu **příznaky** člen v oddílu Poznámky.  
  
 `pHitTestInfo`  
 Adresa [TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448) struktura, která obsahuje pozici narazila na test a který obdrží informace o výsledcích přístupů testu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač položky stromové zobrazení, která sídlí Zadaný bod nebo **NULL** Pokud žádná položka bude zabírat bodem.  
  
### <a name="remarks"></a>Poznámky  
 Když tato funkce je volána, `pt` parametr určuje souřadnice bodu k testování. Funkce vrátí popisovač položku na zadaný bod nebo **NULL** Pokud žádná položka bude zabírat bodem. Kromě toho `pFlags` parametr obsahuje hodnotu, která určuje umístění Zadaný bod. Možné hodnoty jsou:  
  
|||  
|-|-|  
|Hodnota|Význam|  
|TVHT_ABOVE|Výše klientské oblasti.|  
|TVHT_BELOW|Pod oblastí klienta.|  
|TVHT_NOWHERE|V oblasti klienta, ale pod poslední položky.|  
|TVHT_ONITEM|Rastrový obrázek nebo popisek přidružený k položce.|  
|TVHT_ONITEMBUTTON|Na tlačítko přidružený k položce.|  
|TVHT_ONITEMICON|Na bitmapy přidružený k položce.|  
|TVHT_ONITEMINDENT|V odsazení přidružený k položce.|  
|TVHT_ONITEMLABEL|Na popisek (string) přidružený k položce.|  
|TVHT_ONITEMRIGHT|V oblasti napravo od položky.|  
|TVHT_ONITEMSTATEICON|Na ikonu stavu pro položku stromové zobrazení, která je ve stavu, uživatelem definované.|  
|TVHT_TOLEFT|Nalevo od klientské oblasti.|  
|TVHT_TORIGHT|Napravo od klientské oblasti.|  
|||  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#26](../../mfc/reference/codesnippet/cpp/ctreectrl-class_29.cpp)]  
  
##  <a name="insertitem"></a>CTreeCtrl::InsertItem  
 Volání této funkce Vložit novou položku ve stromovém zobrazení.  
  
```  
HTREEITEM InsertItem(LPTVINSERTSTRUCT lpInsertStruct);

 
HTREEITEM InsertItem(
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam,  
    HTREEITEM hParent,  
    HTREEITEM hInsertAfter);

 
HTREEITEM InsertItem(
    LPCTSTR lpszItem,  
    HTREEITEM hParent = TVI_ROOT,  
    HTREEITEM hInsertAfter = TVI_LAST);

 
HTREEITEM InsertItem(
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    HTREEITEM hParent = TVI_ROOT,  
    HTREEITEM hInsertAfter = TVI_LAST);
```  
  
### <a name="parameters"></a>Parametry  
 *lpInsertStruct*  
 Ukazatel na `TVINSERTSTRUCT` určující atributy položky stromové zobrazení nelze vložit.  
  
 `nMask`  
 Celé číslo určující atributy, které chcete nastavit. Najdete v článku `TVITEM` struktura ve Windows SDK.  
  
 `lpszItem`  
 Adresa řetězec obsahující text položky.  
  
 `nImage`  
 Index položky obrázku v seznamu obrázků v ovládacím prvku zobrazení stromu.  
  
 `nSelectedImage`  
 Index obrázku vybrané položky v seznamu obrázků v ovládacím prvku zobrazení stromu.  
  
 `nState`  
 Určuje hodnoty pro položky stavy. Informace najdete v zobrazení stavů ovládacího prvku strom položku v sadě Windows SDK pro seznam příslušné stavy.  
  
 `nStateMask`  
 Určuje, jaké stavy jsou nastavení. Najdete v článku `TVITEM` struktura ve Windows SDK.  
  
 `lParam`  
 Hodnota 32-bit specifické pro aplikace přidružené k položce.  
  
 `hParent`  
 Obslužná rutina nadřazeného vložené položky.  
  
 *hInsertAfter*  
 Obslužná rutina položky, po jejímž uplynutí má vložit novou položku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač nové položky v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Příklad ukazuje situace, ve kterých můžete chtít použít každou verzi funkce při vkládání položku ovládacího prvku strom.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#27](../../mfc/reference/codesnippet/cpp/ctreectrl-class_30.cpp)]  
  
##  <a name="itemhaschildren"></a>CTreeCtrl::ItemHasChildren  
 Tato funkce slouží k určení, zda položka stromové struktury určeného `hItem` obsahuje podřízené položky.  
  
```  
BOOL ItemHasChildren(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud položka stromu Určuje `hItem` obsahuje podřízené položky; 0, pokud neexistuje.  
  
### <a name="remarks"></a>Poznámky  
 Pokud ano, pak můžete použít [CTreeCtrl::GetChildItem](#getchilditem) k načtení těchto podřízené položky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::GetSelectedItem](#getselecteditem).  
  
##  <a name="mapaccidtoitem"></a>CTreeCtrl::MapAccIdToItem  
 Mapuje zadané usnadnění identifikátor popisovač položku zobrazení stromu v ovládacím prvku aktuální zobrazení stromu.  
  
```  
HTREEITEM MapAccIdToItem(UINT uAccId) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`uAccId`|Identifikátor usnadnění pro nějaký element v položce zobrazení stromu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač položku zobrazení stromu ( `HTREEITEM`), který odpovídá `uAccId` parametr. Další informace najdete v tématu `hItem` členem [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) struktury.  
  
### <a name="remarks"></a>Poznámky  
 Usnadnění pomůcky jsou aplikace, které pomáhají osoby s postižením používat počítače. Usnadnění identifikátoru je používán `IAccessible` rozhraní jednoznačně zadat element v okně. Další informace o usnadnění identifikátory, naleznete v tématu "O Active Accessibility podpora" v [Microsoft Developer Network](http://go.microsoft.com/fwlink/p/?linkid=56322).  
  
 Tato metoda odesílá [TVM_MAPACCIDTOHTREEITEM](http://msdn.microsoft.com/library/windows/desktop/bb773734) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_treeCtrl`, který používá pro přístup k aktuální ovládacího prvku zobrazení stromu. Příklad kódu také definuje několik HTREEITEM proměnné a celé číslo bez znaménka. Tyto proměnné se používají v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu používá identifikátor usnadnění a [CTreeCtrl::MapAccIdToItem](#mapaccidtoitem) metoda pro načtení popisovač pro kořenovou položku zobrazení stromu. Tento příklad používá popisovač a [CTreeCtrl::GetItemPartRect](#getitempartrect) metoda 3D obdélník kolem této položky. V předcházející části příklad kódu, který není zobrazený, jsme vytvořili stromové zobrazení, která se skládá z kořenového uzlu země nebo oblast pro Spojené státy americké, podřízených uzlů stavů Velká Británie a Washington a položkami stromu pro města v těchto stavů. Použili jsme [CTreeCtrl::MapItemToAccID](#mapitemtoaccid) metoda, jak přidružit kořenovou položku zobrazení stromu s identifikátorem usnadnění.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/ctreectrl-class_18.cpp)]  
  
##  <a name="mapitemtoaccid"></a>CTreeCtrl::MapItemToAccID  
 Mapuje zadaný popisovač položku zobrazení stromu v ovládacím prvku aktuální zobrazení stromu identifikátorem usnadnění.  
  
```  
UINT MapItemToAccID(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`hItem`|Obslužná rutina položky zobrazení stromu v ovládacím prvku. Další informace najdete v tématu `hItem` členem [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) struktury.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor usnadnění přístupu, která odpovídá `hItem` parametr.  
  
### <a name="remarks"></a>Poznámky  
 Usnadnění pomůcky jsou aplikace, které pomáhají osoby s postižením používat počítače. Usnadnění identifikátoru je používán `IAccessible` rozhraní jednoznačně zadat element v okně. Další informace o usnadnění identifikátory, naleznete v tématu "O Active Accessibility podpora" v [Microsoft Developer Network](http://go.microsoft.com/fwlink/p/?linkid=56322).  
  
 Tato metoda odesílá [TVM_MAPHTREEITEMTOACCID](http://msdn.microsoft.com/library/windows/desktop/bb773735) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_treeCtrl`, který používá pro přístup k aktuální ovládacího prvku zobrazení stromu. Příklad kódu také definuje několik HTREEITEM proměnné a celé číslo bez znaménka. Tyto proměnné se používají v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu získá identifikační číslo pro položku ovládacího prvku zobrazení stromu. V předcházející části příklad kódu, který není zobrazený, jsme vytvořili stromové zobrazení, která se skládá z kořenového uzlu země nebo oblast pro Spojené státy americké, podřízených uzlů stavů Velká Británie a Washington a položkami stromu pro města v těchto stavů. Tento příklad kódu získá jedinečné identifikační číslo pro kořenový uzel země nebo oblast.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/ctreectrl-class_31.cpp)]  
  
##  <a name="select"></a>CTreeCtrl::Select  
 Volání této funkce, vyberte položku dané stromové zobrazení, přejděte do zobrazení položky nebo ho překreslit položky ve stylu slouží k určení cíl operace přetažení myší.  
  
```  
BOOL Select(
    HTREEITEM hItem,  
    UINT nCode);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu.  
  
 `nCode`  
 Typ akce se má provést. Tento parametr může být jedna z následujících hodnot:  
  
- `TVGN_CARET`Nastaví výběr na danou položku.  
  
- `TVGN_DROPHILITE`Daná položka překreslí ve stylu slouží k určení cíl operace přetažení myší.  
  
- `TVGN_FIRSTVISIBLE`Zobrazení stromu posune svisle tak, aby daná položka představuje první položku viditelné.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `nCode` obsahuje hodnotu `TVGN_CARET`, obdrží nadřazeného okna **TVN_SELCHANGING** a **TVN_SELCHANGED** zpráv s oznámením. Kromě toho pokud zadaná položka je podřízeným sbalené nadřazenou položku, nadřazeného seznamu podřízené položky je rozšířit, aby odhalit zadanou položku. V takovém případě obdrží nadřazeného okna **TVN_ITEMEXPANDING** a **TVN_ITEMEXPANDED** zpráv s oznámením.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::HitTest](#hittest).  
  
##  <a name="selectdroptarget"></a>CTreeCtrl::SelectDropTarget  
 Volání této funkce můžete ho překreslit položky ve stylu slouží k určení cíl operace přetažení myší.  
  
```  
BOOL SelectDropTarget(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#9](../../mfc/reference/codesnippet/cpp/ctreectrl-class_9.cpp)]  
  
##  <a name="selectitem"></a>CTreeCtrl::SelectItem  
 Volání této funkce, vyberte položku dané stromové zobrazení.  
  
```  
BOOL SelectItem(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač položka stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `hItem` je **NULL**, pak tato funkce vybere žádná položka.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#26](../../mfc/reference/codesnippet/cpp/ctreectrl-class_29.cpp)]  
  
##  <a name="selectsetfirstvisible"></a>CTreeCtrl::SelectSetFirstVisible  
 Volání této funkce můžete tak, aby daná položka se první položky zobrazené svisle posuňte zobrazení stromu.  
  
```  
BOOL SelectSetFirstVisible(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Položka stromu nastavit jako první položky zobrazené popisovač.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Funkce odešle zprávu do okna s `TVM_SELECTITEM` a `TVGN_FIRSTVISIBLE` zprávy parametry.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#28](../../mfc/reference/codesnippet/cpp/ctreectrl-class_32.cpp)]  
  
##  <a name="setautoscrollinfo"></a>CTreeCtrl::SetAutoscrollInfo  
 Nastaví počet nadřazená aktuální ovládacího prvku zobrazení stromu.  
  
```  
BOOL SetAutoscrollInfo(
    UINT uPixelsPerSec,   
    UINT uUpdateTime);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`uPixelsPerSec`|Počet pixelů na posuňte za sekundu.|  
|[v]`uUpdateTime`|Časový interval mezi aktualizace ovládacího prvku.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy vrátí hodnotu `true`.  
  
### <a name="remarks"></a>Poznámky  
 Automatický posun parametry se používají k přejděte do zobrazení položku, která momentálně není viditelná. Ovládací prvek stromové zobrazení musí mít `TVS_EX_AUTOHSCROLL` rozšířený styl, který je popsán v [rozšířené styly ovládacího prvku zobrazení stromu](http://msdn.microsoft.com/library/windows/desktop/bb759981).  
  
 Tato metoda odesílá [TVM_SETAUTOSCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb773738) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_treeCtrl`, který používá pro přístup k aktuální ovládacího prvku zobrazení stromu. Příklad kódu také definuje několik HTREEITEM proměnné a celé číslo bez znaménka. Tyto proměnné se používají v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví nadřazená chování ovládacího prvku aktuální zobrazení stromu. V předcházející části příklad kódu, který není zobrazený, jsme vytvořili stromové zobrazení, která se skládá z kořenového uzlu země nebo oblast pro Spojené státy americké, podřízených uzlů stavů Velká Británie a Washington a položkami stromu pro města v těchto stavů. Jsme záměrně provedli ovládacího prvku zobrazení stromu úzké tak, aby musí automaticky posouvalo zobrazení položka stromu, který je aktivní. Příklad kódu nastaví automaticky posun 30 pixelů za sekundu každých 5 sekund, dokud položka stromu v zobrazení ovládacího prvku zobrazení stromu.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/ctreectrl-class_33.cpp)]  
  
##  <a name="setbkcolor"></a>CTreeCtrl::SetBkColor  
 Tato funkce člen implementuje chování zprávy Win32 [TVM_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773741), jak je popsáno v sadě Windows SDK.  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 `clr`  
 A **COLORREF** hodnotu, která obsahuje novou barvu pozadí. Pokud je tato hodnota -1, ovládacího prvku se vrátí pomocí systému barvu pro barvu pozadí.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COLORREF** hodnotu, která představuje aktuální barvy. Pokud je tato hodnota -1, používá ovládací prvek barvy systému pro barvu textu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::SetTextColor](#settextcolor).  
  
##  <a name="setcheck"></a>CTreeCtrl::SetCheck  
 Volání této funkce člena pro nastavení kontroly stavu pro položku ovládacího prvku strom.  
  
```  
BOOL SetCheck(
    HTREEITEM hItem,  
    BOOL fCheck = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 **HTREEITEM** přijímat změna kontroly stavu.  
  
 `fCheck`  
 Určuje, zda položka ovládací prvek stromu na zaškrtnuté nebo nezaškrtnuté. Ve výchozím nastavení `SetCheck` nastaví položka, která má být zaškrtnuto.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je zaškrtnuta možnost položky ovládacího prvku strom ( `fCheck` nastavena na **TRUE**), se položka zobrazí s přiléhající zaškrtnutí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#29](../../mfc/reference/codesnippet/cpp/ctreectrl-class_34.cpp)]  
  
### <a name="example"></a>Příklad  
 Pomocí zaškrtávacích políček, nastavte TVS_CHECKBOXES před naplnění ovládací prvek stromu.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl#30](../../mfc/reference/codesnippet/cpp/ctreectrl-class_35.cpp)]  
  
##  <a name="setextendedstyle"></a>CTreeCtrl::SetExtendedStyle  
 Nastaví rozšířené styly pro ovládací prvek aktuální zobrazení stromu.  
  
```  
DWORD SetExtendedStyle(
    DWORD dwExMask,   
    DWORD dwExStyles);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`dwExMask`|Bitová maska, která určuje, jaké styly v ovládacím prvku aktuální zobrazení stromu ovlivněných touto metodou. Pokud má parametr hodnotu nula, bude ignorováno a hodnota `dwExStyles` parametr je přiřazen do ovládacího prvku zobrazení stromu.<br /><br /> Zadejte nula nebo bitovou kombinaci (nebo) styly popsané v [– styly ovládacího prvku rozšířené zobrazení stromu](http://msdn.microsoft.com/library/windows/desktop/bb759981).|  
|[v]`dwExStyles`|Bitová maska, která určuje, jaké styly v aktuálním zobrazení stromu řídit k nastavení nebo zrušení.<br /><br /> Nastavit kombinaci stylů, zadejte bitovou kombinaci (nebo) styly popsané v [– styly ovládacího prvku rozšířené zobrazení stromu](http://msdn.microsoft.com/library/windows/desktop/bb759981). Chcete-li zaškrtnutí sady stylů, zadejte nula.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která obsahuje předchozí rozšířené styly ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vymaže styly definované v `dwExMask` styly definované v Nastaví parametr `dwExStyles` parametr. Pouze rozšířené styly, které odpovídají bity v `dwExMask` změnit.  
  
 Tato metoda odesílá [TVM_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb773744) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_treeCtrl`, který používá pro přístup k aktuální ovládacího prvku zobrazení stromu. Příklad kódu také definuje několik HTREEITEM proměnné a celé číslo bez znaménka. Tyto proměnné se používají v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu přidá `TVS_EX_AUTOHSCROLL` rozšířený styl do ovládacího prvku aktuální zobrazení stromu. V předcházející části příklad kódu, který není zobrazený, jsme vytvořili stromové zobrazení, která se skládá z kořenového uzlu země nebo oblast pro Spojené státy americké, podřízených uzlů stavů Velká Británie a Washington a položkami stromu pro města v těchto stavů. Jsme záměrně provedli ovládacího prvku zobrazení stromu úzké tak, aby musí automaticky posouvalo zobrazení položka stromu, který je aktivní.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/ctreectrl-class_36.cpp)]  
  
##  <a name="setimagelist"></a>CTreeCtrl::SetImageList  
 Volání této funkce můžete nastavit normální nebo seznamu obrázků stavu pro strom zobrazení ovládacího prvku nebo ho překreslit ovládacího prvku pomocí nových bitových kopií.  
  
```  
CImageList* SetImageList(
    CImageList* pImageList,  
    int nImageListType);
```  
  
### <a name="parameters"></a>Parametry  
 `pImageList`  
 Ukazatel na seznamu obrázků přiřadit. Pokud `pImageList` je **NULL**, všechny bitové kopie se odeberou z ovládacího prvku zobrazení stromu.  
  
 `nImageListType`  
 Typ seznamu obrázků nastavit. Seznam obrázků může být jedna z následujících hodnot:  
  
- `TVSIL_NORMAL`Nastaví normální image seznam, který obsahuje vybrané a nevybrané bitových kopií pro položky zobrazení stromu. Tento stav je nutné použít pro bitové kopie překrytí.  
  
- `TVSIL_STATE`Nastaví seznamu obrázků stavu, který obsahuje Image pro strom zobrazit položky, které jsou ve stavu, uživatelem definované.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na předchozí seznamu obrázků, pokud existuje; v opačném případě **NULL**.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::GetImageList](#getimagelist).  
  
##  <a name="setindent"></a>CTreeCtrl::SetIndent  
 Volání této funkce můžete nastavit šířku odsazení pro ovládací prvek stromu zobrazení nebo ho překreslit ovládacího prvku tak, aby odrážely novou šířku.  
  
```  
void SetIndent(UINT nIndent);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndent`  
 Šířka v pixelech odsazení. Pokud `nIndent` je menší než minimální šířka definovaná systémem šířku nové nastavena na minimální definovaná systémem.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::GetIndent](#getindent).  
  
##  <a name="setinsertmark"></a>CTreeCtrl::SetInsertMark  
 Tato funkce člen implementuje chování zprávy Win32 [TVM_SETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb773753), jak je popsáno v sadě Windows SDK.  
  
```  
BOOL SetInsertMark(
    HTREEITEM hItem,  
    BOOL fAfter = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 **HTREEITEM** určující, na která položka bude umístěna značky vložení. Pokud tento argument je **NULL**, značky vložení se odebere.  
  
 *fAfter*  
 **BOOL** hodnotu, která určuje, pokud je značky vložení umístěn před nebo po zadanou položku. Pokud tento argument je nenulové, značky vložení se umístí za položkou. Pokud tento argument je nulová, značky vložení se uskuteční před položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#31](../../mfc/reference/codesnippet/cpp/ctreectrl-class_37.cpp)]  
  
##  <a name="setinsertmarkcolor"></a>CTreeCtrl::SetInsertMarkColor  
 Tato funkce člen implementuje chování zprávy Win32 [TVM_SETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773755), jak je popsáno v sadě Windows SDK.  
  
```  
COLORREF SetInsertMarkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>Parametry  
 `clrNew`  
 A **COLORREF** hodnotu, která obsahuje novou barvu značky vložení.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COLORREF** hodnotu, která obsahuje předchozí barvu značky vložení.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::GetInsertMarkColor](#getinsertmarkcolor).  
  
##  <a name="setitem"></a>CTreeCtrl::SetItem  
 Volejte tuto funkci nastavit atributy položky stromové zobrazení.  
  
```  
BOOL SetItem(TVITEM* pItem);

 
BOOL SetItem(
    HTREEITEM hItem,  
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Ukazatel [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) struktura, která obsahuje novou položku atributy, jak je popsáno v sadě Windows SDK.  
  
 `hItem`  
 Obslužná rutina položky, jejichž atributy jsou nastavení. Najdete v článku **: hItem** členem `TVITEM` struktura ve Windows SDK.  
  
 `nMask`  
 Celé číslo určující atributy, které chcete nastavit. Najdete v článku **maska** členem `TVITEM` struktura.  
  
 `lpszItem`  
 Adresa řetězec obsahující text položky.  
  
 `nImage`  
 Index položky obrázku v seznamu obrázků v ovládacím prvku zobrazení stromu. Najdete v článku `iImage` členem `TVITEM` struktura.  
  
 `nSelectedImage`  
 Index obrázku vybrané položky v seznamu obrázků v ovládacím prvku zobrazení stromu. Najdete v článku **iSelectedImage** členem `TVITEM` struktura.  
  
 `nState`  
 Určuje hodnoty pro položky stavy. Najdete v článku **stavu** členem `TVITEM` struktura.  
  
 `nStateMask`  
 Určuje, jaké stavy jsou nastavení. Najdete v článku **stateMask** členem `TVITEM` struktura.  
  
 `lParam`  
 Hodnota 32-bit specifické pro aplikace přidružené k položce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 V `TVITEM` struktura, **: hItem** člen označuje položku a **maska** člen Určuje atributy, které chcete nastavit.  
  
 Pokud **maska** člen nebo `nMask` parametr určuje `TVIF_TEXT` hodnota, **pszText** člen nebo `lpszItem` je adresa řetězce ukončené hodnotou null a **cchTextMax** člen se ignoruje. Pokud **maska** (nebo `nMask`) určuje `TVIF_STATE` hodnota, **stateMask** člen nebo `nStateMask` parametr určuje, která položka stavů změnit a **stavu**  člen nebo `nState` parametr obsahuje hodnoty pro tyto stavy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#32](../../mfc/reference/codesnippet/cpp/ctreectrl-class_38.cpp)]  
  
##  <a name="setitemdata"></a>CTreeCtrl::SetItemData  
 Volání této funkce můžete nastavit hodnotu 32-bit specifické pro aplikace přidružené k zadané položky.  
  
```  
BOOL SetItemData(
    HTREEITEM hItem,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Obslužná rutina položky, jejichž data se mají být načteny.  
  
 `dwData`  
 Hodnotu 32-bit specifické pro aplikace přidružené k položce určeného `hItem`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#33](../../mfc/reference/codesnippet/cpp/ctreectrl-class_39.cpp)]  
  
##  <a name="setitemexpandedimageindex"></a>CTreeCtrl::SetItemExpandedImageIndex  
 Nastaví index bitovou kopii k zobrazení, pokud zadaná položka aktuální zobrazení stromu ovládacího prvku v rozšířené stavu.  
  
```  
BOOL SetItemExpandedImageIndex(
    HTREEITEM hItem,   
    int iExpandedImage);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`hItem`|Zpracování položky ovládacího prvku zobrazení stromu.|  
|[v]`iExpandedImage`|Index bitové kopie k zobrazení, pokud zadaná položka v rozšířené stavu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TVM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773758) zprávy, která je popsána v sadě Windows SDK. Tato metoda přiřadí `iExpandedImage` parametru `iExpandedImage` členem [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) strukturu a pak používá, které struktury ve zprávě.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_treeCtrl`, který používá pro přístup k aktuální ovládacího prvku zobrazení stromu. Příklad kódu také definuje několik HTREEITEM proměnné a celé číslo bez znaménka. Tyto proměnné se používají v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu je trivial test ke zjištění, zda [CTreeCtrl::GetItemExpandedImageIndex](#getitemexpandedimageindex) metoda vrátí hodnotu, která nastavuje [CTreeCtrl::SetItemExpandedImageIndex](#setitemexpandedimageindex) metoda. V předcházející části příklad kódu, který není zobrazený, jsme vytvořili stromové zobrazení, která se skládá z kořenového uzlu země nebo oblast pro Spojené státy americké, podřízených uzlů stavů Velká Británie a Washington a položkami stromu pro města v těchto stavů.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#8](../../mfc/reference/codesnippet/cpp/ctreectrl-class_40.cpp)]  
  
##  <a name="setitemheight"></a>CTreeCtrl::SetItemHeight  
 Tato funkce člen implementuje chování zprávy Win32 [TVM_SETITEMHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb773761), jak je popsáno v sadě Windows SDK.  
  
```  
SHORT SetItemHeight(SHORT cyHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `cyHeight`  
 Určuje výšku nové každé položky ve stromovém zobrazení v pixelech. Pokud tento argument je menší než výška bitové kopie, pak nastaví se na výšku bitové kopie. Pokud není tento argument i, bude zaokrouhlená dolů na nejbližší i hodnotu. Pokud tento argument je -1, bude ovládací prvek obnovit pomocí jeho výšku položky výchozí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí výška položky v pixelech.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::GetItemHeight](#getitemheight).  
  
##  <a name="setitemimage"></a>CTreeCtrl::SetItemImage  
 Přidruží položku bitové kopie.  
  
```  
BOOL SetItemImage(
    HTREEITEM hItem,  
    int nImage,  
    int nSelectedImage);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Obslužná rutina položky, jejichž bitové kopie má být nastavena.  
  
 `nImage`  
 Index položky obrázku v seznamu obrázků v ovládacím prvku zobrazení stromu.  
  
 `nSelectedImage`  
 Index obrázku vybrané položky v seznamu obrázků v ovládacím prvku zobrazení stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Každá položka v ovládacím prvku stromu zobrazení může mít pár rastrových obrázků s ním spojená. Bitové kopie se zobrazí na levé straně popisku položky. Jednu image se zobrazí, když je položka vybrána, a druhé se zobrazí, pokud není vybrána položka. Například může položky zobrazit, otevřít složku, pokud je vybrána a uzavřené složku Pokud není vybraná.  
  
 Volejte tuto funkci nastavit index položky obrázku a jeho vybrané image v seznamu obrázků v ovládacím prvku zobrazení stromu.  
  
 Další informace o bitových kopií naleznete v tématu [CImageList](../../mfc/reference/cimagelist-class.md).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::GetItemImage](#getitemimage).  
  
##  <a name="setitemstate"></a>CTreeCtrl::SetItemState  
 Nastaví stav položky určeného `hItem`.  
  
```  
BOOL SetItemState(
    HTREEITEM hItem,  
    UINT nState,  
    UINT nStateMask);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Obslužná rutina položky, jejichž stav je možné nastavit.  
  
 `nState`  
 Určuje nové stavy pro položku.  
  
 `nStateMask`  
 Určuje, jaké stavy jsou změnit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Informace o stavu, v tématu [CTreeCtrl::GetItem](#getitem).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::GetItemState](#getitemstate).  
  
##  <a name="setitemstateex"></a>CTreeCtrl::SetItemStateEx  
 Nastaví stav rozšířené zadané položky v ovládacím prvku aktuální zobrazení stromu.  
  
```  
BOOL SetItemStateEx(
    HTREEITEM hItem,   
    UINT uStateEx);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`hItem`|Zpracování položky ovládacího prvku zobrazení stromu.|  
|[v]`uStateEx`|Rozšířené stavové položky. Další informace najdete v tématu `uStateEx` členem [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) struktury.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TVM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773758) zprávy, která je popsána v sadě Windows SDK. Tato metoda přiřadí `uStateEx` parametru `uStateEx` členem [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) strukturu a pak používá, které struktury ve zprávě.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_treeCtrl`, který používá pro přístup k aktuální ovládacího prvku zobrazení stromu. Příklad kódu také definuje několik HTREEITEM proměnné a celé číslo bez znaménka. Tyto proměnné se používají v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví položku zobrazení stromu zakázaném stavu. V předcházející části příklad kódu, který není zobrazený, jsme vytvořili stromové zobrazení, která se skládá z kořenového uzlu země nebo oblast pro Spojené státy americké, podřízených uzlů stavů Velká Británie a Washington a položkami stromu pro města v těchto stavů. Tento příklad kódu nastaví uzlu Velká Británie zakázaném stavu.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctreectrl-class_41.cpp)]  
  
##  <a name="setitemtext"></a>CTreeCtrl::SetItemText  
 Nastaví text položky určeného `hItem`.  
  
```  
BOOL SetItemText(
    HTREEITEM hItem,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Obslužná rutina položky, jejíž text je možné nastavit.  
  
 `lpszItem`  
 Adresa řetězec obsahující nový text pro položku  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#34](../../mfc/reference/codesnippet/cpp/ctreectrl-class_42.cpp)]  
  
##  <a name="setlinecolor"></a>CTreeCtrl::SetLineColor  
 Volání této funkce člen nastavit aktuální barvu čáry pro ovládací prvek zobrazení stromu.  
  
```  
COLORREF SetLineColor(COLORREF clrNew = CLR_DEFAULT);
```  
  
### <a name="parameters"></a>Parametry  
 `clrNew`  
 Nové barvu čáry.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí barvu čáry.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy win32 [TVM_SETLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773764), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#35](../../mfc/reference/codesnippet/cpp/ctreectrl-class_43.cpp)]  
  
##  <a name="setscrolltime"></a>CTreeCtrl::SetScrollTime  
 Volání této funkce člen nastavení scroll maximální doby pro ovládací prvek zobrazení stromu.  
  
```  
UINT SetScrollTime(UINT uScrollTime);
```  
  
### <a name="parameters"></a>Parametry  
 *uScrollTime*  
 Nové scroll maximální dobu v milisekundách. Pokud tato hodnota je menší než 100, bude zaokrouhlené až 100.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí maximální scroll čas v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy win32 [TVM_SETSCROLLTIME](http://msdn.microsoft.com/library/windows/desktop/bb773767), jak je popsáno v sadě Windows SDK.  
  
##  <a name="settextcolor"></a>CTreeCtrl::SetTextColor  
 Tato funkce člen implementuje chování zprávy Win32 [TVM_SETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773769), jak je popsáno v sadě Windows SDK.  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 `clr`  
 A **COLORREF** hodnotu, která obsahuje nové barvy. Pokud tento argument je -1, bude ovládací prvek obnovit pomocí systému barvu pro barvu textu.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COLORREF** hodnotu, která představuje předchozí barvy. Pokud je tato hodnota -1, byl ovládacího prvku pomocí barvy systému pro barvu textu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#36](../../mfc/reference/codesnippet/cpp/ctreectrl-class_44.cpp)]  
  
##  <a name="settooltips"></a>CTreeCtrl::SetToolTips  
 Tato funkce člen implementuje chování zprávy Win32 [TVM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb773772), jak je popsáno v sadě Windows SDK.  
  
```  
CToolTipCtrl* SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndTip`  
 Ukazatel [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objekt, který bude používat ovládací prvek stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objekt obsahující dříve využívaných ovládacím prvku popisek nebo **NULL** Pokud žádné popisy tlačítek používaly dříve.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li použít popisy tlačítek, určit, **TVS_NOTOOLTIPS** stylu při vytváření `CTreeCtrl` objektu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CTreeCtrl::GetToolTips](#gettooltips).  
  
##  <a name="showinfotip"></a>CTreeCtrl::ShowInfoTip  
 Zobrazí informační tip pro zadanou položku v ovládacím prvku aktuální zobrazení stromu.  
  
```  
void ShowInfoTip(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`hItem`|Popisovač pro položku zobrazení stromu v ovládacím prvku. Další informace najdete v tématu `hItem` členem [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) struktury.|  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozdílu mezi popisy tlačítek a infotips, naleznete v tématu "Popisy tlačítek a Infotips" v [Microsoft Developer Network](http://go.microsoft.com/fwlink/p/?linkid=56322).  
  
 Tato metoda odesílá [TVM_SHOWINFOTIP](http://msdn.microsoft.com/library/windows/desktop/bb773779) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="sortchildren"></a>CTreeCtrl::SortChildren  
 Volání této funkce abecedně seřaďte podřízené položky daného nadřazené položky v ovládacím prvku stromu zobrazení.  
  
```  
BOOL SortChildren(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parametry  
 `hItem`  
 Popisovač nadřazené položky, jejichž podřízené položky mají být seřazeny. Pokud `hItem` je **NULL**, řazení bude pokračovat od kořenu stromu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `SortChildren`nebude recurse prostřednictvím stromu; pouze bezprostředně podřízené `hItem` seřadí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#37](../../mfc/reference/codesnippet/cpp/ctreectrl-class_45.cpp)]  
  
##  <a name="sortchildrencb"></a>CTreeCtrl::SortChildrenCB  
 Volání této funkce seřadíte položky zobrazení stromu pomocí funkce zpětné volání definované aplikací, který porovnává položky.  
  
```  
BOOL SortChildrenCB(LPTVSORTCB pSort);
```  
  
### <a name="parameters"></a>Parametry  
 *pSort*  
 Ukazatel na [TVSORTCB](http://msdn.microsoft.com/library/windows/desktop/bb773462) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Funkce strukturu pro porovnání, **lpfnCompare**, musí vracet záporná Pokud první položka by měl předcházet druhý, kladnou hodnotu, pokud první položka byste měli postupovat podle druhý nebo nula v případě dvě položky jsou ekvivalentní.  
  
 `lParam1` a `lParam2` parametry odpovídají **lParam** členem [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) struktury pro dva položky porovnávané. `lParamSort` Parametr odpovídá **lParam** členem `TV_SORTCB` struktura.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CTreeCtrl#38](../../mfc/reference/codesnippet/cpp/ctreectrl-class_46.cpp)]  
  
 [!code-cpp[NVC_MFC_CTreeCtrl#39](../../mfc/reference/codesnippet/cpp/ctreectrl-class_47.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka CMNCTRL1 MFC](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CImageList – třída](../../mfc/reference/cimagelist-class.md)
