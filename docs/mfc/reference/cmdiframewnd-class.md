---
title: Třída CMDIFrameWnd
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
ms.openlocfilehash: a6e68f6368a7b45e0a566a7d2d12f23a9cd62b12
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370060"
---
# <a name="cmdiframewnd-class"></a>Třída CMDIFrameWnd

Poskytuje funkce okna rámce rozhraní Windows multiple document interface (MDI) spolu s členy pro správu okna.

## <a name="syntax"></a>Syntaxe

```
class CMDIFrameWnd : public CFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMDIFrameWnd::CMDIFrameWnd](#cmdiframewnd)|Vytvoří `CMDIFrameWnd`.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMDIFrameWnd::Vytvořit klienta](#createclient)|Vytvoří okno Windows MDICLIENT `CMDIFrameWnd`pro tento . Nazývá `OnCreate` členská funkce `CWnd`.|
|[CMDIFrameWnd::CreateNewChild](#createnewchild)|Vytvoří nové podřízené okno.|
|[CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup)|Vrátí rozbalovací nabídku Okno.|
|[CMDIFrameWnd::MDIAktivovat](#mdiactivate)|Aktivuje jiné podřízené okno MDI.|
|[CMDIFrameWnd::MDICascade](#mdicascade)|Uspořádá všechna podřízená okna ve kaskádovém formátu.|
|[CMDIFrameWnd::MDIGetActive](#mdigetactive)|Načte aktuálně aktivní podřízené okno MDI spolu s příznakem označujícím, zda je podřízený maximalizovaný.|
|[CMDIFrameWnd::MDIIconArrange](#mdiiconarrange)|Uspořádá všechna minimalizovaná podřízená okna dokumentu.|
|[CMDIFrameWnd::MDIMaximize](#mdimaximize)|Maximalizuje podřízené okno MDI.|
|[CMDIFrameWnd::MDINext](#mdinext)|Aktivuje podřízené okno bezprostředně za aktuálně aktivní podřízené okno a umístí aktuálně aktivní podřízené okno za všechna ostatní podřízená okna.|
|[CMDIFrameWnd::MDIPrev](#mdiprev)|Aktivuje předchozí podřízené okno a umístí aktuálně aktivní podřízené okno bezprostředně za něj.|
|[CMDIFrameWnd::MDIRestore](#mdirestore)|Obnoví podřízené okno MDI z maximalizované nebo minimalizované velikosti.|
|[CMDIFrameWnd::MDISetMenu](#mdisetmenu)|Nahradí nabídku okna rámce MDI, rozbalovací nabídky Okno nebo obojí.|
|[CMDIFrameWnd::MDITile](#mditile)|Uspořádá všechna podřízená okna v kachlová formátu.|

## <a name="remarks"></a>Poznámky

Chcete-li vytvořit užitečné okno rámce MDI pro `CMDIFrameWnd`vaši aplikaci, odvodit třídu z . Přidejte členské proměnné do odvozené třídy pro ukládání dat specifických pro vaši aplikaci. Implementujte členské funkce obslužné rutiny zpráv a mapu zpráv v odvozené třídě k určení, co se stane, když jsou zprávy směrovány do okna.

Okno rámce MDI můžete vytvořit voláním členské funkce `CFrameWnd` [Create](../../mfc/reference/cframewnd-class.md#create) nebo [LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe) aplikace .

Před `Create` voláním `LoadFrame`nebo , je nutné vytvořit objekt okna rámce na haldě pomocí **c++ nový** operátor. Před `Create` voláním můžete také zaregistrovat třídu okna s globální funkcí [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) a nastavit styly ikon a tříd pro rámec.

Pomocí `Create` členské funkce předajte parametry vytvoření rámce jako okamžité argumenty.

`LoadFrame`vyžaduje méně argumentů než `Create`aplikace a místo toho načte většinu svých výchozích hodnot z prostředků, včetně titulku, ikony, tabulky akcelerátoru a nabídky rámce. Chcete-li získat `LoadFrame`přístup pomocí , musí mít všechny tyto prostředky stejné ID prostředku (například IDR_MAINFRAME).

Ačkoli `MDIFrameWnd` je odvozen `CFrameWnd`od , rám window `CMDIFrameWnd` třídy odvozené z nemusí být deklarována s `DECLARE_DYNCREATE`.

Třída `CMDIFrameWnd` dědí většinu své výchozí `CFrameWnd`implementace z . Podrobný seznam těchto funkcí naleznete v popisu třídy [CFrameWnd.](../../mfc/reference/cframewnd-class.md) Třída `CMDIFrameWnd` má následující další funkce:

- Okno rámce MDI spravuje okno MDICLIENT a přemisťuje ho ve spojení s ovládacími panely. Okno klienta MDI je přímým nadřazeným oknem podřízeného rámce MDI. Styly WS_HSCROLL a WS_VSCROLL `CMDIFrameWnd` okna zadané v okně klienta MDI, nikoli v okně hlavního rámce, takže uživatel může posouvat klientskou oblast MDI (například ve Správci programů systému Windows).

- Okno rámce MDI vlastní výchozí nabídku, která se používá jako řádek nabídek, pokud není k dispozici žádné aktivní podřízené okno MDI. Pokud je aktivní podřízená mdi, panel nabídek okna rámce MDI je automaticky nahrazen nabídkou podřízeného okna MDI.

- Okno rámce MDI pracuje ve spojení s aktuální podřízené okno MDI, pokud existuje. Například příkaz zprávy jsou delegovány na aktuálně aktivní Podřízené MDI před okno rámce MDI.

- Okno rámce MDI má výchozí obslužné rutiny pro následující standardní příkazy nabídky Window:

  - ID_WINDOW_TILE_VERT

  - ID_WINDOW_TILE_HORZ

  - ID_WINDOW_CASCADE

  - ID_WINDOW_ARRANGE

- Okno rámce MDI má také implementaci ID_WINDOW_NEW, která vytvoří nový snímek a zobrazení v aktuálním dokumentu. Aplikace může přepsat tyto výchozí implementace příkazů přizpůsobit zpracování oken MDI.

Nepoužívejte operátor **delete** jazyka C++ ke zničení okna rámce. Místo toho použijte `CWnd::DestroyWindow`. Implementace `CFrameWnd` `PostNcDestroy` odstraní objekt C++ při zničení okna. Když uživatel zavře okno rámce, `OnClose` bude volat `DestroyWindow`výchozí obslužná rutina .

Další informace `CMDIFrameWnd`naleznete v tématu [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cmdiframewndcmdiframewnd"></a><a name="cmdiframewnd"></a>CMDIFrameWnd::CMDIFrameWnd

Vytvoří `CMDIFrameWnd` objekt.

```
CMDIFrameWnd();
```

### <a name="remarks"></a>Poznámky

Volání `Create` majestát `LoadFrame` nebo členské funkce k vytvoření viditelného okna rámce MDI.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#13](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_1.cpp)]

## <a name="cmdiframewndcreateclient"></a><a name="createclient"></a>CMDIFrameWnd::Vytvořit klienta

Vytvoří okno klienta MDI, `CMDIChildWnd` které spravuje objekty.

```
virtual BOOL CreateClient(
    LPCREATESTRUCT lpCreateStruct,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parametry

*lpCreateStruct*<br/>
Dlouhý ukazatel na strukturu [CREATESTRUCT.](/windows/win32/api/winuser/ns-winuser-createstructw)

*nabídka pWindow*<br/>
Ukazatel na rozbalovací nabídku Okno.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce by měla `OnCreate` být volána, pokud přepíšete přímo členovou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#14](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_2.cpp)]

## <a name="cmdiframewndcreatenewchild"></a><a name="createnewchild"></a>CMDIFrameWnd::CreateNewChild

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
Run-time třídy podřízené okno, které mají být vytvořeny.

*nZdroj*<br/>
ID sdílených prostředků přidružených k podřízenému oknu.

*hNabídka*<br/>
Nabídka podřízeného okna.

*hAccel*<br/>
Akcelerátor podřízeného okna.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k vytvoření podřízených oken okna rámce MDI.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#15](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_3.cpp)]

## <a name="cmdiframewndgetwindowmenupopup"></a><a name="getwindowmenupopup"></a>CMDIFrameWnd::GetWindowMenuPopup

Volání této členské funkce získat popisovač aktuální rozbalovací menu s názvem "Okno" (rozbalovací nabídka s položkami nabídky pro správu oken MDI).

```
virtual HMENU GetWindowMenuPopup(HMENU hMenuBar);
```

### <a name="parameters"></a>Parametry

*hPanel menu*<br/>
Aktuální řádek nabídek.

### <a name="return-value"></a>Návratová hodnota

Rozbalovací nabídka Okno, pokud existuje; jinak NULL.

### <a name="remarks"></a>Poznámky

Výchozí implementace vyhledá rozbalovací nabídku obsahující standardní příkazy nabídky Okna, jako jsou ID_WINDOW_NEW a ID_WINDOW_TILE_HORZ.

Přepište tuto členskou funkci, pokud máte nabídku Window, která nepoužívá ID standardního příkazu nabídky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#16](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_4.cpp)]

## <a name="cmdiframewndmdiactivate"></a><a name="mdiactivate"></a>CMDIFrameWnd::MDIAktivovat

Aktivuje jiné podřízené okno MDI.

```
void MDIActivate(CWnd* pWndActivate);
```

### <a name="parameters"></a>Parametry

*pWndAktivovat*<br/>
Odkazuje na podřízené okno MDI, které má být aktivováno.

### <a name="remarks"></a>Poznámky

Tato členská funkce odešle [zprávu WM_MDIACTIVATE](../../mfc/reference/cwnd-class.md#onmdiactivate) aktivovanému a deaktivovanému oknu.

Toto je stejná zpráva, která je odeslána, pokud uživatel změní fokus na podřízené okno MDI pomocí myši nebo klávesnice.

> [!NOTE]
> Podřízené okno MDI je aktivováno nezávisle na okně rámce MDI. Když se rámeček aktivuje, podřízené okno, které bylo naposledy aktivováno, je odeslána [zpráva WM_NCACTIVATE](../../mfc/reference/cwnd-class.md#onncactivate) nakreslení aktivního rámečku okna a panelu titulků, ale neobdrží další WM_MDIACTIVATE zprávu.

### <a name="example"></a>Příklad

Viz příklad pro [CMDIFrameWnd::GetWindowMenuPopup](#getwindowmenupopup).

## <a name="cmdiframewndmdicascade"></a><a name="mdicascade"></a>CMDIFrameWnd::MDICascade

Uspořádá všechna podřízená okna MDI v kaskádovém formátu.

```
void MDICascade();
void MDICascade(int nType);
```

### <a name="parameters"></a>Parametry

*nTyp*<br/>
Určuje kaskádový příznak. Lze zadat pouze následující příznak: MDITILE_SKIPDISABLED, který zabraňuje kaskádovému přemísťování podřízených oken MDI.

### <a name="remarks"></a>Poznámky

První verze `MDICascade`aplikace , bez parametrů, kaskády všechny Podřízené okna MDI, včetně těch zakázaných. Druhá verze volitelně není kaskádově zakázána podřízená okna MDI, pokud zadáte MDITILE_SKIPDISABLED pro parametr *nType.*

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#17](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_5.cpp)]

## <a name="cmdiframewndmdigetactive"></a><a name="mdigetactive"></a>CMDIFrameWnd::MDIGetActive

Načte aktuální aktivní podřízené okno MDI spolu s příznakem označujícím, zda je podřízené okno maximalizováno.

```
CMDIChildWnd* MDIGetActive(BOOL* pbMaximized = NULL) const;
```

### <a name="parameters"></a>Parametry

*pbMaximalizce*<br/>
Ukazatel na vrácenou hodnotu BOOL. Pokud je okno maximalizováno, nastavte při návratu hodnotu TRUE; jinak FALSE.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktivní podřízené okno MDI.

### <a name="example"></a>Příklad

Viz příklad pro [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdiiconarrange"></a><a name="mdiiconarrange"></a>CMDIFrameWnd::MDIIconArrange

Uspořádá všechna minimalizovaná podřízená okna dokumentu.

```
void MDIIconArrange();
```

### <a name="remarks"></a>Poznámky

Nemá vliv na podřízená okna, která nejsou minimalizována.

### <a name="example"></a>Příklad

Viz příklad pro [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="cmdiframewndmdimaximize"></a><a name="mdimaximize"></a>CMDIFrameWnd::MDIMaximize

Maximalizuje zadané podřízené okno MDI.

```
void MDIMaximize(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno maximalizovat.

### <a name="remarks"></a>Poznámky

Když je podřízené okno maximalizováno, systém Windows změní jeho velikost tak, aby jeho klientská oblast vyplnila okno klienta. Systém Windows umístí nabídku Ovládací prvek podřízeného okna do panelu nabídek rámce, aby uživatel mohl okno podřízeného okna obnovit nebo zavřít. Přidá také název podřízeného okna do názvu okna rámce.

Pokud je aktivováno jiné podřízené okno MDI při maximalizaci aktuálně aktivního podřízeného okna MDI, obnoví systém Windows aktuálně aktivní podřízenou aplikaci a maximalizuje nově aktivované podřízené okno.

### <a name="example"></a>Příklad

Viz příklad pro [CMDIChildWnd::MDIMaximize](../../mfc/reference/cmdichildwnd-class.md#mdimaximize).

## <a name="cmdiframewndmdinext"></a><a name="mdinext"></a>CMDIFrameWnd::MDINext

Aktivuje podřízené okno bezprostředně za aktuálně aktivní podřízené okno a umístí aktuálně aktivní podřízené okno za všechna ostatní podřízená okna.

```
void MDINext();
```

### <a name="remarks"></a>Poznámky

Pokud je maximalizovano aktuálně aktivní podřízené okno MDI, členská funkce obnoví aktuálně aktivní podřízenou aplikaci a maximalizuje nově aktivovanou podřízenou aplikaci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#18](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_6.cpp)]

## <a name="cmdiframewndmdiprev"></a><a name="mdiprev"></a>CMDIFrameWnd::MDIPrev

Aktivuje předchozí podřízené okno a umístí aktuálně aktivní podřízené okno bezprostředně za něj.

```
void MDIPrev();
```

### <a name="remarks"></a>Poznámky

Pokud je maximalizovano aktuálně aktivní podřízené okno MDI, členská funkce obnoví aktuálně aktivní podřízenou aplikaci a maximalizuje nově aktivovanou podřízenou aplikaci.

## <a name="cmdiframewndmdirestore"></a><a name="mdirestore"></a>CMDIFrameWnd::MDIRestore

Obnoví podřízené okno MDI z maximalizované nebo minimalizované velikosti.

```
void MDIRestore(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno obnovit.

### <a name="example"></a>Příklad

Viz příklad pro [CMDIChildWnd::MDIRestore](../../mfc/reference/cmdichildwnd-class.md#mdirestore).

## <a name="cmdiframewndmdisetmenu"></a><a name="mdisetmenu"></a>CMDIFrameWnd::MDISetMenu

Nahradí nabídku okna rámce MDI, rozbalovací nabídky Okno nebo obojí.

```
CMenu* MDISetMenu(
    CMenu* pFrameMenu,
    CMenu* pWindowMenu);
```

### <a name="parameters"></a>Parametry

*pFrameMenu*<br/>
Určuje nabídku nové nabídky frame-window. Pokud null, nabídka se nezmění.

*nabídka pWindow*<br/>
Určuje nabídku nové rozbalovací nabídky Okno. Pokud null, nabídka se nezmění.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nabídku okna rámce nahrazentouto zprávou. Ukazatel může být dočasné a by neměly být uloženy pro pozdější použití.

### <a name="remarks"></a>Poznámky

Po `MDISetMenu`volání musí aplikace volat člennou `CWnd` funkci [DrawMenuBar,](../../mfc/reference/cwnd-class.md#drawmenubar) aby aktualizovala řádek nabídek.

Pokud toto volání nahradí rozbalovací nabídku Okno, položky nabídky podřízeného okna MDI budou odebrány z předchozí nabídky Okno a přidány do nové rozbalovací nabídky Okno.

Pokud je podřízené okno MDI maximalizováno a toto volání nahradí nabídku okna rámce MDI, budou nabídky Control a ovládací prvky obnovení odebrány z předchozí nabídky okna rámce a přidány do nové nabídky.

Nevolejte tuto členská funkci, pokud používáte rozhraní pro správu podřízených oken MDI.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#19](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_7.cpp)]

[!code-cpp[NVC_MFCWindowing#20](../../mfc/reference/codesnippet/cpp/cmdiframewnd-class_8.cpp)]

## <a name="cmdiframewndmditile"></a><a name="mditile"></a>CMDIFrameWnd::MDITile

Uspořádá všechna podřízená okna v kachlová formátu.

```
void MDITile();
void MDITile(int nType);
```

### <a name="parameters"></a>Parametry

*nTyp*<br/>
Určuje příznak dlaždic. Tento parametr může být libovolný z následujících příznaků:

- MDITILE_HORIZONTAL dlaždice MDI podřízených oken tak, aby jedno okno se zobrazí nad jiným.

- MDITILE_SKIPDISABLED Zabrání tomu, aby byla vedlelová na sachlována podřízená okna MDI.

- MDITILE_VERTICAL dlaždice MDI podřízených oken tak, aby se jedno okno zobrazí vedle druhého.

### <a name="remarks"></a>Poznámky

První verze `MDITile`aplikace , bez parametrů, dlaždice okna svisle pod Windows verze 3.1 a novější. Druhá verze dlaždice okna svisle nebo vodorovně, v závislosti na hodnotě *parametru nType.*

### <a name="example"></a>Příklad

Viz příklad pro [CMDIFrameWnd::MDICascade](#mdicascade).

## <a name="see-also"></a>Viz také

[MDI vzorku knihovny MFc](../../overview/visual-cpp-samples.md)<br/>
[MFC Vzorek MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Ukázka knihovny MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[Třída CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Třída CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)
