---
title: Třída CRectTracker
ms.date: 11/19/2018
f1_keywords:
- CRectTracker
- AFXEXT/CRectTracker
- AFXEXT/CRectTracker::CRectTracker
- AFXEXT/CRectTracker::AdjustRect
- AFXEXT/CRectTracker::Draw
- AFXEXT/CRectTracker::DrawTrackerRect
- AFXEXT/CRectTracker::GetHandleMask
- AFXEXT/CRectTracker::GetTrueRect
- AFXEXT/CRectTracker::HitTest
- AFXEXT/CRectTracker::NormalizeHit
- AFXEXT/CRectTracker::OnChangedRect
- AFXEXT/CRectTracker::SetCursor
- AFXEXT/CRectTracker::Track
- AFXEXT/CRectTracker::TrackRubberBand
- AFXEXT/CRectTracker::m_nHandleSize
- AFXEXT/CRectTracker::m_nStyle
- AFXEXT/CRectTracker::m_rect
- AFXEXT/CRectTracker::m_sizeMin
helpviewer_keywords:
- CRectTracker [MFC], CRectTracker
- CRectTracker [MFC], AdjustRect
- CRectTracker [MFC], Draw
- CRectTracker [MFC], DrawTrackerRect
- CRectTracker [MFC], GetHandleMask
- CRectTracker [MFC], GetTrueRect
- CRectTracker [MFC], HitTest
- CRectTracker [MFC], NormalizeHit
- CRectTracker [MFC], OnChangedRect
- CRectTracker [MFC], SetCursor
- CRectTracker [MFC], Track
- CRectTracker [MFC], TrackRubberBand
- CRectTracker [MFC], m_nHandleSize
- CRectTracker [MFC], m_nStyle
- CRectTracker [MFC], m_rect
- CRectTracker [MFC], m_sizeMin
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
ms.openlocfilehash: 4d262ab5f88481d56de1c236effb66fcbf6a706a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368379"
---
# <a name="crecttracker-class"></a>Třída CRectTracker

Umožňuje zobrazení, přesunutí a velikost položky různými způsoby.

## <a name="syntax"></a>Syntaxe

```
class CRectTracker
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CRectTracker::CRectTracker](#crecttracker)|Vytvoří `CRectTracker` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CRectTracker::AdjustRect](#adjustrect)|Nazývá se při velikosti obdélníku.|
|[CRectTracker::Draw](#draw)|Vykreslí obdélník.|
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Nazývá se při kreslení `CRectTracker` ohraničení objektu.|
|[CRectTracker::GetHandleMask](#gethandlemask)|Volána získat masku `CRectTracker` popisovače změny velikosti položky.|
|[CRectTracker::GetTrueRect](#gettruerect)|Vrátí šířku a výšku obdélníku, včetně úchyty pro změny velikosti.|
|[CRectTracker::HitTest](#hittest)|Vrátí aktuální pozici kurzoru `CRectTracker` souvisejícího s objektem.|
|[CRectTracker::NormalizeHit](#normalizehit)|Normalizuje kód testu přístupů.|
|[CRectTracker::OnChangedRect](#onchangedrect)|Nazývá se, když byla změněna velikost obdélníku nebo přesunuta.|
|[CRectTracker::SetKurzor](#setcursor)|Nastaví kurzor v závislosti na jeho umístění nad obdélníkem.|
|[CRectTracker::Sledovat](#track)|Umožňuje uživateli manipulovat s obdélníkem.|
|[CRectTracker::TrackRubberBand](#trackrubberband)|Umožňuje uživateli "gumový pás" výběr.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Určuje velikost úchytů pro měnit velikost.|
|[CRectTracker::m_nStyle](#m_nstyle)|Aktuální styl (y) trackeru.|
|[CRectTracker::m_rect](#m_rect)|Aktuální pozice (v obrazových bodech) obdélníku.|
|[CRectTracker::m_sizeMin](#m_sizemin)|Určuje minimální šířku a výšku obdélníku.|

## <a name="remarks"></a>Poznámky

`CRectTracker`nemá základní třídu.

Přestože `CRectTracker` třída je navržen tak, aby uživatel i nadále pracovat s položkami OLE pomocí grafického rozhraní, jeho použití není omezena na aplikace s podporou OLE. Může být použit kdekoli takové uživatelské rozhraní je vyžadováno.

`CRectTracker`ohraničení může být plné nebo tečkované čáry. Položka může mít šrafované ohraničení nebo překryté šrafovaným vzorem, které označuje různé stavy položky. Na vnější nebo vnitřní okraj položky můžete umístit osm úchytů pro změna velikosti. (Vysvětlení úchyty pro změny velikosti naleznete v tématu [GetHandleMask](#gethandlemask).) Nakonec a `CRectTracker` umožňuje změnit orientaci položky během změny velikosti.

Chcete-li `CRectTracker`použít `CRectTracker` , vytvořte objekt a určete, které stavy zobrazení budou inicializovány. Toto rozhraní pak můžete poskytnout uživateli vizuální zpětnou vazbu na `CRectTracker` aktuální stav položky OLE přidružené k objektu.

Další informace o `CRectTracker`používání naleznete v článku [Sledování](../../mfc/trackers.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CRectTracker`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="crecttrackeradjustrect"></a><a name="adjustrect"></a>CRectTracker::AdjustRect

