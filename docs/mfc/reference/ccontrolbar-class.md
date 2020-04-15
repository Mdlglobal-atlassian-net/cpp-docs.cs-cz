---
title: CControlBar – třída
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
ms.openlocfilehash: deb95d76e6d68ba5b9fad82bca1d88fd71c5a547
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369396"
---
# <a name="ccontrolbar-class"></a>CControlBar – třída

Základní třída pro třídy ovládacího panelu [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md)a [COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Syntaxe

```
class CControlBar : public CWnd
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CControlBar::Ovládací panel CControlBar](#ccontrolbar)|Vytvoří `CControlBar` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Vrátí velikost dynamického ovládacího panelu jako [objektc CSize.](../../atl-mfc-shared/reference/csize-class.md)|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Vrátí velikost ovládacího panelu jako objekt [CSize.](../../atl-mfc-shared/reference/csize-class.md)|
|[CControlBar::CalcInsideRect](#calcinsiderect)|Vrátí aktuální rozměry oblasti ovládacího panelu; včetně hranic.|
|[CControlBar::DoPaint](#dopaint)|Vykreslí ohraničení a úchop ovládacího panelu.|
|[CControlBar::DrawBorders](#drawborders)|Vykreslí okraje ovládacího panelu.|
|[CControlBar::Dujela](#drawgripper)|Vykreslí úchop ovládacího panelu.|
|[CControlBar::EnableDocking](#enabledocking)|Umožňuje ukotvení ovládacího panelu nebo plovoucího ovládacího panelu.|
|[CControlBar::GetbarStyle](#getbarstyle)|Načte nastavení stylu ovládacího panelu.|
|[CControlBar::GetBorders](#getborders)|Načte hodnoty ohraničení ovládacího panelu.|
|[CControlBar::GetCount](#getcount)|Vrátí počet prvků, které nejsou HWND v ovládacím panelu.|
|[CControlBar::GetDockingFrame](#getdockingframe)|Vrátí ukazatel na snímek, do kterého je ukotvěn ovládací panel.|
|[CControlBar::Jeplovoucí](#isfloating)|Vrátí nenulovou hodnotu, pokud je dotyčný ovládací panel plovoucí ovládací panel.|
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Volá obslužné rutiny řídicího než visu.|
|[CControlBar::SetBarStyle](#setbarstyle)|Upraví nastavení stylu ovládacího panelu.|
|[CControlBar::SetBorders](#setborders)|Nastaví hodnoty ohraničení ovládacího panelu.|
|[CControlBar::SetInplaceOwner](#setinplaceowner)|Změní vlastníka ovládacího panelu na místě.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CControlBar::m_bAutoDelete](#m_bautodelete)|Pokud je nenulová, `CControlBar` objekt je odstraněn při zničení ovládacího panelu systému Windows.|
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|Vlastník ovládacího panelu na místě.|

## <a name="remarks"></a>Poznámky

Ovládací panel je okno, které je obvykle zarovnáno doleva nebo doprava okna rámce. Může obsahovat podřízené položky, které jsou buď ovládací prvky založené na HWND, které jsou okna, která generují a reagovat na zprávy systému Windows nebo položky založené na HWND, které nejsou windows a jsou spravovány kódem aplikace nebo kód emitování. Seznamy a ovládací prvky pro úpravy jsou příklady ovládacích prvků založených na HWND; stavový panel a bitmapová tlačítka jsou příklady ovládacích prvků, které nejsou založeny na HWND.

Okna ovládacího panelu jsou obvykle podřízená okna okna nadřazeného rámce a jsou obvykle na stejné úrovni pro zobrazení klienta nebo klienta MDI okna rámce. Objekt `CControlBar` používá informace o obdélníku klienta nadřazeného okna k umístění sebe sama. Potom informuje nadřazené okno o tom, kolik místa zůstává nepřidělené v oblasti klienta nadřazeného okna.

Další informace `CControlBar`naleznete v tématu :

- [Ovládací pruhy](../../mfc/control-bars.md)

- [Technická poznámka 31: Ovládací panely](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="ccontrolbarcalcdynamiclayout"></a><a name="calcdynamiclayout"></a>CControlBar::CalcDynamicLayout

Rozhraní Framework volá tuto členská funkci k výpočtu dimenzí dynamického panelu nástrojů.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Parametry

*nDélka*<br/>
Požadovaný rozměr ovládacího panelu, vodorovný nebo svislý, v závislosti na *dwMode*.

*nRežim*<br/>
K určení výšky a šířky dynamického ovládacího panelu se používají následující předdefinované příznaky. Pomocí operátoru bitové-OR (&#124;) zkombinujte příznaky.

|Příznaky režimu rozložení|Význam|
|-----------------------|-------------------|
|LM_STRETCH|Označuje, zda má být ovládací panel roztažen na velikost rámečku. Nastavte, pokud lišta není dokovací lištou (není k dispozici pro dokování). Není nastavena, když je lišta ukotvená nebo plovoucí (k dispozici pro dokování). Pokud je nastavena, LM_STRETCH ignoruje *nLength* a vrátí dimenze na základě LM_HORZ stavu. LM_STRETCH funguje podobně jako parametr *bStretch* použitý v [calcfixedlayout](#calcfixedlayout); další informace o vztahu mezi roztažením a orientací naleznete v této členské funkci.|
|LM_HORZ|Označuje, že pruh je vodorovně nebo svisle orientovaný. Nastavte, zda je pruh vodorovně orientovaný a pokud je vertikálně orientovaný, není nastaven. LM_HORZ funguje podobně jako parametr *bHorz* použitý v [calcfixedlayout](#calcfixedlayout); další informace o vztahu mezi roztažením a orientací naleznete v této členské funkci.|
|LM_MRUWIDTH|Naposledy použitá dynamická šířka. Ignoruje parametr *nLength* a používá zapamatoženou naposledy použitou šířku.|
|LM_HORZDOCK|Vodorovné ukotvené kóty. Ignoruje parametr *nLength* a vrátí dynamickou velikost s největší šířkou.|
|LM_VERTDOCK|Svislé ukotvené kóty. Ignoruje parametr *nLength* a vrátí dynamickou velikost s největší výškou.|
|LM_LENGTHY|Nastavte, pokud *nDélka* označuje výšku (směr Y) místo šířky.|
|LM_COMMIT|Obnoví LM_MRUWIDTH na aktuální šířku plovoucího ovládacího panelu.|

### <a name="return-value"></a>Návratová hodnota

Velikost ovládacího panelu v obrazových bodech objektu [CSize.](../../atl-mfc-shared/reference/csize-class.md)

### <a name="remarks"></a>Poznámky

Přepište tuto člennou funkci a poskytněte `CControlBar`vlastní dynamické rozložení ve třídách, které jsou odvozeny z aplikace . Třídy knihovny `CControlBar`MFC odvozené z , například [CToolbar,](../../mfc/reference/ctoolbar-class.md)přepsat tuto člennou funkci a poskytují vlastní implementaci.

## <a name="ccontrolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CControlBar::CalcFixedLayout

Volání této členské funkce pro výpočet vodorovné velikosti ovládacího panelu.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*bÚsek*<br/>
Označuje, zda má být pruh roztažen na velikost rámečku. Parametr *bStretch* je nenulový, pokud panel není dokovací lištou (není k dispozici pro ukotvení) a je 0, pokud je ukotven nebo plovoucí (k dispozici pro ukotvení).

*bHorz*<br/>
Označuje, že pruh je vodorovně nebo svisle orientovaný. Parametr *bHorz* je nenulový, pokud je pruh vodorovně orientován, a je 0, pokud je vertikálně orientovaný.

### <a name="return-value"></a>Návratová hodnota

Velikost ovládacího panelu v obrazových bodech objektu. `CSize`

### <a name="remarks"></a>Poznámky

Ovládací panely, jako jsou panely nástrojů, se mohou roztáhnout vodorovně nebo svisle, aby se přizpůsobily tlačítkům obsaženým v ovládacím panelu.

Pokud *je bStretch* TRUE, roztáhněte kótu podél orientace poskytované *pomocí bHorz*. Jinými slovy, pokud *bHorz* je FALSE, ovládací panel je roztažen svisle. Pokud *bStretch* je FALSE, dojde k žádné úsek. V následující tabulce jsou uvedeny možné permutace a výsledné styly ovládacího panelu *bStretch* a *bHorz*.

|bÚsek|bHorz|Protahování|Orientace|Ukotvení/neukotvení|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|Vodorovné protahování|Horizontálně orientované|Není dokování|
|TRUE|FALSE|Vertikální protahování|Vertikálně orientované|Není dokování|
|FALSE|TRUE|Není k dispozici žádné roztahování|Horizontálně orientované|Dokovací|
|FALSE|FALSE|Není k dispozici žádné roztahování|Vertikálně orientované|Dokovací|

## <a name="ccontrolbarcalcinsiderect"></a><a name="calcinsiderect"></a>CControlBar::CalcInsideRect

Framework volá tuto funkci k výpočtu klientské oblasti ovládacího panelu.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Obsahuje aktuální rozměry ovládacího panelu; včetně hranic.

*bHorz*<br/>
Označuje, že pruh je vodorovně nebo svisle orientovaný. Parametr *bHorz* je nenulový, pokud je pruh vodorovně orientován, a je 0, pokud je vertikálně orientovaný.

### <a name="remarks"></a>Poznámky

Tato funkce je volána před vymalování ovládacího panelu.

Přepsáním této funkce můžete přizpůsobit vykreslování ohraničení a úchytu ovládacího panelu.

## <a name="ccontrolbarccontrolbar"></a><a name="ccontrolbar"></a>CControlBar::Ovládací panel CControlBar

Vytvoří `CControlBar` objekt.

```
CControlBar();
```

## <a name="ccontrolbardopaint"></a><a name="dopaint"></a>CControlBar::DoPaint

Nazývá rámci k vykreslení hranice a úchopné lišty ovládacího panelu.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Odkazuje na kontext zařízení, který se má použít k vykreslení ohraničení a úchytu ovládacího panelu.

### <a name="remarks"></a>Poznámky

Přepsáním této funkce přizpůsobíte chování kreslení ovládacího panelu.

Další metodou přizpůsobení je `DrawBorders` přepsat `DrawGripper` funkce a a přidat vlastní kód výkresu pro ohraničení a úchyt. Vzhledem k tomu, `DoPaint` že tyto metody `DoPaint` jsou volány výchozí metodou, není potřeba přepsání.

## <a name="ccontrolbardrawborders"></a><a name="drawborders"></a>CControlBar::DrawBorders

Volat rámci k vykreslení hranice ovládacího panelu.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Odkazuje na kontext zařízení, který se má použít k vykreslení ohraničení ovládacího panelu.

*Rect*<br/>
Objekt `CRect` obsahující rozměry ovládacího panelu.

### <a name="remarks"></a>Poznámky

Přepsáním této funkce přizpůsobíte vzhled ohraničení ovládacího panelu.

## <a name="ccontrolbardrawgripper"></a><a name="drawgripper"></a>CControlBar::Dujela

Volat rámci k vykreslení úchopu ovládacího panelu.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Odkazuje na kontext zařízení, který se má použít k vykreslení úchytu ovládacího panelu.

*Rect*<br/>
Objekt `CRect` obsahující rozměry úchytu ovládacího panelu.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci a přizpůsobte vzhled úchopného zařízení ovládacího panelu.

## <a name="ccontrolbarenabledocking"></a><a name="enabledocking"></a>CControlBar::EnableDocking

Volání této funkce povolit ovládací panel, který má být ukotven.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

*dwDockStyl*<br/>
Určuje, zda ovládací panel podporuje ukotvení a strany nadřazeného okna, do kterého lze řídicí panel ukotvit, pokud je podporován. Může být jeden nebo více z následujících:

- CBRS_ALIGN_TOP Umožňuje ukotvení v horní části klientské oblasti.

- CBRS_ALIGN_BOTTOM Umožňuje ukotvení v dolní části klientské oblasti.

- CBRS_ALIGN_LEFT Umožňuje ukotvení na levé straně klientské oblasti.

- CBRS_ALIGN_RIGHT Umožňuje ukotvení na pravé straně klientské oblasti.

- CBRS_ALIGN_ANY Umožňuje ukotvení na libovolné straně klientské oblasti.

- CBRS_FLOAT_MULTI Umožňuje plovoucí více ovládacích panelů v jednom okně minirámečku.

Pokud 0 (to znamená, že žádné příznaky), ovládací panel nebude ukotven.

### <a name="remarks"></a>Poznámky

Zadané strany se musí shodovat s jednou ze stran povolených pro ukotvení v okně cílového rámce nebo ovládací panel nelze ukotvit do tohoto okna rámce.

## <a name="ccontrolbargetbarstyle"></a><a name="getbarstyle"></a>CControlBar::GetbarStyle

Volánítéto funkce k určení, které **CBRS_** (styly ovládacího panelu) jsou aktuálně nastaveny pro ovládací panel.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální **CBRS_** (styly ovládacího panelu) pro ovládací panel. Úplný seznam dostupných stylů naleznete v tématu [CControlBar::SetBarStyle.](#setbarstyle)

### <a name="remarks"></a>Poznámky

Nezpracovává **styly WS_** (styl okna).

## <a name="ccontrolbargetborders"></a><a name="getborders"></a>CControlBar::GetBorders

Vrátí aktuální hodnoty ohraničení ovládacího panelu.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `CRect` který obsahuje aktuální šířku (v obrazových bodech) každé strany objektu ovládacího panelu. Například hodnota *levého* člena [objektu CRect](../../atl-mfc-shared/reference/crect-class.md) je šířka levého okraje.

## <a name="ccontrolbargetcount"></a><a name="getcount"></a>CControlBar::GetCount

Vrátí počet položek, které nejsou `CControlBar` HWND, na objektu.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek mimo HWND na `CControlBar` objektu. Tato funkce vrátí 0 pro [CDialogBar](../../mfc/reference/cdialogbar-class.md) objektu.

### <a name="remarks"></a>Poznámky

Typ položky závisí na odvozeném objektu: podokna pro objekty [CStatusBar](../../mfc/reference/cstatusbar-class.md) a tlačítka a oddělovače pro objekty [CToolBar.](../../mfc/reference/ctoolbar-class.md)

## <a name="ccontrolbargetdockingframe"></a><a name="getdockingframe"></a>CControlBar::GetDockingFrame

Volání této členské funkce získat ukazatel na aktuální okno rámce, do kterého je ukotven ovládací panel.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno rámce v případě úspěchu; jinak NULL.

Pokud ovládací panel není ukotven k oknu rámce (to znamená, pokud je ovládací panel plovoucí), vrátí tato funkce ukazatel na nadřazený [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).

### <a name="remarks"></a>Poznámky

Další informace o ukotvených ovládacích panelech naleznete v [tématech CControlBar::EnableDocking](#enabledocking) a [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

## <a name="ccontrolbarisfloating"></a><a name="isfloating"></a>CControlBar::Jeplovoucí

Volání této členské funkce k určení, zda ovládací panel je plovoucí nebo ukotvené.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je ovládací panel plovoucí; jinak 0.

### <a name="remarks"></a>Poznámky

Chcete-li změnit stav ovládacího panelu z ukotveného na plovoucí, zavolejte [CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

## <a name="ccontrolbarm_bautodelete"></a><a name="m_bautodelete"></a>CControlBar::m_bAutoDelete

Pokud je nenulová, `CControlBar` objekt je odstraněn při zničení ovládacího panelu systému Windows.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Poznámky

*m_bAutoDelete* je veřejná proměnná typu BOOL.

Objekt ovládacího panelu je obvykle vložen do objektu okna rámce. V tomto případě *m_bAutoDelete* je 0, protože vložený objekt ovládacího panelu je zničen při zničení okna rámce.

Nastavte tuto proměnnou na nenulovou `CControlBar` hodnotu, pokud přidělujete objekt na haldě a neplánujete volat **delete**.

## <a name="ccontrolbarm_pinplaceowner"></a><a name="m_pinplaceowner"></a>CControlBar::m_pInPlaceOwner

Vlastník ovládacího panelu na místě.

```
CWnd* m_pInPlaceOwner;
```

## <a name="ccontrolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CControlBar::OnUpdateCmdUI

Tato členská funkce je volána rozhraním pro aktualizaci stavu panelu nástrojů nebo stavového řádku.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Parametry

*pCíl*<br/>
Odkazuje na okno hlavního rámce aplikace. Tento ukazatel se používá pro směrování aktualizačních zpráv.

*bDisableIfNoHndler*<br/>
Příznak, který označuje, zda ovládací prvek, který nemá žádnou obslužnou rutinu aktualizace by měl být automaticky zobrazen jako zakázán.

### <a name="remarks"></a>Poznámky

Chcete-li aktualizovat jednotlivé tlačítko nebo podokno, nastavte správně pomocí ON_UPDATE_COMMAND_UI makra v mapě zpráv obslužnou rutinu aktualizace. Další informace o používání tohoto makra naleznete [v ON_UPDATE_COMMAND_UI.](message-map-macros-mfc.md#on_update_command_ui)

`OnUpdateCmdUI`je volána rámci při nečinnosti aplikace. Okno rámce, které má být aktualizováno, musí být alespoň nepřímo podřízené okno viditelného okna rámce. `OnUpdateCmdUI`je pokročilý overridable.

## <a name="ccontrolbarsetbarstyle"></a><a name="setbarstyle"></a>CControlBar::SetBarStyle

Voláním této funkce nastavte požadované **CBRS_** styly ovládacího panelu.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Požadované styly ovládacího panelu. Může být jeden nebo více z následujících:

- CBRS_ALIGN_TOP Umožňuje ukotvení ovládacího panelu do horní části klientské oblasti okna rámce.

- CBRS_ALIGN_BOTTOM Umožňuje ukotvení ovládacího panelu do dolní části klientské oblasti okna rámce.

- CBRS_ALIGN_LEFT Umožňuje ukotvení ovládacího panelu na levé straně klientské oblasti okna rámce.

- CBRS_ALIGN_RIGHT Umožňuje ukotvení ovládacího panelu na pravou stranu klientské oblasti okna rámce.

- CBRS_ALIGN_ANY Umožňuje ukotvení ovládacího panelu na libovolnou stranu klientské oblasti okna rámce.

- CBRS_BORDER_TOP Způsobí, že ohraničení nakreslí na horním okraji ovládacího panelu, když by bylo viditelné.

- CBRS_BORDER_BOTTOM Způsobí, že ohraničení nakreslit na dolním okraji ovládacího panelu, když by bylo viditelné.

- CBRS_BORDER_LEFT Způsobí, že ohraničení nakreslit na levém okraji ovládacího panelu, když by bylo viditelné.

- CBRS_BORDER_RIGHT Způsobí, že ohraničení nakreslí na pravém okraji ovládacího panelu, když by bylo viditelné.

- CBRS_FLOAT_MULTI Umožňuje plovoucí více ovládacích panelů v jednom okně minirámečku.

- CBRS_TOOLTIPS Způsobí, že se pro ovládací panel zobrazí tipy nástrojů.

- CBRS_FLYBY Způsobí, že text zprávy bude aktualizován současně s tipy nástrojů.

- CBRS_GRIPPER Způsobí, že úchyt, podobný `CReBar` tomu, který se `CControlBar`používá na pásy v objektu, které mají být vypracovány pro všechny odvozené třídy.

### <a name="remarks"></a>Poznámky

Nemá vliv na nastavení **WS_** (styl okna).

## <a name="ccontrolbarsetborders"></a><a name="setborders"></a>CControlBar::SetBorders

Voláním této funkce nastavte velikost ohraničení ovládacího panelu.

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
Šířka (v obrazových bodech) levého okraje ovládacího panelu.

*cyTop*<br/>
Výška (v obrazových bodech) horního okraje ovládacího panelu.

*cxVpravo*<br/>
Šířka (v obrazových bodech) pravého ohraničení ovládacího panelu.

*cyBottom*<br/>
Výška (v obrazových bodech) dolního okraje ovládacího panelu.

*lpRect*<br/>
Ukazatel na objekt [CRect,](../../atl-mfc-shared/reference/crect-class.md) který obsahuje aktuální šířku (v obrazových bodech) každého ohraničení objektu ovládacího panelu.

### <a name="example"></a>Příklad

Následující příklad kódu nastaví horní a dolní okraj ovládacího panelu na 5 pixelů a levý a pravý okraj na 2 obrazové body:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

## <a name="ccontrolbarsetinplaceowner"></a><a name="setinplaceowner"></a>CControlBar::SetInplaceOwner

Změní vlastníka ovládacího panelu na místě.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na `CWnd` objekt.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CToolBar – třída](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar – třída](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar – třída](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar – třída](../../mfc/reference/crebar-class.md)
