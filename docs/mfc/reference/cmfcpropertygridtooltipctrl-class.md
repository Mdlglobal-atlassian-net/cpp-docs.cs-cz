---
title: "Třída CMFCPropertyGridToolTipCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a0b4a43da8943bc196a799ca4419dea7f34ed76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl – třída
Implementuje a popisku řídit, která [CMFCPropertyGridCtrl třída](../../mfc/reference/cmfcpropertygridctrl-class.md) používá zobrazíte popisy tlačítek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPropertyGridToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Vytvoří `CMFCPropertyGridToolTipCtrl` objektu.|  
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Vytvoří okna pro ovládací prvek popis tlačítka.|  
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Deaktivuje a skryje ovládacího prvku popisek.|  
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Vrátí poslední pozice ovládacího prvku tooltip souřadnice.|  
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Skryje ovládacího prvku popisek.|  
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Používá třída [CWinApp](../../mfc/reference/cwinapp-class.md) přeložit zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. (Přepisuje [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Nastaví mezery mezi text popisku a ohraničení popisku okna.|  
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Zobrazí ovládací prvek popis tlačítka.|  
  
## <a name="remarks"></a>Poznámky  
 Popisy tlačítek se zobrazují, když umístění ukazatele myši na název vlastnosti. [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) třída zobrazí popisek tak, aby se uživatel snadno čitelné. Obvykle je určena pozici popisek pozice ukazatele. Pomocí této třídy popis se zobrazí nad název vlastnosti a podobné fyzické vlastnosti rozšíření, tak, aby název vlastnosti plně.  
  
 MFC automaticky vytvoří tento ovládací prvek a používá ho [CMFCPropertyGridCtrl třída](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCPropertyGridToolTipCtrl` třídy a postupy: zobrazení ovládacího prvku popisek.  
  
 [!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxpropertygridtooltipctrl.h  
  
##  <a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl  
 Vytvoří `CMFCPropertyGridToolTipCtrl` objektu.  
  
```  
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```  
  
##  <a name="create"></a>CMFCPropertyGridToolTipCtrl::Create  
 Vytvoří okna pro ovládací prvek popis tlačítka.  
  
```  
BOOL Create(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParent`  
 Ukazatel do nadřazeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud byl úspěšně vytvořen okna; jinak hodnota FALSE.  
  
##  <a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::Deactivate  
 Deaktivuje a skryje ovládacího prvku popisek.  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví poslední pozice a text na prázdné hodnoty, tak, aby budoucí volá, aby se [CMFCPropertyGridToolTipCtrl::Track](#track) zobrazí popisek.  
  
##  <a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect  
 Vrátí poslední pozice ovládacího prvku tooltip souřadnice.  
  
```  
void GetLastRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`rect`  
 Obsahuje poslední pozice ovládacího prvku popisek.  
  
##  <a name="hide"></a>CMFCPropertyGridToolTipCtrl::Hide  
 Skryje ovládacího prvku popisek.  
  
```  
void Hide();
```  
  
##  <a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin  
 Nastaví mezery mezi text popisku a ohraničení popisku okna.  
  
```  
void SetTextMargin(int nTextMargin);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nTextMargin`  
 Určuje mezery mezi ovládací prvek text popisku a ohraničení popisku okna. Výchozí hodnota je 10 pixelů.  
  
##  <a name="track"></a>CMFCPropertyGridToolTipCtrl::Track  
 Zobrazí ovládací prvek popis tlačítka.  
  
```  
void Track(
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`rect`  
 Určuje umístění a velikost ovládacího prvku tooltip.  
  
 [v]`strText`  
 Určuje text, který se zobrazí v popisu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zobrazí ovládací prvek popisek v umístění a velikost určeného `rect`. Pokud od posledního volání této metody se nezměnily pozici, velikost a text, tato metoda nemá žádný vliv.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