Volat rámci při změně velikosti obdélníku sledování pomocí popisovač změnit velikost.

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*nPopisovat*<br/>
Index použitého popisovače.

*lpRect*<br/>
Ukazatel na aktuální velikost obdélníku. (Velikost obdélníku je dána jeho výškou a šířkou.)

### <a name="remarks"></a>Poznámky

Výchozí chování této funkce umožňuje orientaci obdélníku `Track` změnit `TrackRubberBand` pouze v případě, a jsou volány s invertování povoleno.

Přepište tuto funkci a ovládejte nastavení sledovacího obdélníku během operace přetažení. Jednou z metod je upravit souřadnice určené *lpRect* před návratem.

Přepsáním této funkce `CRectTracker`lze implementovat speciální funkce, které nejsou přímo podporovány , například přichycení k mřížce nebo poměr zachování strany.

## <a name="crecttrackercrecttracker"></a><a name="crecttracker"></a>CRectTracker::CRectTracker

Vytvoří a inicializuje `CRectTracker` objekt.

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*lpSrcRect*<br/>
Souřadnice objektu obdélníku.

*nStyl*<br/>
Určuje styl objektu. `CRectTracker` Podporovány jsou následující styly:

- `CRectTracker::solidLine`Pro ohraničení obdélníku použijte plnou čáru.

- `CRectTracker::dottedLine`Pro ohraničení obdélníku použijte tečkovanou čáru.

- `CRectTracker::hatchedBorder`Pro ohraničení obdélníku použijte šrafovaný vzorek.

- `CRectTracker::resizeInside`Změna velikosti úchyty umístěné uvnitř obdélníku.

- `CRectTracker::resizeOutside`Změna velikosti úchyty umístěné mimo obdélník.

- `CRectTracker::hatchInside`Šrafovaný vzorek pokrývá celý obdélník.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor inicializuje `CRectTracker` objekt s hodnotami z *lpSrcRect* a inicializuje jiné velikosti na výchozí hodnoty systému. Pokud je objekt vytvořen bez parametrů, jsou členy `m_rect` a `m_nStyle` data neinicializovány.

## <a name="crecttrackerdraw"></a><a name="draw"></a>CRectTracker::Draw

Volání této funkce nakreslit obdélníku vnější čáry a vnitřní oblasti.

```
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zařízení, na kterém chcete kreslit.

### <a name="remarks"></a>Poznámky

Styl sledování určuje, jak se výkres provádí. Další informace o `CRectTracker` dostupných stylech naleznete v konstruktoru.

## <a name="crecttrackerdrawtrackerrect"></a><a name="drawtrackerrect"></a>CRectTracker::DrawTrackerRect

Volat rámci vždy, když se změní pozice `Track` trackeru, zatímco uvnitř funkce nebo `TrackRubberBand` člena.

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Ukazatel `RECT` na, který obsahuje obdélník kreslit.

*pWndClipTo*<br/>
Ukazatel na okno pro oříznutí obdélníku.

*Pdc*<br/>
Ukazatel na kontext zařízení, na kterém chcete kreslit.

*pWnd*<br/>
Ukazatel na okno, ve kterém dojde k výkresu.

### <a name="remarks"></a>Poznámky

Výchozí implementace provede volání `CDC::DrawFocusRect`, který kreslí tečkovaný obdélník.

Přepsat tuto funkci poskytnout různé zpětnou vazbu během operace sledování.

## <a name="crecttrackergethandlemask"></a><a name="gethandlemask"></a>CRectTracker::GetHandleMask

Rozhraní Framework volá tuto člennou funkci k načtení masky pro popisovače změny velikosti obdélníku.

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>Návratová hodnota

Maska úchyty pro měnit velikost `CRectTracker` položky.

### <a name="remarks"></a>Poznámky

Úchyty pro změně velikosti se zobrazí po stranách a rozích obdélníku a umožní uživateli ovládat tvar a velikost obdélníku.

Obdélník má 8 popisovačů pro změny velikosti číslovaných 0-7. Každý úchyt pro změně velikosti je v masce reprezentován bitem; hodnota tohoto bitu je 2^ *n*, kde *n* je číslo popisovače změny velikosti. Bity 0-3 odpovídají rohovým úchytům pro měnit velikost, počínaje levým horním bodem ve směru hodinových ručiček. Bity 4-7 odpovídají bočním úchytům pro změny velikosti začínajícím v horní části pohybu ve směru hodinových ručiček. Následující obrázek znázorňuje úchyty pro změně velikosti obdélníku a jejich odpovídající čísla a hodnoty popisovačů velikosti:

![Změna velikosti čísel popisovačů](../../mfc/reference/media/vc35dp1.gif "Změna velikosti čísel popisovačů")

Výchozí implementace `GetHandleMask` vrátí masku bitů tak, aby se zobrazily úchyty pro změny velikosti. Pokud je jeden bit zapnutý, bude vykreslen odpovídající úchyt pro změně velikosti.

Přepsáním této členské funkce skryjte nebo zobrazte uvedené úchyty pro měnit velikost.

## <a name="crecttrackergettruerect"></a><a name="gettruerect"></a>CRectTracker::GetTrueRect

Volání této funkce načíst souřadnice obdélníku.

```
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>Parametry

