---
title: Třída CTabView | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
dev_langs:
- C++
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08c0cff2f6586ab5e385808fb806ed435b00bfc9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ctabview-class"></a>CTabView – třída
`CTabView` Třída zjednodušuje použití třídy ovládacího prvku karta ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) v aplikacích používajících knihovny MFC document/view – architektura.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CTabbedView : public CView  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTabView::AddView](#addview)|Přidá nové zobrazení ovládacího prvku karta.|  
|[CTabView::FindTab](#findtab)|Vrátí index zadané zobrazení ovládacího prvku karta.|  
|[CTabView::GetActiveView](#getactiveview)|Vrací ukazatel na aktuálně aktivní zobrazení|  
|[CTabView::GetTabControl](#gettabcontrol)|Vrátí odkaz na ovládacího prvku karta přidružené zobrazení.|  
|[CTabView::RemoveView](#removeview)|Odebere z ovládacího prvku Karta zobrazení.|  
|[CTabView::SetActiveView](#setactiveview)|Nastaví zobrazení jako aktivní.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTabView::IsScrollBar](#isscrollbar)|Voláno rámcem při vytváření zobrazení Karta určit, zda karta zobrazení má sdílené vodorovného posuvníku.|  
|[CTabView::OnActivateView](#onactivateview)|Voláno rámcem při zobrazení Karta je aktivní nebo neaktivní.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída umožňuje snadno záložkách zobrazení vložena dokument/zobrazení aplikace. `CTabView` je `CView`-odvozené třídy, kterou obsahuje vložený `CMFCTabCtrl` objektu. `CTabView` zpracovává všechny zprávy, které jsou potřebné k podpoře `CMFCTabCtrl` objektu. Jednoduše odvození třídy z `CTabView` a zařadit ho do své aplikace a pak přidejte `CView`-odvozených tříd pomocí `AddView` metoda. Ovládacího prvku karta zobrazí jako karty těchto zobrazení.  
  
 Například může mít dokument, který může být reprezentován různými způsoby: jako tabulkou, graf, upravovat formulář a tak dále. Můžete vytvořit jednotlivé zobrazení kreslení data podle potřeby, vložte je do vašeho `CTabView`-odvozené objekt a potom kliknul na kartách bez další kódování.  
  
 [Ukázka TabbedView: MFC – záložkami zobrazení aplikace](../../visual-cpp-samples.md) ukazuje použití `CTabView`.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob `CTabView` se používá v ukázce TabbedView.  
  
 [!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxTabView.h  
  
##  <a name="addview"></a>  CTabView::AddView  
 Přidá do ovládacího prvku Karta zobrazení.  
  
```  
int AddView(
    CRuntimeClass* pViewClass,  
    const CString& strViewLabel,  
    int iIndex=-1,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pViewClass`  
 Ukazatel na třídu runtime vložené zobrazení.  
  
 [v] `strViewLabel`  
 Určuje text, na kartě.  
  
 [v] `iIndex`  
 Určuje pozici od nuly, kam chcete vložit zobrazení. Je-li pozice -1 je na konci vložit novou kartu.  
  
 [v] `pContext`  
 Ukazatel `CCreateContext` zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index zobrazení, pokud tato metoda bude úspěšná. Jinak hodnota -1.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se zobrazení přidat do ovládacího prvku karta vložené v rámečku.  
  
##  <a name="findtab"></a>  CTabView::FindTab  
 Vrátí index zadané zobrazení ovládacího prvku karta.  
  
```  
int FindTab(HWND hWndView) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v] `hWndView`  
 Popisovač zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index zobrazení, pokud je nalezena; jinak hodnota -1.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce načíst index zobrazení, který má Zadaný popisovač.  
  
##  <a name="getactiveview"></a>  CTabView::GetActiveView  
 Vrací ukazatel na aktuálně aktivní zobrazení.  
  
```  
CView* GetActiveView() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Neplatný ukazatel na aktivní zobrazení, nebo `NULL` Pokud neexistuje žádné aktivní zobrazení.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettabcontrol"></a>  CTabView::GetTabControl  
 Vrátí odkaz na ovládacího prvku karta přidružené zobrazení.  
  
```  
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na ovládacího prvku karta přidružené zobrazení.  
  
##  <a name="isscrollbar"></a>  CTabView::IsScrollBar  
 Voláno rámcem při vytváření zobrazení Karta určit, zda karta zobrazení má sdílené vodorovného posuvníku.  
  
```  
virtual BOOL IsScrollBar() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud by se vytvořit zobrazení kartě spolu s sdílené posuvníku. V opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá framework při `CTabView` vytvoření objektu.  
  
 Přepsání `IsScrollBar` metoda v `CTabView`-odvozené třídy a vraťte se `TRUE` Pokud chcete vytvořit zobrazení, který má sdílené vodorovného posuvníku.  
  
##  <a name="onactivateview"></a>  CTabView::OnActivateView  
 Voláno rámcem při zobrazení Karta je aktivní nebo neaktivní.  
  
```  
virtual void OnActivateView(CView* view);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `view`  
 Ukazatel na zobrazení.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace neprovede žádnou akci. Potlačí tuto metodu v `CTabView`-odvozené třídy ke zpracování tohoto oznámení.  
  
##  <a name="removeview"></a>  CTabView::RemoveView  
 Odebere z ovládacího prvku Karta zobrazení.  
  
```  
BOOL RemoveView(int iTabNum);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iTabNum`  
 Index zobrazení odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index zobrazení odebrána, pokud tato metoda bude úspěšná. Jinak-1.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setactiveview"></a>  CTabView::SetActiveView  
 Nastaví zobrazení jako aktivní.  
  
```  
BOOL SetActiveView(int iTabNum);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `iTabNum`  
 Index založený na nule kartě zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud bylo zadané zobrazení aktivní, `FALSE` Pokud zobrazení index není platný.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v části [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)   
 [CView – třída](../../mfc/reference/cview-class.md)
