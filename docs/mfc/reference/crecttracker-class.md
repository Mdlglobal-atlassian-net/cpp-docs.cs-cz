---
title: Crecttracker – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 519f88a3706812ae77d7dbd77e199b3e3ef4e97a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473369"
---
# <a name="crecttracker-class"></a>Crecttracker – třída

Umožňuje položku, která má být zobrazen, přesouvat a různými způsoby se změněnou velikostí.

## <a name="syntax"></a>Syntaxe

```
class CRectTracker
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CRectTracker::CRectTracker](#crecttracker)|Vytvoří `CRectTracker` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CRectTracker::AdjustRect](#adjustrect)|Volá se při změně velikosti obdélníku.|
|[CRectTracker::Draw](#draw)|Vykresluje obdélník.|
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Volá se při vykreslování ohraničení `CRectTracker` objektu.|
|[CRectTracker::GetHandleMask](#gethandlemask)|Volá za účelem získání maska `CRectTracker` úchyty pro změnu velikosti položky.|
|[CRectTracker::GetTrueRect](#gettruerect)|Vrátí šířku a výšku obdélníku, včetně úchyty pro změnu velikosti.|
|[CRectTracker::HitTest](#hittest)|Vrátí aktuální pozici kurzoru souvisí `CRectTracker` objektu.|
|[CRectTracker::NormalizeHit](#normalizehit)|Normalizuje kód spuštění testu.|
|[CRectTracker::OnChangedRect](#onchangedrect)|Volá se, když byl obdélník se změněnou velikostí nebo přesunut.|
|[CRectTracker::SetCursor](#setcursor)|Nastaví kurzor, v závislosti na jeho pozice v obdélníku.|
|[CRectTracker::Track](#track)|Umožňuje uživateli manipulovat s obdélníku.|
|[CRectTracker::TrackRubberBand](#trackrubberband)|Umožňuje uživateli "pružných" výběr.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Určuje velikost úchyty pro změnu velikosti.|
|[CRectTracker::m_nStyle](#m_nstyle)|Aktuální style(s) sledovacímu modulu.|
|[CRectTracker::m_rect](#m_rect)|Aktuální pozice (v pixelech) obdélníku.|
|[CRectTracker::m_sizeMin](#m_sizemin)|Určuje minimální obdélník šířku a výšku.|

## <a name="remarks"></a>Poznámky

`CRectTracker` nemá základní třídu.

I když `CRectTracker` třída je navržena k umožnění uživatelům pracovat s položkami OLE pomocí grafického rozhraní, jeho použití se neomezuje na aplikace pro práci s OLE. Dá se použít kdekoli uživatelské rozhraní je povinný.

`CRectTracker` ohraničení může být plná nebo tečkované čáry. Položky můžete daný šrafované ohraničení nebo překrývající se šrafované vzorem k označení různých stavů položky. Můžete umístit na vnější nebo vnitřní osm úchyty pro změnu velikosti ohraničení položky. (Vysvětlení úchyty pro změnu velikosti, najdete v článku [GetHandleMask](#gethandlemask).) A konečně `CRectTracker` vám umožní změnit orientaci ovládacího prvku položky během změny velikosti.

Použití `CRectTracker`, sestavit `CRectTracker` a určení, které stavy zobrazení jsou inicializovány. Pak můžete toto rozhraní poskytnout uživateli vizuální zpětnou vazbu na aktuální stav přidružené položky OLE `CRectTracker` objektu.

Další informace o používání `CRectTracker`, najdete v článku [snímače](../../mfc/trackers.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CRectTracker`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

##  <a name="adjustrect"></a>  CRectTracker::AdjustRect

Volá se rozhraním při změně velikosti obdélník sledování pomocí úchyt pro změnu velikosti.

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*nHandle*<br/>
Index popisovač použitý.

*lprect –*<br/>
Ukazatel na aktuální velikost pravoúhelníku. (Velikost obdélníku je dán jeho výška a šířka.)

### <a name="remarks"></a>Poznámky

Výchozí chování této funkce umožňuje změnit pouze tehdy, když orientaci v obdélníku `Track` a `TrackRubberBand` jsou volány pomocí převrácení povolené.

