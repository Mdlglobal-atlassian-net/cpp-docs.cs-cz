---
title: Cmfcheaderctrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97e0a81fc5e317f018924efd3d564d39618cb2b5
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850079"
---
# <a name="cmfcheaderctrl-class"></a>Cmfcheaderctrl – třída
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
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Povolí nebo zakáže *řazení více sloupců* režim pro aktuální ovládacího prvku záhlaví.|  
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Označuje, zda sloupec není seřazen, nebo je seřadit ve vzestupném nebo sestupném pořadí.|  
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Načte z nuly vycházející index první seřazený sloupec v ovládacím prvku záhlaví.|  
|`CMFCHeaderCtrl::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|  
|[CMFCHeaderCtrl::IsAscending](#isascending)|Určuje, zda všechny sloupce v ovládacím prvku záhlaví je seřazen vzestupně.|  
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Označuje, zda nadřazené okno ovládacího prvku aktuální záhlaví dialogového okna.|  
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Určuje, zda je aktuální ovládací prvek záhlaví v *řazení více sloupců* režimu.|  
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Odebere zadané sloupce ze seznamu řazení sloupců.|  
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Nastaví pořadí řazení zadané sloupce v ovládacím prvku hlavička.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Volá se rozhraním k vykreslení ovládacího prvku záhlaví sloupce.|  
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Volá se rozhraním, chcete-li nakreslit na šipku řazení.|  
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Volá se rozhraním vyplnit pozadí ovládacího prvku záhlaví sloupce.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCHeaderCtrl` třídy a jak povolit *řazení více sloupců* režim pro aktuální ovládacího prvku záhlaví.  
  
 [!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]  
  
