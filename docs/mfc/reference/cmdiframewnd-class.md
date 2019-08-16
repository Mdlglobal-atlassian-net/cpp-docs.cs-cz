---
title: CMDIFrameWnd – – třída
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
ms.openlocfilehash: 20d74030cdc90ed2e1a7809c121967e74db21b4a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505570"
---
# <a name="cmdiframewnd-class"></a>CMDIFrameWnd – – třída

Poskytuje funkce okna rámce rozhraní Windows MDI (Multiple Document Interface) spolu se členy pro správu okna.

## <a name="syntax"></a>Syntaxe

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMDIFrameWnd –:: CMDIFrameWnd –](#cmdiframewnd)|`CMDIFrameWnd`Vytvoří.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMDIFrameWnd –:: CreateClient](#createclient)|Vytvoří okno MDICLIENT pro `CMDIFrameWnd`Windows. Volá se `OnCreate` členskou `CWnd`funkcí.|
|[CMDIFrameWnd –:: CreateNewChild](#createnewchild)|Vytvoří nové podřízené okno.|
|[CMDIFrameWnd –:: GetWindowMenuPopup](#getwindowmenupopup)|Vrátí místní nabídku okna.|
|[CMDIFrameWnd –:: MDIActivate](#mdiactivate)|Aktivuje jiné podřízené okno MDI.|
|[CMDIFrameWnd –:: MDICascade](#mdicascade)|Uspořádá všechna podřízená okna v Kaskádovém formátu.|
|[CMDIFrameWnd –:: MDIGetActive](#mdigetactive)|Načte aktuálně aktivní podřízené okno MDI spolu s příznakem označujícím, zda je podřízený objekt maximalizován.|
|[CMDIFrameWnd –:: MDIIconArrange](#mdiiconarrange)|Uspořádá všechna minimalizovaná podřízená okna dokumentu.|
|[CMDIFrameWnd –:: MDIMaximize](#mdimaximize)|Maximalizuje podřízené okno MDI.|
|[CMDIFrameWnd –:: MDINext](#mdinext)|Aktivuje podřízené okno hned za aktuálně aktivního podřízeného okna a umístí aktuálně aktivní podřízené okno za všechna ostatní podřízená okna.|
|[CMDIFrameWnd –:: MDIPrev](#mdiprev)|Aktivuje předchozí podřízené okno a hned za něj umístí aktuálně aktivní podřízené okno.|
|[CMDIFrameWnd –:: MDIRestore](#mdirestore)|Obnoví podřízené okno MDI z maximalizace nebo minimalizované velikosti.|
|[CMDIFrameWnd –:: MDISetMenu](#mdisetmenu)|Nahrazuje nabídku okna rámce MDI, místní nabídky okna nebo obou.|
|[CMDIFrameWnd –:: MDITile](#mditile)|Uspořádá všechna podřízená okna v dlaždicovém formátu.|

## <a name="remarks"></a>Poznámky

Chcete-li vytvořit užitečné okno rámce MDI pro aplikaci, odvodit třídu z `CMDIFrameWnd`. Přidejte členské proměnné do odvozené třídy pro uložení dat specifických pro vaši aplikaci. Implementací členských funkcí obslužných rutin zpráv a mapy zpráv v odvozené třídě určíte, co se stane, když se zprávy přesměrují do okna.

Můžete vytvořit okno rámce MDI voláním členské funkce [Create](../../mfc/reference/cframewnd-class.md#create) nebo [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) objektu `CFrameWnd`.

Před voláním `Create` nebo `LoadFrame`je nutné vytvořit objekt okna rámce na haldě pomocí C++ operátoru **New** . Před voláním `Create` můžete také zaregistrovat třídu okna s globální funkcí [AfxRegisterWndClass –](application-information-and-management.md#afxregisterwndclass) k nastavení ikony a stylů třídy pro daný rámec.

`Create` Pomocí členské funkce předejte parametry vytváření rámce jako okamžité argumenty.

`LoadFrame`vyžaduje méně argumentů než `Create`a místo toho načte většinu jeho výchozích hodnot z prostředků, včetně titulku rámce, ikony, tabulky akcelerátorů a nabídky. Aby k nim `LoadFrame`bylo možné využívat všechny tyto prostředky, musí mít stejné ID prostředku (například IDR_MAINFRAME).

I `MDIFrameWnd` když je odvozen `CFrameWnd`z, třída okna rámce odvozená `CMDIFrameWnd` od nemusí být deklarována `DECLARE_DYNCREATE`s.

Třída zdědí většinu výchozí implementace z `CFrameWnd`. `CMDIFrameWnd` Podrobný seznam těchto funkcí najdete v popisu třídy [CFrameWnd](../../mfc/reference/cframewnd-class.md) . `CMDIFrameWnd` Třída má následující další funkce:

- Okno rámce MDI spravuje okno MDICLIENT a přemístění ho v kombinaci s ovládacími panely. Okno klienta MDI je přímým nadřazeným oknem podřízených oken MDI. Styly oken WS_HSCROLL a WS_VSCROLL určené pro `CMDIFrameWnd` použití v klientském okně MDI, nikoli v hlavním okně rámce, takže uživatel může přejít do klientské oblasti MDI (například ve Správci programů systému Windows).

- Okno rámce MDI vlastní výchozí nabídku, která se používá jako panel nabídek, když není k dispozici žádné aktivní podřízené okno MDI. Je-li k dispozici aktivní podřízený objekt MDI, je panel nabídek okna MDI automaticky nahrazen podnabídkou podřízeného okna MDI.

- Okno rámce MDI funguje ve spojení s aktuálním podřízeným oknem MDI, pokud je jeden. Například zprávy příkazů jsou delegovány na aktuálně aktivní podřízenou položku MDI před oknem rámce MDI.

- Okno rámce MDI má výchozí obslužné rutiny pro následující standardní příkazy nabídky okna:

    - ID_WINDOW_TILE_VERT

    - ID_WINDOW_TILE_HORZ

    - ID_WINDOW_CASCADE

    - ID_WINDOW_ARRANGE

- Okno rámce MDI má také implementaci ID_WINDOW_NEW, která vytváří nový rámec a zobrazení v aktuálním dokumentu. Aplikace může přepsat tyto výchozí implementace příkazů pro přizpůsobení zpracování okna MDI.

Nepoužívejte C++ operátor **Delete** ke zničení okna rámce. Místo nich se používá `CWnd::DestroyWindow`. Implementace odstraní C++ objekt, když dojde ke zničení okna. `PostNcDestroy` `CFrameWnd` Když uživatel zavře okno rámce, výchozí `OnClose` obslužná rutina bude volat. `DestroyWindow`

Další informace o `CMDIFrameWnd`naleznete v tématu [okna](../../mfc/frame-windows.md)s rámečkem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cmdiframewnd"></a>CMDIFrameWnd –:: CMDIFrameWnd –

`CMDIFrameWnd` Vytvoří objekt.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Poznámky

Chcete-li `LoadFrame` vytvořit viditelné okno rámce MDI, zavolejte členskou funkci nebo.`Create`

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

##  <a name="createclient"></a>CMDIFrameWnd –:: CreateClient

Vytvoří okno klienta MDI, které spravuje `CMDIChildWnd` objekty.

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parametry

*lpCreateStruct*<br/>
Dlouhý ukazatel na strukturu [CREATESTRUCT –](/windows/win32/api/winuser/ns-winuser-createstructw) .

*pWindowMenu*<br/>
Ukazatel na místní nabídku okna.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce by měla být volána, pokud `OnCreate` přepíšete členskou funkci přímo.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

##  <a name="createnewchild"></a>CMDIFrameWnd –:: CreateNewChild

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
Běhová Třída podřízeného okna, které má být vytvořeno.

*nResource*<br/>
ID sdílených prostředků přidružených k podřízenému oknu.

*hMenu*<br/>
Nabídka podřízeného okna.

*hAccel*<br/>
Akcelerátor podřízeného okna.

### <a name="remarks"></a>Poznámky

Pomocí této funkce lze vytvořit podřízená okna okna rámce MDI.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

##  <a name="getwindowmenupopup"></a>CMDIFrameWnd –:: GetWindowMenuPopup

Voláním této členské funkce získáte popisovač aktuální místní nabídky s názvem "Window" (místní nabídka s položkami nabídky pro správu okna MDI).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Parametry

*hMenuBar*<br/>
Aktuální řádek nabídek.

### <a name="return-value"></a>Návratová hodnota

Místní nabídka okna, pokud existuje; jinak NULL.

### <a name="remarks"></a>Poznámky

Výchozí implementace vyhledá místní nabídku obsahující standardní příkazy nabídky okna, jako je například ID_WINDOW_NEW a ID_WINDOW_TILE_HORZ.

Tuto členskou funkci přepište, pokud máte nabídku okna, která nepoužívá standardní ID příkazů nabídky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

##  <a name="mdiactivate"></a>CMDIFrameWnd –:: MDIActivate

Aktivuje jiné podřízené okno MDI.

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Parametry

*pWndActivate*<br/>
Odkazuje na podřízené okno MDI, které se má aktivovat.

### <a name="remarks"></a>Poznámky

Tato členská funkce pošle zprávu [WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) do aktivovaného podřízeného okna a podřízeného okna, které se deaktivuje.

Jedná se o stejnou zprávu, která se odešle, když uživatel změní fokus na podřízené okno MDI pomocí myši nebo klávesnice.

> [!NOTE]
>  Podřízené okno MDI je aktivováno nezávisle na okně rámce MDI. Když bude rámec aktivní, pošle se podřízené okno, které bylo naposledy aktivováno, zprávu [WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) , která Nakreslí aktivní rámec okna a záhlaví, ale neobdrží jinou zprávu WM_MDIACTIVATE.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMDIFrameWnd –:: GetWindowMenuPopup](#getwindowmenupopup).

##  <a name="mdicascade"></a>CMDIFrameWnd –:: MDICascade

Uspořádá všechna podřízená okna MDI v Kaskádovém formátu.

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Parametry

*nType*<br/>
Určuje příznak Cascade. Lze zadat pouze následující příznak: MDITILE_SKIPDISABLED, která znemožňuje, aby se zakázaná podřízená okna MDI mohla přenést.

### <a name="remarks"></a>Poznámky

První verze `MDICascade`, bez parametrů, uspořádá všechna podřízená okna MDI, včetně zakázaných. Druhá verze se volitelně nevypne, pokud zadáte MDITILE_SKIPDISABLED pro parametr *noznámení* .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

##  <a name="mdigetactive"></a>CMDIFrameWnd –:: MDIGetActive

Načte aktuální aktivní podřízené okno MDI spolu s příznakem označujícím, zda je podřízené okno maximalizováno.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Parametry

*pbMaximized*<br/>
Ukazatel na návratovou hodnotu BOOL. Nastavte na hodnotu TRUE při návratu, pokud se okno maximalizuje; v opačném případě FALSE.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní podřízené okno MDI.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMDIChildWnd –:: MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

##  <a name="mdiiconarrange"></a>CMDIFrameWnd –:: MDIIconArrange

Uspořádá všechna minimalizovaná podřízená okna dokumentu.

```
void MDIIconArrange();
```

### <a name="remarks"></a>Poznámky

Nemá vliv na podřízené systémy Windows, které nejsou minimalizovány.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMDIFrameWnd –:: MDICascade](#mdicascade).

##  <a name="mdimaximize"></a>CMDIFrameWnd –:: MDIMaximize

Maximalizuje zadané podřízené okno MDI.

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, aby se maximalizoval.

### <a name="remarks"></a>Poznámky

Když dojde k maximalizaci podřízeného okna, systém Windows změní jeho velikost tak, aby jeho klientské oblasti naplnila okno klienta. Systém Windows umístí řídicí nabídku podřízeného okna do řádku nabídek rámce, takže uživatel může obnovit nebo zavřít podřízené okno. Také přidá název podřízeného okna do nadpisu okna s rámečkem.

Pokud je při maximalizaci aktivního podřízeného okna MDI aktivováno jiné podřízené okno MDI, systém Windows obnoví aktuálně aktivní podřízenou položku a maximalizuje nově aktivované podřízené okno.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMDIChildWnd –:: MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

##  <a name="mdinext"></a>CMDIFrameWnd –:: MDINext

Aktivuje podřízené okno hned za aktuálně aktivního podřízeného okna a umístí aktuálně aktivní podřízené okno za všechna ostatní podřízená okna.

```
void MDINext();
```

### <a name="remarks"></a>Poznámky

Pokud je aktuálně aktivní podřízené okno MDI maximalizované, vrátí členské funkce aktuálně aktivní podřízenou položku a maximalizuje nově aktivovaného podřízeného.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

##  <a name="mdiprev"></a>CMDIFrameWnd –:: MDIPrev

Aktivuje předchozí podřízené okno a hned za něj umístí aktuálně aktivní podřízené okno.

```
void MDIPrev();
```

### <a name="remarks"></a>Poznámky

Pokud je aktuálně aktivní podřízené okno MDI maximalizované, vrátí členské funkce aktuálně aktivní podřízenou položku a maximalizuje nově aktivovaného podřízeného.

##  <a name="mdirestore"></a>CMDIFrameWnd –:: MDIRestore

Obnoví podřízené okno MDI z maximalizace nebo minimalizované velikosti.

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, které má být obnoveno.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMDIChildWnd –:: MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

##  <a name="mdisetmenu"></a>CMDIFrameWnd –:: MDISetMenu

Nahrazuje nabídku okna rámce MDI, místní nabídky okna nebo obou.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parametry

*pFrameMenu*<br/>
Určuje nabídku nové nabídky okna s rámečkem. Pokud má hodnotu NULL, nabídka se nezmění.

*pWindowMenu*<br/>
Určuje nabídku nového okna v místní nabídce. Pokud má hodnotu NULL, nabídka se nezmění.

### <a name="return-value"></a>Návratová hodnota

V nabídce okna s rámečkem se nahradí ukazatel na tuto zprávu. Ukazatel může být dočasný a neměl by být uložen pro pozdější použití.

### <a name="remarks"></a>Poznámky

Po volání `MDISetMenu`musí aplikace zavolat členskou funkci `CWnd` [DrawMenuBar](../../mfc/reference/cwnd-class.md#drawmenubar) pro aktualizaci řádku nabídek.

Pokud toto volání nahradí místní nabídku okna, položky nabídky pro podřízený objekt MDI se z předchozí nabídky okna odeberou a přidají se do místní nabídky nové okno.

Pokud je podřízené okno MDI maximalizované a toto volání nahrazuje nabídku okna MDI, nabídka ovládacího prvku a ovládací prvky obnovení jsou odebrány z předchozí nabídky okna s rámečkem a přidány do nové nabídky.

Tuto členskou funkci Nevolejte, pokud použijete rozhraní ke správě podřízených oken MDI.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

##  <a name="mditile"></a>CMDIFrameWnd –:: MDITile

Uspořádá všechna podřízená okna v dlaždicovém formátu.

```
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Parametry

*nType*<br/>
Určuje příznak dláždění. Tento parametr může být jeden z následujících příznaků:

- MDITILE_HORIZONTAL dlaždice MDI podřízená okna, aby se jedno okno zobrazovalo nad jiným.

- MDITILE_SKIPDISABLED zabraňuje dlaždici zakázaných podřízených oken MDI.

- MDITILE_VERTICAL dlaždice MDI podřízená okna, aby se jedno okno zobrazilo vedle jiného.

### <a name="remarks"></a>Poznámky

První verze `MDITile`, bez parametrů, dlaždice Windows svisle pod Windows verze 3,1 a novější. Druhá verze dlaždice Windows svisle nebo vodorovně dlaždici v závislosti na hodnotě parametru *noznámení* .

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CMDIFrameWnd –:: MDICascade](#mdicascade).

## <a name="see-also"></a>Viz také:

[Ukázka MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[MDIDOCVW Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[SNAPVW Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[CMDIChildWnd – třída](../../mfc/reference/cmdichildwnd-class.md)
