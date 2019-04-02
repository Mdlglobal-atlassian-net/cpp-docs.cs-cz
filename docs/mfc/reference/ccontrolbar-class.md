---
title: Ccontrolbar – třída
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
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773239"
---
# <a name="ccontrolbar-class"></a>Ccontrolbar – třída

Základní třída pro třídy ovládacích pruhů [cstatusbar –](../../mfc/reference/cstatusbar-class.md), [ctoolbar –](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [crebar –](../../mfc/reference/crebar-class.md), a [ Coleresizebar –](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Syntaxe

```
class CControlBar : public CWnd
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name|Popis|
|----------|-----------------|
|[CControlBar::CControlBar](#ccontrolbar)|Vytvoří `CControlBar` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Vrátí velikost položky jako dynamický ovládací panel [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Vrátí velikost panelu ovládacího prvku jako [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.|
|[CControlBar::CalcInsideRect](#calcinsiderect)|Vrátí aktuální rozměry oblasti panelu ovládacího prvku. včetně ohraničení.|
|[CControlBar::DoPaint](#dopaint)|Vykreslí ohraničení a úchytu ovládacím panelu.|
|[CControlBar::DrawBorders](#drawborders)|Vykreslí ohraničení panelu ovládacího prvku.|
|[CControlBar::DrawGripper](#drawgripper)|Vykreslí úchytu ovládacím panelu.|
|[CControlBar::EnableDocking](#enabledocking)|Umožňuje ovládací panel ukotvené nebo plovoucí.|
|[CControlBar::GetBarStyle](#getbarstyle)|Načte nastavení stylu řádku ovládacího prvku.|
|[CControlBar::GetBorders](#getborders)|Načte hodnoty ohraničení panelu ovládacího prvku.|
|[CControlBar::GetCount](#getcount)|Vrátí počet prvků než HWND v ovládacím panelu.|
|[CControlBar::GetDockingFrame](#getdockingframe)|Vrací ukazatel na rámec, ke kterému je ovládací panel ukotven.|
|[CControlBar::IsFloating](#isfloating)|Vrací nenulovou hodnotu, pokud v ovládacím panelu je panel ovládacího prvku s plovoucí desetinnou čárkou.|
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Volání obslužné rutiny příkazu uživatelského rozhraní.|
|[CControlBar::SetBarStyle](#setbarstyle)|Upraví nastavení stylu řádku ovládacího prvku.|
|[CControlBar::SetBorders](#setborders)|Nastaví hodnoty ohraničení panelu ovládacího prvku.|
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|Změny v místní vlastník ovládacího panelu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CControlBar::m_bAutoDelete](#m_bautodelete)|Pokud nenulovou hodnotu, `CControlBar` objektu se odstraní při zničení ovládacím panelu Windows.|
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|Místní vlastník ovládacího panelu.|

## <a name="remarks"></a>Poznámky

Ovládací panel je okno, které obvykle zarovnán nalevo nebo napravo od okna rámce. Může obsahovat podřízené položky, které jsou založené na HWND ovládací prvky, které jsou windows, která generují a reagovat na zprávy Windows nebo nezaložené HWND položky, které nejsou windows a jsou spravované pomocí kódu aplikace nebo kódu architektury. Pole se seznamem a ovládacích prvcích pro úpravy jsou příklady ovládacích prvků na základě HWND; Stavový řádek podokna a rastrového obrázku tlačítka jsou příklady nezaložené HWND ovládacích prvků.

Ovládacích panelů windows jsou obvykle podřízená okna nadřazené okno rámce a obvykle jsou na stejné úrovni jako zobrazení klienta nebo klienta MDI okna rámce. A `CControlBar` objekt používá informace o klientský obdélník nadřazené okno k umístění samotný. Potom informuje nadřazené okno jde o tom, kolik místa zůstane v klientské oblasti okna nadřazené volné.

Další informace o `CControlBar`, naleznete v tématu:

- [Ovládací pruhy](../../mfc/control-bars.md)

- [Technická poznámka 31: Ovládací pruhy](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

##  <a name="calcdynamiclayout"></a>  CControlBar::CalcDynamicLayout

Rozhraní volá tuto funkci člena k výpočtu rozměrů dynamického panelu nástrojů.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Parametry

*nLength*<br/>
Požadovaný dimenze ovládací panel, buď vodorovně nebo svisle, v závislosti na *dwMode*.

*nMode*<br/>
Následující předdefinované příznaky slouží k určení výšku a šířku na dynamický ovládací prvek panelu. Použít bitový operátor OR (&#124;) – operátor kombinování příznaků.

|Příznaky režim rozložení|Význam|
|-----------------------|-------------------|
|LM_STRETCH|Určuje, zda ovládací prvek panel by měl roztažen tak, aby velikost rámce. Nastavte, pokud není panel dokovací panel (není k dispozici pro ukotvení). Nebyla nastavena při panelu je ukotvené nebo plovoucí (k dispozici pro ukotvení). Pokud nastavíte, LM_STRETCH ignoruje *nLength* a vrací na základě stavu LM_HORZ dimenze. LM_STRETCH funguje podobně jako *bStretch* parametr použitý v [CalcFixedLayout](#calcfixedlayout); zobrazit tuto funkci člena pro další informace o vztahu mezi roztažení a orientaci.|
|LM_HORZ|Označuje, že na panelu je orientovaný vodorovně nebo svisle. Nastavte, pokud je panel je orientovaný vodorovně, a pokud svisle orientovaný, není nastaven. LM_HORZ funguje podobně jako *bHorz* parametr použitý v [CalcFixedLayout](#calcfixedlayout); zobrazit tuto funkci člena pro další informace o vztahu mezi roztažení a orientaci.|
|LM_MRUWIDTH|Naposledy použité dynamické šířku. Ignoruje *nLength* parametr a použije zapamatovaných naposledy použité šířky.|
|LM_HORZDOCK|Vodorovné ukotven dimenze. Ignoruje *nLength* parametr a vrátí dynamická velikost s největší šířka.|
|LM_VERTDOCK|Svislé ukotven dimenze. Ignoruje *nLength* parametr a vrátí dynamická velikost největší výšce.|
|LM_LENGTHY|Nastavte, pokud *nLength* Určuje výšku (směru osy Y) namísto šířku.|
|LM_COMMIT|Obnoví LM_MRUWIDTH na aktuální šířku plovoucí panel ovládacího prvku.|

### <a name="return-value"></a>Návratová hodnota

Ovládací panel velikost, v pixelech, o [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.

### <a name="remarks"></a>Poznámky

Přepsání této členské funkce lze zadat dynamické rozložení v odvozujete od třídy `CControlBar`. Třídy MFC odvozené od `CControlBar`, jako například [ctoolbar –](../../mfc/reference/ctoolbar-class.md), přepište tuto členskou funkci a poskytli vlastní implementaci.

##  <a name="calcfixedlayout"></a>  CControlBar::CalcFixedLayout

Voláním této členské funkce k výpočtu šířky ovládacího panelu.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*bStretch*<br/>
Určuje, zda panel by měl roztažen tak, aby velikost rámce. *BStretch* parametr je nenulová, pokud panelu není dokovací panel (není k dispozici pro ukotvení) a 0 až bude ukotvené nebo plovoucí (k dispozici pro ukotvení).

*bHorz*<br/>
Označuje, že na panelu je orientovaný vodorovně nebo svisle. *BHorz* parametr je nenulová, pokud panelu orientován vodorovně a je 0, pokud je svisle orientovaný.

### <a name="return-value"></a>Návratová hodnota

Ovládací panel velikost, v pixelech, o `CSize` objektu.

### <a name="remarks"></a>Poznámky

Ovládací pruhy, jako je například panely nástrojů lze roztáhnout vodorovně nebo svisle tak, aby vyhovovaly tlačítka obsažené v ovládacím panelu.

Pokud *bStretch* má hodnotu TRUE, roztáhnout dimenze podél orientace poskytované *bHorz*. Jinými slovy Pokud *bHorz* má hodnotu FALSE, je ovládací prvek panelu svisle roztažená. Pokud *bStretch* má hodnotu FALSE, dojde k žádné stretch. V následující tabulce jsou uvedeny možná bude připadat a výsledné styly ovládacích panelů z *bStretch* a *bHorz*.

|bStretch|bHorz|Roztažení|Orientace|Ukotvení nebo není ukotvení|
|--------------|-----------|----------------|-----------------|--------------------------|
|HODNOTA TRUE|HODNOTA TRUE|Vodorovné roztažení|Orientovaný vodorovně|Není ukotvení|
|HODNOTA TRUE|FALSE|Svislé roztažení|Orientovány svisle|Není ukotvení|
|FALSE|HODNOTA TRUE|Žádné roztažení k dispozici|Orientovaný vodorovně|Ukotvení|
|FALSE|FALSE|Žádné roztažení k dispozici|Orientovány svisle|Ukotvení|

##  <a name="calcinsiderect"></a>  CControlBar::CalcInsideRect

Rozhraní volá tuto funkci k výpočtu klientské oblasti ovládacího panelu.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Obsahuje aktuální rozměry ovládacího panelu; včetně ohraničení.

*bHorz*<br/>
Označuje, že na panelu je orientovaný vodorovně nebo svisle. *BHorz* parametr je nenulová, pokud panelu orientován vodorovně a je 0, pokud je svisle orientovaný.

### <a name="remarks"></a>Poznámky

Tato funkce je volána před vymalováním ovládacím panelu.

Přepsání této funkce můžete přizpůsobit vykreslování ohraničení a úchyt ovládacího panelu.

##  <a name="ccontrolbar"></a>  CControlBar::CControlBar

Vytvoří `CControlBar` objektu.

```
CControlBar();
```

##  <a name="dopaint"></a>  CControlBar::DoPaint

Volá se rozhraním vykreslit ohraničení a úchyt ovládacího panelu.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Odkazuje na kontext zařízení má být použit pro vykreslování ohraničení a úchytu ovládacím panelu.

### <a name="remarks"></a>Poznámky

Přepsání této funkce můžete přizpůsobit chování vykreslování ovládacího panelu.

Přizpůsobení se přepsat `DrawBorders` a `DrawGripper` funkce a přidat vlastní kód vykreslování ohraničení a úchytu. Protože tyto metody jsou volány ve výchozím nastavení `DoPaint` metody, přepíše `DoPaint` není potřeba.

##  <a name="drawborders"></a>  CControlBar::DrawBorders

Volá se rozhraním k vykreslení ohraničení panelu ovládacího prvku.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Odkazuje na kontext zařízení má být použit pro vykreslení ohraničení panelu ovládacího prvku.

*Rect*<br/>
A `CRect` objekt, který obsahuje rozměry ovládacího panelu.

### <a name="remarks"></a>Poznámky

Potlačí tuto funkci pro přizpůsobení vzhledu ohraničení panelu ovládacího prvku.

##  <a name="drawgripper"></a>  CControlBar::DrawGripper

Volá se rozhraním pro vykreslení úchytu ovládacím panelu.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Odkazuje na kontext zařízení má být použit pro vykreslení úchytu ovládacího panelu.

*Rect*<br/>
A `CRect` objekt, který obsahuje rozměry úchytu ovládacího panelu.

### <a name="remarks"></a>Poznámky

Přepsání této funkce můžete přizpůsobit vzhled úchytu ovládacího panelu.

##  <a name="enabledocking"></a>  CControlBar::EnableDocking

Voláním této funkce umožňující ovládací panel ukotvit.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

*dwDockStyle*<br/>
Určuje, jestli podporuje ovládací panel ukotvení a po stranách nezašle nadřazenému oknu, ke které lze ukotvit panel ovládacího prvku, pokud se podporuje. Může být jeden nebo více z následujících akcí:

- CBRS_ALIGN_TOP umožňuje ukotvení v horní části klientské oblasti.

- CBRS_ALIGN_BOTTOM umožňuje ukotvení v dolní části klientské oblasti.

- CBRS_ALIGN_LEFT umožňuje Ukotvování na levé straně od klientské oblasti.

- CBRS_ALIGN_RIGHT umožňuje ukotvení na pravé straně, od klientské oblasti.

- CBRS_ALIGN_ANY umožňuje ukotvení na žádné straně od klientské oblasti.

- CBRS_FLOAT_MULTI umožňuje více ovládací pruhy pro obtékané v okně jednoho okna s minirámcem.

Pokud je 0 (to znamená, to znamená žádné příznaky), nebude ukotvení panelu ovládacího prvku.

### <a name="remarks"></a>Poznámky

Strany zadaný musí odpovídat jedné ze stran povoleno pro ukotvení v rámci okna cílové nebo ovládacím panelu nelze ukotvit do tohoto okna rámce.

##  <a name="getbarstyle"></a>  CControlBar::GetBarStyle

Voláním této funkce určete, které **CBRS_** (– styly ovládacího prvku panelu) aktuálně nastavení pro ovládací prvek panel.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální **CBRS_** (– styly ovládacího prvku panelu) nastavení pro ovládací prvek panel. Zobrazit [CControlBar::SetBarStyle](#setbarstyle) úplný seznam dostupných stylů.

### <a name="remarks"></a>Poznámky

Nezpracovává **WS_** styly (styl okna).

##  <a name="getborders"></a>  CControlBar::GetBorders

Vrátí aktuální hodnoty ohraničení panelu ovládacího prvku.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Návratová hodnota

A `CRect` objekt, který obsahuje aktuální šířku (v pixelech) každé straně objekt panelu ovládacího prvku. Například hodnota *levé* člena z [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu, je šířka levého ohraničení.

##  <a name="getcount"></a>  CControlBar::GetCount

Vrátí počet položek bez HWND `CControlBar` objektu.

```
int GetCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek bez HWND na `CControlBar` objektu. Tato funkce vrátí hodnotu 0 [CDialogBar](../../mfc/reference/cdialogbar-class.md) objektu.

### <a name="remarks"></a>Poznámky

Typ položky závisí na objekt odvozené: podokna pro [cstatusbar –](../../mfc/reference/cstatusbar-class.md) objekty a tlačítka a oddělovače pro [ctoolbar –](../../mfc/reference/ctoolbar-class.md) objekty.

##  <a name="getdockingframe"></a>  CControlBar::GetDockingFrame

Voláním této členské funkce na ukazatel na aktuální okno rámce, ke kterému je ovládací panel ukotven.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno rámce v případě úspěchu; v opačném případě hodnota NULL.

Pokud se ovládací panel není ukotven k okně s rámečkem (tj. Pokud je plovoucí panel ovládacího prvku), tato funkce vrátí ukazatel k nadřazené úloze [cminiframewnd –](../../mfc/reference/cminiframewnd-class.md).

### <a name="remarks"></a>Poznámky

Další informace o ukotvitelné ovládací pruhy, naleznete v tématu [CControlBar::EnableDocking](#enabledocking) a [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

##  <a name="isfloating"></a>  CControlBar::IsFloating

Voláním této členské funkce k určení, zda ovládací prvek panelu nebo jsou ukotveny.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je plovoucí panel ovládacího prvku; jinak 0.

### <a name="remarks"></a>Poznámky

Chcete-li změnit stav z ovládací panel ukotven na plovoucí, volání [CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

##  <a name="m_bautodelete"></a>  CControlBar::m_bAutoDelete

Pokud nenulovou hodnotu, `CControlBar` objektu se odstraní při zničení ovládacím panelu Windows.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Poznámky

*m_bAutoDelete* je veřejná proměnná typu BOOL.

Objekt ovládacích panelů je obvykle součástí objekt okna rámce. V takovém případě *m_bAutoDelete* je 0, protože vložený ovládacích panelů objekt je zničen při zničení okno rámce.

Tuto proměnnou nastavit na nenulovou hodnotu, pokud přidělíte `CControlBar` objektu na haldě a vy nemáte v plánu volání **odstranit**.

##  <a name="m_pinplaceowner"></a>  CControlBar::m_pInPlaceOwner

Místní vlastník ovládacího panelu.

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>  CControlBar::OnUpdateCmdUI

Tato členská funkce se volá se rozhraním pro aktualizaci stavu panelu nástrojů nebo stavového řádku.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Odkazuje na hlavní okno rámce aplikace. This – ukazatel se používá pro směrování zpráv aktualizace.

*bDisableIfNoHndler*<br/>
Příznak, který označuje, zda ovládací prvek, který nemá žádná obslužná rutina aktualizace by měla automaticky zobrazí jako zakázané.

### <a name="remarks"></a>Poznámky

Aktualizace podokna nebo jednotlivá tlačítka, použijte ON_UPDATE_COMMAND_UI – makro v mapě zpráv k odpovídajícím způsobem nastavit obslužnou rutinu aktualizace. Zobrazit [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) pro další informace o použití tohoto makra.

`OnUpdateCmdUI` se volá se rozhraním, když je aplikace nečinnosti. Rámeček okna k aktualizaci musí být podřízené okno alespoň nepřímo viditelné rámce okna. `OnUpdateCmdUI` je moderní overridable.

##  <a name="setbarstyle"></a>  CControlBar::SetBarStyle

Voláním této funkce nastavit požadovaný **CBRS_** styly pro ovládací prvek panel.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Požadovaný styly pro ovládací prvek panel. Může být jeden nebo více z následujících akcí:

- CBRS_ALIGN_TOP umožňuje ovládací panel ukotvit do horní části klientské oblasti okna rámce.

- CBRS_ALIGN_BOTTOM umožňuje ovládací panel ukotvit k dolnímu okraji klientské oblasti okna rámce.

- CBRS_ALIGN_LEFT umožňuje panelu Ovládací prvek ukotven k levé části klientské oblasti okna rámce.

- CBRS_ALIGN_RIGHT umožňuje ovládací panel ukotvit k pravému okraji klientské oblasti okna rámce.

- CBRS_ALIGN_ANY umožňuje ovládací panel ukotvit do libovolné části klientské oblasti okna rámce.

- CBRS_BORDER_TOP způsobí, že se vykreslí na horním okrajem ovládacího prvku panelu kdy by bylo viditelné ohraničení.

- CBRS_BORDER_BOTTOM způsobí, že chcete kreslit na dolním okraji ovládacího panelu při by být viditelné ohraničení.

- CBRS_BORDER_LEFT způsobí, že chcete kreslit na levém okraji ovládacího panelu při by být viditelné ohraničení.

- CBRS_BORDER_RIGHT způsobí, že chcete kreslit na pravém okraji ovládacího panelu při by být viditelné ohraničení.

- CBRS_FLOAT_MULTI umožňuje více ovládací pruhy pro obtékané v okně jednoho okna s minirámcem.

- CBRS_TOOLTIPS způsobí, že popisy tlačítek zobrazeného panelu ovládacího prvku.

- CBRS_FLYBY způsobí, že text zprávy aktualizovat ve stejnou dobu jako popisy tlačítek.

- CBRS_GRIPPER úchytu, podobně jako, který používá na pruhy v způsobí, že `CReBar` objekt vykreslit pro všechny `CControlBar`-odvozené třídy.

### <a name="remarks"></a>Poznámky

Nemá vliv **WS_** nastavení (styl okna).

##  <a name="setborders"></a>  CControlBar::SetBorders

Voláním této funkce nastavit velikost ohraničení panelu ovládacího prvku.

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
Šířka levého ohraničení panelu ovládacího prvku (v pixelech).

*cyTop*<br/>
Výška horního ohraničení panelu ovládacího prvku (v pixelech).

*cxRight*<br/>
Šířka pravého ohraničení panelu ovládacího prvku (v pixelech).

*cyBottom*<br/>
Výška ovládací panel dolního ohraničení (v pixelech).

*lpRect*<br/>
Ukazatel [crect –](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje aktuální šířku (v pixelech) každé ohraničení panelu objekt ovládacího prvku.

### <a name="example"></a>Příklad

Následující příklad kódu nastaví horní a dolní ohraničení panelu ovládacího prvku na 5 pixelů a levé a pravé ohraničení na hodnotu 2 pixelech:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>  CControlBar::SetInPlaceOwner

Změny v místní vlastník ovládacího panelu.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel `CWnd` objektu.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CToolBar – třída](../../mfc/reference/ctoolbar-class.md)<br/>
[CDialogBar – třída](../../mfc/reference/cdialogbar-class.md)<br/>
[CStatusBar – třída](../../mfc/reference/cstatusbar-class.md)<br/>
[CReBar – třída](../../mfc/reference/crebar-class.md)
