---
title: CControlBar – – třída
ms.date: 11/04/2016
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
ms.openlocfilehash: 41e40b3da7b4a294fe396a9d93f7c6a93593ff95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866426"
---
# <a name="ccontrolbar-class"></a>CControlBar – – třída

Základní třída pro třídy ovládacích panelů [CStatusBar –](../../mfc/reference/cstatusbar-class.md), [CToolBar –](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar –](../../mfc/reference/crebar-class.md)a [COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Syntaxe

```
class CControlBar : public CWnd
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CControlBar –:: CControlBar –](#ccontrolbar)|Vytvoří objekt `CControlBar`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CControlBar –:: CalcDynamicLayout](#calcdynamiclayout)|Vrací velikost dynamického ovládacího panelu jako objekt [CSize](../../atl-mfc-shared/reference/csize-class.md) .|
|[CControlBar –:: CalcFixedLayout](#calcfixedlayout)|Vrátí velikost ovládacího panelu jako objekt [CSize](../../atl-mfc-shared/reference/csize-class.md) .|
|[CControlBar –:: CalcInsideRect](#calcinsiderect)|Vrátí aktuální rozměry oblasti ovládacího panelu; včetně ohraničení.|
|[CControlBar –::D oPaint](#dopaint)|Vykreslí ohraničení a úchyt ovládacího panelu.|
|[CControlBar –::D rawBorders](#drawborders)|Vykreslí ohraničení ovládacího panelu.|
|[CControlBar –::D rawGripper](#drawgripper)|Vykreslí úchyt ovládacího panelu.|
|[CControlBar –:: EnableDocking](#enabledocking)|Umožňuje, aby byl ovládací panel ukotven nebo plovoucí.|
|[CControlBar –:: GetBarStyle](#getbarstyle)|Načte nastavení stylu ovládacího panelu.|
|[CControlBar –:: GetBorders](#getborders)|Načte hodnoty ohraničení ovládacího panelu.|
|[CControlBar –:: GetCount](#getcount)|Vrátí počet prvků bez HWND na ovládacím panelu.|
|[CControlBar –:: GetDockingFrame](#getdockingframe)|Vrátí ukazatel na rámec, ke kterému je ovládací panel ukotven.|
|[CControlBar –::-float](#isfloating)|Vrací nenulovou hodnotu, pokud je ovládací panel, který je v seznamu, plovoucí ovládací panel.|
|[CControlBar –:: OnUpdateCmdUI](#onupdatecmdui)|Volá obslužné rutiny uživatelského rozhraní příkazu.|
|[CControlBar –:: SetBarStyle](#setbarstyle)|Upraví nastavení stylu ovládacího panelu.|
|[CControlBar –:: SetBorders](#setborders)|Nastaví hodnoty ohraničení ovládacího panelu.|
|[CControlBar –:: SetInPlaceOwner](#setinplaceowner)|Změní místního vlastníka ovládacího panelu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CControlBar –:: m_bAutoDelete](#m_bautodelete)|Pokud je nenulová, objekt `CControlBar` se odstraní při zničení ovládacího panelu systému Windows.|
|[CControlBar –:: m_pInPlaceOwner](#m_pinplaceowner)|Místní vlastník ovládacího panelu|

## <a name="remarks"></a>Poznámky

Ovládací panel je okno, které je obvykle zarovnáno vlevo nebo vpravo od okna rámce. Může obsahovat podřízené položky, které jsou buď ovládací prvky založené na HWND, což jsou okna, která generují a reagují na zprávy systému Windows nebo položky nezaložené na HWND, které nejsou v systému Windows a jsou spravovány kódem aplikace nebo kódem rozhraní. Příklady ovládacích prvků založených na HWND jsou seznamy a textové ovládací prvky. podokna stavového panelu a tlačítka rastrových obrázků jsou příklady ovládacích prvků založených na jiných než HWND.

Okna ovládacích panelů jsou obvykle podřízená okna nadřazeného okna rámce a jsou obvykle na úrovni zobrazení klienta nebo klienta MDI okna rámce. Objekt `CControlBar` používá informace o tom, že je v obdélníku klienta nadřazeného okna samotné umístění. Pak bude nadřazené okno informovat o tom, kolik místa zůstane v klientské oblasti nadřazeného okna nepřidělené.

Další informace o `CControlBar`najdete v tématech:

- [Ovládací pruhy](../../mfc/control-bars.md)

- [Technická poznámka 31: Ovládací panely](../../mfc/tn031-control-bars.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext. h

##  <a name="calcdynamiclayout"></a>CControlBar –:: CalcDynamicLayout

Rozhraní volá tuto členskou funkci pro výpočet rozměrů dynamického panelu nástrojů.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Parametry

*nLength*<br/>
Požadovaná dimenze ovládacího panelu, buď vodorovně nebo svisle, v závislosti na *dwMode*.

*nMode*<br/>
Následující předdefinované příznaky slouží k určení výšky a šířky dynamického ovládacího panelu. K kombinování příznaků použijte operátor&#124;bitového operátoru OR ().

|Příznaky režimu rozložení|Význam|
|-----------------------|-------------------|
|LM_STRETCH|Určuje, zda má být ovládací panel roztažen na velikost rámečku. Nastaví, zda se nejedná o ukotvený panel (není k dispozici pro docking). Nenastaveno, když je panel ukotven nebo plovoucí (k dispozici pro docking). Pokud je nastaveno, LM_STRETCH ignoruje *nLength* a vrátí rozměry na základě stavu LM_HORZ. LM_STRETCH funguje podobně jako parametr *bStretch* používaný v [CalcFixedLayout](#calcfixedlayout); Další informace o vztahu mezi roztažením a orientací naleznete v této členské funkci.|
|LM_HORZ|Indikuje, že je pruh vodorovně nebo svisle orientovaný. Nastaví, zda je pruh vodorovně orientovaný, a pokud je svisle orientovaný, není nastaven. LM_HORZ funguje podobně jako parametr *bHorz* používaný v [CalcFixedLayout](#calcfixedlayout); Další informace o vztahu mezi roztažením a orientací naleznete v této členské funkci.|
|LM_MRUWIDTH|Naposledy použitá Dynamická šířka. Ignoruje parametr *nLength* a použije zapamatovatelné naposledy použité šířky.|
|LM_HORZDOCK|Vodorovné ukotvené dimenze. Ignoruje parametr *nLength* a vrátí dynamickou velikost s největší šířkou.|
|LM_VERTDOCK|Svislé ukotvené dimenze. Ignoruje parametr *nLength* a vrátí dynamickou velikost s největší výškou.|
|LM_LENGTHY|Nastaví, zda *nLength* indikuje výšku (Y-Direction) místo šířky.|
|LM_COMMIT|Obnoví LM_MRUWIDTH k aktuální šířce plovoucího řídicího panelu.|

### <a name="return-value"></a>Návratová hodnota

Velikost ovládacího panelu (v pixelech) objektu [CSize](../../atl-mfc-shared/reference/csize-class.md)

### <a name="remarks"></a>Poznámky

Přepište tuto členskou funkci tak, aby poskytovala vlastní dynamické rozložení v třídách odvozených od `CControlBar`. Třídy MFC odvozené od `CControlBar`, jako je například [CToolBar –](../../mfc/reference/ctoolbar-class.md), přepíší tuto členskou funkci a poskytují svou vlastní implementaci.

##  <a name="calcfixedlayout"></a>CControlBar –:: CalcFixedLayout

Chcete-li vypočítat vodorovnou velikost ovládacího panelu, zavolejte tuto členskou funkci.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*bStretch*<br/>
Označuje, zda má být pruh roztažen na velikost rámečku. Parametr *bStretch* je nenulový, pokud se nejedná o ukotvený panel (není k dispozici pro dokování) a je 0, pokud je ukotven nebo plovoucí (k dispozici pro docking).

*bHorz*<br/>
Indikuje, že je pruh vodorovně nebo svisle orientovaný. Parametr *bHorz* je nenulový, pokud je pruh vodorovně orientovaný a je 0, pokud je svisle orientovaný.

### <a name="return-value"></a>Návratová hodnota

Velikost ovládacího panelu `CSize` objektu v pixelech.

### <a name="remarks"></a>Poznámky

Ovládací panely, jako jsou panely nástrojů, se dají roztáhnout vodorovně nebo svisle, aby se vešla tlačítka obsažená na ovládacím panelu.

Pokud má *bStretch* hodnotu true, roztáhněte dimenzi podél orientace, kterou poskytuje *bHorz*. Jinými slovy, pokud je *BHORZ* false, ovládací panel je roztažen svisle. Pokud má *bStretch* hodnotu false, nedochází k roztažení. V následující tabulce jsou uvedeny možné permutace a výsledné styly ovládacích panelů, *bStretch* a *bHorz*.

|bStretch|bHorz|Táhnout|Orientace|Docking/neukotvení|
|--------------|-----------|----------------|-----------------|--------------------------|
|PRAVDA|PRAVDA|Horizontální roztažení|Vodorovně orientované|Bez ukotvení|
|PRAVDA|CHYBNÉ|Svislé roztažení|Svisle orientované|Bez ukotvení|
|CHYBNÉ|PRAVDA|Není k dispozici žádná roztažení|Vodorovně orientované|Ukotvení|
|CHYBNÉ|CHYBNÉ|Není k dispozici žádná roztažení|Svisle orientované|Ukotvení|

##  <a name="calcinsiderect"></a>CControlBar –:: CalcInsideRect

Rozhraní volá tuto funkci pro výpočet klientské oblasti ovládacího panelu.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
Obsahuje aktuální rozměry ovládacího panelu; včetně ohraničení.

*bHorz*<br/>
Indikuje, že je pruh vodorovně nebo svisle orientovaný. Parametr *bHorz* je nenulový, pokud je pruh vodorovně orientovaný a je 0, pokud je svisle orientovaný.

### <a name="remarks"></a>Poznámky

Tato funkce je volána před vykreslením ovládacího panelu.

Tuto funkci můžete přepsat, chcete-li přizpůsobit vykreslování ohraničení a úchytového panelu ovládacího panelu.

##  <a name="ccontrolbar"></a>CControlBar –:: CControlBar –

Vytvoří objekt `CControlBar`.

```
CControlBar();
```

##  <a name="dopaint"></a>CControlBar –::D oPaint

Volá se rozhraním, aby se vykreslila ohraničení a úchyt ovládacího panelu.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Odkazuje na kontext zařízení, který se má použít k vykreslování ohraničení a úchytu ovládacího panelu.

### <a name="remarks"></a>Poznámky

Přepsáním této funkce upravíte chování vykreslování ovládacího panelu.

Další metodou přizpůsobení je přepsat `DrawBorders` a `DrawGripper` funkce a přidat vlastní kód kresby pro ohraničení a úchyt. Vzhledem k tomu, že tyto metody jsou volány výchozí `DoPaint` metodou, přepsání `DoPaint` není nutné.

##  <a name="drawborders"></a>CControlBar –::D rawBorders

Volá se rozhraním, aby se vykreslilo ohraničení ovládacího panelu.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Odkazuje na kontext zařízení, který se má použít k vykreslování ohraničení ovládacího panelu.

*OBD*<br/>
Objekt `CRect` obsahující rozměry ovládacího panelu.

### <a name="remarks"></a>Poznámky

Přepsáním této funkce upravíte vzhled ohraničení ovládacích panelů.

##  <a name="drawgripper"></a>CControlBar –::D rawGripper

Volá se rozhraním, aby se vykreslil úchyt ovládacího panelu.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Emulátor*<br/>
Odkazuje na kontext zařízení, který se má použít pro vykreslování úchytu ovládacího panelu.

*OBD*<br/>
Objekt `CRect` obsahující rozměry úchytu ovládacího panelu.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci, chcete-li přizpůsobit vzhled úchytu ovládacího panelu.

##  <a name="enabledocking"></a>CControlBar –:: EnableDocking

Voláním této funkce povolíte ukotvení řídicího panelu.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

*dwDockStyle*<br/>
Určuje, zda ovládací panel podporuje ukotvení a strany jeho nadřazeného okna, ve kterém lze ovládací panel ukotvit, pokud je podporován. Může se jednat o jednu nebo více z následujících možností:

- CBRS_ALIGN_TOP povoluje ukotvení v horní části klientské oblasti.

- CBRS_ALIGN_BOTTOM umožňuje ukotvení v dolní části klientské oblasti.

- CBRS_ALIGN_LEFT umožňuje ukotvení na levé straně klientské oblasti.

- CBRS_ALIGN_RIGHT umožňuje ukotvení na pravé straně klientské oblasti.

- CBRS_ALIGN_ANY umožňuje ukotvení na kterékoli straně klientské oblasti.

- CBRS_FLOAT_MULTI umožňuje, aby bylo v jednom okně s minimálním rámcem plovoucí více řídicích panelů.

Pokud 0 (to znamená bez příznaků), ovládací panel nebude ukotven.

### <a name="remarks"></a>Poznámky

Zadané strany musí odpovídat jedné ze stran, které jsou povoleny pro ukotvení v cílovém okně rámce, nebo ovládací panel nelze ukotvit do tohoto okna rámce.

##  <a name="getbarstyle"></a>CControlBar –:: GetBarStyle

Voláním této funkce určíte, které **CBRS_** (styly ovládacích panelů) jsou aktuálně nastaveny pro ovládací panel.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Návratová hodnota

Nastavení aktuálního **CBRS_** (styly řídicích panelů) ovládacího panelu Úplný seznam dostupných stylů naleznete v tématu [CControlBar –:: SetBarStyle](#setbarstyle) .

### <a name="remarks"></a>Poznámky

Nezpracovává styly **WS_** (styl oken).

##  <a name="getborders"></a>CControlBar –:: GetBorders

Vrátí aktuální hodnoty ohraničení ovládacího panelu.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CRect`, který obsahuje aktuální šířku (v pixelech) všech stran objektu ovládacího panelu. Například hodnota *levého* členu objektu [CRect](../../atl-mfc-shared/reference/crect-class.md) je šířkou levého ohraničení.

##  <a name="getcount"></a>CControlBar –:: GetCount

Vrátí počet položek, které nejsou typu HWND, na objektu `CControlBar`.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek, které nejsou typu HWND, u objektu `CControlBar` Tato funkce vrátí 0 pro objekt [CDialogBar](../../mfc/reference/cdialogbar-class.md) .

### <a name="remarks"></a>Poznámky

Typ položky závisí na odvozeném objektu: podokna pro objekty [CStatusBar –](../../mfc/reference/cstatusbar-class.md) a tlačítka a oddělovače pro objekty [CToolBar –](../../mfc/reference/ctoolbar-class.md) .

##  <a name="getdockingframe"></a>CControlBar –:: GetDockingFrame

Zavolejte tuto členskou funkci, aby získala ukazatel na aktuální okno rámce, ke kterému je ukotven ovládací panel.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno rámce, pokud bylo úspěšné. jinak NULL.

Pokud není ovládací panel ukotven do okna rámce (to znamená, pokud je ovládací prvek plovoucí), tato funkce vrátí ukazatel na svůj nadřazený [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).

### <a name="remarks"></a>Poznámky

Další informace o ovládacích panelech ukotvit naleznete v tématu [CControlBar –:: EnableDocking](#enabledocking) a [CFrameWnd::D ockcontrolbar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

##  <a name="isfloating"></a>CControlBar –::-float

Voláním této členské funkce určíte, zda je ovládací panel plovoucí nebo ukotvený.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je ovládací panel plovoucí; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Chcete-li změnit stav ovládacího panelu z ukotveno na plovoucí, zavolejte [CFrameWnd:: FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

##  <a name="m_bautodelete"></a>CControlBar –:: m_bAutoDelete

Pokud je nenulová, objekt `CControlBar` se odstraní při zničení ovládacího panelu systému Windows.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Poznámky

*m_bAutoDelete* je veřejná proměnná typu bool.

Objekt řídicího panelu je obvykle vložen do objektu rámečku okna. V tomto případě je *m_bAutoDelete* 0, protože vložený objekt ovládacího panelu je zničen při zničení okna rámce.

Nastavte tuto proměnnou na nenulovou hodnotu, pokud přidělíte objekt `CControlBar` v haldě a nechcete volat metodu **Delete**.

##  <a name="m_pinplaceowner"></a>CControlBar –:: m_pInPlaceOwner

Místní vlastník ovládacího panelu

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>CControlBar –:: OnUpdateCmdUI

Tato členská funkce je volána rozhraním, aby se aktualizoval stav panelu nástrojů nebo stavového řádku.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Odkazuje na hlavní okno rámce aplikace. Tento ukazatel se používá pro zprávy o aktualizaci směrování.

*bDisableIfNoHndler*<br/>
Příznak, který označuje, zda má být ovládací prvek bez obslužné rutiny aktualizace automaticky zobrazen jako zakázaný.

### <a name="remarks"></a>Poznámky

Chcete-li aktualizovat individuální tlačítko nebo podokno, použijte Makro ON_UPDATE_COMMAND_UI v mapě zprávy pro správné nastavení obslužné rutiny aktualizace. Další informace o použití tohoto makra najdete v tématu [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) .

`OnUpdateCmdUI` je volána rozhraním, když je aplikace nečinná. Okno rámce, které se má aktualizovat, musí být podřízené okno, alespoň nepřímo, viditelného okna s rámečkem. `OnUpdateCmdUI` je pokročilá přepsatelné.

##  <a name="setbarstyle"></a>CControlBar –:: SetBarStyle

Voláním této funkce nastavíte požadované styly **CBRS_** ovládacího panelu.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Požadované styly ovládacího panelu Může se jednat o jednu nebo více z následujících možností:

- CBRS_ALIGN_TOP umožňuje ukotvení ovládacího panelu na začátek klientské oblasti okna rámce.

- CBRS_ALIGN_BOTTOM umožňuje ukotvení ovládacího panelu do dolní části klientské oblasti okna rámce.

- CBRS_ALIGN_LEFT umožňuje ukotvení ovládacího panelu na levou stranu klientské oblasti okna rámce.

- CBRS_ALIGN_RIGHT umožňuje ukotvení ovládacího panelu na pravé straně klientské oblasti okna rámce.

- CBRS_ALIGN_ANY umožňuje ukotvení ovládacího panelu na kterékoli straně klientské oblasti okna rámce.

- CBRS_BORDER_TOP způsobí, že se ohraničení vykreslí na horní okraj ovládacího panelu, když by se zobrazilo.

- CBRS_BORDER_BOTTOM způsobí, že se ohraničení vykreslí na spodní okraj ovládacího panelu, pokud by se zobrazilo.

- CBRS_BORDER_LEFT způsobí vykreslení ohraničení na levém okraji ovládacího panelu, pokud by byl viditelný.

- CBRS_BORDER_RIGHT způsobí vykreslení ohraničení na pravém okraji ovládacího panelu, pokud by byl viditelný.

- CBRS_FLOAT_MULTI umožňuje, aby bylo v jednom okně s minimálním rámcem plovoucí více řídicích panelů.

- CBRS_TOOLTIPS způsobí, že se pro ovládací panel zobrazí popisy nástrojů.

- CBRS_FLYBY způsobí, že se text zprávy aktualizuje ve stejnou chvíli jako tipy nástrojů.

- CBRS_GRIPPER způsobuje, že je úchyt podobný jako použitý na pruzích v objektu `CReBar`, aby se vykreslily pro jakoukoliv třídu odvozenou od `CControlBar`.

### <a name="remarks"></a>Poznámky

Nemá vliv na nastavení **WS_** (styl okna).

##  <a name="setborders"></a>CControlBar –:: SetBorders

Voláním této funkce nastavíte velikost ohraničení ovládacího panelu.

```
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*cxLeft*<br/>
Šířka (v pixelech) levého ohraničení ovládacího panelu

*cyTop*<br/>
Výška (v pixelech) horního ohraničení ovládacího panelu

*cxRight*<br/>
Šířka (v pixelech) pravého ohraničení ovládacího panelu

*cyBottom*<br/>
Výška (v pixelech) dolního ohraničení ovládacího panelu

*lpRect*<br/>
Ukazatel na objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , který obsahuje aktuální šířku (v pixelech) každého ohraničení objektu ovládacího panelu.

### <a name="example"></a>Příklad

Následující příklad kódu nastaví horní a dolní ohraničení ovládacího panelu na 5 pixelů a levý a pravý okraj na 2 pixely:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>CControlBar –:: SetInPlaceOwner

Změní místního vlastníka ovládacího panelu.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na objekt `CWnd`.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[CTRLBARS Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CToolBar – třída](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar – třída](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar – třída](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar – třída](../../mfc/reference/crebar-class.md)