*lpTrueRect*<br/>
Ukazatel na `RECT` strukturu, která bude obsahovat `CRectTracker` souřadnice zařízení objektu.

### <a name="remarks"></a>Poznámky

Rozměry obdélníku zahrnují výšku a šířku všech úchytů pro změny velikosti umístěných na vnějším okraji. Po návratu *lpTrueRect* je vždy normalizovaný obdélník v souřadnicích zařízení.

## <a name="crecttrackerhittest"></a><a name="hittest"></a>CRectTracker::HitTest

Volání této funkce zjistit, zda uživatel má popadl popisovač změny velikosti.

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Bod, v souřadnicích zařízení, k testování.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je založena na ve `CRectTracker::TrackerHit` výčtu typu a může mít jednu z následujících hodnot:

- `CRectTracker::hitNothing`-1

- `CRectTracker::hitTopLeft`0

- `CRectTracker::hitTopRight`1

- `CRectTracker::hitBottomRight`2

- `CRectTracker::hitBottomLeft`3

- `CRectTracker::hitTop`4

- `CRectTracker::hitRight`5

- `CRectTracker::hitBottom`6

- `CRectTracker::hitLeft`7

- `CRectTracker::hitMiddle`8

## <a name="crecttrackerm_nhandlesize"></a><a name="m_nhandlesize"></a>CRectTracker::m_nHandleSize

Velikost úchytů `CRectTracker` pro změny velikosti v obrazových bodech.

```
int m_nHandleSize;
```

### <a name="remarks"></a>Poznámky

Inicializováno s výchozí systémovou hodnotou.

## <a name="crecttrackerm_rect"></a><a name="m_rect"></a>CRectTracker::m_rect

Aktuální pozice obdélníku v souřadnicích klienta (pixely).

```
CRect m_rect;
```

## <a name="crecttrackerm_sizemin"></a><a name="m_sizemin"></a>CRectTracker::m_sizeMin

Minimální velikost obdélníku.

```
CSize m_sizeMin;
```

### <a name="remarks"></a>Poznámky

Obě výchozí `cx` hodnoty `cy`a aplikace jsou vypočteny z výchozí systémové hodnoty pro šířku ohraničení. Tento datový člen používá `AdjustRect` pouze členská funkce.

## <a name="crecttrackerm_nstyle"></a><a name="m_nstyle"></a>CRectTracker::m_nStyle

Aktuální styl obdélníku.

```
UINT m_nStyle;
```

### <a name="remarks"></a>Poznámky

