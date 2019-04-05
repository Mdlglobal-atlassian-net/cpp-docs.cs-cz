---
title: CMDIFrameWnd – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 9f5289491a7c14749865cfd163417440bc542aba
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776528"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd – třída

Poskytuje funkce Windows více dokumentů (MDI) rozhraní okna rámce spolu se členy pro správu okna.

## <a name="syntax"></a>Syntaxe

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|Vytvoří `CMDIFrameWnd`.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
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

- Spravuje okna rámce MDI okno MDICLIENT přemístění ve spojení s ovládací pruhy. Okno klienta MDI je přímou nadřazenou podřízených oken rámce MDI. WS_HSCROLL a WS_VSCROLL styly oken na `CMDIFrameWnd` platí pro okno klienta MDI namísto oknem hlavního rámce, takže uživatel může posunout oblasti klienta MDI (jako Windows manažer programu, například).

- Okna rámce MDI vlastní výchozí nabídka, která se používá jako nabídek, pokud neexistuje žádná aktivní podřízené okno MDI. Když je aktivní podřízený formulář MDI, panel nabídek okna rámce MDI automaticky nahrazena podřízené okno MDI.

- Okna rámce MDI funguje ve spojení s aktuální podřízené okno MDI, pokud existuje. Zprávy s příkazy jsou například delegovat na aktuálně aktivní podřízený formulář MDI před okna rámce MDI.

- Okna rámce MDI má výchozích obslužných rutin pro následující standardní příkazy nabídky okna:

    - ID_WINDOW_TILE_VERT

    - ID_WINDOW_TILE_HORZ

    - ID_WINDOW_CASCADE

    - ID_WINDOW_ARRANGE

- Okna rámce MDI má také implementace id_window_new –, který vytvoří nový snímek a zobrazení pro aktuální dokument. Aplikace můžete přepsat tyto výchozí implementace příkazu k přizpůsobení zpracování okna MDI.

Nepoužívejte C++ **odstranit** operátor zničit okno rámce. Místo nich se používá `CWnd::DestroyWindow`. `CFrameWnd` Provádění `PostNcDestroy` odstraní při zničení okně objekt jazyka C++. Když uživatel zavře okno rámce, výchozí `OnClose` obslužná rutina zavolá `DestroyWindow`.

Další informace o `CMDIFrameWnd`, naleznete v tématu [rámce Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget –](../../mfc/reference/ccmdtarget-class.md)

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

*lpCreateStruct*<br/>
Dlouhým ukazatelem na [soubor CREATESTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcreatestructa) struktury.

*pWindowMenu*<br/>
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

*pClass*<br/>
Run-time Třída podřízeného okna, který se má vytvořit.

*Prostředků*<br/>
ID sdílené prostředky přidružené k podřízené okno.

*hMenu*<br/>
Nabídka podřízené okno.

*hAccel*<br/>
Akcelerátor podřízené okno.

### <a name="remarks"></a>Poznámky

Pomocí této funkce pro vytváření podřízených windows okna rámce MDI.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

##  <a name="getwindowmenupopup"></a>  CMDIFrameWnd::GetWindowMenuPopup

Voláním této členské funkce se získat popisovač aktuální rozbalovací nabídky s názvem "Okno" (rozbalovací nabídky s položkami nabídky pro správu okna MDI).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Parametry

*hMenuBar*<br/>
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

*pWndActivate*<br/>
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

*nType*<br/>
Určuje příznak cascade. Lze zadat pouze příznak následující: MDITILE_SKIPDISABLED, což zabrání se kaskádových zakázané podřízených oken MDI.

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

*pbMaximized*<br/>
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

*pWnd*<br/>
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

*pWnd*<br/>
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

*pFrameMenu*<br/>
Určuje nabídku nové nabídky okna rámce. Pokud má hodnotu NULL, v nabídce se nezmění.

*pWindowMenu*<br/>
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

*nType*<br/>
Určuje příznak dělení do bloků. Tento parametr může být jedna z následujících příznaků:

- MDITILE_HORIZONTAL dlaždice podřízených oken MDI tak tohoto jednoho okna se zobrazí nad jiného.

- Zabraňuje MDITILE_SKIPDISABLED zakázané podřízených oken MDI z se vedle sebe.

- MDITILE_VERTICAL dlaždice podřízených oken MDI tak tohoto jednoho okna se zobrazí vedle jiného.

### <a name="remarks"></a>Poznámky

První verze `MDITile`, bez parametrů, dlaždice windows svisle v rámci Windows verze 3.1 nebo novější. Druhá verze dlaždice windows vertikálně nebo horizontálně, závisí na hodnotě *nTyp* parametru.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CWnd](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd – třída](../../mfc/reference/cmdichildwnd-class.md)
