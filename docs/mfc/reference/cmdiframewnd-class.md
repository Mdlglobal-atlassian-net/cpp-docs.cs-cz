---
title: CMDIFrameWnd – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMDIFrameWnd
- AFXWIN/CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CMDIFrameWnd
- AFXWIN/CMDIFrameWnd::CreateClient
- AFXWIN/CMDIFrameWnd::CreateNewChild
- AFXWIN/CMDIFrameWnd::GetWindowMenuPopup
- AFXWIN/CMDIFrameWnd::MDIActivate
- AFXWIN/CMDIFrameWnd::MDICascade
- AFXWIN/CMDIFrameWnd::MDIGetActive
- AFXWIN/CMDIFrameWnd::MDIIconArrange
- AFXWIN/CMDIFrameWnd::MDIMaximize
- AFXWIN/CMDIFrameWnd::MDINext
- AFXWIN/CMDIFrameWnd::MDIPrev
- AFXWIN/CMDIFrameWnd::MDIRestore
- AFXWIN/CMDIFrameWnd::MDISetMenu
- AFXWIN/CMDIFrameWnd::MDITile
dev_langs:
- C++
helpviewer_keywords:
- CMDIFrameWnd [MFC], CMDIFrameWnd
- CMDIFrameWnd [MFC], CreateClient
- CMDIFrameWnd [MFC], CreateNewChild
- CMDIFrameWnd [MFC], GetWindowMenuPopup
- CMDIFrameWnd [MFC], MDIActivate
- CMDIFrameWnd [MFC], MDICascade
- CMDIFrameWnd [MFC], MDIGetActive
- CMDIFrameWnd [MFC], MDIIconArrange
- CMDIFrameWnd [MFC], MDIMaximize
- CMDIFrameWnd [MFC], MDINext
- CMDIFrameWnd [MFC], MDIPrev
- CMDIFrameWnd [MFC], MDIRestore
- CMDIFrameWnd [MFC], MDISetMenu
- CMDIFrameWnd [MFC], MDITile
ms.assetid: fa8736e6-511b-4c51-8b4d-eba78378aeb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a33158f438eaeaf6416540cdf7a03094ec3164d7
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336745"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd – třída
Poskytuje funkce Windows více dokumentů (MDI) rozhraní okna rámce spolu se členy pro správu okna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMDIFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|Vytvoří `CMDIFrameWnd`.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMDIFrameWnd::CreateClient](#createclient)|Vytvoří okno Windows MDICLIENT pro tento `CMDIFrameWnd`. Volá `OnCreate` členskou funkci `CWnd`.|  
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Vytvoří nové podřízené okno.|  
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Vrátí místní nabídka okna.|  
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Aktivuje různé podřízené okno MDI.|  
|[CMDIFrameWnd::MDICascade](#mdicascade)|Uspořádá všechna podřízená okna ve formátu kaskádových akcí.|  
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Načte aktuálně aktivní podřízené okno MDI, spolu s příznak označující, zda maximalizované podřízené.|  
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Uspořádá všech podřízených oken minimalizované dokumentu.|  
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maximalizuje podřízené okno MDI.|  
|[CMDIFrameWnd::MDINext](#mdinext)|Aktivuje podřízené okno bezprostředně za aktuálně aktivní podřízené okno a umístí aktuálně aktivní podřízené okno za všechny ostatní podřízená okna.|  
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Aktivuje předchozí podřízeného okna a umístí aktuálně aktivní podřízené okno bezprostředně za.|  
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Obnoví ze minimalizované nebo maximalizované velikost podřízené okno MDI.|  
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Nahradí v nabídce okna rámce MDI a místní nabídka okna.|  
|[CMDIFrameWnd::MDITile](#mditile)|Uspořádá všechna podřízená okna ve formátu vedle sebe.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li vytvořit okno rámce MDI užitečné pro vaši aplikaci, odvoďte třídu z `CMDIFrameWnd`. Přidání členské proměnné do odvozené třídy k ukládání dat, které jsou specifické pro vaši aplikaci. Implementujte popisovač zprávy členské funkce a napište zprávu, mapování v odvozené třídě k určení, co se stane, když zprávy jsou přesměrovány do okna.  
  
 Okna rámce MDI lze vytvořit voláním [vytvořit](../../mfc/reference/cframewnd-class.md#create) nebo [loadframe –](../../mfc/reference/cframewnd-class.md#loadframe) členskou funkci `CFrameWnd`.  
  
 Před voláním `Create` nebo `LoadFrame`, je nutné vytvořit objekt okna rámce na haldě pomocí jazyka C++ **nové** operátor. Před voláním `Create` budete taky moct registrovat třídu okna s [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) globální funkce nastavit ikonu a třída styly pro rámec.  
  
 Použití `Create` členskou funkci pro předání parametrů vytváření rámce jako okamžité argumenty.  
  
 `LoadFrame` vyžaduje méně argumentů než `Create`a místo toho načte většinu jeho výchozími hodnotami z prostředků, včetně titulek rámce, ikony, tabulky akcelerátorů a nabídky. Přístup k `LoadFrame`, tyto prostředky musí mít stejné ID prostředku (například IDR_MAINFRAME).  
  
 I když `MDIFrameWnd` je odvozen z `CFrameWnd`, okna rámce třídy odvozené z `CMDIFrameWnd` nemusí být deklarovaný s `DECLARE_DYNCREATE`.  
  
 `CMDIFrameWnd` Třída dědí velkou část jeho výchozí implementace ze `CFrameWnd`. Podrobný seznam těchto funkcí, najdete [CFrameWnd](../../mfc/reference/cframewnd-class.md) třídy popis. `CMDIFrameWnd` Třída má Tyhle další funkce:  
  
-   Spravuje okna rámce MDI okno MDICLIENT přemístění ve spojení s ovládací pruhy. Okno klienta MDI je přímou nadřazenou podřízených oken rámce MDI. WS_HSCROLL a WS_VSCROLL styly oken na `CMDIFrameWnd` platí pro okno klienta MDI namísto oknem hlavního rámce, takže uživatel může posunout oblasti klienta MDI (jako Windows manažer programu, například).  
  
-   Okna rámce MDI vlastní výchozí nabídka, která se používá jako nabídek, pokud neexistuje žádná aktivní podřízené okno MDI. Když je aktivní podřízený formulář MDI, panel nabídek okna rámce MDI automaticky nahrazena podřízené okno MDI.  
  
-   Okna rámce MDI funguje ve spojení s aktuální podřízené okno MDI, pokud existuje. Zprávy s příkazy jsou například delegovat na aktuálně aktivní podřízený formulář MDI před okna rámce MDI.  
  
-   Okna rámce MDI má výchozích obslužných rutin pro následující standardní příkazy nabídky okna:  
  
    - ID_WINDOW_TILE_VERT –  
  
    - ID_WINDOW_TILE_HORZ –  
  
    - ID_WINDOW_CASCADE –  
  
    - ID_WINDOW_ARRANGE –  
  
-   Okna rámce MDI má také implementace id_window_new –, který vytvoří nový snímek a zobrazení pro aktuální dokument. Aplikace můžete přepsat tyto výchozí implementace příkazu k přizpůsobení zpracování okna MDI.  
  
 Nepoužívejte C++ **odstranit** operátor zničit okno rámce. Místo nich se používá `CWnd::DestroyWindow`. `CFrameWnd` Provádění `PostNcDestroy` odstraní při zničení okně objekt jazyka C++. Když uživatel zavře okno rámce, výchozí `OnClose` obslužná rutina zavolá `DestroyWindow`.  
  
 Další informace o `CMDIFrameWnd`, naleznete v tématu [rámce Windows](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIFrameWnd`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cmdiframewnd"></a>  CMDIFrameWnd::CMDIFrameWnd  
 Vytvoří `CMDIFrameWnd` objektu.  
  
```  
CMDIFrameWnd();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání `Create` nebo `LoadFrame` členské funkce můžete vytvořit viditelné okna rámce MDI.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]  
  
##  <a name="createclient"></a>  CMDIFrameWnd::CreateClient  
 Vytvoří okno klienta MDI, která spravuje `CMDIChildWnd` objekty.  
  
```  
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>Parametry  
 *lpCreateStruct*  
 Dlouhým ukazatelem na [soubor CREATESTRUCT](../../mfc/reference/createstruct-structure.md) struktury.  
  
 *pWindowMenu*  
 Ukazatel na místní nabídka okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce by měla být volána, pokud přepíšete `OnCreate` přímo členskou funkci.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]  
  
##  <a name="createnewchild"></a>  CMDIFrameWnd::CreateNewChild  
 Vytvoří nové podřízené okno.  
  
```  
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,  
    UINT nResource,  
    HMENU hMenu = NULL,  
    HACCEL hAccel = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pClass*  
 Run-time Třída podřízeného okna, který se má vytvořit.  
  
 *Prostředků*  
 ID sdílené prostředky přidružené k podřízené okno.  
  
 *hMenu*  
 Nabídka podřízené okno.  
  
 *hAccel*  
 Akcelerátor podřízené okno.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce pro vytváření podřízených windows okna rámce MDI.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]  
  
 Tento příklad je výpisem z článku znalostní báze Q201045, "postupy: Přidání více typů okno MDI Non-Document/View aplikace." Články znalostní báze jsou k dispozici na [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="getwindowmenupopup"></a>  CMDIFrameWnd::GetWindowMenuPopup  
 Voláním této členské funkce se získat popisovač aktuální rozbalovací nabídky s názvem "Okno" (rozbalovací nabídky s položkami nabídky pro správu okna MDI).  
  
```  
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```  
  
### <a name="parameters"></a>Parametry  
 *hMenuBar*  
 Aktuální řádek nabídek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Místní nabídka okna pokud existuje; v opačném případě hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace hledá místní nabídky, který obsahuje standardní příkazy nabídky okna například id_window_new – a id_window_tile_horz –.  
  
 Tato členská funkce přepište, pokud máte nabídka okna, která nepoužívá ID příkazu standardní nabídky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]  
  
##  <a name="mdiactivate"></a>  CMDIFrameWnd::MDIActivate  
 Aktivuje různé podřízené okno MDI.  
  
```  
void MDIActivate(CWnd* pWndActivate);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndActivate*  
 Odkazuje na podřízené okno MDI aktivaci.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce odešle [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) zpráva, která má podřízené okno, které je aktivováno a podřízené okno právě deaktivována.  
  
 Toto je stejná zpráva, která se odešle, pokud uživatel změní fokus na podřízené okno MDI pomocí myši nebo klávesnice.  
  
> [!NOTE]
>  Bez ohledu na jejich okna rámce MDI je aktivováno podřízené okno MDI. Když se aktivují rámce, posílají se podřízené okno, které poslední aktivace [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) zprávu pro kreslení aktivní okno rámce a záhlaví, ale nepřijímá další WM_MDIACTIVATE zprávu.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).  
  
##  <a name="mdicascade"></a>  CMDIFrameWnd::MDICascade  
 Uspořádá všechny podřízených oken MDI ve formátu cascade.  
  
```  
void MDICascade();  
void MDICascade(int nType);
```  
  
### <a name="parameters"></a>Parametry  
 *nTyp*  
 Určuje příznak cascade. Je možné zadat pouze následující příznak: MDITILE_SKIPDISABLED, což zabrání se kaskádových zakázané podřízených oken MDI.  
  
### <a name="remarks"></a>Poznámky  
 První verze `MDICascade`, bez parametrů, uspořádá sebe všech podřízených oken MDI, včetně zakázané značky. Druhá verze volitelně nemá zakázané cascade MDI podřízených oken, pokud zadáte MDITILE_SKIPDISABLED pro *nTyp* parametru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]  
  
##  <a name="mdigetactive"></a>  CMDIFrameWnd::MDIGetActive  
 Načte aktuální aktivní podřízené okno MDI, spolu s příznak označující, zda je podřízené okno maximalizované.  
  
```  
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pbMaximized*  
 Ukazatel na návratovou hodnotu typu BOOL. Nastavte na hodnotu TRUE při návratu, pokud je okno maximalizované; v opačném případě FALSE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktivní podřízené okno MDI.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).  
  
##  <a name="mdiiconarrange"></a>  CMDIFrameWnd::MDIIconArrange  
 Uspořádá všech podřízených oken minimalizované dokumentu.  
  
```  
void MDIIconArrange();
```  
  
### <a name="remarks"></a>Poznámky  
 Neovlivňuje podřízených oken, které nejsou minimalizovaný.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIFrameWnd::MDICascade](#mdicascade).  
  
##  <a name="mdimaximize"></a>  CMDIFrameWnd::MDIMaximize  
 Maximalizuje zadaný podřízené okno MDI.  
  
```  
void MDIMaximize(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Body do okna pro maximalizaci.  
  
### <a name="remarks"></a>Poznámky  
 Když je podřízené okno maximalizované, změní velikost Windows ho tak, aby klientské oblasti okna klienta. Windows umístí ovládací prvek nabídky podřízené okno rámce nabídek, uživatel může obnovit nebo podřízené okno zavřete. Také přidá název podřízené okno na titulek okna rámce.  
  
 Pokud jiné podřízené okno MDI je aktivována, když maximalizované aktuálně aktivní podřízené okno MDI, Windows obnoví aktuálně aktivní podřízený a maximalizuje nově aktivovaného podřízené okno.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).  
  
##  <a name="mdinext"></a>  CMDIFrameWnd::MDINext  
 Aktivuje podřízené okno bezprostředně za aktuálně aktivní podřízené okno a umístí aktuálně aktivní podřízené okno za všechny ostatní podřízená okna.  
  
```  
void MDINext();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je aktuálně aktivní podřízené okno MDI maximalizované, členské funkce obnoví aktuálně aktivní podřízený a maximalizuje nově aktivovaného podřízené.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]  
  
##  <a name="mdiprev"></a>  CMDIFrameWnd::MDIPrev  
 Aktivuje předchozí podřízeného okna a umístí aktuálně aktivní podřízené okno bezprostředně za.  
  
```  
void MDIPrev();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je aktuálně aktivní podřízené okno MDI maximalizované, členské funkce obnoví aktuálně aktivní podřízený a maximalizuje nově aktivovaného podřízené.  
  
##  <a name="mdirestore"></a>  CMDIFrameWnd::MDIRestore  
 Obnoví ze minimalizované nebo maximalizované velikost podřízené okno MDI.  
  
```  
void MDIRestore(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Odkazuje na okno pro obnovení.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).  
  
##  <a name="mdisetmenu"></a>  CMDIFrameWnd::MDISetMenu  
 Nahradí v nabídce okna rámce MDI a místní nabídka okna.  
  
```  
CMenu* MDISetMenu(
    CMenu* pFrameMenu,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>Parametry  
 *pFrameMenu*  
 Určuje nabídku nové nabídky okna rámce. Pokud má hodnotu NULL, v nabídce se nezmění.  
  
 *pWindowMenu*  
 Určuje nabídku nové okno rozbalovací nabídky. Pokud má hodnotu NULL, v nabídce se nezmění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nabídce oken s rámečkem nahrazuje tuto zprávu. Ukazatel může být dočasné a neměl by být uložen pro pozdější použití.  
  
### <a name="remarks"></a>Poznámky  
 Po volání `MDISetMenu`, musí aplikace volat [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) členskou funkci `CWnd` aktualizace řádku nabídek.  
  
 Pokud toto volání nahrazuje místní nabídka okna, jsou položky nabídky podřízené okno MDI odebrána z předchozí nabídky okna a přidat do nové místní nabídka okna.  
  
 Pokud maximalizované podřízené okno MDI a toto volání nahrazuje nabídky okna rámce MDI, ovládací prvek nabídky a obnovení ovládací prvky se odeberou z předchozí nabídky oken s rámečkem a přidat do nové nabídky.  
  
 Nevolejte tuto členskou funkci, pokud používáte rozhraní Správa podřízených oken MDI.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]  
  
##  <a name="mditile"></a>  CMDIFrameWnd::MDITile  
 Uspořádá všechna podřízená okna ve formátu vedle sebe.  
  
```  
void MDITile();  
void MDITile(int nType);
```  
  
### <a name="parameters"></a>Parametry  
 *nTyp*  
 Určuje příznak dělení do bloků. Tento parametr může být jedna z následujících příznaků:  
  
- MDITILE_HORIZONTAL dlaždice podřízených oken MDI tak tohoto jednoho okna se zobrazí nad jiného.  
  
- Zabraňuje MDITILE_SKIPDISABLED zakázané podřízených oken MDI z se vedle sebe.  
  
- MDITILE_VERTICAL dlaždice podřízených oken MDI tak tohoto jednoho okna se zobrazí vedle jiného.  
  
### <a name="remarks"></a>Poznámky  
 První verze `MDITile`, bez parametrů, dlaždice windows svisle v rámci Windows verze 3.1 nebo novější. Druhá verze dlaždice windows vertikálně nebo horizontálně, závisí na hodnotě *nTyp* parametru.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIFrameWnd::MDICascade](#mdicascade).  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC MDI](../../visual-cpp-samples.md)   
 [Ukázky knihovny MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Ukázky knihovny MFC SNAPVW](../../visual-cpp-samples.md)   
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CMDIChildWnd – třída](../../mfc/reference/cmdichildwnd-class.md)
