---
title: "Třída CTooltipManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
dev_langs: C++
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 532203c753a61e4d242d4e749e9912a6b6ce7b5c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ctooltipmanager-class"></a>CTooltipManager – třída
Uchovává informace o běhu programu o tlačítkách. `CTooltipManager` Třída je instancí jednou na aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CTooltipManager : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTooltipManager::CreateToolTip](#createtooltip)|Vytvoří ovládací prvek popis tlačítka pro uvedené typy ovládacího prvku systému Windows.|  
|[CTooltipManager::DeleteToolTip](#deletetooltip)|Odstraní ovládacího prvku popisek.|  
|[CTooltipManager::SetTooltipParams](#settooltipparams)|Přizpůsobí vzhled ovládacího prvku tooltip pro uvedené typy ovládacího prvku systému Windows.|  
|[CTooltipManager::SetTooltipText](#settooltiptext)|Nastaví text a popis pro ovládací prvek popis tlačítka.|  
|[CTooltipManager::UpdateTooltips](#updatetooltips)||  
  
## <a name="remarks"></a>Poznámky  
 Použití [CMFCToolTipCtrl třída](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, a `CTooltipManager` dohromady a implementovat vlastní popisy tlačítek v aplikaci. Příklad použití těchto tříd popis v tématu [CMFCToolTipCtrl třída](../../mfc/reference/cmfctooltipctrl-class.md) tématu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtooltipmanager.h  
  
##  <a name="createtooltip"></a>CTooltipManager::CreateToolTip  
 Vytvoří ovládací prvek popis tlačítka.  
  
```  
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,  
    CWnd* pWndParent,  
    UINT nType);
```  
  
### <a name="parameters"></a>Parametry  
 [out]`pToolTip`  
 Odkaz na ukazatel popisku. Je nastaven tak, aby odkazoval na nově vytvořený popisek při funkce vrátí hodnotu.  
  
 [v]`pWndParent`  
 Nadřazené popisek.  
  
 [v]`nType`  
 Typ popisu tlačítka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud popisek bylo úspěšně vytvořeno.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat [CTooltipManager::DeleteToolTip](#deletetooltip) odstranit ovládací prvek popisek, který je předán zpět v `pToolTip`.  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) sady visual zobrazení parametry každý popisek vytvoří podle popisek typu `nType` určuje. Chcete-li změnit parametry pro jeden nebo více typů popisu tlačítka, volejte [CTooltipManager::SetTooltipParams](#settooltipparams).  
  
 Popisek platné typy jsou uvedeny v následující tabulce:  
  
|ToolTip – typ|Kategorie ovládacího prvku|Příklad typy|  
|------------------|----------------------|-------------------|  
|AFX_TOOLTIP_TYPE_BUTTON|Tlačítko.|CMFCButton|  
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Záhlaví.|CMFCCaptionBar|  
|AFX_TOOLTIP_TYPE_DEFAULT|Libovolný ovládací prvek, který se nevejde jiné kategorii.|Žádné|  
|AFX_TOOLTIP_TYPE_DOCKBAR|Lze ukotvit podokně.|CDockablePane|  
|AFX_TOOLTIP_TYPE_EDIT|Textové pole.|Žádné|  
|AFX_TOOLTIP_TYPE_MINIFRAME|Miniframe.|CPaneFrameWnd|  
|AFX_TOOLTIP_TYPE_PLANNER|Plánovač.|Žádné|  
|AFX_TOOLTIP_TYPE_RIBBON|Pás karet.|CMFCRibbonBar CMFCRibbonPanelMenuBar|  
|AFX_TOOLTIP_TYPE_TAB|Ovládacího prvku karta.|CMFCTabCtrl|  
|AFX_TOOLTIP_TYPE_TOOLBAR|Panel nástrojů.|CMFCToolBar CMFCPopupMenuBar|  
|AFX_TOOLTIP_TYPE_TOOLBOX|Panelu nástrojů.|Žádné|  
  
##  <a name="deletetooltip"></a>CTooltipManager::DeleteToolTip  
 Odstraní ovládacího prvku popisek.  
  
```  
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```  
  
### <a name="parameters"></a>Parametry  
 [ve out]`pToolTip`  
 Odkaz na ukazatel na popisek zničení.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody pro každou [CToolTipCtrl – třída](../../mfc/reference/ctooltipctrl-class.md) který byl vytvořen [CTooltipManager::CreateToolTip](#createtooltip). Nadřazeného ovládacího prvku by měly volat tuto metodu z jeho `OnDestroy` obslužné rutiny. To je nutné správně popisek odebrání rozhraní. Tato metoda nastaví `pToolTip` k `NULL` před vrátí.  
  
##  <a name="settooltipparams"></a>CTooltipManager::SetTooltipParams  
 Přizpůsobení vzhledu ovládacího prvku tooltip pro zadané typy ovládacích prvků Windows.  
  
```  
void SetTooltipParams(
    UINT nTypes,  
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),  
    CMFCToolTipInfo* pParams=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nTypes`  
 Určuje typy ovládacích prvků.  
  
 [v]`pRTC`  
 Modul runtime třída vlastní popisek.  
  
 [v]`pParams`  
 Popisek parametry.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví runtime třídy a počátečních parametrů, [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) používá při vytváření popisů tlačítek. Při volání ovládacího prvku [CTooltipManager::CreateToolTip](#createtooltip) a předává ve formě popisu tlačítka typ, který je jeden z typů indikován `nTypes`, popisek správce vytvoří ovládacího prvku popisek, který je instanci zadané třídy modulu runtime podle `pRTC` a předává parametry určeného `pParams` pro nový popis.  
  
 Pokud tuto metodu lze volat, všechny existující popisek vlastníky, zobrazí se zpráva AFX_WM_UPDATETOOLTIPS a jejich popisy tlačítek se musíte znovu vytvořit pomocí [CTooltipManager::CreateToolTip](#createtooltip).  
  
 `nTypes`může být libovolnou kombinací platný popisek typy, [CTooltipManager::CreateToolTip](#createtooltip) používá, nebo může být AFX_TOOLTIP_TYPE_ALL. Pokud předáte AFX_TOOLTIP_TYPE_ALL, všechny typy popisek je zasaženo.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `SetTooltipParams` metodu `CTooltipManager` třídy. Tento fragment kódu je součástí [Ukázka kreslení klienta](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]  
  
##  <a name="settooltiptext"></a>CTooltipManager::SetTooltipText  
 Nastaví text a popis pro popisek.  
  
```  
static void SetTooltipText(
    TOOLINFO* pTI,  
    CToolTipCtrl* pToolTip,  
    UINT nType,  
    const CString strText,  
    LPCTSTR lpszDescr=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pTI`  
 Ukazatel na objekt TOOLINFO.  
  
 [ve out]`pToolTip`  
 Ukazatel na ovládací prvek popis tlačítka pro kterou chcete nastavit text a popis.  
  
 [v]`nType`  
 Určuje typ ovládacího prvku, ke kterému je přiřazeno toto popisku.  
  
 [v]`strText`  
 Text, který chcete nastavit jako text popisku.  
  
 [v]`lpszDescr`  
 Ukazatel na popis popisku. Může být `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota `nType` musí být stejná hodnota jako `nType` parametr [CTooltipManager::CreateToolTip](#createtooltip) při vytvoření popisek.  
  
##  <a name="updatetooltips"></a>CTooltipManager::UpdateTooltips  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void UpdateTooltips();
```  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolTipCtrl – třída](../../mfc/reference/cmfctooltipctrl-class.md)   
 [CMFCToolTipInfo – třída](../../mfc/reference/cmfctooltipinfo-class.md)