Přepsání této funkce ovládací prvek úprav obdélník sledování během operace přetahování. Jedním ze způsobů je upravit podle zadané souřadnice *lprect –* před vrácením.

Speciální funkce, které nejsou přímo podporované `CRectTracker`, jako jsou přichycení k mřížce nebo keep poměr stran, lze provést tak, že přepíšete této funkce.

##  <a name="crecttracker"></a>  CRectTracker::CRectTracker

Vytvoří a inicializuje `CRectTracker` objektu.

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*lpSrcRect*<br/>
Souřadnice objektu obdélník.

*nStyle*<br/>
Určuje styl `CRectTracker` objektu. Podporují se tyto styly:

- `CRectTracker::solidLine` Použijte plnou čáru ohraničení obdélníku.

- `CRectTracker::dottedLine` Použijte tečkovaná čára ohraničení obdélníku.

- `CRectTracker::hatchedBorder` Použití vzoru šrafované ohraničení obdélníku.

- `CRectTracker::resizeInside` Změna velikosti popisovače umístěný uvnitř obdélníku.

- `CRectTracker::resizeOutside` Změna velikosti popisovače nacházejících se mimo obdélníku.

- `CRectTracker::hatchInside` Zasílána modelu zahrnuje celou obdélník.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor inicializuje `CRectTracker` objektu s hodnotami z *lpSrcRect* a inicializuje výchozí systémové nastavení dalších velikostí. Pokud objekt je vytvořen bez parametrů, `m_rect` a `m_nStyle` neinicializované datové členy.

##  <a name="draw"></a>  CRectTracker::Draw

Voláním této funkce kreslení obdélníku vnější čar a vnitřní oblasti.

```
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
Ukazatel na kontext zařízení na základě které chcete kreslit.

### <a name="remarks"></a>Poznámky

Styl sledovacímu modulu za Určuje, jak se dělá výkresu. Zobrazit v konstruktoru pro `CRectTracker` Další informace o dostupných stylů.

##  <a name="drawtrackerrect"></a>  CRectTracker::DrawTrackerRect

Volá se rozhraním, když došlo ke změně pozice sledovacímu modulu za while uvnitř `Track` nebo `TrackRubberBand` členskou funkci.

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*lprect –*<br/>
Ukazatel `RECT` nakreslit obdélník, který obsahuje.

*pWndClipTo*<br/>
Ukazatel na okno pro použití v obdélníku oříznutí.

*primární řadič domény*<br/>
Ukazatel na kontext zařízení na základě které chcete kreslit.

*pWnd*<br/>
Ukazatel na okno, ve kterém bude probíhat výkresu.

### <a name="remarks"></a>Poznámky

Výchozí implementace volá `CDC::DrawFocusRect`, které kreslí tečkovaná obdélník.

Přepsání této funkce můžete zadat jinou zpětnou vazbu během operace sledování.

##  <a name="gethandlemask"></a>  CRectTracker::GetHandleMask

Rozhraní volá tuto funkci člena k načtení maska pro obdélníku úchyty pro změnu velikosti.

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>Návratová hodnota

Maska `CRectTracker` úchyty pro změnu velikosti položky.

### <a name="remarks"></a>Poznámky

Úchyty pro změnu velikosti objeví na strany a rohů obdélníku a umožní uživateli řídit tvaru a velikosti obdélníku.

Obdélník má číslované 0-7 8 úchyty pro změnu velikosti. Každý úchyt pro změnu velikosti je reprezentován trochu v masce; Hodnota této verze je 2 ^ *n*, kde *n* je číslo popisovač změny velikosti. Služba BITS 0 – 3 odpovídají úchyty pro změnu velikosti roh, počínaje nahoře vlevo přesunutí po směru hodinových ručiček. BITS 4 – 7 odpovídají na straně změnit velikost v horní části po směru hodinových ručiček od obslužné rutiny. Následující obrázek znázorňuje úchyty pro změnu velikosti obdélníku a jejich odpovídající velikost popisovač čísla a hodnoty:

![Změnit velikost čísla popisovač](../../mfc/reference/media/vc35dp1.gif "vc35dp1")

Výchozí implementace `GetHandleMask` vrátí maska bitů tak, aby zobrazily úchyty pro změnu velikosti. Pokud jeden bit zapnutý, bude vykreslen odpovídající úchyt pro změnu velikosti.

Přepište tato členská funkce pro skrytí nebo zobrazení, že na zadaný úchyty pro změnu velikosti.

##  <a name="gettruerect"></a>  CRectTracker::GetTrueRect

Volání této funkce načtete souřadnice obdélníku.

```
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>Parametry

