---
title: CMDIFrameWnd – třída | Microsoft Docs
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
ms.openlocfilehash: 9f3ba2a92ad523994a458abad9d4acee506e8e85
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038887"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd – třída
Poskytuje funkci Windows více okna rámce rozhraní (MDI) dokumentu, společně s členů pro správu okna.  
  
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
|[CMDIFrameWnd::CreateClient](#createclient)|Vytvoří Windows **MDICLIENT** okna pro to `CMDIFrameWnd`. Volá `OnCreate` členské funkce `CWnd`.|  
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Vytvoří nového podřízeného okna.|  
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Vrátí místní nabídky okna.|  
|[CMDIFrameWnd::MDIActivate](#mdiactivate)|Aktivuje různých podřízeného okna MDI.|  
|[CMDIFrameWnd::MDICascade](#mdicascade)|Uspořádá okna všechny podřízené v kaskádě formátu.|  
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Načte aktuálně aktivní podřízeného okna MDI, společně s příznak indikující, zda je Maximalizovaný podřízený objekt.|  
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Uspořádá okna podřízené všechny minimalizovaném okně dokumentu.|  
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maximalizuje okna MDI podřízené.|  
|[CMDIFrameWnd::MDINext](#mdinext)|Aktivuje podřízeného okna hned za aktuálně aktivní podřízeného okna a umístí aktuálně aktivní podřízeného okna za všechny ostatní podřízená okna.|  
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Aktivuje předchozí podřízeného okna a umístí aktuálně aktivní podřízeného okna hned za.|  
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Podřízená okna MDI obnoví z velikost maximalizovaném okně nebo minimalizovaném okně.|  
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Nahradí v nabídce rámce okna MDI, v rozbalovací nabídce okno nebo obojí.|  
|[CMDIFrameWnd::MDITile](#mditile)|Uspořádá okna všechny podřízené ve formátu vedle sebe.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete vytvořit užitečné rámce okna MDI pro aplikace, odvození třídy z `CMDIFrameWnd`. Přidání členské proměnné do odvozené třídy k ukládání dat, které jsou specifické pro vaši aplikaci. Implementace obslužné rutiny zpráv členských funkcí a zprávu mapovat v odvozené třídě k určení, co se stane, když jsou směrované zprávy do okna.  
  
 Můžete vytvořit rámce okna MDI pomocí volání [vytvořit](../../mfc/reference/cframewnd-class.md#create) nebo [loadframe –](../../mfc/reference/cframewnd-class.md#loadframe) členské funkce `CFrameWnd`.  
  
 Před voláním `Create` nebo `LoadFrame`, je nutné vytvořit objekt rámce okna v haldě pomocí C++ **nové** operátor. Před voláním `Create` budete taky moct registrovat třídu okno s [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) globální funkce nastavit ikonu a třída styly pro rámečku.  
  
 Použití `Create` – členská funkce předat parametry vytvoření rámečku jako okamžitou argumenty.  
  
 `LoadFrame` vyžaduje argumenty méně než `Create`a místo toho načítá většinu jeho výchozí hodnoty z prostředků, včetně titulku rámečku, ikona, tabulka akcelerátoru a nabídky. Přístup `LoadFrame`, tyto prostředky musí mít stejné ID prostředku (například **IDR_MAINFRAME**).  
  
 I když **MDIFrameWnd** je odvozený od `CFrameWnd`, třídy oken s rámečkem odvozené od `CMDIFrameWnd` nemusí deklarovat s `DECLARE_DYNCREATE`.  
  
 `CMDIFrameWnd` Třída dědí velkou část jeho výchozí implementace z `CFrameWnd`. Podrobný seznam tyto funkce, najdete v části [CFrameWnd](../../mfc/reference/cframewnd-class.md) třídy popis. `CMDIFrameWnd` Třída má následující funkce:  
  
-   Spravuje rámce okna MDI **MDICLIENT** okně přemístění ve spojení s ovládací pruhy. Okna MDI klienta je přímou nadřazenou rámce podřízených oken MDI. **Ws_hscroll –** a **ws_vscroll –** okno Styly definované na `CMDIFrameWnd` aplikovány okna MDI klienta namísto hlavního okna rámce, uživatel může posuňte klientské oblasti MDI (jako v systému Windows Správce programů, například).  
  
-   Rámec okna MDI vlastní výchozí nabídka, která se používá jako panelu nabídek, pokud neexistuje žádné aktivní podřízeného okna MDI. Když dojde aktivního podřízeného MDI, řádku nabídek rámce okna MDI v nabídce podřízených oken MDI nahrazuje automaticky.  
  
-   Rámec okna MDI funguje ve spojení s aktuální podřízeného okna MDI, jestliže existuje. Příkaz zprávy jsou například delegovat na aktuálně aktivní podřízeného MDI před rámce okna MDI.  
  
-   Rámec okna MDI má výchozí obslužné rutiny pro tyto standardní příkazy nabídky okna:  
  
    - **ID_WINDOW_TILE_VERT –**  
  
    - **ID_WINDOW_TILE_HORZ –**  
  
    - **ID_WINDOW_CASCADE –**  
  
    - **ID_WINDOW_ARRANGE –**  
  
-   Rámec okna MDI má také implementace **id_window_new –**, která vytvoří nový snímek a zobrazení v aktuálním dokumentu. Aplikace můžete přepsat tyto výchozí implementace příkaz k přizpůsobení MDI okno zpracování.  
  
 Nepoužívejte C++ **odstranit** operátor zrušení rámce okna. Místo nich se používá `CWnd::DestroyWindow`. `CFrameWnd` Implementace `PostNcDestroy` se odstranit objekt C++, když okno zničena. Když uživatel nezavře okno rámce, výchozí `OnClose` bude volat obslužná rutina `DestroyWindow`.  
  
 Další informace o `CMDIFrameWnd`, najdete v části [okna s rámečkem](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
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
 Volání `Create` nebo `LoadFrame` – členská funkce vytvořit viditelné rámce okna MDI.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]  
  
##  <a name="createclient"></a>  CMDIFrameWnd::CreateClient  
 Vytvoří okna MDI klienta, který spravuje `CMDIChildWnd` objekty.  
  
```  
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>Parametry  
 *lpCreateStruct*  
 Dlouhé ukazatel [createstruct –](../../mfc/reference/createstruct-structure.md) struktura.  
  
 *pWindowMenu*  
 Ukazatel na okno místní nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce by měla být volána, pokud přepíšete `OnCreate` – členská funkce přímo.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]  
  
##  <a name="createnewchild"></a>  CMDIFrameWnd::CreateNewChild  
 Vytvoří nového podřízeného okna.  
  
```  
CMDIChildWnd* CreateNewChild(
    CRuntimeClass* pClass,  
    UINT nResource,  
    HMENU hMenu = NULL,  
    HACCEL hAccel = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pClass*  
 Run-time třída z podřízeného okna, který se má vytvořit.  
  
 *nResource*  
 ID sdílené prostředky, které jsou přidružené k podřízeného okna.  
  
 *hMenu*  
 Nabídka podřízeného okna.  
  
 *hAccel*  
 Accelerator podřízeného okna.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete vytvořit podřízenou windows rámce okna MDI.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]  
  
 V tomto příkladu je výňatek ze článku znalostní báze Q201045, "postupy: přidat více typy oken MDI Non-Document/View – aplikace." Články znalostní báze jsou k dispozici na [ http://support.microsoft.com ](http://support.microsoft.com/).  
  
##  <a name="getwindowmenupopup"></a>  CMDIFrameWnd::GetWindowMenuPopup  
 Volání této funkce člen se získat popisovač pro aktuální místní nabídky s názvem "Okno" (místní nabídky k položkám nabídky pro Správa oken MDI).  
  
```  
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```  
  
### <a name="parameters"></a>Parametry  
 *hMenuBar*  
 Aktuální řádku nabídek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Místní nabídky okna pokud existuje; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace hledá místní nabídky, jako který obsahuje standardní příkazy nabídky okna **id_window_new –** a **id_window_tile_horz –**.  
  
 Funkci člena přepište, pokud máte okno nabídky, která nepoužívá příkaz nabídky standardní identifikátory.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]  
  
##  <a name="mdiactivate"></a>  CMDIFrameWnd::MDIActivate  
 Aktivuje různých podřízeného okna MDI.  
  
```  
void MDIActivate(CWnd* pWndActivate);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndActivate*  
 Body do okna MDI podřízené chcete aktivovat.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci člen odešle [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) zpráva podřízeného okna, Probíhá aktivace i podřízeného okna právě deaktivována.  
  
 Toto je stejný zprávu, která je odeslána, pokud uživatel změní fokus na podřízené okna MDI pomocí myši a klávesnice.  
  
> [!NOTE]
>  Podřízená okna MDI se aktivuje nezávisle na rámce okna MDI. Když rámečku stane aktivní, je odeslána podřízeného okna, který poslední aktivace [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) zpráva k vykreslení rámce aktivní okno a záhlaví, ale jiné neobdrží `WM_MDIACTIVATE` zprávy.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).  
  
##  <a name="mdicascade"></a>  CMDIFrameWnd::MDICascade  
 Uspořádá všechny podřízených oken MDI ve formátu cascade.  
  
```  
void MDICascade();  
void MDICascade(int nType);
```  
  
### <a name="parameters"></a>Parametry  
 *Noznámení*  
 Určuje příznak cascade. Lze zadat pouze následující příznak: `MDITILE_SKIPDISABLED`, která zabraňuje zakázané podřízených oken MDI se kaskádových.  
  
### <a name="remarks"></a>Poznámky  
 První verze součásti `MDICascade`, bez parametrů, uspořádá sebe všech podřízených oken MDI včetně ty, které jsou zakázány. Druhá verze volitelně nemá cascade zakázáno MDI podřízená okna, pokud zadáte `MDITILE_SKIPDISABLED` pro `nType` parametr.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]  
  
##  <a name="mdigetactive"></a>  CMDIFrameWnd::MDIGetActive  
 Načte aktuální aktivní MDI podřízené okno, společně s příznak označující, zda je maximalizovaný podřízeného okna.  
  
```  
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pbMaximized*  
 Ukazatel **BOOL** vrátit hodnotu. Nastavte na **TRUE** na vrátit, pokud je okno maximalizovaném okně; jinak hodnota **FALSE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na aktivní podřízeného okna MDI.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).  
  
##  <a name="mdiiconarrange"></a>  CMDIFrameWnd::MDIIconArrange  
 Uspořádá okna podřízené všechny minimalizovaném okně dokumentu.  
  
```  
void MDIIconArrange();
```  
  
### <a name="remarks"></a>Poznámky  
 Podřízená okna, které nejsou minimalizovaná nemá vliv.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIFrameWnd::MDICascade](#mdicascade).  
  
##  <a name="mdimaximize"></a>  CMDIFrameWnd::MDIMaximize  
 Maximalizuje zadaný podřízeného okna MDI.  
  
```  
void MDIMaximize(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Body do okna maximalizovat.  
  
### <a name="remarks"></a>Poznámky  
 Když maximalizaci podřízeného okna Windows změní ji a ujistěte se jeho klientské oblasti okna klienta. Windows umístí podřízeného okna Ovládací prvek nabídky v řádku nabídek rámečku, uživatel může obnovit nebo zavřete okno podřízené. Také přidá název podřízeného okna nadpis oken s rámečkem.  
  
 Pokud jiný podřízeného okna MDI je aktivována, pokud je aktuálně aktivní podřízeného okna MDI maximalizované, systém Windows obnoví aktuálně aktivních podřízených a maximalizuje nově aktivovaný podřízeného okna.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).  
  
##  <a name="mdinext"></a>  CMDIFrameWnd::MDINext  
 Aktivuje podřízeného okna hned za aktuálně aktivní podřízeného okna a umístí aktuálně aktivní podřízeného okna za všechny ostatní podřízená okna.  
  
```  
void MDINext();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je aktuálně aktivní podřízeného okna MDI maximalizované, – členská funkce obnoví aktuálně aktivních podřízených a maximalizuje nově aktivovaný podřízené.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]  
  
##  <a name="mdiprev"></a>  CMDIFrameWnd::MDIPrev  
 Aktivuje předchozí podřízeného okna a umístí aktuálně aktivní podřízeného okna hned za.  
  
```  
void MDIPrev();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je aktuálně aktivní podřízeného okna MDI maximalizované, – členská funkce obnoví aktuálně aktivních podřízených a maximalizuje nově aktivovaný podřízené.  
  
##  <a name="mdirestore"></a>  CMDIFrameWnd::MDIRestore  
 Podřízená okna MDI obnoví z velikost maximalizovaném okně nebo minimalizovaném okně.  
  
```  
void MDIRestore(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Body do okna obnovení.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).  
  
##  <a name="mdisetmenu"></a>  CMDIFrameWnd::MDISetMenu  
 Nahradí v nabídce rámce okna MDI, v rozbalovací nabídce okno nebo obojí.  
  
```  
CMenu* MDISetMenu(
    CMenu* pFrameMenu,  
    CMenu* pWindowMenu);
```  
  
### <a name="parameters"></a>Parametry  
 *pFrameMenu*  
 Určuje, v nabídce nové nabídky oken s rámečkem. Pokud **NULL**, v nabídce se nezmění.  
  
 *pWindowMenu*  
 Určuje, v nabídce místní nabídky okna. Pokud **NULL**, v nabídce se nezmění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na v nabídce oken s rámečkem nahrazuje tuto zprávu. Ukazatele může být v dočasné a by neměly být uloženy pro pozdější použití.  
  
### <a name="remarks"></a>Poznámky  
 Po volání `MDISetMenu`, aplikace musí volat [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) členské funkce `CWnd` k aktualizaci řádku nabídek.  
  
 Pokud toto volání nahradí okno místní nabídky, položky nabídky podřízených oken MDI se odeberou z předchozí nabídky okna a přidat do nové okno místní nabídky.  
  
 Pokud je maximalizovaný podřízeného okna MDI a toto volání nahrazuje nabídce MDI oken s rámečkem, jsou ovládací prvky pro nabídky a obnovení řízení odebrán z nabídky předchozích oken s rámečkem a přidat do nové nabídky.  
  
 Nevolejte tuto funkci člen, pokud používáte rozhraní ke správě vašeho podřízených oken MDI.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]  
  
##  <a name="mditile"></a>  CMDIFrameWnd::MDITile  
 Uspořádá okna všechny podřízené ve formátu vedle sebe.  
  
```  
void MDITile();  
void MDITile(int nType);
```  
  
### <a name="parameters"></a>Parametry  
 *Noznámení*  
 Určuje příznak vedle sebe. Tento parametr může být některého z následujících příznaků:  
  
- `MDITILE_HORIZONTAL` Dlaždice podřízených oken MDI tak dané jeden okno se zobrazí nad jiné.  
  
- `MDITILE_SKIPDISABLED` Zabrání zakázané podřízených oken MDI se vedle sebe.  
  
- `MDITILE_VERTICAL` Dlaždice podřízených oken MDI tak dané jeden okno se zobrazí vedle jiné.  
  
### <a name="remarks"></a>Poznámky  
 První verze součásti `MDITile`, bez parametrů, dlaždice windows svisle v systémech Windows verze 3.1 nebo novější. Druhá verze dlaždice windows vertikálně nebo horizontálně, v závislosti na hodnotě *Noznámení* parametr.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CMDIFrameWnd::MDICascade](#mdicascade).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MDI](../../visual-cpp-samples.md)   
 [Ukázka MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Ukázka MFC SNAPVW](../../visual-cpp-samples.md)   
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CMDIChildWnd – třída](../../mfc/reference/cmdichildwnd-class.md)
