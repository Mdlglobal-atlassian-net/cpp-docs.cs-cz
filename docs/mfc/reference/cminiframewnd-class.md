---
title: CMiniFrameWnd – třída
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
ms.openlocfilehash: 45b4698cc70487a6c3fe1470fe27f7b5c4f95402
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504592"
---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd – třída

Představuje okno rámce s poloviční výškou, které se obvykle zobrazuje okolo plovoucích panelů nástrojů.

## <a name="syntax"></a>Syntaxe

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|`CMiniFrameWnd` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMiniFrameWnd:: Create](#create)|`CMiniFrameWnd` Vytvoří objekt po konstrukci.|
|[CMiniFrameWnd::CreateEx](#createex)|`CMiniFrameWnd` Vytvoří objekt (s dalšími možnostmi) po konstrukci.|

## <a name="remarks"></a>Poznámky

Tyto zkrácené systémy Windows se chovají stejně jako normální okna s rámečkem, s tím rozdílem, že nemají tlačítka pro minimalizaci, maximalizaci a nabídky, a stačí pouze jedním kliknutím na systémovou nabídku, která je odpustit.

Chcete-li `CMiniFrameWnd` použít objekt, nejprve jej definujte. Potom zavolejte funkci [vytvořit](#create) členskou funkci pro zobrazení okna se zkráceným rámcem.

Další informace o tom, jak používat `CMiniFrameWnd` objekty, najdete v článku [docked a plovoucí panely nástrojů](../../mfc/docking-and-floating-toolbars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd

`CMiniFrameWnd` Vytvoří objekt, ale nevytvoří okno.

```
CMiniFrameWnd();
```

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit okno, zavolejte [CMiniFrameWnd:: Create](#create).

##  <a name="create"></a>CMiniFrameWnd:: Create

Vytvoří okno se zkráceným rámcem Windows a připojí ho k `CMiniFrameWnd` objektu.

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

*lpClassName*<br/>
Odkazuje na řetězec znaků zakončený hodnotou null, který pojmenovává třídu systému Windows. Název třídy může být jakýkoli název zaregistrovaný s globální funkcí [AfxRegisterWndClass –](application-information-and-management.md#afxregisterwndclass) . Pokud má hodnotu NULL, třída okna bude pro vás zaregistrována rozhraním. Knihovna MFC poskytuje výchozí třídě následující styly a atributy:

- Nastaví styl bitového CS_DBLCLKS, který odešle dvakrát klikněte na zprávy, když uživatel dvakrát klikne na myš.

- Nastaví styl bitů CS_HREDRAW a CS_VREDRAW, který směruje obsah oblasti klienta, která se má překreslit, když se změní velikost okna.

- Nastaví kurzor třídy na IDC_ARROW Windows Standard.

- Nastaví štětec pozadí třídy na hodnotu NULL, takže okno neodstraní své pozadí.

- Nastaví ikonu třídy na standardní ikonu logo Windows mávající-Flag.

- Nastaví výchozí velikost a polohu okna tak, jak je uvedeno v systému Windows.

*lpWindowName*<br/>
Odkazuje na řetězec znaků zakončený hodnotou null, který obsahuje název okna.

*dwStyle*<br/>
Určuje atributy stylu okna. Ty mohou zahrnovat standardní styly oken a jeden nebo více následujících speciálních stylů:

- MFS_MOVEFRAME umožňuje přesunout okno se zkráceným rámcem kliknutím na libovolné místo v okně, nikoli pouze na titulek.

- MFS_4THICKFRAME zakáže změnu velikosti okna se zkrácenými snímky.

- MFS_SYNCACTIVE synchronizuje aktivaci okna se zkráceným rámcem do aktivace jeho nadřazeného okna.

- MFS_THICKFRAME umožňuje, aby okno s minimálním rámcem bylo co nejmenší velikosti jako obsah klientské oblasti.

- MFS_BLOCKSYSMENU zakáže přístup k systémové nabídce a nabídce ovládacího prvku a převede je na část titulku (záhlaví).

Popis možných hodnot stylu okna naleznete v tématu [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) . Typická kombinace použitá pro okna se zkrácenými rámečky je&#124;WS_POPUP&#124;WS_CAPTION WS_SYSMENU.

*OBD*<br/>
`RECT` Struktura určující požadované rozměry okna.

*pParentWnd*<br/>
Odkazuje na nadřazené okno. Pro okna nejvyšší úrovně použijte hodnotu NULL.

*nID*<br/>
Pokud je okno se zkráceným rámcem vytvořeno jako podřízené okno, jedná se o identifikátor podřízeného ovládacího prvku; v opačném případě 0.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`Create`Inicializuje název třídy okna a název okna a registruje výchozí hodnoty pro svůj styl a nadřazenou položku.

##  <a name="createex"></a>CMiniFrameWnd::CreateEx

`CMiniFrameWnd` Vytvoří objekt.

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

*dwExStyle*<br/>
Určuje rozšířený styl `CMiniFrameWnd` , který je vytvářen. Použijte libovolné [Rozšířené styly okna](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) v okně.

*lpClassName*<br/>
Odkazuje na řetězec znaků zakončený hodnotou null, který má název třídy systému Windows ( [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) struktura). Název třídy může být libovolný název zaregistrovaný s globální funkcí [AfxRegisterWndClass –](application-information-and-management.md#afxregisterwndclass) nebo libovolným předdefinovaným názvem třídy ovládacího prvku. Nesmí mít hodnotu NULL.

*lpWindowName*<br/>
Odkazuje na řetězec znaků zakončený hodnotou null, který obsahuje název okna.

*dwStyle*<br/>
Určuje atributy stylu okna. Popis možných hodnot naleznete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) .

*OBD*<br/>
Velikost a poloha okna v souřadnicích klienta *pParentWnd*.

*pParentWnd*<br/>
Odkazuje na objekt nadřazeného okna.

*nID*<br/>
Identifikátor podřízeného okna.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE při úspěchu, FALSE při selhání.

### <a name="remarks"></a>Poznámky

`CreateEx` Parametry určují WNDCLASS, styl okna a (volitelně) počáteční polohu a velikost okna. `CreateEx`Určuje také nadřazené okno (pokud existuje) a ID.

Když `CreateEx` se spustí, Windows pošle do okna zprávy [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)a [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) .

Chcete-li zvětšit výchozí zpracování zprávy, odvodit třídu `CMiniFrameWnd`z, přidat do nové třídy mapu zprávy a poskytnout členské funkce pro výše uvedené zprávy. Přepsání `OnCreate`, například k provedení potřebné inicializace pro novou třídu.

Přepište `On`další obslužné rutiny zpráv *zpráv* pro přidání dalších funkcí do odvozené třídy.

Pokud je zadán styl WS_VISIBLE, Windows pošle okno všechny zprávy vyžadované k aktivaci a zobrazení okna. Určuje-li styl okna záhlaví, zobrazí se v záhlaví zobrazený název okna, na které se odkazuje parametr *lpszWindowName* .

Parametr *dwStyle* může být libovolná kombinace [stylů oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).

Okna panelu nástrojů palety původní styl již nejsou podporována. Starý styl, který neměl tlačítko pro uzavření "X", byl podporován při spuštění aplikace MFC v předchozích verzích systému Windows, ale již není podporován v aplikaci Visual C++.NET. Nyní je podporován pouze nový styl WS_EX_TOOLWINDOW; Popis tohoto stylu naleznete v tématu [Rozšířené styly oken](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="see-also"></a>Viz také:

[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)