*lpTrueRect*<br/>
Ukazatel `RECT` struktura, která bude obsahovat zařízení souřadnice `CRectTracker` objektu.

### <a name="remarks"></a>Poznámky

Dimenze obdélníku zahrnují výšku a šířku jakékoli úchyty pro změnu velikosti umístěn na vnější okraj. Při vrácení, *lpTrueRect* je vždy normalizované rámečku v souřadnicích zařízení.

##  <a name="hittest"></a>  CRectTracker::HitTest

Voláním této funkce zjistěte, zda má uživatel obstaral úchyt pro změnu velikosti.

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>Parametry

*Bod*<br/>
Bod, v souřadnicích zařízení pro testování.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota je založena na Výčtový typ `CRectTracker::TrackerHit` a může mít jednu z následujících hodnot:

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight` 1

- `CRectTracker::hitBottomRight` 2

- `CRectTracker::hitBottomLeft` 3

- `CRectTracker::hitTop` 4

- `CRectTracker::hitRight` 5

- `CRectTracker::hitBottom` 6

- `CRectTracker::hitLeft` 7

- `CRectTracker::hitMiddle` 8

##  <a name="m_nhandlesize"></a>  CRectTracker::m_nHandleSize

Velikost v pixelech, o `CRectTracker` úchyty pro změnu velikosti.

```
int m_nHandleSize;
```

### <a name="remarks"></a>Poznámky

Inicializovat výchozí systém hodnotou.

##  <a name="m_rect"></a>  CRectTracker::m_rect

Aktuální pozice rámečku v souřadnicích klienta (v pixelech).

```
CRect m_rect;
```

##  <a name="m_sizemin"></a>  CRectTracker::m_sizeMin

Minimální velikost pravoúhelníku.

```
CSize m_sizeMin;
```

### <a name="remarks"></a>Poznámky

Obě hodnoty výchozí `cx` a `cy`, se počítají na základě systému výchozí hodnota pro šířku ohraničení. Tento datový člen je používán pouze `AdjustRect` členskou funkci.

##  <a name="m_nstyle"></a>  CRectTracker::m_nStyle

Aktuální styl rámečku.

```
UINT m_nStyle;
```

### <a name="remarks"></a>Poznámky

Zobrazit [CRectTracker::CRectTracker](#crecttracker) seznam možných styly.

##  <a name="normalizehit"></a>  CRectTracker::NormalizeHit

Volání této funkce převedete potenciálně obrácenou popisovač.

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>Parametry

*nHandle*<br/>
Obslužná rutina vybraný uživatelem.

### <a name="return-value"></a>Návratová hodnota

Index normalizované popisovač.

### <a name="remarks"></a>Poznámky

Když `CRectTracker::Track` nebo `CRectTracker::TrackRubberBand` se volá s převrácení povoleny, je možné pro obdélník obrácený na ose x a osy y. Pokud k tomu dojde, `HitTest` vrátí popisovačů, které se také převrátí s ohledem na obdélníku. Totiž nevhodný pro kreslení zpětnou vazbu kurzor zpětnou vazbu, závisí na obrazovce pozici obdélníku, ne část obdélník datová struktura, která budou upraveny.

##  <a name="onchangedrect"></a>  CRectTracker::OnChangedRect

Volá se rozhraním, pokaždé, když se obdélník sledovací modul byl změněn během volání `Track`.

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>Parametry

*rectOld*<br/>
Obsahuje staré souřadnice zařízení `CRectTracker` objektu.

### <a name="remarks"></a>Poznámky

V době je tato funkce volána, veškerá zpětná vazba nakreslit `DrawTrackerRect` byla odebrána. Výchozí implementace této funkce nemá žádný účinek.

Tato funkce přepište, pokud chcete provádět všechny akce po změně velikosti obdélníku.

##  <a name="setcursor"></a>  CRectTracker::SetCursor

Voláním této funkce změnit tvar ukazatele, zatímco je nad `CRectTracker` objektu oblasti.

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Odkazuje na okno, které aktuálně obsahuje kurzor.

*nHitTest*<br/>
Výsledky předchozí volání testu ze zprávy ovládací prvky WM_SETCURSOR.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud předchozí položka prostřednictvím sledování obdélník; jinak 0.

### <a name="remarks"></a>Poznámky

Voláním této funkce z uvnitř funkce, která zpracovává zprávu WM_SETCURSOR okno (obvykle `OnSetCursor`).

##  <a name="track"></a>  CRectTracker::Track

Voláním této funkce k zobrazení uživatelského rozhraní pro změnu velikosti obdélníku.

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Okno objekt, který obsahuje obdélníku.

*Bod*<br/>
Souřadnice zařízení aktuální pozice myši vzhledem ke klientské oblasti.

*bAllowInvert*<br/>
Při hodnotě TRUE se obdélník můžete obrácený společně osu x nebo y; v opačném případě FALSE.

*pWndClipTo*<br/>
Okno, které kreslicí operace bude oříznut, aby. Pokud má hodnotu NULL, *pWnd* slouží jako obdélník oříznutí.

### <a name="return-value"></a>Návratová hodnota

Pokud se stiskne klávesu ESC, zastavení procesu sledování, obdélník uložené v nástroji Sledování se nezmění, a vrátí se 0. Pokud změna se potvrdí, hýbání myší a uvolněním levé tlačítko myši, novou pozici a velikost je zaznamenán v nástroji Sledování obdélníku a vrátí nenulovou hodnotu.

### <a name="remarks"></a>Poznámky

To je obvykle volána z uvnitř funkce aplikace, která zpracovává `WM_LBUTTONDOWN` zprávy (obvykle `OnLButtonDown`).

Tuto funkci bude zachycení myši, dokud uživatel uvolní levé tlačítko myši, stiskne klávesu ESC nebo stiskne pravé tlačítko myši. Jak uživatel přesouvá ukazatel myši, zpětná vazba se aktualizuje voláním `DrawTrackerRect` a `OnChangedRect`.

Pokud *bAllowInvert* má hodnotu TRUE, obdélník sledování můžete obrácený na osu x nebo osu y.

##  <a name="trackrubberband"></a>  CRectTracker::TrackRubberBand

Voláním této funkce dělat výběr metodou pružných.

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Okno objekt, který obsahuje obdélníku.

*Bod*<br/>
Souřadnice zařízení aktuální pozice myši vzhledem ke klientské oblasti.

*bAllowInvert*<br/>
Při hodnotě TRUE se obdélník můžete obrácený společně osu x nebo y; v opačném případě FALSE.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se přesunul myš a rámeček není prázdná. jinak 0.

### <a name="remarks"></a>Poznámky

Je obvykle volána z uvnitř funkce aplikace, která zpracovává zprávu WM_LBUTTONDOWN (obvykle `OnLButtonDown`).

Tuto funkci bude zachycení myši, dokud uživatel uvolní levé tlačítko myši, stiskne klávesu ESC nebo stiskne pravé tlačítko myši. Jak uživatel přesouvá ukazatel myši, zpětná vazba se aktualizuje voláním `DrawTrackerRect` a `OnChangedRect`.

Sledování probíhá s typ pružné pásma výběr z pravého dolního popisovače. Pokud převrácení je povolený, můžou mít velikost obdélník přetažením buď nahoru a vlevo nebo dolů a doprava.

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC sledovací modul](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC DRAWCLI](../../visual-cpp-samples.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleResizeBar – třída](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect – třída](../../atl-mfc-shared/reference/crect-class.md)
