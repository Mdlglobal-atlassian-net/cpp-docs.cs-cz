---
title: "Třída CMouseManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
dev_langs: C++
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f50b74731089346a9675b5340ba0ea1a0b2879f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmousemanager-class"></a>CMouseManager – třída
Uživatel může přidružit jiné příkazy na konkrétní [CView](../../mfc/reference/cview-class.md) objektu při poklepání uvnitř tohoto zobrazení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMouseManager : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMouseManager::AddView](#addview)|Přidá `CView` do objektu **přizpůsobení** dialogové okno. **Přizpůsobení** dialogové okno umožňuje uživatelům přidružit příkaz dvakrát klikněte na soubor pro každou z uvedených zobrazení.|  
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Vrátí příkaz, který se spustí při poklepání uvnitř zadané zobrazení.|  
|[CMouseManager::GetViewIconId](#getviewiconid)|Vrátí ikony přidružené k ID zadané zobrazení.|  
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Vrátí ID zobrazení, které jsou přidružené k názvu zadané zobrazení.|  
|[CMouseManager::GetViewNames](#getviewnames)|Načte seznam všech názvů přidané zobrazení.|  
|[CMouseManager::LoadState](#loadstate)|Načítání `CMouseManager` stavu z registru systému Windows.|  
|[CMouseManager::SaveState](#savestate)|Zapíše `CMouseManager` stavu do registru systému Windows.|  
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Přidruží zadané příkaz a zadané zobrazení.|  
  
## <a name="remarks"></a>Poznámky  
 `CMouseManager` Třída udržuje kolekci `CView` objekty. Každé zobrazení je identifikován podle názvu a podle ID. Tato zobrazení se zobrazují v **přizpůsobení** dialogové okno. Uživatel může změnit příkaz, který je přidružen ke žádné zobrazení prostřednictvím **přizpůsobení** dialogové okno. Přidružený příkaz se spustí při poklepání v tomto zobrazení. Pro podporu tohoto z hlediska kódování, je nutné zpracovat `WM_LBUTTONDBLCLK` zprávu a volání [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) funkce v kódu pro tento `CView` objektu...  
  
 Byste je neměli vytvářet `CMouseManager` objekt ručně. Vytvoří se rámcem vaší aplikace. Ho bude také být zničený, automaticky při ukončení aplikace uživatelem. Chcete-li získat ukazatel myši správci pro vaši aplikaci, volejte [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMouseManager`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmousemanager.h  
  
##  <a name="addview"></a>CMouseManager::AddView  
 Zaregistruje [CView](../../mfc/reference/cview-class.md) objektu s [CMouseManager třída](../../mfc/reference/cmousemanager-class.md) pro podporu vlastních myši chování.  
  
```  
BOOL AddView(
    int iViewId,  
    UINT uiViewNameResId,  
    UINT uiIconId = 0);

 
BOOL AddView(
    int iId,  
    LPCTSTR lpszViewName,  
    UINT uiIconId = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iViewId`  
 ID zobrazení.  
  
 [v]`uiViewNameResId`  
 ID prostředku řetězec, který odkazuje na název zobrazení.  
  
 [v]`uiIconId`  
 Ikona ID zobrazení  
  
 [v]`iId`  
 ID zobrazení.  
  
 [v]`lpszViewName`  
 Název zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Za účelem podpory chování vlastní myši, musí být registrovaný zobrazení pomocí `CMouseManager` objektu. Jakýkoli objekt odvozené z `CView` třídy lze registrovat pomocí myši správce. Řetězec a ikony přidružené zobrazení se zobrazují v **myši** kartě **přizpůsobit** dialogové okno.  
  
 Je zodpovědností programátory k vytváření a údržbě zobrazení ID, jako `iViewId` a `iId`.  
  
 Další informace o tom, jak poskytnout vlastní myši chování najdete v tématu [přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst ukazatel na `CMouseManager` objekt pomocí `CWinAppEx::GetMouseManager` metoda a `AddView` metoda v `CMouseManager` – třída. Tento fragment kódu je součástí [vzorek sběru stavu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]  
  
##  <a name="getviewdblclickcommand"></a>CMouseManager::GetViewDblClickCommand  
 Vrátí příkaz, který se spustí při poklepání uvnitř zadané zobrazení.  
  
```  
UINT GetViewDblClickCommand(int iId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iId`  
 ID zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor příkazu, pokud je zobrazení přidružený příkaz; jinak 0.  
  
##  <a name="getviewiconid"></a>CMouseManager::GetViewIconId  
 Načte ikonu spojené s ID zobrazení.  
  
```  
UINT GetViewIconId(int iViewId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iViewId`  
 ID zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor prostředku ikony v případě úspěšného; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se nezdaří, pokud zobrazení není nejprve zaregistrovat pomocí [CMouseManager::AddView](#addview).  
  
##  <a name="getviewidbyname"></a>CMouseManager::GetViewIdByName  
 Načte ID zobrazení související s názvem zobrazení.  
  
```  
int GetViewIdByName(LPCTSTR lpszName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszName`  
 Název zobrazení.  
  
### <a name="return-value"></a>Návratová hodnota  
 ID zobrazení v případě úspěšného; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyhledá prostřednictvím zobrazení registrovaný pomocí [CMouseManager::AddView](#addview).  
  
##  <a name="getviewnames"></a>CMouseManager::GetViewNames  
 Načte seznam všech názvů registrované zobrazení.  
  
```  
void GetViewNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`listOfNames`  
 Odkaz na `CStringList` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda doplní parametr `listOfNames` s názvy všech zobrazení registrovaný pomocí [CMouseManager::AddView](#addview).  
  
##  <a name="loadstate"></a>CMouseManager::LoadState  
 Načte stav [CMouseManager třída](../../mfc/reference/cmousemanager-class.md) z registru.  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Cesta klíče registru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Informace o stavu, který je načten z registru zahrnuje registrované zobrazení, zobrazit identifikátory a přidružené příkazy. Pokud parametr `lpszProfileName` je `NULL`, načte tato funkce `CMouseManager` data z umístění v registru výchozí řízené [CWinAppEx Class](../../mfc/reference/cwinappex-class.md).  
  
 Ve většině případů nemáte přímo volání této funkce. Je volána jako součást procesu inicializace pracovního prostoru. Další informace o procesu inicializace pracovního prostoru najdete v tématu [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).  
  
##  <a name="savestate"></a>CMouseManager::SaveState  
 Zapíše stav [CMouseManager třída](../../mfc/reference/cmousemanager-class.md) do registru.  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Cesta klíče registru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Informace o stavu zapsat do registru zahrnuje všechny registrované zobrazení, zobrazit identifikátory a přidružené příkazy. Pokud parametr `lpszProfileName` je `NULL`, zapisuje tato funkce `CMouseManager` data do výchozího umístění registru řízené [CWinAppEx Class](../../mfc/reference/cwinappex-class.md).  
  
 Ve většině případů nemáte přímo volání této funkce. Je volána v rámci procesu serializace pracovního prostoru. Další informace o procesu serializace prostoru najdete v tématu [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).  
  
##  <a name="setcommandfordblclk"></a>CMouseManager::SetCommandForDblClk  
 Přidruží vlastního příkazu zobrazení, které je nejprve zaregistrovat pomocí myši správce.  
  
```  
void SetCommandForDblClk(
    int iViewId,  
    UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iViewId`  
 Identifikátor zobrazení.  
  
 [v]`uiCmd`  
 Identifikátor příkazu.  
  
### <a name="remarks"></a>Poznámky  
 Aby bylo možné přidružit vlastního příkazu k zobrazení, je nutné nejprve zaregistrovat zobrazení pomocí [CMouseManager::AddView](#addview). `AddView` Metoda vyžaduje identifikátor zobrazení jako vstupní parametr. Jakmile si zaregistrujete zobrazení, můžete volat `CMouseManager::SetCommandForDblClk` s stejné zobrazení identifikátor vstupní parametr, který jste zadali do `AddView`. Při poklepání myši v registrovaných zobrazení, následně bude aplikace spustit příkaz indikován `uiCmd.` pro podporu chování vlastní myš, budete také muset přizpůsobit zobrazení zaregistrována správce myši. Další informace o chování vlastní myši, najdete v části [přizpůsobení klávesnice a myši]--brokenlink--(.. / myši a klávesnice customization.md).  
  
 Pokud `uiCmd` je nastaven na hodnotu 0, zadané zobrazení je už přidružený příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)   
 [Přizpůsobení klávesnice a myši](../../mfc/keyboard-and-mouse-customization.md)