## <a name="remarks"></a>Poznámky  
 `CMFCHeaderCtrl` Třídy nakreslí řazení šipku na záhlaví sloupce ovládacího prvku k označení, že je seřazený sloupec. Použití *řazení více sloupců* režim, pokud sadu sloupců v ovládacím prvku seznamu nadřazeného ( [cmfclistctrl – třída](../../mfc/reference/cmfclistctrl-class.md)) lze seřadit ve stejnou dobu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)  
  
 [Cmfcheaderctrl –](../../mfc/reference/cmfcheaderctrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxheaderctrl.h  
  
##  <a name="cmfcheaderctrl"></a>  CMFCHeaderCtrl::CMFCHeaderCtrl  
 Vytvoří `CMFCHeaderCtrl` objektu.  
  
```  
CMFCHeaderCtrl::CMFCHeaderCtrl()  
```  
  
### <a name="remarks"></a>Poznámky  
 Tento konstruktor inicializuje následující proměnné členů na zadané hodnoty:  
  
|Členské proměnné|Hodnota|  
|---------------------|-----------|  
|`m_bIsMousePressed`|FALSE|  
|`m_bMultipleSort`|FALSE|  
|`m_bAscending`|HODNOTA TRUE|  
|`m_nHighlightedItem`|-1|  
|`m_bTracked`|FALSE|  
|`m_bIsDlgControl`|FALSE|  
|`m_hFont`|NULL|  
  
##  <a name="enablemultiplesort"></a>  CMFCHeaderCtrl::EnableMultipleSort  
 Povolí nebo zakáže *řazení více sloupců* režim pro aktuální ovládacího prvku záhlaví.  
  
```  
void EnableMultipleSort(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bEnable*  
 TRUE, pokud chcete povolit režim řazení více sloupců; FALSE, chcete-li zakázat režim řazení více sloupců a odeberte všechny sloupce v seznamu seřazené sloupce. Výchozí hodnota je TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete povolit nebo zakázat režim řazení více sloupců. Dva nebo více sloupců mohou účastnit řazení, pokud je ovládací prvek záhlaví v režimu řazení více sloupců.  
  
##  <a name="getcolumnstate"></a>  CMFCHeaderCtrl::GetColumnState  
 Označuje, zda sloupec se neseřazené nebo seřazené ve vzestupném nebo sestupném pořadí.  
  
```  
int GetColumnState(int iColumn) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iColumn*  
 Z nuly vycházející index sloupce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která indikuje stav řazení pro určený sloupec. V následující tabulce jsou uvedeny možné hodnoty:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|-1|Seřazené v sestupném pořadí.|  
|0|Nejsou seřazené.|  
|1|Seřazené ve vzestupném pořadí.|  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getsortcolumn"></a>  CMFCHeaderCtrl::GetSortColumn  
 Načte z nuly vycházející index první seřazený sloupec v ovládacím prvku záhlaví.  
  
```  
int GetSortColumn() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index seřazený sloupec nebo -1, pokud se nenajde žádný seřazený sloupec.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je ovládací prvek záhlaví v *řazení více sloupců* režimu a můžete zkompilovat aplikaci v režimu ladění, tato metoda nepodmíněné výrazy a doporučí, abyste použili [CMFCHeaderCtrl::GetColumnState](#getcolumnstate) metoda místo. Pokud je ovládací prvek záhlaví v režimu řazení více sloupců a zkompilovat aplikaci v režimu maloobchodního prodeje, tato metoda vrátí hodnotu -1.  
  
##  <a name="isascending"></a>  CMFCHeaderCtrl::IsAscending  
 Určuje, zda všechny sloupce v ovládacím prvku záhlaví je seřazen vzestupně.  
  
```  
BOOL IsAscending() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud libovolný sloupec v ovládacím prvku záhlaví je seřazen vzestupně; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota, kterou vrací tato metoda slouží k zobrazení odpovídající řazení šipku u položky ovládacího prvku záhlaví. Použití [CMFCHeaderCtrl::SetSortColumn](#setsortcolumn) metoda k nastavení pořadí řazení.  
  
##  <a name="isdialogcontrol"></a>  CMFCHeaderCtrl::IsDialogControl  
 Označuje, zda nadřazené okno ovládacího prvku aktuální záhlaví dialogového okna.  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE v případě nadřazené okno ovládacího prvku aktuální záhlaví je dialogové okno; v opačném případě hodnota FALSE.  
  
##  <a name="ismultiplesort"></a>  CMFCHeaderCtrl::IsMultipleSort  
 Určuje, zda je aktuální ovládací prvek záhlaví v *řazení více sloupců* režimu.  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je povolený režim řazení více sloupců; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) metody, které chcete povolit nebo zakázat režim řazení více sloupců. Dva nebo více sloupců mohou účastnit řazení, pokud je ovládací prvek záhlaví v režimu řazení více sloupců.  
  
##  <a name="ondrawitem"></a>  CMFCHeaderCtrl::OnDrawItem  
 Volá se rozhraním k vykreslení ovládacího prvku záhlaví sloupce.  
  
```  
virtual void OnDrawItem(
    CDC* pDC,  
    int iItem,  
    CRect rect,  
    BOOL bIsPressed,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
 [in] *položky*  
 Index položky k vykreslení založený na nule.  
  
 [in] *rect*  
 Ohraničující obdélník položky k vykreslení.  
  
 [in] *bIsPressed*  
 TRUE, pokud chcete kreslit položky při stisknutí stavu; v opačném případě hodnota FALSE.  
  
 [in] *bIsHighlighted*  
 TRUE, pokud chcete kreslit položky v zvýrazněné stavu; v opačném případě hodnota FALSE.  
  
##  <a name="ondrawsortarrow"></a>  CMFCHeaderCtrl::OnDrawSortArrow  
 Volá se rozhraním, chcete-li nakreslit na šipku řazení.  
  
```  
virtual void OnDrawSortArrow(
    CDC* pDC,  
    CRect rectArrow);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
 [in] *rectArrow*  
 Ohraničující obdélník na šipku řazení.  
  
##  <a name="onfillbackground"></a>  CMFCHeaderCtrl::OnFillBackground  
 Volá se rozhraním vyplnit pozadí ovládacího prvku záhlaví sloupce.  
  
```  
virtual void OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="removesortcolumn"></a>  CMFCHeaderCtrl::RemoveSortColumn  
 Odebere zadané sloupce ze seznamu řazení sloupců.  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iColumn*  
 Z nuly vycházející index sloupce za účelem odebrání.  
  
##  <a name="setsortcolumn"></a>  CMFCHeaderCtrl::SetSortColumn  
 Nastaví pořadí řazení zadané sloupce v ovládacím prvku hlavička.  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending=TRUE,  
    BOOL bAdd=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iColumn*  
 Z nuly vycházející index sloupce záhlaví ovládacího prvku. Pokud tento parametr menší než nula, tato metoda odebere všechny sloupce ze seznamu sloupců seřadit.  
  
 [in] *bAscending*  
 Určuje pořadí řazení ve sloupci, který *iColumn* parametrem. TRUE, pokud chcete nastavit vzestupné pořadí. FALSE, pokud chcete nastavit sestupném pořadí. Výchozí hodnota je TRUE.  
  
 [in] *bAdd*  
 Hodnota true pro nastavení pořadí řazení ve sloupci, který *iColumn* parametrem.  
  
 Pokud je aktuální ovládací prvek záhlaví v *řazení více sloupců* režimu, tato metoda přidá zadaný sloupec na seznam řazení sloupců. Použití [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) nastavit režim řazení více sloupců.  
  
 Pokud není nastaven režim řazení více sloupců a tato metoda je kompilován v režimu ladění, vyhodnotí tuto metodu. Pokud není nastaven režim řazení více sloupců a tato metoda je kompilován v režimu maloobchodního prodeje, tato metoda nejprve odebere všechny sloupce ze seznamu řazení sloupců a pak přidá do seznamu zadaný sloupec.  
  
 FALSE, nejprve odeberte všechny sloupce ze seznamu řazení sloupců a pak přidejte do seznamu zadaný sloupec. Výchozí hodnota je FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k nastavení pořadí řazení sloupce. V případě potřeby, tato metoda přidá sloupec na seznam řazení sloupců. Pořadí řazení ovládacího prvku záhlaví používá nakreslete řazení šipku, která odkazuje směrem nahoru nebo dolů.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl – třída](../../mfc/reference/cmfclistctrl-class.md)
