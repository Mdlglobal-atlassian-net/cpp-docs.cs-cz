---
title: "Třída CMFCHeaderCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
dev_langs: C++
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d3b8b95b161704d5d5b2ca56e22cfe818e4785d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl – třída
`CMFCHeaderCtrl` Třída podporuje řazení více sloupců v ovládacím prvku hlavička.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCHeaderCtrl : public CHeaderCtrl  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|Vytvoří `CMFCHeaderCtrl` objektu.|  
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Povolí nebo zakáže *více sloupec řazení* režimu pro aktuální ovládací prvek záhlaví.|  
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Určuje, zda sloupec není seřazen nebo je seřadit ve vzestupném nebo sestupném pořadí.|  
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Načte index první seřazený sloupec v ovládacím prvku záhlaví na nule.|  
|`CMFCHeaderCtrl::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCHeaderCtrl::IsAscending](#isascending)|Určuje, zda všechny sloupce v ovládacím prvku záhlaví je seřadit ve vzestupném pořadí.|  
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Určuje, zda okno nadřazeného prvku aktuální záhlaví dialogového okna.|  
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Určuje, zda je aktuální ovládacího prvku záhlaví v *více sloupec řazení* režimu.|  
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Odebere zadaný sloupec v seznamu řadit sloupce.|  
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Nastaví pořadí řazení zadané sloupce v ovládacím prvku hlavička.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Voláno rámcem k vykreslení sloupec ovládacího prvku záhlaví.|  
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Voláno rámcem k vykreslení šipku řazení.|  
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Voláno rámcem k vyplnění na pozadí ovládacího prvku záhlaví sloupce.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCHeaderCtrl` třídy a povolení *více sloupec řazení* režimu pro aktuální ovládací prvek záhlaví.  
  
 [!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]  
  
## <a name="remarks"></a>Poznámky  
 `CMFCHeaderCtrl` Třída nevykresluje řazení šipku na sloupci ovládacího prvku záhlaví k označení, že je sloupec seřadit. Použití *více sloupec řazení* režim, pokud sada sloupců v ovládacím prvku seznamu nadřazeného ( [CMFCListCtrl třída](../../mfc/reference/cmfclistctrl-class.md)) může být seřazeny ve stejnou dobu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)  
  
 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxheaderctrl.h  
  
##  <a name="cmfcheaderctrl"></a>CMFCHeaderCtrl::CMFCHeaderCtrl  
 Vytvoří `CMFCHeaderCtrl` objektu.  
  
