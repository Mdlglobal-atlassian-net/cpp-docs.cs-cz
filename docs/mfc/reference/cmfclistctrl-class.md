---
title: "Třída CMFCListCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
dev_langs: C++
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 770a1cec528355d6f7be7800ba1f77f2394bef79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl – třída
`CMFCListCtrl` Třídy rozšiřuje funkce [CListCtrl – třída](../../mfc/reference/clistctrl-class.md) třída díky podpoře funkce ovládacího prvku rozšířené hlavičky [CMFCHeaderCtrl třída](../../mfc/reference/cmfcheaderctrl-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCListCtrl : public CListCtrl  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Umožňuje možnost označte seřazený sloupec s jinou barvu pozadí.|  
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Umožňuje více režim řazení.|  
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Vrátí odkaz na ovládacím prvku podtržené záhlaví.|  
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Ověří, zda ovládacího prvku seznam v několika režim řazení.|  
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Voláno rámcem, pokud ji musí porovnat dvě položky ovládací prvek seznamu.|  
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Voláno rámcem, pokud je třeba určit barvu pozadí jedné buňky.|  
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Voláno rámcem, pokud je nutné získat písmo pro buňky přitahuje.|  
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Voláno rámcem, pokud je třeba určit barvu textu jedné buňky.|  
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Odebere sloupec pro řazení seznamu seřazené sloupců.|  
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Nastaví aktuální seřazený sloupec a pořadí řazení.|  
|[CMFCListCtrl::Sort](#sort)|Seřadí ovládacího prvku seznam.|  
  
## <a name="remarks"></a>Poznámky  
 `CMFCListCtrl`nabízí dvě vylepšení [CListCtrl – třída](../../mfc/reference/clistctrl-class.md) třídy. Nejprve označuje, že řazení sloupců či je k dispozici možnost automaticky kreslení šipku řazení v hlavičce. Druhý podporuje data řazení do více sloupců ve stejnou dobu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod v nástroji `CMFCListCtrl` třídy. Tento příklad ukazuje, jak pro vytvoření ovládací prvek seznamu, sloupce k vložení, vložit položky, nastavit text položky a nastavení z písma daného ovládacího prvku seznam. Tento fragment kódu je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxlistctrl.h  
  
##  <a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn  
 Označí seřazené sloupce s jinou barvu pozadí.  
  
```  
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bMark`  
 Parametr typu Boolean, která určuje, jestli se má povolit jinou barvu pozadí.  
  
 [v]`bRedraw`  
 Parametr typu Boolean, která určuje, zda se okamžitě ho překreslit ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 `EnableMarkSortedColumn`použije metodu `CDrawingManager::PixelAlpha` k výpočtu, jaká barva má použít pro seřadit sloupce. Zaznamenání barva je založena na barvu pozadí regulární.  
  
##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort  
 Umožňuje řazení řádky dat v ovládacím prvku seznamu podle více sloupců.  
  
```  
void EnableMultipleSort(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 Logická hodnota, která určuje, jestli chcete povolit režim řazení více sloupců.  
  
### <a name="remarks"></a>Poznámky  
 Když povolíte řazení podle více sloupců, mají sloupce hierarchie. Řádky dat, bude nejprve seřadit podle primární sloupce. Ekvivalent hodnoty jsou pak seřazené podle jednotlivých dalších sloupců na základě priority.  
  
##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl  
 Vrátí odkaz na ovládacím prvku záhlaví.  
  
```  
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na základní [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvky záhlaví pro ovládací prvek seznamu je okno, které obsahuje názvy sloupců. Obvykle je umístěný přímo nad sloupce.  
  
##  <a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort  
 Kontroluje, zda seznam aktuálně podporuje řazení do více sloupců.  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud ovládací prvek seznamu podporuje více řazení; `FALSE` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Když [CMFCListCtrl třída](../../mfc/reference/cmfclistctrl-class.md) podporuje více řazení, uživatel může seřadit dat v ovládacím prvku seznamu více sloupců. Chcete-li povolit více řazení, volejte [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort).  
  
##  <a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems  
 Tato metoda volá framework při porovná dvě položky.  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lParam1`  
 První položka k porovnání.  
  
 [v]`lParam2`  
 Druhá položka k porovnání.  
  
 [v]`iColumn`  
 Index sloupce, který tato metoda je řazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo, které je relativní umístění dvě položky. Záporná označuje, že první položka by měl předcházet druhý kladná hodnota označuje, že první položka byste měli postupovat podle druhý a nula znamená, že dvě položky jsou ekvivalentní.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace vždy vrátí hodnotu 0. Tato funkce vám umožňuje řazení algoritmus musí přepsat.  
  
##  <a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor  
 Rozhraní framework volá tuto metodu, pokud je třeba určit barvu pozadí jedné buňky.  
  
```  
virtual COLORREF OnGetCellBkColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nRow`  
 Řádek buněk v.  
  
 [v]`nColumn`  
 Sloupce v buňky.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `COLOREF` hodnotu, která určuje barvu pozadí buňky.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementaci `OnGetCellBkColor` nepoužívá zadaný vstupní parametry a místo toho jednoduše volá `GetBkColor`. Ve výchozím nastavení, tedy ovládacího prvku celý seznam bude mít stejnou barvu pozadí. Můžete přepsat `OnGetCellBkColor` v odvozené třídě k označení jednotlivých buněk barvou pozadí samostatné.  
  
##  <a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont  
 Tato metoda volá framework při získání písma u jednotlivých buněk.  
  
```  
virtual HFONT OnGetCellFont(
    int nRow,  
    int nColumn,  
    DWORD dwData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nRow`  
 Řádek buněk v.  
  
 [v]`nColumn`  
 Sloupce v buňky.  
  
 [v]`dwData`  
 Uživatelská data. Výchozí implementace nepoužívá tento parametr.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro písma, který se používá pro aktuální buňky.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, tato metoda vrátí hodnotu `NULL`. Všechny buňky v ovládacím prvku seznamu mít stejné písmo. Potlačí tuto metodu za účelem poskytnutí různá písma pro různé buňky.  
  
##  <a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor  
 Rozhraní framework volá tuto metodu, pokud je třeba určit barvu textu jedné buňky.  
  
```  
virtual COLORREF OnGetCellTextColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nRow`  
 Řádek buněk v.  
  
 [v]`nColumn`  
 Sloupce v buňky.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `COLOREF` hodnotu, která určuje barvu textu buňky.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, tato metoda volá `GetTextColor` bez ohledu na to vstupní parametry. Ovládacího prvku celý seznam bude mít stejné barvy. Můžete přepsat `OnGetCellTextColor` v odvozené třídě k označení jednotlivých buněk s samostatné barvy.  
  
##  <a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn  
 Odebere sloupec pro řazení seznamu seřazené sloupců.  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iColumn`  
 Sloupec, který chcete odebrat.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odebere řazení sloupců z ovládacího prvku záhlaví. Zavolá [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).  
  
##  <a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn  
 Nastaví aktuální seřazený sloupec a pořadí řazení.  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending = TRUE,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iColumn`  
 Tento sloupec seřadit.  
  
 [v]`bAscending`  
 Logická hodnota, která určuje pořadí řazení.  
  
 [v]`bAdd`  
 Logická hodnota, která určuje, zda metoda přidá sloupec indikován `iColumn` do seznamu řazení sloupců.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda předá vstupní parametry do ovládacího prvku záhlaví pomocí metody [CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).  
  
##  <a name="sort"></a>CMFCListCtrl::Sort  
 Seřadí ovládacího prvku seznam.  
  
```  
virtual void Sort(
    int iColumn,  
    BOOL bAscending = TRUE,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iColumn`  
 Tento sloupec seřadit.  
  
 [v]`bAscending`  
 Logická hodnota, která určuje pořadí řazení.  
  
 [v]`bAdd`  
 Logická hodnota, která určuje, zda tato metoda přidá sloupec indikován `iColumn` do seznamu řazení sloupců.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CListCtrl – třída](../../mfc/reference/clistctrl-class.md)
