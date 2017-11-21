---
title: "Třída CContextMenuManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::CContextMenuManager
- AFXCONTEXTMENUMANAGER/CContextMenuManager::AddMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuById
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuByName
- AFXCONTEXTMENUMANAGER/CContextMenuManager::GetMenuNames
- AFXCONTEXTMENUMANAGER/CContextMenuManager::LoadState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ResetState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SaveState
- AFXCONTEXTMENUMANAGER/CContextMenuManager::SetDontCloseActiveMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::ShowPopupMenu
- AFXCONTEXTMENUMANAGER/CContextMenuManager::TrackPopupMenu
dev_langs: C++
helpviewer_keywords:
- CContextMenuManager [MFC], CContextMenuManager
- CContextMenuManager [MFC], AddMenu
- CContextMenuManager [MFC], GetMenuById
- CContextMenuManager [MFC], GetMenuByName
- CContextMenuManager [MFC], GetMenuNames
- CContextMenuManager [MFC], LoadState
- CContextMenuManager [MFC], ResetState
- CContextMenuManager [MFC], SaveState
- CContextMenuManager [MFC], SetDontCloseActiveMenu
- CContextMenuManager [MFC], ShowPopupMenu
- CContextMenuManager [MFC], TrackPopupMenu
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ceed1a7127d86ced1c68d92269a6b1a55f41991f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccontextmenumanager-class"></a>CContextMenuManager – třída
`CContextMenuManager` Objekt spravuje místní nabídky, také známé jako kontextové nabídky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CContextMenuManager : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CContextMenuManager::CContextMenuManager](#ccontextmenumanager)|Vytvoří `CContextMenuManager` objektu.|  
|`CContextMenuManager::~CContextMenuManager`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CContextMenuManager::AddMenu](#addmenu)|Přidá novou místní nabídky.|  
|[CContextMenuManager::GetMenuById](#getmenubyid)|Vrátí popisovač do nabídky přidružené k ID zadaného zdroje.|  
|[CContextMenuManager::GetMenuByName](#getmenubyname)|Vrátí popisovač v nabídce, která odpovídá názvu zadaný nabídky.|  
|[CContextMenuManager::GetMenuNames](#getmenunames)|Vrátí seznam hodnot názvy nabídek.|  
|[CContextMenuManager::LoadState](#loadstate)|Načte místní nabídky, které jsou uložené v registru systému Windows.|  
|[CContextMenuManager::ResetState](#resetstate)|Vymaže místní nabídky ze Správce kontextové nabídky.|  
|[CContextMenuManager::SaveState](#savestate)|Uloží místní nabídky do registru systému Windows.|  
|[CContextMenuManager::SetDontCloseActiveMenu](#setdontcloseactivemenu)|Ovládací prvky jestli `CContextMenuManager` zavře aktivní místní nabídky, když se zobrazí nový místní nabídky.|  
|[CContextMenuManager::ShowPopupMenu](#showpopupmenu)|Zobrazí zadané místní nabídky.|  
|[CContextMenuManager::TrackPopupMenu](#trackpopupmenu)|Zobrazí zadané místní nabídky. Vrátí index příkaz vybrané nabídky.|  
  
## <a name="remarks"></a>Poznámky  
 `CContextMenuManager`Spravuje místní nabídky a zajišťuje, že mají konzistentní vzhled.  
  
 Byste je neměli vytvářet `CContextMenuManager` objekt ručně. Vytvoří rozhraní vaší aplikace `CContextMenuManager` objektu. Nicméně, by měly volat [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) při inicializaci aplikace. Po inicializaci správce kontextu, použijte metodu [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager) k získání ukazatele na kontext správce pro vaši aplikaci.  
  
 Místní nabídky v době běhu může vytvořit voláním `AddMenu`. Pokud chcete zobrazit v nabídce bez první přijímající vstup uživatele, zavolejte `ShowPopupMenu`. `TrackPopupMenu`se používá, pokud chcete vytvořit nabídku a čekání na vstup uživatele. `TrackPopupMenu`Vrátí index vybraný příkaz nebo 0, pokud uživatel byl ukončen bez provedení výběru.  
  
 `CContextMenuManager` Můžete také uložit a načíst stav do registru systému Windows.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat nabídku `CContextMenuManager` objektu a jak není zavřít rozbalovací nabídce active při `CContextMenuManager` objekt zobrazuje nové místní nabídky. Tento fragment kódu je součástí [vlastní stránky ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/cpp/ccontextmenumanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CContextMenuManager`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcontextmenumanager.h  
  
##  <a name="addmenu"></a>CContextMenuManager::AddMenu  
 Přidá novou místní nabídky k [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).  
  
```  
BOOL AddMenu(
    UINT uiMenuNameResId,  
    UINT uiMenuResId);

 
BOOL AddMenu(
    LPCTSTR lpszName,  
    UINT uiMenuResId);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiMenuNameResId`  
 ID prostředku pro řetězec, který obsahuje název pro nové nabídky.  
  
 [v]`uiMenuResId`  
 ID nabídky prostředku.  
  
 [v]`lpszName`  
 Řetězec, který obsahuje název pro nové nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud metoda byla úspěšná. 0, pokud metoda selže.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda selže, pokud `uiMenuResId` je neplatný nebo pokud jiné nabídky se stejným názvem již probíhá `CContextMenuManager`.  
  
##  <a name="ccontextmenumanager"></a>CContextMenuManager::CContextMenuManager  
 Vytvoří [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) objektu.  
  
```  
CContextMenuManager();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve většině případů byste je neměli vytvářet `CContextMenuManager` ručně. Vytvoří rozhraní vaší aplikace `CContextMenuManager` objektu. By měly volat [CWinAppEx::InitContextMenuManager](../../mfc/reference/cwinappex-class.md#initcontextmenumanager) během inicializace aplikace. Chcete-li získání ukazatele na správce kontextu, volejte [CWinAppEx::GetContextMenuManager](../../mfc/reference/cwinappex-class.md#getcontextmenumanager).  
  
##  <a name="getmenubyid"></a>CContextMenuManager::GetMenuById  
 Vrátí popisovač do nabídky přidružené daného prostředku.  
  
```  
HMENU GetMenuById(UINT nMenuResId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`nMenuResId`  
 ID prostředku pro nabídce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro přidružené nabídky nebo `NULL` Pokud nebyl nalezen v nabídce.  
  
##  <a name="getmenubyname"></a>CContextMenuManager::GetMenuByName  
 Vrátí popisovač konkrétní nabídky.  
  
```  
HMENU GetMenuByName(
    LPCTSTR lpszName,  
    UINT* puiOrigResID = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszName`  
 Řetězec, který obsahuje název nabídky k načtení.  
  
 [out]`puiOrigResID`  
 Ukazatel na `UINT`. Tento parametr obsahuje ID prostředku zadaný nabídky, pokud nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro nabídky, název, který byl zadaný parametrem `lpszName`. `NULL`Pokud neexistuje žádné nabídky s názvem `lpszName`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato metoda vyhledá nabídky, která odpovídá `lpszName`, `GetMenuByName` ukládá ID prostředku nabídky v parametru `puiOrigResID`.  
  
##  <a name="getmenunames"></a>CContextMenuManager::GetMenuNames  
 Vrátí seznam názvů nabídky přidat do [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md).  
  
```  
void GetMenuNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`listOfNames`  
 Odkaz na [CStringList](../../mfc/reference/cstringlist-class.md) parametr. Tato metoda zapíše seznam názvů nabídky pro tento parametr.  
  
##  <a name="loadstate"></a>CContextMenuManager::LoadState  
 Načte informace o přidružené [CContextMenuManager třída](../../mfc/reference/ccontextmenumanager-class.md) z registru systému Windows.  
  
```  
virtual BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Řetězec, který obsahuje relativní cestu klíče registru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je metoda úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `lpszProfileName` Parametr není absolutní cesta pro položku registru. Je relativní cestu, která se přidá na konec výchozí klíč registru pro vaši aplikaci. Chcete-li získat nebo nastavit klíč registru výchozí, použijte metody [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) a [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) v uvedeném pořadí.  
  
 Pomocí této metody [CContextMenuManager::SaveState](#savestate) uložit místní nabídky do registru.  
  
##  <a name="resetstate"></a>CContextMenuManager::ResetState  
 Vymaže všechny položky z místní nabídky přidružené [CContextMenuManager třída](../../mfc/reference/ccontextmenumanager-class.md).  
  
```  
virtual BOOL ResetState();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je metoda úspěšná. `FALSE` Pokud dojde k chybě.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odstraní místní nabídky a odebere je ze `CContextMenuManager`.  
  
##  <a name="savestate"></a>CContextMenuManager::SaveState  
 Uloží informace o přidružené [CContextMenuManager třída](../../mfc/reference/ccontextmenumanager-class.md) do registru systému Windows.  
  
```  
virtual BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszProfileName`  
 Řetězec, který obsahuje relativní cestu klíče registru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je metoda úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `lpszProfileName` Parametr není absolutní cesta pro položku registru. Je relativní cestu, která se přidá na konec výchozí klíč registru pro vaši aplikaci. Chcete-li získat nebo nastavit klíč registru výchozí, použijte metody [CWinAppEx::GetRegistryBase](../../mfc/reference/cwinappex-class.md#getregistrybase) a [CWinAppEx::SetRegistryBase](../../mfc/reference/cwinappex-class.md#setregistrybase) v uvedeném pořadí.  
  
 Pomocí této metody [CContextMenuManager::LoadState](#loadstate) z registru načíst místní nabídky.  
  
##  <a name="setdontcloseactivemenu"></a>CContextMenuManager::SetDontCloseActiveMenu  
 Ovládací prvky jestli [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md) zavře active místní nabídky, když se zobrazí nový místní nabídky.  
  
```  
void SetDontCloseActiveMenu (BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bSet`  
 Parametr typu Boolean, který řídí, zda zavřete aktivní místní nabídky. Hodnota `TRUE` Určuje, v rozbalovací nabídce active není uzavřený. `FALSE`Označuje, že je uzavřené active místní nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení `CContextMenuManager` zavře aktivní místní nabídky.  
  
##  <a name="showpopupmenu"></a>CContextMenuManager::ShowPopupMenu  
 Zobrazí zadané místní nabídky.  
  
```  
virtual BOOL ShowPopupMenu(
    UINT uiMenuResId,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bOwnMessage = FALSE,  
    BOOL bRightAlign = FALSE);

 
virtual CMFCPopupMenu* ShowPopupMenu(
    HMENU hmenuPopup,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bOwnMessage = FALSE,  
    BOOL bAutoDestroy = TRUE,  
    BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiMenuResId`  
 ID prostředku v nabídce, která se zobrazí tato metoda.  
  
 [v]`x`  
 Vodorovný posun pro místní nabídky v souřadnicích klienta.  
  
 [v]`y`  
 Svislý posun pro místní nabídky v souřadnice klienta  
  
 [v]`pWndOwner`  
 Ukazatel do nadřazeného okna místní nabídky.  
  
 [v]`bOwnMessage`  
 Parametr typu Boolean, která určuje, jak se směrují zprávy. Pokud `bOwnMessage` je `FALSE`, standardní MFC směrování se používá. V opačném `pWndOwner` přijímá zprávy.  
  
 [v]`hmenuPopup`  
 Obslužná rutina nabídky, která se zobrazí tato metoda.  
  
 [v]`bAutoDestroy`  
 Parametr typu Boolean, která určuje, zda v nabídce budou automaticky zničena.  
  
 [v]`bRightAlign`  
 Parametr typu Boolean, která určuje způsob zarovnání položek nabídky. Pokud `bRightAlign` je `TRUE`, je v nabídce vpravo zarovnaný pro čtení zprava doleva pořadí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první přetížení metody nenulové hodnoty, pokud metoda zobrazuje v nabídce úspěšně; jinak 0. Druhý přetížení metody vrací ukazatel na [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) Pokud v místní nabídce zobrazí správně; v opačném případě `NULL`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda se podobá metodu [CContextMenuManager::TrackPopupMenu](#trackpopupmenu) v tom, že obě metody zobrazení místní nabídky. Ale `TrackPopupMenu` vrátí index příkaz vybrané nabídky.  
  
 Pokud parametr `bAutoDestroy` je `FALSE`, musíte nejprve ručně zavolat zděděné `DestroyMenu` metodu pro uvolnění paměťových prostředků. Výchozí implementaci `ShowPopupMenu` nepoužívá parametr `bAutoDestroy`. Je poskytována pro budoucí použití nebo pro vlastní třídy odvozené od třídy `CContextMenuManager` třídy.  
  
##  <a name="trackpopupmenu"></a>CContextMenuManager::TrackPopupMenu  
 Zobrazí zadané místní nabídky a vrátí index příkazu vybrané místní nabídky.  
  
```  
virtual UINT TrackPopupMenu(
    HMENU hmenuPopup,  
    int x,  
    int y,  
    CWnd* pWndOwner,  
    BOOL bRightAlign = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hmenuPopup`  
 Popisovač místní nabídky, která zobrazí tuto metodu.  
  
 [v]`x`  
 Vodorovný posun pro místní nabídky v souřadnicích klienta.  
  
 [v]`y`  
 Svislý posun pro místní nabídky v souřadnicích klienta.  
  
 [v]`pWndOwner`  
 Ukazatel do nadřazeného okna místní nabídky.  
  
 [v]`bRightAlign`  
 Parametr typu Boolean, která určuje způsob zarovnání položek nabídky. Pokud `bRightAlign` je `TRUE`, je v nabídce vpravo zarovnaný pro čtení zprava doleva pořadí. Pokud `bRightAlign` je `FALSE`, je v nabídce vlevo zarovnaný pro pořadí čtení zleva doprava.  
  
### <a name="return-value"></a>Návratová hodnota  
 ID příkazu nabídky příkazu, který uživatel vybere; 0, pokud uživatel nezavře bez výběru příkazu v nabídce místní nabídky.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda funguje jako modální volání zobrazení místní nabídky. Aplikace nebudou nadále následující řádek v kódu, dokud uživatel zavře místní nabídky nebo výběru příkazu. Alternativní metodu, můžete použít k zobrazení místní nabídky je [CContextMenuManager::ShowPopupMenu](#showpopupmenu). Tato metoda není modální volání a nevrátí ID vybraný příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)
