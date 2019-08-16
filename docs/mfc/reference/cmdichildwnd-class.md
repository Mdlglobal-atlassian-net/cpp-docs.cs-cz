---
title: CMDIChildWnd – – třída
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
ms.openlocfilehash: 09a9846cc3d242ef7d812cb31b4dcdd515d5f6ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506083"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd – – třída

Poskytuje funkce podřízeného okna rozhraní Windows MDI (Multiple Document Interface) spolu se členy pro správu okna.

## <a name="syntax"></a>Syntaxe

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMDIChildWnd –:: CMDIChildWnd –](#cmdichildwnd)|`CMDIChildWnd` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMDIChildWnd –:: Create](#create)|Vytvoří podřízené okno Windows MDI spojené s `CMDIChildWnd` objektem.|
|[CMDIChildWnd –:: GetMDIFrame](#getmdiframe)|Vrátí nadřazený rámec MDI okna klienta MDI.|
|[CMDIChildWnd –:: MDIActivate](#mdiactivate)|Aktivuje toto podřízené okno MDI.|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Odstraní toto podřízené okno MDI.|
|[CMDIChildWnd –:: MDIMaximize](#mdimaximize)|Maximalizuje toto podřízené okno MDI.|
|[CMDIChildWnd –:: MDIRestore](#mdirestore)|Obnoví toto podřízené okno MDI z maximalizace nebo minimalizované velikosti.|
|[CMDIChildWnd –:: SetHandles](#sethandles)|Nastaví popisovače pro prostředky nabídky a akcelerátoru.|

## <a name="remarks"></a>Poznámky

Podřízené okno MDI vypadá podobně jako typické okno rámce, s tím rozdílem, že se podřízené okno MDI zobrazuje v rámci okna rámce MDI, nikoli na ploše. Podřízené okno MDI nemá vlastní panel nabídek, ale místo toho sdílí nabídku okna rámce MDI. Rozhraní automaticky změní nabídku rámce MDI tak, aby představovala aktuálně aktivní podřízené okno MDI.

Pro vytvoření užitečného podřízeného okna MDI pro aplikaci odvodit třídu z `CMDIChildWnd`. Přidejte členské proměnné do odvozené třídy pro uložení dat specifických pro vaši aplikaci. Implementací členských funkcí obslužných rutin zpráv a mapy zpráv v odvozené třídě určíte, co se stane, když se zprávy přesměrují do okna.

Existují tři způsoby, jak vytvořit podřízené okno MDI:

- Přímo jej Sestavte pomocí `Create`.

- Přímo jej Sestavte pomocí `LoadFrame`.

- Nepřímo ji vytvoří pomocí šablony dokumentu.

Před voláním `Create` nebo `LoadFrame`je nutné vytvořit objekt rámečku okna na haldě pomocí C++ operátoru **New** . Před voláním `Create` můžete také zaregistrovat třídu okna s globální funkcí [AfxRegisterWndClass –](application-information-and-management.md#afxregisterwndclass) k nastavení ikony a stylů třídy pro daný rámec.

`Create` Pomocí členské funkce předejte parametry vytváření rámce jako okamžité argumenty.

`LoadFrame`vyžaduje méně argumentů než `Create`a místo toho načte většinu jeho výchozích hodnot z prostředků, včetně titulku rámce, ikony, tabulky akcelerátorů a nabídky. Aby k nim měli `LoadFrame`přístup všechny tyto prostředky, musí mít stejné ID prostředku (například IDR_MAINFRAME).

`CMDIChildWnd` Pokud objekt obsahuje zobrazení a dokumenty, jsou vytvořeny nepřímo rozhraním, nikoli přímo programátorem. `CDocTemplate` Objekt orchestruje vytvoření snímku, vytvoření obsahujícího zobrazení a připojení zobrazení k příslušnému dokumentu. Parametry `CDocTemplate` konstruktoru`CRuntimeClass` určují, jaké tři třídy jsou zahrnuty (dokument, rámeček a zobrazení). `CRuntimeClass` Objekt je používán rozhraním k dynamickému vytváření nových rámců, pokud jsou zadány uživatelem (například pomocí příkazu soubor nový nebo nový příkaz MDI v okně Nový).

Třída okna rámce odvozená z `CMDIChildWnd` musí být deklarovaná s DECLARE_DYNCREATE, aby výše uvedený mechanismus RUNTIME_CLASS správně fungoval.

Třída zdědí většinu výchozí implementace z `CFrameWnd`. `CMDIChildWnd` Podrobný seznam těchto funkcí najdete v popisu třídy [CFrameWnd](../../mfc/reference/cframewnd-class.md) . `CMDIChildWnd` Třída má následující další funkce:

- Ve spojení s `CMultiDocTemplate` třídou více `CMDIChildWnd` objektů ze stejné šablony dokumentu sdílejí stejnou nabídku a ukládá systémové prostředky systému Windows.

- V aktuálně aktivní nabídce podřízeného okna MDI se úplně nahradila nabídka okna rámce MDI a titulek aktuálně aktivního podřízeného okna MDI se přidá do titulku okna MDI. Další příklady funkcí podřízeného okna MDI, které jsou implementovány ve spojení s oknem rámce MDI, naleznete `CMDIFrameWnd` v popisu třídy.

Nepoužívejte C++ operátor **Delete** ke zničení okna rámce. Místo nich se používá `CWnd::DestroyWindow`. Implementace odstraní C++ objekt, když dojde ke zničení okna. `PostNcDestroy` `CFrameWnd` Když uživatel zavře okno rámce, výchozí `OnClose` obslužná rutina bude volat. `DestroyWindow`

Další informace o `CMDIChildWnd`naleznete v tématu [okna](../../mfc/frame-windows.md)s rámečkem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cmdichildwnd"></a>CMDIChildWnd –:: CMDIChildWnd –

Volání konstruktoru `CMDIChildWnd` objektu.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Poznámky

Voláním `Create` pro vytvoření viditelného okna.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMDIChildWnd –:: Create](#create).

##  <a name="create"></a>CMDIChildWnd –:: Create

Zavolejte tuto členskou funkci pro vytvoření podřízeného okna Windows MDI a připojte ho k `CMDIChildWnd` objektu.

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
Odkazuje na řetězec znaků zakončený hodnotou null, který má název třídy systému Windows ( [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) struktura). Název třídy může být jakýkoli název zaregistrovaný s globální funkcí [AfxRegisterWndClass –](application-information-and-management.md#afxregisterwndclass) . Pro standard `CMDIChildWnd`by měla být null.

*lpszWindowName*<br/>
Odkazuje na řetězec znaků zakončený hodnotou null, který představuje název okna. Slouží jako text záhlaví.

*dwStyle*<br/>
Určuje atributy [stylu](../../mfc/reference/styles-used-by-mfc.md#window-styles) okna. Je vyžadován styl WS_CHILD.

*OBD*<br/>
Obsahuje velikost a polohu okna. Hodnota umožňuje systému Windows určit velikost a polohu nového `CMDIChildWnd`. `rectDefault`

*pParentWnd*<br/>
Určuje nadřazený prvek okna. Pokud má hodnotu NULL, použije se hlavní okno aplikace.

*pContext*<br/>
Určuje strukturu [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . Tento parametr může mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

V aktuálně aktivním okně podřízeného rámce MDI lze určit titulek nadřazeného okna rámce. Tato funkce je zakázaná vypnutím FWS_ADDTOTITLE stylu podřízeného okna rámce.

Rozhraní volá tuto členskou funkci v reakci na uživatelský příkaz pro vytvoření podřízeného okna a rozhraní používá parametr *pContext* pro správné připojení podřízeného okna k aplikaci. Když zavoláte `Create`, může mít *pContext* hodnotu null.

### <a name="example"></a>Příklad

Příklad 1:

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Příklad

Příklad 2:

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

##  <a name="getmdiframe"></a>CMDIChildWnd –:: GetMDIFrame

Voláním této funkce vrátíte nadřazený rámec MDI.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno nadřazeného rámce MDI.

### <a name="remarks"></a>Poznámky

Vrácený rámec má dva rodiče odebrané z `CMDIChildWnd` a je nadřazeným oknem okna typu MDICLIENT, které `CMDIChildWnd` spravuje objekt. Zavolejte funkci [GetParent](../../mfc/reference/cwnd-class.md#getparent) member, která vrátí `CMDIChildWnd` bezprostřední nadřazený objekt MdiClient objektu jako dočasný `CWnd` ukazatel.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMDIFrameWnd –:: MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

##  <a name="mdiactivate"></a>CMDIChildWnd –:: MDIActivate

Zavolejte tuto členskou funkci pro aktivaci podřízeného okna MDI nezávisle na okně rámce MDI.

```
void MDIActivate();
```

### <a name="remarks"></a>Poznámky

Když se rámec změní na aktivní, aktivuje se i podřízené okno, které bylo naposledy aktivováno.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CMDIFrameWnd –:: GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

##  <a name="mdidestroy"></a>CMDIChildWnd –:: MDIDestroy

Chcete-li zničit podřízené okno MDI, zavolejte tuto členskou funkci.

```
void MDIDestroy();
```

### <a name="remarks"></a>Poznámky

Členská funkce odstraní název podřízeného okna z okna rámce a deaktivuje podřízené okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

##  <a name="mdimaximize"></a>CMDIChildWnd –:: MDIMaximize

Zavolejte tuto členskou funkci pro maximalizaci podřízeného okna MDI.

```
void MDIMaximize();
```

### <a name="remarks"></a>Poznámky

Když dojde k maximalizaci podřízeného okna, systém Windows změní jeho velikost tak, aby jeho oblast klienta naplnila klientské oblasti okna rámce. Systém Windows umístí řídicí nabídku podřízeného okna do řádku nabídek rámce, aby uživatel mohl obnovit nebo zavřít podřízené okno a přidat název podřízeného okna do nadpisu okna rámce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

##  <a name="mdirestore"></a>CMDIChildWnd –:: MDIRestore

Zavolejte tuto členskou funkci pro obnovení podřízeného okna MDI z maximalizace nebo minimalizované velikosti.

```
void MDIRestore();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

##  <a name="sethandles"></a>CMDIChildWnd –:: SetHandles

Nastaví popisovače pro prostředky nabídky a akcelerátoru.

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Parametry

*hMenu*<br/>
Popisovač prostředku nabídky

*hAccel*<br/>
Popisovač prostředku akcelerátoru.

### <a name="remarks"></a>Poznámky

Voláním této funkce nastavíte prostředky nabídky a akcelerátoru používané objektem podřízeného okna MDI.

## <a name="see-also"></a>Viz také:

[Ukázka MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[MDIDOCVW Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[SNAPVW Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd – třída](../../mfc/reference/cmdiframewnd-class.md)
