---
title: "Třída CUserToolsManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CUserToolsManager
- AFXUSERTOOLSMANAGER/CUserToolsManager::CreateNewTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::FindTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetArgumentsMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetFilter
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetInitialDirMenuID
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetMaxTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetToolsEntryCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::GetUserTools
- AFXUSERTOOLSMANAGER/CUserToolsManager::InvokeTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::IsUserToolCmd
- AFXUSERTOOLSMANAGER/CUserToolsManager::LoadState
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolDown
- AFXUSERTOOLSMANAGER/CUserToolsManager::MoveToolUp
- AFXUSERTOOLSMANAGER/CUserToolsManager::RemoveTool
- AFXUSERTOOLSMANAGER/CUserToolsManager::SaveState
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetDefExt
- AFXUSERTOOLSMANAGER/CUserToolsManager::SetFilter
dev_langs: C++
helpviewer_keywords:
- CUserToolsManager [MFC], CUserToolsManager
- CUserToolsManager [MFC], CreateNewTool
- CUserToolsManager [MFC], FindTool
- CUserToolsManager [MFC], GetArgumentsMenuID
- CUserToolsManager [MFC], GetDefExt
- CUserToolsManager [MFC], GetFilter
- CUserToolsManager [MFC], GetInitialDirMenuID
- CUserToolsManager [MFC], GetMaxTools
- CUserToolsManager [MFC], GetToolsEntryCmd
- CUserToolsManager [MFC], GetUserTools
- CUserToolsManager [MFC], InvokeTool
- CUserToolsManager [MFC], IsUserToolCmd
- CUserToolsManager [MFC], LoadState
- CUserToolsManager [MFC], MoveToolDown
- CUserToolsManager [MFC], MoveToolUp
- CUserToolsManager [MFC], RemoveTool
- CUserToolsManager [MFC], SaveState
- CUserToolsManager [MFC], SetDefExt
- CUserToolsManager [MFC], SetFilter
ms.assetid: bdfa37ae-efca-4616-abb5-9d0dcd2d335b
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 520e6ae9aebdc35c07acac3f99c16be393f79e74
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cusertoolsmanager-class"></a>CUserToolsManager – třída
Udržuje kolekci [CUserTool třída](../../mfc/reference/cusertool-class.md) objekty v aplikaci. Nástroj pro uživatele je položku nabídky, který spouští externí aplikací. `CUserToolsManager` Objektu umožňuje uživateli nebo vývojáři přidat nové uživatele nástroje k aplikaci. Podporuje provádění příkazů související nástroje pro uživatele, a také ukládá informace o nástrojích uživatele do registru systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CUserToolsManager : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CUserToolsManager::CUserToolsManager](#cusertoolsmanager)|Vytvoří `CUserToolsManager`.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CUserToolsManager::CreateNewTool](#createnewtool)|Vytvoří nového uživatele nástroje.|  
|[CUserToolsManager::FindTool](#findtool)|Vrátí ukazatele myši `CMFCUserTool` objekt, který je přidružen ID zadaného příkazu.|  
|[CUserToolsManager::GetArgumentsMenuID](#getargumentsmenuid)|Vrátí ID prostředku, který je spojen s **argumenty** nabídce **nástroje** kartě **přizpůsobit** dialogové okno.|  
|[CUserToolsManager::GetDefExt](#getdefext)|Vrátí výchozí rozšíření, která **otevřít soubor** dialogové okno ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) používá v **příkaz** na **nástroje** kartě **Přizpůsobit** dialogové okno.|  
|[CUserToolsManager::GetFilter](#getfilter)|Vrací filtr souborů, které **otevřít soubor** dialogové okno ( [CFileDialog třída](../../mfc/reference/cfiledialog-class.md)) používá v **příkaz** na **nástroje** kartě **Přizpůsobit** dialogové okno.|  
|[CUserToolsManager::GetInitialDirMenuID](#getinitialdirmenuid)|Vrátí ID prostředku, který je přidružený **directory počáteční** nabídce **nástroje** kartě **přizpůsobit** dialogové okno.|  
|[CUserToolsManager::GetMaxTools](#getmaxtools)|Vrátí maximální počet uživatelů nástroje, které mohou být přiděleny v aplikaci.|  
|[CUserToolsManager::GetToolsEntryCmd](#gettoolsentrycmd)|Vrátí ID příkazu, který zástupného textu položky nabídky pro uživatele nástroje.|  
|[CUserToolsManager::GetUserTools](#getusertools)|Vrátí odkaz na seznam nástrojů uživatele.|  
|[CUserToolsManager::InvokeTool](#invoketool)|Spustí aplikaci přidruženou k nástroji uživatele, který má zadaný příkaz ID.|  
|[CUserToolsManager::IsUserToolCmd](#isusertoolcmd)|Určuje, zda je přidružena k nástroji uživatelské ID příkazu.|  
|[CUserToolsManager::LoadState](#loadstate)|Načte informace o nástrojích uživatele z registru systému Windows.|  
|[CUserToolsManager::MoveToolDown](#movetooldown)|Přesune nástroj pro zadaného uživatele v seznamu uživatelů nástrojů dolů.|  
|[CUserToolsManager::MoveToolUp](#movetoolup)|Přesune nástroj pro zadaného uživatele v seznamu uživatelů nástrojů nahoru.|  
|[CUserToolsManager::RemoveTool](#removetool)|Nástroj pro zadaného uživatele se odebere z aplikace.|  
|[CUserToolsManager::SaveState](#savestate)|Ukládá informace o nástrojích uživatele v registru systému Windows.|  
|[CUserToolsManager::SetDefExt](#setdefext)|Určuje výchozí příponu, **otevřít soubor** dialogové okno ( [CFileDialog třída](../../mfc/reference/cfiledialog-class.md)) používá v **příkaz** na **nástroje** karta z **přizpůsobit** dialogové okno.|  
|[CUserToolsManager::SetFilter](#setfilter)|Určuje soubor filtru, který **otevřít soubor** dialogové okno ( [CFileDialog třída](../../mfc/reference/cfiledialog-class.md)) používá v **příkaz** na **nástroje** kartě **Přizpůsobit** dialogové okno.|  
  
## <a name="remarks"></a>Poznámky  
 Do aplikace zahrnout nástroje pro uživatele, musíte:  
  
 1. Rezervujte položku nabídky a přidružený příkaz ID pro položku nabídky Nástroje uživatele.  
  
 2. Rezervujte ID sekvenční příkazu pro každého uživatele nástroj, který můžete definovat uživatele ve vaší aplikaci.  
  
 3. Volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) metoda a zadejte následující parametry: nabídky ID příkazu, první nástroj příkaz ID uživatele a ID poslední uživatele nástroj příkazu.  
  
 Měla by existovat pouze jedna globální `CUserToolsManager` objektu na aplikaci.  
  
 Příklad nástrojů pro uživatele naleznete v části VisualStudioDemo ukázkový projekt.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst odkaz na `CUserToolsManager` objekt a postup vytvoření nových nástrojů uživatele. Tento fragment kódu je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#38](../../mfc/codesnippet/cpp/cusertoolsmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CUserToolsManager`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxusertoolsmanager.h  
  
##  <a name="createnewtool"></a>CUserToolsManager::CreateNewTool  
 Vytvoří nového uživatele nástroje.  
  
```  
CUserTool* CreateNewTool();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nástroj nově vytvořeného uživatele nebo `NULL` překračování maximální počet uživatelů nástroje. Typ vrácený je stejný jako typ, který je předán `CWinAppEx::EnableUserTools` jako `pToolRTC` parametr.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyhledá první ID příkazu nabídky k dispozici v rozsahu, který je zadaný ve volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) a přiřadí nástroj pro uživatele mu ID této.  
  
 Metoda selže, pokud počet nástroje byl dosažen maximální počet. K tomu dochází, když uživatel nástroje jsou přiřazeny všechny identifikátory příkazů v rozsahu. Maximální počet nástrojů můžete načíst pomocí volání [CUserToolsManager::GetMaxTools](#getmaxtools). Můžete získat přístup k seznamu nástroje voláním [CUserToolsManager::GetUserTools](#getusertools) metoda.  
  
##  <a name="cusertoolsmanager"></a>CUserToolsManager::CUserToolsManager  
 Vytvoří `CUserToolsManager`. Každá aplikace musí mít maximálně jeden správce nástrojů uživatelů.  
  
```  
CUserToolsManager();

 
CUserToolsManager(
    const UINT uiCmdToolsDummy,  
    const UINT uiCmdFirst,  
    const UINT uiCmdLast,  
    CRuntimeClass* pToolRTC=RUNTIME_CLASS(CUserTool),  
    UINT uArgMenuID=0,  
    UINT uInitDirMenuID=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmdToolsDummy`  
 Celé číslo bez znaménka, který rozhraní používá jako zástupný symbol pro ID příkazu v nabídce Nástroje pro uživatele.  
  
 [v]`uiCmdFirst`  
 ID příkazu pro příkaz první nástroj uživatele.  
  
 [v]`uiCmdLast`  
 ID příkazu pro příkaz poslední nástroj uživatele.  
  
 [v]`pToolRTC`  
 Třída, [CUserToolsManager::CreateNewTool](#createnewtool) vytvoří. Pomocí této třídy lze použít odvozené typ [CUserTool třída](../../mfc/reference/cusertool-class.md) místo výchozí implementace.  
  
 [v]`uArgMenuID`  
 ID prostředku nabídky argumenty místní nabídky.  
  
 [v]`uInitDirMenuID`  
 ID prostředku nabídky Počáteční adresář místní nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Nevolejte tento konstruktor. Místo toho volat [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) povolit uživatele nástroje a volání [CWinAppEx::GetUserToolsManager](../../mfc/reference/cwinappex-class.md#getusertoolsmanager) k získání ukazatele na `CUserToolsManager`. Další informace najdete v tématu [uživatelem definované nástroje](../../mfc/user-defined-tools.md).  
  
##  <a name="findtool"></a>CUserToolsManager::FindTool  
 Vrátí má ukazatel na [CUserTool třída](../../mfc/reference/cusertool-class.md) objekt, který je přidružen ID zadaného příkazu.  
  
```  
CUserTool* FindTool(UINT uiCmdId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmdId`  
 Identifikátor příkazu nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na [CUserTool třída](../../mfc/reference/cusertool-class.md) nebo `CUserTool`-odvozené objektu, pokud úspěch; v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Když `FindTool` je úspěšné, typ vrácený je, stejný jako typ `pToolRTC` parametru [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).  
  
##  <a name="getargumentsmenuid"></a>CUserToolsManager::GetArgumentsMenuID  
 Vrátí ID prostředku, který je spojen s **argumenty** nabídce **nástroje** kartě **přizpůsobit** dialogové okno.  
  
```  
UINT GetArgumentsMenuID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor prostředku nabídky.  
  
### <a name="remarks"></a>Poznámky  
 `uArgMenuID` Parametr [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) Určuje ID prostředku.  
  
##  <a name="getdefext"></a>CUserToolsManager::GetDefExt  
 Vrátí výchozí rozšíření, která **otevřít soubor** dialogové okno ( [CFileDialog](../../mfc/reference/cfiledialog-class.md#cfiledialog)) používá v **příkaz** na **nástroje** kartě **Přizpůsobit** dialogové okno.  
  
```  
const CString& GetDefExt() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `CString` objekt, který obsahuje rozšíření.  
  
##  <a name="getfilter"></a>CUserToolsManager::GetFilter  
 Vrací filtr souborů, které **otevřít soubor** dialogové okno ( [CFileDialog třída](../../mfc/reference/cfiledialog-class.md)) používá v **příkaz** na **nástroje** kartě **Přizpůsobit** dialogové okno.  
  
```  
const CString& GetFilter() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `CString` objekt, který obsahuje filtru.  
  
##  <a name="getinitialdirmenuid"></a>CUserToolsManager::GetInitialDirMenuID  
 Vrátí ID prostředku, který je přidružený **directory počáteční** nabídce **nástroje** kartě **přizpůsobit** dialogové okno.  
  
```  
UINT GetInitialDirMenuID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor prostředku nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Vrácený ID je uveden v `uInitDirMenuID` parametr [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).  
  
##  <a name="getmaxtools"></a>CUserToolsManager::GetMaxTools  
 Vrátí maximální počet uživatelů nástroje, které mohou být přiděleny v aplikaci.  
  
```  
int GetMaxTools() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální počet uživatelů nástroje, které mohou být přiděleny.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu za účelem načtení maximální počet nástroje, které mohou být přiděleny v aplikaci. Toto číslo je číslo v rozsahu od ID `uiCmdFirst` prostřednictvím `uiCmdLast` parametry, které můžete předat [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools).  
  
##  <a name="gettoolsentrycmd"></a>CUserToolsManager::GetToolsEntryCmd  
 Vrátí ID příkazu, který zástupného textu položky nabídky pro uživatele nástroje.  
  
```  
UINT GetToolsEntryCmd() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 ID příkazu zástupného textu.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li povolit nástroje pro uživatele, zavolejte [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools). `uiCmdToolsDummy` Parametr určuje ID příkazu, který položka příkazu nástroje. Tato metoda vrátí ID nástroje položka příkazu. Bez ohledu na toto ID se používá v nabídce, nahrazuje seznam nástrojů uživatele po zobrazení nabídky.  
  
##  <a name="getusertools"></a>CUserToolsManager::GetUserTools  
 Vrátí odkaz na seznam nástrojů uživatele.  
  
```  
const CObList& GetUserTools() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Const odkaz na [CObList třída](../../mfc/reference/coblist-class.md) objekt, který obsahuje seznam nástrojů pro uživatele.  
  
### <a name="remarks"></a>Poznámky  
 Volání nástrojů pro tuto metodu za účelem načtení seznamu uživatele, který [CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md) udržuje objektu. Nástroj pro každého uživatele je reprezentována objekt typu [CUserTool třída](../../mfc/reference/cusertool-class.md) nebo typ odvozený z `CUserTool`. Typ je zadána `pToolRTC` parametr při volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) k povolení nástrojů uživatele.  
  
##  <a name="invoketool"></a>CUserToolsManager::InvokeTool  
 Spustí aplikaci přidruženou k nástroji uživatele, který má zadaný příkaz ID.  
  
```  
BOOL InvokeTool(UINT uiCmdId);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmdId`  
 ID příkazu nabídky přidružené nástroj pro uživatele.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud příkaz spojené s nástrojem pro uživatele byla spuštěna úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání tuto metodu provést aplikace přidružené k uživateli nástroj, který má ID příkazu, který je určeného `uiCmdId`.  
  
##  <a name="isusertoolcmd"></a>CUserToolsManager::IsUserToolCmd  
 Určuje, zda je přidružena k nástroji uživatelské ID příkazu.  
  
```  
BOOL IsUserToolCmd(UINT uiCmdId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmdId`  
 ID příkazu položky nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud daný příkaz ID je přidružena k nástroji uživatele; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda ověří, zda ID daného příkazu, který je v rozsahu ID příkazu. Zadejte rozsah při volání [CWinAppEx::EnableUserTools](../../mfc/reference/cwinappex-class.md#enableusertools) k povolení nástrojů uživatele.  
  
##  <a name="loadstate"></a>CUserToolsManager::LoadState  
 Načte informace o nástrojích uživatele z registru systému Windows.  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Cesta klíče registru Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud stav byl načten úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda načte stav `CUserToolsManager` objekt z registru systému Windows.  
  
 Obvykle je tato metoda není volána přímo. [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate) nazve je jako součást procesu inicializace pracovního prostoru.  
  
##  <a name="movetooldown"></a>CUserToolsManager::MoveToolDown  
 Přesune nástroj pro zadaného uživatele v seznamu uživatelů nástrojů dolů.  
  
```  
BOOL MoveToolDown(CUserTool* pTool);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pTool`  
 Určuje nástroj uživatele přesunout.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud nástroj pro uživatele byla úspěšně; přesunout jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Metoda selže, pokud nástroj který `pTool` určuje není v seznamu interní nebo pokud tento nástroj je poslední v seznamu.  
  
##  <a name="movetoolup"></a>CUserToolsManager::MoveToolUp  
 Přesune nástroj pro zadaného uživatele v seznamu uživatelů nástrojů nahoru.  
  
```  
BOOL MoveToolUp(CUserTool* pTool);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pTool`  
 Určuje nástroj uživatele přesunout.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud nástroj pro uživatele byla úspěšně; přesunout nahoru jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Metoda selže, pokud nástroj který `pTool` parametr určuje není v seznamu interní nebo pokud tento nástroj je první nástroj položky v seznamu.  
  
##  <a name="removetool"></a>CUserToolsManager::RemoveTool  
 Nástroj pro zadaného uživatele se odebere z aplikace.  
  
```  
BOOL RemoveTool(CUserTool* pTool);
```  
  
### <a name="parameters"></a>Parametry  
 [ve out]`pTool`  
 Ukazatel na nástroj uživatele k odebrání.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud tento nástroj se úspěšně odebral. V opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tento nástroj je úspěšně odebrána, tato metoda odstraní `pTool`.  
  
##  <a name="savestate"></a>CUserToolsManager::SaveState  
 Ukládá informace o nástrojích uživatele v registru systému Windows.  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Cesta ke klíči registru systému Windows.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud byl úspěšně; uložen stav jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Metoda ukládá aktuální stav `CUserToolsManager` objekt v registru systému Windows.  
  
 Obvykle, není potřeba volat tuto metodu přímo, [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate) nazve je automaticky jako součást procesu serializace pracovní prostor aplikace.  
  
##  <a name="setdefext"></a>CUserToolsManager::SetDefExt  
 Určuje výchozí příponu, **otevřít soubor** dialogové okno ( [CFileDialog třída](../../mfc/reference/cfiledialog-class.md)) používá v **příkaz** na **nástroje** karta z **přizpůsobit** dialogové okno.  
  
```  
void SetDefExt(const CString& strDefExt);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`strDefExt`  
 Textový řetězec, který obsahuje výchozí příponu názvu souboru.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu za účelem zadejte příponu názvu souboru výchozí v **otevřít soubor** dialogové okno, které se zobrazí, když uživatel vybere aplikaci přidružit nástroj pro uživatele. Výchozí hodnota je "exe".  
  
##  <a name="setfilter"></a>CUserToolsManager::SetFilter  
 Určuje soubor filtru, který **otevřít soubor** dialogové okno ( [CFileDialog třída](../../mfc/reference/cfiledialog-class.md)) používá v **příkaz** na **nástroje** kartě **Přizpůsobit** dialogové okno.  
  
```  
void SetFilter(const CString& strFilter);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`strFilter`  
 Určuje filtr.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)   
 [CUserTool – třída](../../mfc/reference/cusertool-class.md)