```  
CMFCHeaderCtrl::CMFCHeaderCtrl()  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento konstruktor inicializuje následující proměnné člena na zadané hodnoty:  
  
|Členské proměnné|Hodnota|  
|---------------------|-----------|  
|`m_bIsMousePressed`|`FALSE`|  
|`m_bMultipleSort`|`FALSE`|  
|`m_bAscending`|`TRUE`|  
|`m_nHighlightedItem`|-1|  
|`m_bTracked`|`FALSE`|  
|`m_bIsDlgControl`|`FALSE`|  
|`m_hFont`|`NULL`|  
  
##  <a name="enablemultiplesort"></a>CMFCHeaderCtrl::EnableMultipleSort  
 Povolí nebo zakáže *více sloupec řazení* režimu pro aktuální ovládací prvek záhlaví.  
  
```  
void EnableMultipleSort(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bEnable`  
 `TRUE`Pokud chcete povolit režim řazení více sloupců; `FALSE` zakázat více režim řazení sloupců a odebrat ze seznamu sloupců seřazené žádné sloupce. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte, pokud chcete povolit nebo zakázat režim řazení více sloupců. Dvě nebo více sloupců účastnit řazení Pokud ovládacím prvku záhlaví je v režimu řazení více sloupců.  
  
##  <a name="getcolumnstate"></a>CMFCHeaderCtrl::GetColumnState  
 Určuje, zda sloupec není seřazen nebo je seřadit ve vzestupném nebo sestupném pořadí.  
  
```  
int GetColumnState(int iColumn) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iColumn`  
 Index založený na nule sloupce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která indikuje stav řazení pro určený sloupec. Následující tabulka uvádí možné hodnoty:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|-1|Seřazené v sestupném pořadí.|  
|0|Není seřazen.|  
|1|Seřazené ve vzestupném pořadí.|  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getsortcolumn"></a>CMFCHeaderCtrl::GetSortColumn  
 Načte index první seřazený sloupec v ovládacím prvku záhlaví na nule.  
  
```  
int GetSortColumn() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index seřazený sloupec nebo -1, pokud se nenajde žádný seřazený sloupec.  
  
### <a name="remarks"></a>Poznámky  
 Pokud v ovládacím prvku záhlaví *více sloupec řazení* režimu a kompilované aplikace v režimu ladění, tato metoda vyhodnotí a informuje o tom, abyste použili [CMFCHeaderCtrl::GetColumnState](#getcolumnstate) metoda místo. Pokud ovládacím prvku záhlaví více režim řazení sloupců a kompilované aplikace v režimu prodejní, tato metoda vrátí hodnotu -1.  
  
##  <a name="isascending"></a>CMFCHeaderCtrl::IsAscending  
 Určuje, zda všechny sloupce v ovládacím prvku záhlaví je seřadit ve vzestupném pořadí.  
  
```  
BOOL IsAscending() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud žádné sloupce v ovládacím prvku záhlaví je seřadit ve vzestupném pořadí. v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota, vrátí tato metoda slouží k zobrazení šipku odpovídající řazení položku ovládacího prvku záhlaví. Použití [CMFCHeaderCtrl::SetSortColumn](#setsortcolumn) metodu a nastavit pořadí řazení.  
  
##  <a name="isdialogcontrol"></a>CMFCHeaderCtrl::IsDialogControl  
 Určuje, zda okno nadřazeného prvku aktuální záhlaví dialogového okna.  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je dialogové okno nadřazené aktuální ovládacího prvku záhlaví v opačném `FALSE`.  
  
##  <a name="ismultiplesort"></a>CMFCHeaderCtrl::IsMultipleSort  
 Určuje, zda je aktuální ovládacího prvku záhlaví v *více sloupec řazení* režimu.  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je povoleno více režim řazení sloupce; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) metoda chcete povolit nebo zakázat režim řazení více sloupců. Dvě nebo více sloupců účastnit řazení Pokud ovládacím prvku záhlaví je v režimu řazení více sloupců.  
  
##  <a name="ondrawitem"></a>CMFCHeaderCtrl::OnDrawItem  
 Voláno rámcem k vykreslení sloupec ovládacího prvku záhlaví.  
  
```  
virtual void OnDrawItem(
    CDC* pDC,  
    int iItem,  
    CRect rect,  
    BOOL bIsPressed,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`iItem`  
 Index založený na nule položky k vykreslení.  
  
 [v]`rect`  
 Ohraničující obdélník položky k vykreslení.  
  
 [v]`bIsPressed`  
 `TRUE`k položce v při stisknutí tlačítka stavu; v opačném `FALSE`.  
  
 [v]`bIsHighlighted`  
 `TRUE`k položce v zvýrazněná stavu; v opačném `FALSE`.  
  
##  <a name="ondrawsortarrow"></a>CMFCHeaderCtrl::OnDrawSortArrow  
 Voláno rámcem k vykreslení šipku řazení.  
  
```  
virtual void OnDrawSortArrow(
    CDC* pDC,  
    CRect rectArrow);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
 [v]`rectArrow`  
 Ohraničující obdélník šipku řazení.  
  
##  <a name="onfillbackground"></a>CMFCHeaderCtrl::OnFillBackground  
 Voláno rámcem k vyplnění na pozadí ovládacího prvku záhlaví sloupce.  
  
```  
virtual void OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontextu zařízení.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removesortcolumn"></a>CMFCHeaderCtrl::RemoveSortColumn  
 Odebere zadaný sloupec v seznamu řadit sloupce.  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iColumn`  
 Index založený na nule sloupce, který se odebrat.  
  
##  <a name="setsortcolumn"></a>CMFCHeaderCtrl::SetSortColumn  
 Nastaví pořadí řazení zadané sloupce v ovládacím prvku hlavička.  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending=TRUE,  
    BOOL bAdd=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iColumn`  
 Index založený na nule ovládacího prvku záhlaví sloupce. Pokud tento parametr menší než nula, tato metoda odebere všechny sloupce v seznamu řadit sloupce.  
  
 [v]`bAscending`  
 Určuje pořadí řazení sloupce, který `iColumn` určuje parametr. `TRUE`Chcete-li nastavit vzestupné pořadí; `FALSE` nastavit sestupném pořadí. Výchozí hodnota je `TRUE`.  
  
 [v]`bAdd`  
 `TRUE`k nastavení pořadí řazení sloupce, který `iColumn` určuje parametr.  
  
 Pokud je aktuální ovládací prvek záhlaví v *více sloupec řazení* režimu, tato metoda přidá zadaný sloupec do seznamu řazení sloupců. Použití [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) nastavit režim řazení více sloupců.  
  
 Pokud není nastaven více režim řazení sloupců a tato metoda kompiluje v režimu ladění, vyhodnotí se tato metoda. Pokud není nastaven více režim řazení sloupců a tato metoda kompiluje v režimu prodejní, tato metoda nejprve odebere všechny sloupce ze seznamu řazení sloupců a potom přidá zadaný sloupec do seznamu.  
  
 `FALSE`nejdřív odebrat všechny sloupce ze seznamu řazení sloupců a poté přidejte zadaný sloupec do seznamu. Výchozí hodnota je `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k nastavení pořadí řazení sloupce. V případě potřeby tato metoda přidá sloupec do seznamu řazení sloupců. Ovládací prvek záhlaví používá pořadí řazení k vykreslení šipku řazení, který odkazuje nahoru nebo dolů.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl – třída](../../mfc/reference/cmfclistctrl-class.md)
