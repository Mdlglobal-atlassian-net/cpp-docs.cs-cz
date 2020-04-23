---
title: Třída CMDIChildWnd
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
ms.openlocfilehash: a547a21b96d035f507e749aeb19f891175498d5d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754573"
---
# <a name="cmdichildwnd-class"></a>Třída CMDIChildWnd

Poskytuje funkce podřízeného okna rozhraní Windows s více dokumenty (MDI) spolu s členy pro správu okna.

## <a name="syntax"></a>Syntaxe

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Vytvoří `CMDIChildWnd` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMDIChildWnd::Vytvořit](#create)|Vytvoří podřízené okno Windows MDI přidružené k objektu. `CMDIChildWnd`|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Vrátí nadřazený rámec MDI klientského okna MDI.|
|[CMDIChildWnd::MDIAktivovat](#mdiactivate)|Aktivuje toto podřízené okno MDI.|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Zničí toto podřízené okno MDI.|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Maximalizuje toto podřízené okno MDI.|
|[CMDIChildWnd::MDIRestore](#mdirestore)|Obnoví toto podřízené okno MDI z maximalizované nebo minimalizované velikosti.|
|[CMDIChildWnd::SetHandles](#sethandles)|Nastaví úchyty pro prostředky nabídky a akcelerátoru.|

## <a name="remarks"></a>Poznámky

Podřízené okno MDI vypadá podobně jako typické okno rámce, s tím rozdílem, že podřízené okno MDI se zobrazí uvnitř okna rámce MDI, nikoli na ploše. Podřízené okno MDI nemá vlastní panel nabídek, ale místo toho sdílí nabídku okna rámce MDI. Rozhraní framework automaticky změní nabídku rámce MDI tak, aby představovala aktuálně aktivní podřízené okno MDI.

Chcete-li vytvořit užitečné podřízené okno MDI `CMDIChildWnd`pro vaši aplikaci, odvodit třídu z . Přidejte členské proměnné do odvozené třídy pro ukládání dat specifických pro vaši aplikaci. Implementujte členské funkce obslužné rutiny zpráv a mapu zpráv v odvozené třídě k určení, co se stane, když jsou zprávy směrovány do okna.

Existují tři způsoby, jak vytvořit podřízené okno MDI:

- Přímo postavit `Create`pomocí .

- Přímo postavit `LoadFrame`pomocí .

- Nepřímo jej vytvořte pomocí šablony dokumentu.

Před `Create` voláním `LoadFrame`nebo , je nutné vytvořit objekt okno rámce na haldě pomocí **c++ nový** operátor. Před `Create` voláním můžete také zaregistrovat třídu okna s globální funkcí [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) a nastavit styly ikon a tříd pro rámec.

Pomocí `Create` členské funkce předajte parametry vytvoření rámce jako okamžité argumenty.

`LoadFrame`vyžaduje méně argumentů než `Create`aplikace a místo toho načte většinu svých výchozích hodnot z prostředků, včetně titulku, ikony, tabulky akcelerátoru a nabídky rámce. Chcete-li `LoadFrame`být přístupné podle , všechny tyto prostředky musí mít stejné ID prostředku (například IDR_MAINFRAME).

Pokud `CMDIChildWnd` objekt obsahuje zobrazení a dokumenty, jsou vytvořeny nepřímo rámci namísto přímo programátorem. Objekt `CDocTemplate` orchestruje vytvoření rámce, vytvoření obsahujících pohledů a připojení pohledů k příslušnému dokumentu. Parametry konstruktoru `CDocTemplate` `CRuntimeClass` určují tři zúčastněné třídy (dokument, rámeček a zobrazení). Objekt `CRuntimeClass` je používán rozhraním dynamicky vytvářet nové rámce, když je určen uživatelem (například pomocí příkazu File New nebo příkazu MDI Window New).

Frame-window třídy odvozené z `CMDIChildWnd` musí být deklarována s DECLARE_DYNCREATE, aby výše uvedený RUNTIME_CLASS mechanismus pracovat správně.

Třída `CMDIChildWnd` dědí většinu své výchozí `CFrameWnd`implementace z . Podrobný seznam těchto funkcí naleznete v popisu třídy [CFrameWnd.](../../mfc/reference/cframewnd-class.md) Třída `CMDIChildWnd` má následující další funkce:

- Ve spojení `CMultiDocTemplate` s třídou sdílí více `CMDIChildWnd` objektů ze stejné šablony dokumentu stejnou nabídku, která šetří systémové prostředky systému Windows.

- Aktuálně aktivní podřízená nabídka podřízeného okna MDI zcela nahradí nabídku okna rámce MDI a titulek aktuálně aktivního podřízeného okna MDI je přidán do titulku okna rámce MDI. Další příklady funkcí podřízeného okna MDI, které jsou implementovány ve `CMDIFrameWnd` spojení s oknem rámce MDI, naleznete v popisu třídy.

Nepoužívejte operátor **delete** jazyka C++ ke zničení okna rámce. Místo toho použijte `CWnd::DestroyWindow`. Implementace `CFrameWnd` `PostNcDestroy` odstraní objekt C++ při zničení okna. Když uživatel zavře okno rámce, `OnClose` bude volat `DestroyWindow`výchozí obslužná rutina .

Další informace `CMDIChildWnd`naleznete v tématu [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a>CMDIChildWnd::CMDIChildWnd

Volání k `CMDIChildWnd` vytvoření objektu.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Poznámky

Volání `Create` k vytvoření viditelného okna.

### <a name="example"></a>Příklad

  Viz příklad pro [CMDIChildWnd::Create](#create).

## <a name="cmdichildwndcreate"></a><a name="create"></a>CMDIChildWnd::Vytvořit

Volání této členské funkce vytvořit podřízené okno Windows MDI a připojit k objektu. `CMDIChildWnd`

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

*název lpszClassName*<br/>
Odkazuje na řetězec znaků ukončený nulou, který pojmenovává třídu systému Windows (strukturu [WNDCLASS).](/windows/win32/api/winuser/ns-winuser-wndclassw) Název třídy může být libovolný název registrovaný globální funkcí [AfxRegisterWndClass.](application-information-and-management.md#afxregisterwndclass) By měla být `CMDIChildWnd`NULL pro standard .

*lpszNázev_okna*<br/>
Odkazuje na řetězec znaků ukončený hodnotou null, který představuje název okna. Používá se jako text pro záhlaví.

*dwStyl*<br/>
Určuje atributy [stylu](../../mfc/reference/styles-used-by-mfc.md#window-styles) okna. Je vyžadován WS_CHILD styl.

*Rect*<br/>
Obsahuje velikost a umístění okna. Hodnota `rectDefault` umožňuje systému Windows určit velikost `CMDIChildWnd`a umístění nového .

*pParentWnd*<br/>
Určuje nadřazený okno. Pokud null, hlavní okno aplikace se používá.

*pKontext*<br/>
Určuje strukturu [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md) Tento parametr může být NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Aktuálně aktivní okno podřízeného rámce MDI může určit titulek okna nadřazeného rámečku. Tato funkce je zakázána vypnutím bitu FWS_ADDTOTITLE stylu podřízeného okna rámce.

Rozhraní Framework volá tuto členskou funkci v reakci na příkaz uživatele k vytvoření podřízeného okna a framework používá parametr *pContext* k správnému připojení podřízeného okna k aplikaci. Při volání `Create`může být *pContext* null.

### <a name="example"></a>Příklad

Příklad 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Příklad

Příklad 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

## <a name="cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a>CMDIChildWnd::GetMDIFrame

Volání této funkce vrátí nadřazený rámec MDI.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno nadřazeného rámce MDI.

### <a name="remarks"></a>Poznámky

Vrácený rámec je dva `CMDIChildWnd` nadřazené položky odebrány z a je `CMDIChildWnd` nadřazený okna typu MDICLIENT, který spravuje objekt. Volání [GetParent](../../mfc/reference/cwnd-class.md#getparent) členské funkce `CMDIChildWnd` vrátit objektu bezprostřední MDICLIENT `CWnd` nadřazený jako dočasný ukazatel.

### <a name="example"></a>Příklad

  Viz příklad pro [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

## <a name="cmdichildwndmdiactivate"></a><a name="mdiactivate"></a>CMDIChildWnd::MDIAktivovat

Volání této členské funkce k aktivaci podřízené okno MDI nezávisle na okně rámce MDI.

```cpp
void MDIActivate();
```

### <a name="remarks"></a>Poznámky

Jakmile se rámeček aktivuje, aktivuje se také podřízené okno, které bylo naposledy aktivováno.

### <a name="example"></a>Příklad

  Viz příklad pro [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

## <a name="cmdichildwndmdidestroy"></a><a name="mdidestroy"></a>CMDIChildWnd::MDIDestroy

Volání této členské funkce zničit podřízené okno MDI.

```cpp
void MDIDestroy();
```

### <a name="remarks"></a>Poznámky

Členská funkce odebere název podřízeného okna z okna rámce a deaktivuje podřízené okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

## <a name="cmdichildwndmdimaximize"></a><a name="mdimaximize"></a>CMDIChildWnd::MDIMaximize

Volání této členské funkce maximalizovat podřízené okno MDI.

```cpp
void MDIMaximize();
```

### <a name="remarks"></a>Poznámky

Když je podřízené okno maximalizováno, systém Windows změní jeho velikost tak, aby jeho klientská oblast vyplnila klientskou oblast okna rámce. Systém Windows umístí nabídku Ovládací prvek podřízeného okna do řádku nabídek rámce, aby uživatel mohl obnovit nebo zavřít podřízené okno a přidá název podřízeného okna do názvu okna rámce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

## <a name="cmdichildwndmdirestore"></a><a name="mdirestore"></a>CMDIChildWnd::MDIRestore

Volání této členské funkce obnovit podřízené okno MDI z maximalizované nebo minimalizované velikosti.

```cpp
void MDIRestore();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

## <a name="cmdichildwndsethandles"></a><a name="sethandles"></a>CMDIChildWnd::SetHandles

Nastaví úchyty pro prostředky nabídky a akcelerátoru.

```cpp
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Parametry

*hNabídka*<br/>
Popisovač prostředku nabídky.

*hAccel*<br/>
Popisovač prostředku akcelerátoru.

### <a name="remarks"></a>Poznámky

Volání této funkce nastavit nabídku a akcelerátor prostředky používané objektu podřízené okno MDI.

## <a name="see-also"></a>Viz také

[MDI vzorku knihovny MFc](../../overview/visual-cpp-samples.md)<br/>
[MFC Vzorek MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Třída CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Třída CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)
