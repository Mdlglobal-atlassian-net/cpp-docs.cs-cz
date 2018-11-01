---
title: CMDIChildWnd – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: ffe7b975443b8bdc050bcb19af4f990b2e5ffafa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576628"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd – třída

Poskytuje funkce pro Windows více dokumentů (MDI) interface podřízené okno, spolu se členy pro správu okna.

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
|[CMDIChildWnd::Create](#create)|Vytvoří podřízené okno Windows MDI spojené s `CMDIChildWnd` objektu.|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Vrací nadřazeného rámce MDI klienta okna MDI.|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Aktivuje toto podřízené okno MDI.|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Zničí této podřízené okno MDI.|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Maximalizuje této podřízené okno MDI.|
|[CMDIChildWnd::MDIRestore](#mdirestore)|Obnoví ze minimalizované nebo maximalizované velikost této podřízené okno MDI.|
|[CMDIChildWnd::SetHandles](#sethandles)|Nastaví obslužné rutiny pro prostředky nabídky a akcelerátoru.|

## <a name="remarks"></a>Poznámky

Podřízené okno MDI vypadá podobně jako typické okno rámce, s tím rozdílem, že podřízené okno MDI se zobrazí uvnitř okna rámce MDI namísto ploše. Podřízené okno MDI nemá vlastní panel nabídek, ale místo toho sdílené složky v nabídce okna rámce MDI. Rozhraní automaticky změní nabídky rámce MDI představující aktivní podřízené okno MDI.

K vytvoření užitečné podřízené okno MDI pro vaši aplikaci, odvoďte třídu z `CMDIChildWnd`. Přidání členské proměnné do odvozené třídy k ukládání dat, které jsou specifické pro vaši aplikaci. Implementujte popisovač zprávy členské funkce a napište zprávu, mapování v odvozené třídě k určení, co se stane, když zprávy jsou přesměrovány do okna.

Existují tři způsoby, jak vytvořit podřízené okno MDI:

- Vytvořit přímo pomocí `Create`.

- Vytvořit přímo pomocí `LoadFrame`.

- Nepřímo ji vytvořte pomocí šablony dokumentu.

Před voláním `Create` nebo `LoadFrame`, je nutné vytvořit objekt oken s rámečkem na haldě pomocí jazyka C++ **nové** operátor. Před voláním `Create` budete taky moct registrovat třídu okna s [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) globální funkce nastavit ikonu a třída styly pro rámec.

Použití `Create` členskou funkci pro předání parametrů vytváření rámce jako okamžité argumenty.

`LoadFrame` vyžaduje méně argumentů než `Create`a místo toho načte většinu jeho výchozími hodnotami z prostředků, včetně titulek rámce, ikony, tabulky akcelerátorů a nabídky. Aby byl přístupný `LoadFrame`, tyto prostředky musí mít stejné ID prostředku (například IDR_MAINFRAME).

Když `CMDIChildWnd` objekt obsahuje zobrazení a dokumenty, jsou vytvořena nepřímo rozhraním namísto přímo programátorem. `CDocTemplate` Objekt orchestruje vytváření rámce, vytvoření nadřazeného zobrazení a připojení zobrazení k příslušné dokumentu. Parametry `CDocTemplate` zadejte konstruktoru `CRuntimeClass` tři třídy zahrnuty (dokument, rámce a zobrazení). A `CRuntimeClass` objektu se používá v rámci rozhraní dynamicky se vytvářejí nové rámce, když uživatel zadá (třeba pomocí příkazu soubor nový nebo nového okna MDI).

Z odvozené třídy oken s rámečkem `CMDIChildWnd` musí být deklarován s DECLARE_DYNCREATE v pořadí pro výše uvedené mechanismus RUNTIME_CLASS fungovat správně.

`CMDIChildWnd` Třída dědí velkou část jeho výchozí implementace ze `CFrameWnd`. Podrobný seznam těchto funkcí, najdete [CFrameWnd](../../mfc/reference/cframewnd-class.md) třídy popis. `CMDIChildWnd` Třída má Tyhle další funkce:

- Ve spojení s `CMultiDocTemplate` třídy, více `CMDIChildWnd` objekty ze stejné šablony dokumentu sdílejí stejnou nabídku ukládání systémových prostředků Windows.

- Aktuálně aktivní podřízené okno MDI zcela nahrazují nabídka okna rámce MDI a titulek aktuálně aktivní podřízené okno MDI je přidán do titulek okna rámce MDI. Další příklady funkcí MDI podřízené okno, které jsou implementovány ve spojení s oknem rámce MDI, najdete v článku `CMDIFrameWnd` třídy popis.

Nepoužívejte C++ **odstranit** operátor zničit okno rámce. Místo nich se používá `CWnd::DestroyWindow`. `CFrameWnd` Provádění `PostNcDestroy` odstraní při zničení okně objekt jazyka C++. Když uživatel zavře okno rámce, výchozí `OnClose` obslužná rutina zavolá `DestroyWindow`.

Další informace o `CMDIChildWnd`, naleznete v tématu [rámce Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cmdichildwnd"></a>  CMDIChildWnd::CMDIChildWnd

Volání k vytvoření `CMDIChildWnd` objektu.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Poznámky

Volání `Create` vytvořit okno viditelné.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMDIChildWnd::Create](#create).

##  <a name="create"></a>  CMDIChildWnd::Create

Voláním této členské funkce podřízeného okna Windows MDI a vytvořte tak, `CMDIChildWnd` objektu.

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

*lpszClassName*<br/>
Odkazuje na řetězec znaků zakončené znakem null, který názvy třídy Windows ( [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) struktura). Název třídy může být jakýkoli název zaregistrované [afxregisterwndclass –](application-information-and-management.md#afxregisterwndclass) globální funkce. By měl mít hodnotu NULL pro standardní `CMDIChildWnd`.

*lpszWindowName*<br/>
Odkazuje na řetězec znaků zakončené znakem null představující název okna. Používá jako text záhlaví.

*dwStyle*<br/>
Určuje, okno [styl](../../mfc/reference/styles-used-by-mfc.md#window-styles) atributy. Styl WS_CHILD je povinný.

*Rect*<br/>
Obsahuje velikost a umístění okna. `rectDefault` Hodnota umožňuje Windows zadejte velikost a umístění nového `CMDIChildWnd`.

*pParentWnd*<br/>
Určuje nadřazeného okna. Pokud má hodnotu NULL, použije se hlavního okna aplikace.

*pContext*<br/>
Určuje [ccreatecontext –](../../mfc/reference/ccreatecontext-structure.md) struktury. Tento parametr může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Aktuálně aktivní okna podřízeného rámce MDI určit titulek okna nadřazeného rámce. Tato funkce je zakázaná vypnutím FWS_ADDTOTITLE bit stylu okna podřízeného rámce.

Rozhraní volá tuto funkci člena v reakci na příkaz uživatele vytvořit podřízené okno a rozhraní používá *pContext* parametr správně podřízeného okna připojit k aplikaci. Při volání `Create`, *pContext* může mít hodnotu NULL.

### <a name="example"></a>Příklad

Příklad 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Příklad

Příklad 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

##  <a name="getmdiframe"></a>  CMDIChildWnd::GetMDIFrame

Voláním této funkce vrátí nadřazeného rámce MDI.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rámec nadřazeného okna MDI.

### <a name="remarks"></a>Poznámky

Vrátí rámec je příkaz dva nadřazené položky odebrat ze `CMDIChildWnd` a je nadřazené okno MDICLIENT, který spravuje typu `CMDIChildWnd` objektu. Volání [getparent –](../../mfc/reference/cwnd-class.md#getparent) členská funkce se vraťte `CMDIChildWnd` nadřazeného objektu okamžité MDICLIENT jako dočasný `CWnd` ukazatele.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

##  <a name="mdiactivate"></a>  CMDIChildWnd::MDIActivate

Voláním této členské funkce aktivovat podřízené okno MDI nezávisle na okno rámce MDI.

```
void MDIActivate();
```

### <a name="remarks"></a>Poznámky

Když se stane aktivní rámec, aktivuje se i podřízené okno, které poslední aktivace.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

##  <a name="mdidestroy"></a>  CMDIChildWnd::MDIDestroy

Voláním této členské funkce pro zrušení podřízené okno MDI.

```
void MDIDestroy();
```

### <a name="remarks"></a>Poznámky

Členská funkce Odebere název podřízeného okna z okna rámce a deaktivuje podřízené okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

##  <a name="mdimaximize"></a>  CMDIChildWnd::MDIMaximize

Voláním této členské funkce pro maximalizaci podřízené okno MDI.

```
void MDIMaximize();
```

### <a name="remarks"></a>Poznámky

Když je podřízené okno maximalizované, ho tak, aby klientské oblasti vyplnění klientské oblasti okna rámce Windows změní. Windows umístí ovládací prvek nabídky podřízené okno rámce nabídek tak, aby uživatel mohl obnovit nebo podřízené okno zavřít a přidá název podřízené okno na titulek okna rámce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

##  <a name="mdirestore"></a>  CMDIChildWnd::MDIRestore

Voláním této členské funkce obnovení ze minimalizované nebo maximalizované velikost podřízené okno MDI.

```
void MDIRestore();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

##  <a name="sethandles"></a>  CMDIChildWnd::SetHandles

Nastaví obslužné rutiny pro prostředky nabídky a akcelerátoru.

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
Popisovač nabídky prostředků.

*hAccel*<br/>
Popisovač prostředku akcelerátoru.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavíte nabídky a akcelerátor prostředky používané tímto objektem podřízené okno MDI.

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC MDI](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC MDIDOCVW](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC SNAPVW](../../visual-cpp-samples.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd – třída](../../mfc/reference/cmdiframewnd-class.md)
