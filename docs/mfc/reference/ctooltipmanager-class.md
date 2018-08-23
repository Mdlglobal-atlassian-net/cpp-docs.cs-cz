---
title: Ctooltipmanager – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
dev_langs:
- C++
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9de39d2054f3c75e00e8827ebb4aaefac9970d59
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465766"
---
# <a name="ctooltipmanager-class"></a>Ctooltipmanager – třída
Udržuje běhové informace o popiscích. `CTooltipManager` Třída je instance jednou za každou aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CTooltipManager : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CTooltipManager::CreateToolTip](#createtooltip)|Vytvoří ovládací prvek tooltip pro zadaný ovládací prvek typy Windows.|  
|[CTooltipManager::DeleteToolTip](#deletetooltip)|Odstraní ovládací prvek tooltip.|  
|[CTooltipManager::SetTooltipParams](#settooltipparams)|Přizpůsobí vzhled ovládacího prvku tooltip pro zadaný ovládací prvek typy Windows.|  
|[CTooltipManager::SetTooltipText](#settooltiptext)|Nastaví text a popis pro ovládací prvek tooltip.|  
|[CTooltipManager::UpdateTooltips](#updatetooltips)||  
  
## <a name="remarks"></a>Poznámky  
 Použití [cmfctooltipctrl – třída](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, a `CTooltipManager` společně k implementaci vlastní popisy ve vaší aplikaci. Příklad použití těchto tříd popisu tlačítka, najdete v článku [cmfctooltipctrl – třída](../../mfc/reference/cmfctooltipctrl-class.md) tématu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Ctooltipmanager –](../../mfc/reference/ctooltipmanager-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtooltipmanager.h  
  
##  <a name="createtooltip"></a>  CTooltipManager::CreateToolTip  
 Vytvoří ovládací prvek tooltip.  
  
```  
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,  
    CWnd* pWndParent,  
    UINT nType);
```  
  
### <a name="parameters"></a>Parametry  
 [out] *pToolTip*  
 Odkaz na ukazatel na popisek. Je nastaven tak, aby odkazoval na nově vytvořený popisek, když funkce vrátí.  
  
 [in] *pWndParent*  
 Nadřazený popisek.  
  
 [in] *nTyp*  
 Typ ovládacího prvku tooltip.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud popisek byl úspěšně vytvořen.  
  
### <a name="remarks"></a>Poznámky  
 Je nutné volat [CTooltipManager::DeleteToolTip](#deletetooltip) odstranit ToolTip – ovládací prvek, který je předán zpět do *pToolTip*.  
  
 [Ctooltipmanager –](../../mfc/reference/ctooltipmanager-class.md) Nastaví zobrazení vizuálu parametry každý popisek vytvoří podle popisu typ, který *nTyp* určuje. Chcete-li změnit parametry pro jeden nebo více typů popisu tlačítka, zavolejte [CTooltipManager::SetTooltipParams](#settooltipparams).  
  
 Neplatný popis typy jsou uvedeny v následující tabulce:  
  
|Popis typu|Kategorie ovládacího prvku|Vzorové typy|  
|------------------|----------------------|-------------------|  
|AFX_TOOLTIP_TYPE_BUTTON|Tlačítko.|Cmfcbutton –|  
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Záhlaví.|CMFCCaptionBar –|  
|AFX_TOOLTIP_TYPE_DEFAULT|Libovolný ovládací prvek, který není vhodná pro jinou kategorii.|Žádné|  
|AFX_TOOLTIP_TYPE_DOCKBAR|Ukotvit panel.|CDockablePane –|  
|AFX_TOOLTIP_TYPE_EDIT|Textové pole.|Žádné|  
|AFX_TOOLTIP_TYPE_MINIFRAME|Miniframe.|Cpaneframewnd –|  
|AFX_TOOLTIP_TYPE_PLANNER|Plánovač.|Žádné|  
|AFX_TOOLTIP_TYPE_RIBBON|Panel pásu karet.|CMFCRibbonBar cmfcribbonpanelmenubar –|  
|AFX_TOOLTIP_TYPE_TAB|Ovládací prvek karty.|Cmfctabctrl –|  
|AFX_TOOLTIP_TYPE_TOOLBAR|Panel nástrojů.|Cmfctoolbar – cmfcpopupmenubar –|  
|AFX_TOOLTIP_TYPE_TOOLBOX|Panelu nástrojů.|Žádné|  
  
##  <a name="deletetooltip"></a>  CTooltipManager::DeleteToolTip  
 Odstraní ovládací prvek tooltip.  
  
```  
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```  
  
### <a name="parameters"></a>Parametry  
 [out v] *pToolTip*  
 Odkaz na ukazatel na popisek, který se má zničit.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu volat pro každou [ctooltipctrl – třída](../../mfc/reference/ctooltipctrl-class.md) , který vytvořil [CTooltipManager::CreateToolTip](#createtooltip). Nadřazený ovládací prvek by měly volat tuto metodu z jeho `OnDestroy` obslužné rutiny. To je nutné správně odebrat popisek z rozhraní framework. Tato metoda nastaví *pToolTip* na hodnotu NULL, před jeho vrácením.  
  
##  <a name="settooltipparams"></a>  CTooltipManager::SetTooltipParams  
 Přizpůsobení vzhledu ovládacího prvku popisu tlačítka pro zadané typy ovládacích prvků Windows.  
  
```  
void SetTooltipParams(
    UINT nTypes,  
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),  
    CMFCToolTipInfo* pParams=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nTypes*  
 Určuje typy ovládacích prvků.  
  
 [in] *pRTC*  
 Modul runtime třídy vlastní popisek.  
  
 [in] *pParams*  
 Popisek parametrů.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví třídy modulu runtime a počáteční parametry, které [ctooltipmanager –](../../mfc/reference/ctooltipmanager-class.md) používá při vytváření popisů tlačítek. Když ovládacího prvku volá [CTooltipManager::CreateToolTip](#createtooltip) a předá v popisku typ, který je jedním z typů indikován *nTypes*, vytvoří správce popisku ToolTip – ovládací prvek, který je instancí modul runtime třída určená typem *pRTC* a předává parametry určené *pParams* na nový popisek.  
  
 Při volání této metody, všichni stávající vlastníci popisek AFX_WM_UPDATETOOLTIPS zpráva a uživatel bude muset znovu vytvořit jejich popisy tlačítek s použitím [CTooltipManager::CreateToolTip](#createtooltip).  
  
 *nTypes* může být libovolnou kombinací platný popis typy, které [CTooltipManager::CreateToolTip](#createtooltip) používá nebo to může být AFX_TOOLTIP_TYPE_ALL. Pokud předáte AFX_TOOLTIP_TYPE_ALL, ovlivníte všechny typy popisu tlačítka.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `SetTooltipParams` metodu `CTooltipManager` třídy. Tento fragment kódu je součástí [nakreslit Client sample](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]  
  
##  <a name="settooltiptext"></a>  CTooltipManager::SetTooltipText  
 Nastaví text a popis pro popis.  
  
```  
static void SetTooltipText(
    TOOLINFO* pTI,  
    CToolTipCtrl* pToolTip,  
    UINT nType,  
    const CString strText,  
    LPCTSTR lpszDescr=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pTI*  
 Ukazatel na objekt TOOLINFO.  
  
 [out v] *pToolTip*  
 Ukazatel na ovládací prvek tooltip, pro kterou chcete nastavit text a popis.  
  
 [in] *nTyp*  
 Určuje typ ovládacího prvku, ke kterému je přidružené tento popisek.  
  
 [in] *strText*  
 Text, který nastavíte jako text popisku.  
  
 [in] *lpszDescr*  
 Ukazatel na popis popisku. Může mít hodnotu NULL.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota *nTyp* musí mít stejnou hodnotu jako *nTyp* parametr [CTooltipManager::CreateToolTip](#createtooltip) při vytváření popisek.  
  
##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips  
 Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.  
  
```  
void UpdateTooltips();
```  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [Cmfctooltipctrl – třída](../../mfc/reference/cmfctooltipctrl-class.md)   
 [CMFCToolTipInfo – třída](../../mfc/reference/cmfctooltipinfo-class.md)
