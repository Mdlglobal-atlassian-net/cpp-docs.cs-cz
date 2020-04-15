---
title: Třída CMiniFrameWnd
ms.date: 11/04/2016
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
ms.openlocfilehash: e9b91161f4207f4d2215d8777beade93617ddfac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319822"
---
# <a name="cminiframewnd-class"></a>Třída CMiniFrameWnd

Představuje okno rámce s poloviční výškou, které je obvykle vidět kolem plovoucích panelů nástrojů.

## <a name="syntax"></a>Syntaxe

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|Vytvoří `CMiniFrameWnd` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMiniFrameWnd::Vytvořit](#create)|Vytvoří `CMiniFrameWnd` objekt po konstrukci.|
|[CMiniFrameWnd::CreateEx](#createex)|Vytvoří `CMiniFrameWnd` objekt (s dalšími možnostmi) po konstrukci.|

## <a name="remarks"></a>Poznámky

Tato okna s minirámečkem se chovají jako normální okna rámů, kromě toho, že nemají tlačítka nebo nabídky minimalizovat / maximalizovat a stačí je pouze jedním kliknutím na systémové menu zavřít.

Chcete-li `CMiniFrameWnd` použít objekt, nejprve definujte objekt. Potom voláním členské funkce [Vytvořit](#create) zobrazíte okno minirámečku.

Další informace o použití `CMiniFrameWnd` objektů naleznete v článku [Ukotvení a plovoucí panely nástrojů](../../mfc/docking-and-floating-toolbars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cminiframewndcminiframewnd"></a><a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd

Vytvoří `CMiniFrameWnd` objekt, ale nevytvoří okno.

```
CMiniFrameWnd();
```

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit okno, zavolejte [CMiniFrameWnd::Create](#create).

## <a name="cminiframewndcreate"></a><a name="create"></a>CMiniFrameWnd::Vytvořit

Vytvoří okno minirámečku systému Windows `CMiniFrameWnd` a připojí jej k objektu.

```
virtual BOOL Create(
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>Parametry

*název lpClassName*<br/>
Odkazuje na řetězec znaků ukončený nulou, který pojmenovává třídu systému Windows. Název třídy může být libovolný název registrovaný s globální funkcí [AfxRegisterWndClass.](application-information-and-management.md#afxregisterwndclass) Pokud null, třída okna bude registrována pro vás rámci. Knihovna MFC poskytuje výchozí třídě následující styly a atributy:

- Nastaví bit stylu CS_DBLCLKS, který odesílá poklepání na zprávy do procedury okna, když uživatel poklepe myší.

- Nastaví bity stylu CS_HREDRAW a CS_VREDRAW, které směrují obsah klientské oblasti, která má být překreslena při změně velikosti okna.

- Nastaví kurzor třídy na standardní IDC_ARROW systému Windows.

- Nastaví stopu pozadí třídy na hodnotu NULL, takže okno nevymaže jeho pozadí.

- Nastaví ikonu třídy na standardní ikonu loga Windows s mávajícívlajkou.

- Nastaví okno na výchozí velikost a umístění, jak je uvedeno systémem Windows.

*lpNázev_okna*<br/>
Odkazuje na řetězec znaků ukončený hodnotou null, který obsahuje název okna.

*dwStyl*<br/>
Určuje atributy stylu okna. Mohou zahrnovat standardní styly oken a jeden nebo více následujících speciálních stylů:

- MFS_MOVEFRAME Umožňuje přesunutí okna minirámečku kliknutím na libovolný okraj okna, nikoli pouze na titulek.

- MFS_4THICKFRAME Zakáže změna velikosti okna minirámečku.

- MFS_SYNCACTIVE Synchronizuje aktivaci okna minirámečku s aktivací nadřazeného okna.

- MFS_THICKFRAME Umožňuje velikost okna mini-frame tak malé, jak umožňuje obsah klientské oblasti.

- MFS_BLOCKSYSMENU Zakáže přístup k systémové nabídce a nabídce ovládacího prvku a převede je na část titulku (záhlaví).

Viz [CWnd::Create](../../mfc/reference/cwnd-class.md#create) pro popis možných hodnot stylu okna. Typická kombinace používaná pro okna s minirámy je WS_POPUP&#124;WS_CAPTION WS_CAPTION&#124;WS_SYSMENU.

*Rect*<br/>
Struktura `RECT` určující požadované rozměry okna.

*pParentWnd*<br/>
Odkazuje na nadřazené okno. Pro okna nejvyšší úrovně použijte hodnotu NULL.

*Nid*<br/>
Pokud je okno minirámečku vytvořeno jako podřízené okno, jedná se o identifikátor podřízeného ovládacího prvku; jinak 0.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

`Create`inicializuje název třídy a název okna okna a zaregistruje výchozí hodnoty pro jeho styl a nadřazený.

## <a name="cminiframewndcreateex"></a><a name="createex"></a>CMiniFrameWnd::CreateEx

Vytvoří `CMiniFrameWnd` objekt.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>Parametry

*dwExStyl*<br/>
Určuje rozšířený styl vytvářeného souboru. `CMiniFrameWnd` Použijte některý ze [stylů rozšířeného okna](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) v okně.

*název lpClassName*<br/>
Odkazuje na řetězec znaků ukončený nulou, který pojmenovává třídu systému Windows (strukturu [WNDCLASS).](/windows/win32/api/winuser/ns-winuser-wndclassw) Název třídy může být libovolný název registrovaný s globální funkcí [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) nebo libovolný majek řazených názvů třídovládacích prvků. Nesmí být null.

*lpNázev_okna*<br/>
Odkazuje na řetězec znaků ukončený hodnotou null, který obsahuje název okna.

*dwStyl*<br/>
Určuje atributy stylu okna. Viz [Styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [CWnd::Create](../../mfc/reference/cwnd-class.md#create) pro popis možných hodnot.

*Rect*<br/>
Velikost a umístění okna v klientských souřadnicích *pParentWnd*.

*pParentWnd*<br/>
Odkazuje na nadřazený objekt okna.

*Nid*<br/>
Identifikátor podřízeného okna.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA při úspěchu, nepravda při neúspěchu.

### <a name="remarks"></a>Poznámky

Parametry `CreateEx` určují WNDCLASS, styl okna a (volitelně) počáteční pozici a velikost okna. `CreateEx`také určuje nadřazené okno (pokud existuje) a ID.

Při `CreateEx` spuštění systémwindows odešle do okna zprávy [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)a [WM_CREATE.](../../mfc/reference/cwnd-class.md#oncreate)

Chcete-li rozšířit výchozí zpracování zpráv, odvodit třídu z `CMiniFrameWnd`, přidat mapu zpráv do nové třídy a poskytnout členské funkce pro výše uvedené zprávy. Přepište `OnCreate`, například provést potřebnou inicializaci pro novou třídu.

Přepsat další `On` *zprávy* zprávy obslužné rutiny přidat další funkce odvozené třídy.

Pokud je uveden WS_VISIBLE styl, systém Windows odešle okno všechny zprávy potřebné k aktivaci a zobrazení okna. Pokud styl okna určuje záhlaví, zobrazí se v záhlaví název okna, na který ukazuje parametr *lpszWindowName.*

Parametr *dwStyle* může být libovolná kombinace [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

Okna panelu nástrojů palety starého stylu již nejsou podporována. Starý styl, který neměl tlačítko Zavřít "X", byl podporován při spuštění aplikace knihovny MFC v předchozích verzích systému Windows, ale již není podporován v jazyce Visual C++.NET. Nyní je podporován pouze nový styl WS_EX_TOOLWINDOW; Popis tohoto stylu naleznete v tématu [Rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="see-also"></a>Viz také

[Třída CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CFrameWnd](../../mfc/reference/cframewnd-class.md)
