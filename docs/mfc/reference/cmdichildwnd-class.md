---
title: "CMDIChildWnd – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
dev_langs: C++
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: deca38c7c1fdaf9523e4186b801e5ed25042e46e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd – třída
Poskytuje funkci Windows více okna podřízené rozhraní (MDI) dokumentu, společně s členů pro správu okna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMDIChildWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Vytvoří `CMDIChildWnd` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMDIChildWnd::Create](#create)|Vytvoří podřízeného okna Windows MDI, přidružené `CMDIChildWnd` objektu.|  
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Vrací nadřazeného MDI rámce okna MDI klienta.|  
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Aktivuje toto okno podřízeného MDI.|  
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Zničí tento podřízeného okna MDI.|  
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Maximalizuje tohoto okna MDI podřízené.|  
|[CMDIChildWnd::MDIRestore](#mdirestore)|Obnoví tento podřízeného okna MDI z velikost maximalizovaném okně nebo minimalizovaném okně.|  
|[CMDIChildWnd::SetHandles](#sethandles)|Nastaví obslužné rutiny pro nabídky a akcelerátoru prostředky.|  
  
## <a name="remarks"></a>Poznámky  
 Podřízená okna MDI vypadá podobně jako okno typické rámce, s tím rozdílem, že podřízeného okna MDI se zobrazí uvnitř rámce okna MDI a nikoli na ploše. Podřízená okna MDI nemá řádku nabídek své vlastní, ale místo toho sdílí nabídky rámce okna MDI. Rozhraní framework automaticky změní v nabídce MDI představují aktuálně aktivní podřízeného okna MDI.  
  
 Pokud chcete vytvořit užitečné podřízeného okna MDI pro vaši aplikaci, odvození třídy z `CMDIChildWnd`. Přidání členské proměnné do odvozené třídy k ukládání dat, které jsou specifické pro vaši aplikaci. Implementace obslužné rutiny zpráv členských funkcí a zprávu mapovat v odvozené třídě k určení, co se stane, když jsou směrované zprávy do okna.  
  
 Existují tři způsoby, jak vytvořit okna MDI podřízené:  
  
-   Přímo vytvořit pomocí **vytvořit**.  
  
-   Přímo vytvořit pomocí `LoadFrame`.  
  
-   Nepřímo ho vytvořte pomocí šablony dokumentu.  
  
 Před voláním **vytvořit** nebo `LoadFrame`, je nutné vytvořit objekt oken s rámečkem v haldě pomocí C++ **nové** operátor. Před voláním **vytvořit** budete taky moct registrovat třídu okno s [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) globální funkce nastavit ikonu a třída styly pro rámečku.  
  
 Použití **vytvořit** – členská funkce předat parametry vytvoření rámečku jako okamžitou argumenty.  
  
 `LoadFrame`vyžaduje argumenty méně než **vytvořit**a místo toho načítá většinu jeho výchozí hodnoty z prostředků, včetně titulku rámečku, ikona, tabulka akcelerátoru a nabídky. Chcete-li být přístupné `LoadFrame`, tyto prostředky musí mít stejné ID prostředku (například **IDR_MAINFRAME**).  
  
 Když `CMDIChildWnd` objekt obsahuje zobrazení a dokumenty, jsou nepřímo vytvořené pomocí rozhraní místo přímo z programátorů. `CDocTemplate` Objekt orchestruje vytvoření rámečku, vytvoření obsahující zobrazení a připojení k zobrazení odpovídající dokumentu. Parametry `CDocTemplate` zadejte konstruktor `CRuntimeClass` tří tříd podílejí (dokumentu, rámečkem a zobrazení). A `CRuntimeClass` objekt používají rozhraní dynamicky vytvořit nové rámce při zadané uživatelem (například pomocí souboru nový příkaz nebo nového okna MDI příkazu).  
  
 Odvozené třídy oken s rámečkem z `CMDIChildWnd` je třeba deklarovat s `DECLARE_DYNCREATE` v pořadí pro výše `RUNTIME_CLASS` mechanismus fungovala správně.  
  
 `CMDIChildWnd` Třída dědí velkou část jeho výchozí implementace z `CFrameWnd`. Podrobný seznam těchto funkcí, naleznete [CFrameWnd](../../mfc/reference/cframewnd-class.md) třídy popis. `CMDIChildWnd` Třída má následující funkce:  
  
-   Ve spojení s `CMultiDocTemplate` třída, více `CMDIChildWnd` objekty ze stejné šablony dokumentu sdílejí stejné nabídce ukládání systémových prostředků Windows.  
  
-   Aktuálně aktivní nabídky okna MDI podřízené zcela nahradí rámce okna MDI nabídku a titulek aktuálně aktivní podřízeného okna MDI se přidá rámce okna MDI titulek. Další příklady MDI podřízené okno funkcí, které jsou implementované ve spojení s rámce okna MDI najdete v tématu `CMDIFrameWnd` třídy popis.  
  
 Nepoužívejte C++ **odstranit** operátor zrušení rámce okna. Místo nich se používá `CWnd::DestroyWindow`. `CFrameWnd` Implementace `PostNcDestroy` se odstranit objekt C++, když okno zničena. Když uživatel nezavře okno rámce, výchozí `OnClose` bude volat obslužná rutina `DestroyWindow`.  
  
 Další informace o `CMDIChildWnd`, najdete v části [okna s rámečkem](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIChildWnd`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="cmdichildwnd"></a>CMDIChildWnd::CMDIChildWnd  
 Volání k vytvoření `CMDIChildWnd` objektu.  
  
```  
CMDIChildWnd();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání **vytvořit** vytvořit okno viditelné.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMDIChildWnd::Create](#create).  
  
##  <a name="create"></a>CMDIChildWnd::Create  
 Volání této funkce člen podřízeného okna Windows MDI a vytvořte jej do `CMDIChildWnd` objektu.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,  
    const RECT& rect = rectDefault,  
    CMDIFrameWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszClassName`  
 Odkazuje na řetězec znaků ukončené hodnotou null, který pojmenuje třídě Windows ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktura). Název třídy může být jakýkoli název zaregistrována [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) globální funkce. Musí být **NULL** pro standardní `CMDIChildWnd`.  
  
 `lpszWindowName`  
 Odkazuje na řetězec znaků ukončené hodnotou null, který představuje název okna. Používá jako text záhlaví.  
  
 `dwStyle`  
 Určuje okno [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles) atributy. **Ws_child –** styl se vyžaduje.  
  
 `rect`  
 Obsahuje velikost a umístění okna. `rectDefault` Systému Windows zadejte velikost a umístění nového umožní hodnotu `CMDIChildWnd`.  
  
 `pParentWnd`  
 Určuje nadřazený okna. Pokud **NULL**, hlavní okno aplikace se používá.  
  
 `pContext`  
 Určuje [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. Tento parametr může být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Aktuálně aktivní okno rámce podřízeného MDI můžete určit titulek nadřazeného rámce okna. Tato funkce je vypnutá vypnutím **fws_addtotitle –** styl bit podřízeného rámce okna.  
  
 Volá rámec této funkce člen v reakci na příkaz uživatele k vytvoření podřízeného okna a používá rozhraní `pContext` parametru správně podřízeného okna připojit k aplikaci. Při volání **vytvořit**, `pContext` může být **NULL**.  
  
### <a name="example"></a>Příklad  
 Příklad 1:  
  
 [!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]  
  
### <a name="example"></a>Příklad  
 Příklad 2:  
  
 [!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]  
  
##  <a name="getmdiframe"></a>CMDIChildWnd::GetMDIFrame  
 Volání této funkce vrátit MDI nadřazeného rámce.  
  
```  
CMDIFrameWnd* GetMDIFrame();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rámec nadřazeného okna MDI.  
  
### <a name="remarks"></a>Poznámky  
 Rámečku vrátil je dva nadřazené položky odebrat z `CMDIChildWnd` a nadřazeného okna typu **MDICLIENT** která spravuje `CMDIChildWnd` objekt. Volání [getparent –](../../mfc/reference/cwnd-class.md#getparent) – členská funkce vrátit `CMDIChildWnd` objektu je okamžitou **MDICLIENT** nadřazené jako dočasného `CWnd` ukazatel.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).  
  
##  <a name="mdiactivate"></a>CMDIChildWnd::MDIActivate  
 Volání této funkce člen aktivovat podřízené okna MDI nezávisle na rámce okna MDI.  
  
```  
void MDIActivate();
```  
  
### <a name="remarks"></a>Poznámky  
 Když rámečku stane aktivní, aktivuje se také podřízeného okna, který poslední aktivace.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).  
  
##  <a name="mdidestroy"></a>CMDIChildWnd::MDIDestroy  
 Volání této funkce člen při zavírání okna MDI podřízené.  
  
```  
void MDIDestroy();
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce Odebere název podřízeného okna z okna rámce a deaktivuje podřízeného okna.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]  
  
##  <a name="mdimaximize"></a>CMDIChildWnd::MDIMaximize  
 Volání této funkce člen maximalizovat okna MDI podřízené.  
  
```  
void MDIMaximize();
```  
  
### <a name="remarks"></a>Poznámky  
 Když maximalizaci podřízeného okna Windows změní ji a ujistěte se jeho klientské oblasti vyplnění klientské oblasti okně s rámečkem. Windows tak, aby uživatel může obnovit nebo zavřete okno podřízené umístí podřízeného okna Ovládací prvek nabídky v řádku nabídek rámečku a přidá název podřízeného okna nadpis oken s rámečkem.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]  
  
##  <a name="mdirestore"></a>CMDIChildWnd::MDIRestore  
 Volání této funkce člen obnovit podřízeného okna MDI ze velikost maximalizovaném okně nebo minimalizovaném okně.  
  
```  
void MDIRestore();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]  
  
##  <a name="sethandles"></a>CMDIChildWnd::SetHandles  
 Nastaví obslužné rutiny pro nabídky a akcelerátoru prostředky.  
  
```  
void SetHandles(
    HMENU hMenu,  
    HACCEL hAccel);
```  
  
### <a name="parameters"></a>Parametry  
 `hMenu`  
 Obslužná rutina nabídky prostředku.  
  
 `hAccel`  
 Popisovač prostředek akcelerátoru.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto funkci nastavit nabídky a akcelerátoru prostředky využívané třídou okna MDI podřízený objekt.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC MDI](../../visual-cpp-samples.md)   
 [Ukázka MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Ukázka MFC SNAPVW](../../visual-cpp-samples.md)   
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd – třída](../../mfc/reference/cmdiframewnd-class.md)