Seznam možných stylů najdete v tématu [CRectTracker::CRectTracker.](#crecttracker)

## <a name="crecttrackernormalizehit"></a><a name="normalizehit"></a>CRectTracker::NormalizeHit

Volání této funkce převést potenciálně obrácený popisovač.

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>Parametry

*nPopisovat*<br/>
Popisovač vybraný uživatelem.

### <a name="return-value"></a>Návratová hodnota

Index normalizovaného popisovače.

### <a name="remarks"></a>Poznámky

Když `CRectTracker::Track` `CRectTracker::TrackRubberBand` nebo je volána s invertování povoleno, je možné pro obdélník, který má být obrácený na ose x, osy y nebo obojí. V takovém `HitTest` případě vrátí popisovače, které jsou také invertované vzhledem k obdélníku. To je nevhodné pro kreslení zpětné vazby kurzoru, protože zpětná vazba závisí na umístění na obrazovce obdélníku, nikoli na části obdélníkové datové struktury, která bude změněna.

## <a name="crecttrackeronchangedrect"></a><a name="onchangedrect"></a>CRectTracker::OnChangedRect

Volat rámci vždy, když se během volání `Track`do aplikace změnil obdélník sledování .

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>Parametry

*rectOld*<br/>
Obsahuje staré souřadnice `CRectTracker` zařízení objektu.

### <a name="remarks"></a>Poznámky

V době, kdy je tato funkce `DrawTrackerRect` volána, byla odebrána veškerá zpětná vazba nakreslená. Výchozí implementace této funkce neprovede žádné provádění.

Tuto funkci přepište, pokud chcete provést jakékoli akce po změněné velikosti obdélníku.

## <a name="crecttrackersetcursor"></a><a name="setcursor"></a>CRectTracker::SetKurzor

Volánítéto funkce změnit obrazec kurzoru, zatímco je nad oblasti objektu. `CRectTracker`

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, které aktuálně obsahuje kurzor.

*nHitTest*<br/>
Výsledky předchozího testu přístupů, ze zprávy WM_SETCURSOR.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud předchozí zásah byl přes obdélník sledování; jinak 0.

### <a name="remarks"></a>Poznámky

Volání této funkce zevnitř funkce okna, která zpracovává zprávu `OnSetCursor`WM_SETCURSOR (obvykle).

## <a name="crecttrackertrack"></a><a name="track"></a>CRectTracker::Sledovat

Volání této funkce zobrazí uživatelské rozhraní pro změna velikosti obdélníku.

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Window objekt, který obsahuje obdélník.

*Bod*<br/>
Souřadnice zařízení aktuální polohy myši vzhledem k oblasti klienta.

*bAllowInvert*<br/>
Pokud TRUE, obdélník může být obrácený podél osy x nebo y; jinak FALSE.

*pWndClipTo*<br/>
Okno, na které budou oříznuty operace kreslení. Pokud null, *pWnd* se používá jako ořezový obdélník.

### <a name="return-value"></a>Návratová hodnota

Pokud je stisknuto klávesa ESC, proces sledování je zastaven, obdélník uložený v trackeru se nezmění a 0 je vrácena. Pokud je změna potvrzena, přesunutím myši a uvolněním levého tlačítka myši je v obdélníku sledování zaznamenána nová pozice a/nebo velikost a je vrácena nenulová.

### <a name="remarks"></a>Poznámky

To je obvykle volána zuvnitř funkce aplikace, která zpracovává `WM_LBUTTONDOWN` zprávu (obvykle `OnLButtonDown`).

Tato funkce zachytí myš, dokud uživatel neuvolní levé tlačítko myši, nestiskne klávesu ESC nebo nestiskne pravé tlačítko myši. Když uživatel přesune kurzor myši, zpětná `DrawTrackerRect` `OnChangedRect`vazba se aktualizuje voláním a .

Pokud *je hodnota bAllowInvert* TRUE, lze měřicí obdélník převrátit na ose x nebo ose y.

## <a name="crecttrackertrackrubberband"></a><a name="trackrubberband"></a>CRectTracker::TrackRubberBand

Volání této funkce pro výběr gumičky.

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Window objekt, který obsahuje obdélník.

*Bod*<br/>
Souřadnice zařízení aktuální polohy myši vzhledem k oblasti klienta.

*bAllowInvert*<br/>
Pokud TRUE, obdélník může být obrácený podél osy x nebo y; jinak FALSE.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud se myš přesunula a obdélník není prázdný; jinak 0.

### <a name="remarks"></a>Poznámky

Obvykle je volána zevnitř funkce aplikace, která zpracovává zprávu `OnLButtonDown`WM_LBUTTONDOWN (obvykle ).

Tato funkce zachytí myš, dokud uživatel neuvolní levé tlačítko myši, nestiskne klávesu ESC nebo nestiskne pravé tlačítko myši. Když uživatel přesune kurzor myši, zpětná `DrawTrackerRect` `OnChangedRect`vazba se aktualizuje voláním a .

Sledování se provádí s gumovým páskem typu výběru z pravého dolního rukojeti. Pokud je invertování povoleno, může být velikost obdélníku velikosti přetažením nahoru a doleva nebo dolů a doprava.

## <a name="see-also"></a>Viz také

[Sledování vzorků mfc](../../overview/visual-cpp-samples.md)<br/>
[Vzorek mfc DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleResizeBar – třída](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect – třída](../../atl-mfc-shared/reference/crect-class.md)
