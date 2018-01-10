---
title: "Crecttracker – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1f870ef92296636c8d27fc166d41cdefc54d1585
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crecttracker-class"></a>Crecttracker – třída
Umožňuje položku, kterou chcete zobrazit, přesunout a změnit různé způsoby.  
  
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
|[CRectTracker::AdjustRect](#adjustrect)|Volá se při změně velikosti rámeček.|  
|[CRectTracker::Draw](#draw)|Vykreslí rámeček.|  
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Volá se při vykreslování ohraničení `CRectTracker` objektu.|  
|[CRectTracker::GetHandleMask](#gethandlemask)|Volat za účelem získání maska `CRectTracker` úchyty pro změnu velikosti položky.|  
|[CRectTracker::GetTrueRect](#gettruerect)|Vrátí šířky a výšky obdélníku, včetně změny velikosti obslužné rutiny.|  
|[CRectTracker::HitTest](#hittest)|Vrátí aktuální pozice kurzoru související s `CRectTracker` objektu.|  
|[CRectTracker::NormalizeHit](#normalizehit)|Normalizuje stiskněte klávesu testovacího kódu.|  
|[CRectTracker::OnChangedRect](#onchangedrect)|Voláno, pokud byl po změně velikosti nebo přesunut rámeček.|  
|[CRectTracker::SetCursor](#setcursor)|Nastaví kurzor, v závislosti na jeho pozice přes rámeček.|  
|[CRectTracker::Track](#track)|Umožňuje uživateli upravit rámeček.|  
|[CRectTracker::TrackRubberBand](#trackrubberband)|Umožňuje uživateli "pružné vzdálené správy" výběr.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Určuje velikost popisovačů změny velikosti.|  
|[CRectTracker::m_nStyle](#m_nstyle)|Aktuální style(s) ke sledovacímu modulu.|  
|[CRectTracker::m_rect](#m_rect)|Aktuální pozici (v pixelech) rámeček.|  
|[CRectTracker::m_sizeMin](#m_sizemin)|Určuje minimální obdélníku šířku a výšku.|  
  
## <a name="remarks"></a>Poznámky  
 `CRectTracker`nemá základní třídu.  
  
 I když `CRectTracker` třída je navržena k umožnění uživatelům interakci s OLE – položky pomocí grafického rozhraní, není omezen na aplikací s povolenými OLE jeho použití. Dá se použít kdekoli se vyžaduje uživatelské rozhraní.  
  
 `CRectTracker`ohraničení může být plného nebo čáry s koncovými body. Položky můžete danou šrafované ohraničení nebo jako překryvný obrázek s šrafované vzor k označení různé stavy položky. Obslužné rutiny osm změny velikosti můžete umístit na vnější nebo vnitřní ohraničení položky. (Vysvětlení popisovačů změny velikosti najdete v tématu [GetHandleMask](#gethandlemask).) Nakonec `CRectTracker` vám umožní změnit orientaci položky při změně velikosti.  
  
 Chcete-li použít `CRectTracker`, vytvořit `CRectTracker` objektu a určete, které stavy zobrazení jsou inicializovány. Pak můžete toto rozhraní zaslání názoru visual uživatele na aktuální stav položky OLE přidružený `CRectTracker` objektu.  
  
 Další informace o používání `CRectTracker`, najdete v článku [snímačů](../../mfc/trackers.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CRectTracker`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="adjustrect"></a>CRectTracker::AdjustRect  
 Voláno rámcem při změně velikosti obdélníku sledování pomocí popisovač změny velikosti.  
  
```  
virtual void AdjustRect(
    int nHandle,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `nHandle`  
 Index popisovače použít.  
  
 `lpRect`  
 Ukazatel na aktuální velikost rámeček. (Velikost obdélníku je dána jeho výškou a šířkou.)  
  
### <a name="remarks"></a>Poznámky  
 Výchozí chování tato funkce umožňuje orientaci obdélníku, chcete-li změnit pouze tehdy, když `Track` a `TrackRubberBand` se nazývají s převrácení povoleny.  
  
 Funkci k řízení úpravu rámeček sledování během operace přetahování přepište. Jednou z možností je nastavit souřadnice určeného `lpRect` před vrácením.  
  
 Speciální funkce, které nepodporují přímo `CRectTracker`, jako například přichycení k mřížce nebo udržování poměr stran, může být implementováno přepsáním této funkce.  
  
##  <a name="crecttracker"></a>CRectTracker::CRectTracker  
 Vytvoří a inicializuje `CRectTracker` objektu.  
  
```  
CRectTracker();

 
CRectTracker(
    LPCRECT lpSrcRect,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `lpSrcRect`  
 Souřadnice objektu obdélník.  
  
 `nStyle`  
 Určuje styl `CRectTracker` objektu. Podporovány jsou následující styly:  
  
- **CRectTracker::solidLine** použít na souvislou čáru ohraničení rámečku.  
  
- **CRectTracker::dottedLine** použít tečkovaná čára ohraničení rámečku.  
  
- **CRectTracker::hatchedBorder** použití šrafované vzoru ohraničení rámečku.  
  
- **CRectTracker::resizeInside** úchyty umístěný v obdélníku pro změnu velikosti.  
  
- **CRectTracker::resizeOutside** úchyty nacházejících se mimo rámeček pro změnu velikosti.  
  
- **CRectTracker::hatchInside** Hatched vzor popisuje celý rámeček.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí konstruktor inicializuje `CRectTracker` objektu hodnotami z `lpSrcRect` a inicializuje dalších velikostí systémových výchozích hodnot. Pokud objekt je vytvořen bez parametrů, `m_rect` a `m_nStyle` datových členů Neinicializovaný.  
  
##  <a name="draw"></a>CRectTracker::Draw  
 Volání této funkce kreslení obdélníku vnější čar a vnitřní oblasti.  
  
```  
void Draw(CDC* pDC) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na kontext zařízení, ve kterém k vykreslení.  
  
### <a name="remarks"></a>Poznámky  
 Styl ke sledovacímu modulu určuje, jak se provádí kreslení. Najdete v části v konstruktoru pro `CRectTracker` Další informace o dostupných stylů.  
  
##  <a name="drawtrackerrect"></a>CRectTracker::DrawTrackerRect  
 Voláno rámcem vždy, když došlo ke změně pozice ke sledovacímu modulu při uvnitř `Track` nebo `TrackRubberBand` – členská funkce.  
  
```  
virtual void DrawTrackerRect(
    LPCRECT lpRect,  
    CWnd* pWndClipTo,  
    CDC* pDC,  
    CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Ukazatel `RECT` obsahující rámeček k vykreslení.  
  
 `pWndClipTo`  
 Ukazatel na okna pro použití v výstřižek rámeček.  
  
 `pDC`  
 Ukazatel na kontext zařízení, ve kterém k vykreslení.  
  
 `pWnd`  
 Ukazatel na okno, kdy nastane kreslení.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace zavolá `CDC::DrawFocusRect`, který nevykresluje desítkovém obdélníku.  
  
 Funkci k poskytnutí zpětné vazby různých během operace sledování přepište.  
  
##  <a name="gethandlemask"></a>CRectTracker::GetHandleMask  
 Rozhraní framework volá tuto funkci člen načíst maska pro obdélníku změnit velikost obslužné rutiny.  
  
```  
virtual UINT GetHandleMask() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maska `CRectTracker` úchyty pro změnu velikosti položky.  
  
### <a name="remarks"></a>Poznámky  
 Obslužné rutiny změny velikosti se zobrazují v postranní a rozích obdélníku a povolit uživateli řídit velikost obdélníku a tvar.  
  
 Obdélníku má 8 zpracovává změny velikosti číslované 0-7. Je každý popisovač změny velikosti reprezentována trochu v masce; Hodnota této verze je 2 ^  *n* , kde  *n*  je číslo popisovač změny velikosti. Bity 0 až 3 odpovídají obslužných rutin změny velikosti rohu počínaje nahoře vlevo přesunutí po směru hodinových ručiček. Služba BITS 4-7 odpovídají na straně změnit velikost popisovače od nejvyšší po směru hodinových ručiček. Následující obrázek znázorňuje zpracovává obdélníku změny velikosti a jejich odpovídajících změnit velikost popisovač čísla a hodnoty:  
  
 ![Změnit velikost popisovač čísla](../../mfc/reference/media/vc35dp1.gif "vc35dp1")  
  
 Výchozí implementaci **GetHandleMask** vrátí maska bity úchyty změny velikosti. Pokud jeden bit na, budou vykreslovat odpovídající popisovač změny velikosti.  
  
 Člen funkci pro skrytí nebo zobrazení, že že označené úchyty pro změnu velikosti přepište.  
  
##  <a name="gettruerect"></a>CRectTracker::GetTrueRect  
 Volání této funkce pro načtení souřadnice rámeček.  
  
```  
void GetTrueRect(LPRECT lpTrueRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpTrueRect`  
 Ukazatel `RECT` souřadnic struktura, která bude obsahovat zařízení `CRectTracker` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Dimenze obdélníku zahrnují výška a šířka všechny změny velikosti popisovače umístěn na vnější ohraničení. Při vrácení, `lpTrueRect` je vždy normalizovaný rámečku v souřadnicích zařízení.  
  
##  <a name="hittest"></a>CRectTracker::HitTest  
 Volání této funkce a zjistěte, zda má uživatel převzatý popisovač změny velikosti.  
  
```  
int HitTest(CPoint point) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Bod v souřadnicích zařízení k testování.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je založena na Výčtový typ **CRectTracker::TrackerHit** a může mít jeden z následujících hodnot:  
  
- **CRectTracker::hitNothing** -1  
  
- **CRectTracker::hitTopLeft** 0  
  
- **CRectTracker::hitTopRight** 1  
  
- **CRectTracker::hitBottomRight** 2  
  
- **CRectTracker::hitBottomLeft** 3  
  
- **CRectTracker::hitTop** 4  
  
- **CRectTracker::hitRight** 5  
  
- **CRectTracker::hitBottom** 6  
  
- **CRectTracker::hitLeft** 7  
  
- **CRectTracker::hitMiddle** 8  
  
##  <a name="m_nhandlesize"></a>CRectTracker::m_nHandleSize  
 Velikost v pixelech z `CRectTracker` úchyty pro změnu velikosti.  
  
```  
int m_nHandleSize;  
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje výchozí hodnota systému.  
  
##  <a name="m_rect"></a>CRectTracker::m_rect  
 Aktuální pozice rámečku v souřadnicích klienta (v pixelech).  
  
```  
CRect m_rect;  
```  
  
##  <a name="m_sizemin"></a>CRectTracker::m_sizeMin  
 Minimální velikost rámeček.  
  
```  
CSize m_sizeMin;  
```  
  
### <a name="remarks"></a>Poznámky  
 Jak výchozí hodnoty, **cx** a **cy**, jsou vypočítávány z výchozí hodnoty systému pro šířku ohraničení. Tento člen dat se používá pouze pomocí `AdjustRect` – členská funkce.  
  
##  <a name="m_nstyle"></a>CRectTracker::m_nStyle  
 Aktuální styl rámečku.  
  
```  
UINT m_nStyle;  
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [CRectTracker::CRectTracker](#crecttracker) seznam možných stylů.  
  
##  <a name="normalizehit"></a>CRectTracker::NormalizeHit  
 Volání této funkce převést potenciálně obráceným popisovač.  
  
```  
int NormalizeHit(int nHandle) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nHandle`  
 Obslužná rutina vybraný uživatelem.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index normalizovaný popisovač.  
  
### <a name="remarks"></a>Poznámky  
 Když `CRectTracker::Track` nebo `CRectTracker::TrackRubberBand` je volána s převrácení povoleny, je možné pro rámeček k Invertovat na ose x, osy y nebo obojí. V takovém případě `HitTest` vrátí obslužných rutin, které jsou s ohledem na rámeček také obrácený. To je nevhodná pro kreslení zpětnou vazbu kurzoru, protože zpětnou vazbu, závisí na obrazovce pozice rámečku, není část obdélníku datová struktura, která se změní.  
  
##  <a name="onchangedrect"></a>CRectTracker::OnChangedRect  
 Voláno rámcem vždy, když došlo ke změně rámeček sledovací modul během volání `Track`.  
  
```  
virtual void OnChangedRect(const CRect& rectOld);
```  
  
### <a name="parameters"></a>Parametry  
 *rectOld*  
 Obsahuje původní souřadnice zařízení `CRectTracker` objektu.  
  
### <a name="remarks"></a>Poznámky  
 V době tato funkce je volána, všechny zpětnou vazbu vykreslené s `DrawTrackerRect` byla odebrána. Výchozí implementace této funkce neprovede žádnou akci.  
  
 Tato funkce přepsání, pokud chcete po změně velikosti rámeček provádět žádné akce.  
  
##  <a name="setcursor"></a>CRectTracker::SetCursor  
 Volání této funkce změnit tvar kurzoru, i když je přes `CRectTracker` oblast objektu.  
  
```  
BOOL SetCursor(
    CWnd* pWnd,  
    UINT nHitTest) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Odkazuje na okno, které aktuálně obsahuje kurzor.  
  
 `nHitTest`  
 Výsledky předchozí přístupů testu z `WM_SETCURSOR` zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud předchozí položka prostřednictvím sledovací modul rámeček; nenulové hodnoty jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce z uvnitř funkce okna, která zpracovává `WM_SETCURSOR` zprávy (obvykle `OnSetCursor`).  
  
##  <a name="track"></a>CRectTracker::Track  
 Volání této funkce, které chcete zobrazit uživatelské rozhraní pro změnu velikosti rámeček.  
  
```  
BOOL Track(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = FALSE,  
    CWnd* pWndClipTo = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Okno objekt, který obsahuje rámeček.  
  
 `point`  
 Souřadnice zařízení aktuální myši pozice relativně k klientské oblasti.  
  
 `bAllowInvert`  
 Pokud **TRUE**, rámeček lze obráceným podél osy x nebo y; jinak **FALSE**.  
  
 `pWndClipTo`  
 Okno, které kreslení operace bude oříznut, aby. Pokud **NULL**, `pWnd` slouží jako rámeček výstřižek.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud stisknutí klávesy ESC se zastavit proces sledování, rámeček uložené v nástroji Sledování se nezmění, a 0 se vrátí. Pokud změna se potvrdí, tak, že pohyb myši a uvolněním levým tlačítkem myši, nové pozice a velikosti se zaznamenává v obdélníku ke sledovacímu modulu a nenulové hodnoty se vrátí.  
  
### <a name="remarks"></a>Poznámky  
 To je obvykle volat z funkce aplikace, který zpracovává `WM_LBUTTONDOWN` zprávy (obvykle `OnLButtonDown`).  
  
 Tato funkce zaznamená myš, dokud uživatel uvolní levé tlačítko myši, stisknutí klávesy ESC nebo stiskem tlačítka pravým tlačítkem myši. Uživatel přesune myší, zpětné vazby aktualizuje voláním `DrawTrackerRect` a `OnChangedRect`.  
  
 Pokud `bAllowInvert` je **TRUE**, rámeček sledování můžete obrácený na ose x nebo osy y.  
  
##  <a name="trackrubberband"></a>CRectTracker::TrackRubberBand  
 Volání této funkce Uděláte to pružné vzdálené výběr.  
  
```  
BOOL TrackRubberBand(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Okno objekt, který obsahuje rámeček.  
  
 `point`  
 Souřadnice zařízení aktuální myši pozice relativně k klientské oblasti.  
  
 `bAllowInvert`  
 Pokud **nastavena hodnota TRUE,** rámeček lze obráceným podél osy x nebo y; jinak **FALSE**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se přesunul myši a rámeček není prázdná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Obvykle nazývá z uvnitř funkce aplikace, který zpracovává `WM_LBUTTONDOWN` zprávy (obvykle `OnLButtonDown`).  
  
 Tato funkce zaznamená myš, dokud uživatel uvolní levé tlačítko myši, stisknutí klávesy ESC nebo stiskem tlačítka pravým tlačítkem myši. Uživatel přesune myší, zpětné vazby aktualizuje voláním `DrawTrackerRect` a `OnChangedRect`.  
  
 Sledování se provádí pomocí typ vzdálené pružné výběr z pravém popisovač. Pokud je povolen převrácení, rámeček velikost lze přizpůsobit tak, že přetáhnete buď nahoru a doleva nebo dolů a doprava.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC sledovací modul](../../visual-cpp-samples.md)   
 [Ukázka MFC DRAWCLI](../../visual-cpp-samples.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleResizeBar – třída](../../mfc/reference/coleresizebar-class.md)   
 [CRect – třída](../../atl-mfc-shared/reference/crect-class.md)
