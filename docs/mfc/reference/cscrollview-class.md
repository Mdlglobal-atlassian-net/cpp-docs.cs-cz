---
title: Třída CScrollView | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CScrollView
- AFXWIN/CScrollView
- AFXWIN/CScrollView::CScrollView
- AFXWIN/CScrollView::CheckScrollBars
- AFXWIN/CScrollView::FillOutsideRect
- AFXWIN/CScrollView::GetDeviceScrollPosition
- AFXWIN/CScrollView::GetDeviceScrollSizes
- AFXWIN/CScrollView::GetScrollPosition
- AFXWIN/CScrollView::GetTotalSize
- AFXWIN/CScrollView::ResizeParentToFit
- AFXWIN/CScrollView::ScrollToPosition
- AFXWIN/CScrollView::SetScaleToFitSize
- AFXWIN/CScrollView::SetScrollSizes
dev_langs:
- C++
helpviewer_keywords:
- CScrollView [MFC], CScrollView
- CScrollView [MFC], CheckScrollBars
- CScrollView [MFC], FillOutsideRect
- CScrollView [MFC], GetDeviceScrollPosition
- CScrollView [MFC], GetDeviceScrollSizes
- CScrollView [MFC], GetScrollPosition
- CScrollView [MFC], GetTotalSize
- CScrollView [MFC], ResizeParentToFit
- CScrollView [MFC], ScrollToPosition
- CScrollView [MFC], SetScaleToFitSize
- CScrollView [MFC], SetScrollSizes
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b480ee1118551b09c705fb4f79f8a50c0a1f895
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079564"
---
# <a name="cscrollview-class"></a>CScrollView – třída
A [CView](../../mfc/reference/cview-class.md) s možností posouvání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CScrollView : public CView  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CScrollView::CScrollView](#cscrollview)|Vytvoří `CScrollView` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CScrollView::CheckScrollBars](#checkscrollbars)|Označuje, zda má posuňte zobrazení vodorovného a svislého posuvníky.|  
|[CScrollView::FillOutsideRect](#filloutsiderect)|Vyplní celé oblasti zobrazení mimo oblast posouvání.|  
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Získá aktuální pozici posunutí v jednotkách zařízení.|  
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Získá aktuální režim mapování, celková velikost a velikosti řádku a stránka posouvatelného zobrazení. Velikosti jsou v jednotkách zařízení.|  
|[CScrollView::GetScrollPosition](#getscrollposition)|Získá aktuální pozici posunutí v logické jednotky.|  
|[CScrollView::GetTotalSize](#gettotalsize)|Získá celková velikost posuňte zobrazení v logické jednotky.|  
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|Způsobí, že velikost zobrazení určují velikost jeho rámečku.|  
|[CScrollView::ScrollToPosition](#scrolltoposition)|Posune zobrazení tak, aby k danému bodu, zadaný v logické jednotky.|  
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Posuňte zobrazení umístí do režimu škálování přizpůsobit.|  
|[CScrollView::SetScrollSizes](#setscrollsizes)|Nastaví režim mapování, celková velikost a vodorovného a svislého posouvacího objemy posuňte zobrazení.|  
  
## <a name="remarks"></a>Poznámky  
 Dokáže zpracovat standard posouvání sami všechny třídy odvozené od `CView` přepsáním mapované zpráva [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) členské funkce. Ale `CScrollView` přidá následující funkce, které chcete jeho `CView` možnosti:  
  
-   Spravuje mapování režimy a velikosti oken a zobrazení.  
  
-   Posune automaticky v odpovědi na zprávy posuvníku.  
  
-   V odpovědi na zprávy z klávesnice, myš posouvání nebo kolečkem posune automaticky.  
  
 Chcete-li posouvat automaticky v odpovědi na zprávy z klávesnice, přidejte zprávu WM_KEYDOWN a testovat VK_DOWN, VK_PREV a volání [SetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787597).  
  
 Dokáže zpracovat kolečka myši posouvání sami přepsáním mapované zpráva [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) a [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) členské funkce. Stejně jako jsou `CScrollView`, doporučené chování pro podporu těchto členských funkcí [WM_MOUSEWHEEL](http://msdn.microsoft.com/library/windows/desktop/ms645617), zpráva otočení kolečka.  
  
 Pokud chcete využít výhod automatické posouvání, odvozena třídě zobrazení z `CScrollView` místo z `CView`. Když je zobrazení nejprve vytvořit, pokud chcete vypočítat velikost posouvatelného zobrazení na základě velikosti dokumentu, volání `SetScrollSizes` – členská funkce z přepsání buď [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) nebo [ CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Musíte napsat vlastní kód pro dotaz na velikost dokumentu. Příklad, naleznete v části [Scribble ukázka](../../visual-cpp-samples.md).)  
  
 Volání `SetScrollSizes` – členská funkce nastaví režim zobrazení mapování, celkový počet rozměrů posuňte zobrazení a objemy posun vodorovně a svisle. Všech velikostí jsou logické jednotky. Logická velikost zobrazení se obvykle počítá z dat uložených v dokumentu, ale v některých případech můžete chtít zadat s pevnou velikostí. Příklady obou přístupů najdete v tématu [CScrollView::SetScrollSizes](#setscrollsizes).  
  
 Zadáte objemy posun vodorovně a svisle ve logické jednotky. Ve výchozím nastavení, pokud uživatel klikne posuvníku panelu hřídel mimo posouvací políčko `CScrollView` posune "stránka". Pokud uživatel klikne na libovolném konci posuvníku, posouvací šipky `CScrollView` posune "řádek". Ve výchozím nastavení na stránce je 1/10 celkové velikosti zobrazení; řádek je 1/10 velikost stránky. Tyto výchozí hodnoty přepsání předáním vlastní velikostí v `SetScrollSizes` – členská funkce. Může například nastavit vodorovné velikost na některé podíl šířky celková velikost a na svislé velikost height výšky řádku v aktuálním písmem.  
  
 Místo posouvání, `CScrollView` může automaticky škálovat zobrazení aktuální velikost okna. V tomto režimu zobrazení nemá žádné posuvníky a logickém zobrazení je roztažen tak nebo zmenšit, přesně podle okna klientské oblasti. Chcete-li použít tuto funkci škálování přizpůsobit, volejte [CScrollView::SetScaleToFitSize](#setscaletofitsize). (Volání buď `SetScaleToFitSize` nebo `SetScrollSizes`, ale ne obojí.)  
  
 Před `OnDraw` je volána funkce člen vaší třídy odvozené zobrazení, `CScrollView` automaticky přizpůsobí počátek zobrazení `CPaintDC` objekt kontextu zařízení, který předává do `OnDraw`.  
  
 Upravit zobrazení počátek okno posouvání `CScrollView` přepsání [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Toto nastavení je automatické pro `CPaintDC` kontextu zařízení, `CScrollView` předá `OnDraw`, ale musí volat `CScrollView::OnPrepareDC` sami pro jiné kontexty zařízení použijete, například `CClientDC`. Můžete přepsat `CScrollView::OnPrepareDC` nastavit pera, barva pozadí a další atributy kreslení, ale volat základní třídy, chcete-li provést škálování.  
  
 Posuvníky můžete zobrazit na třech místech relativně k zobrazení, jak je znázorněno v následujících případech:  
  
-   Posuvníky standardní styl okna lze nastavit pro zobrazení pomocí **ws_hscroll –** a **ws_vscroll –**[Windows styly](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
-   Ovládací prvky posuvníku lze také přidat na snímek, který obsahuje zobrazení, ve kterém se předává případ rozhraní `WM_HSCROLL` a `WM_VSCROLL` zprávy okně s rámečkem zobrazit aktuálně aktivní.  
  
-   Rozhraní framework také předá posuňte zprávy z `CSplitterWnd` ovládací prvek typu rozdělovač do podokna aktuálně aktivní rozdělovače (zobrazení). Při umístění do [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) s sdílené posuvníky `CScrollView` objekt použije těm, které jsou sdílené nikoli vytvářet vlastní.  
  
 Další informace o používání `CScrollView`, najdete v části [Document/View – architektura](../../mfc/document-view-architecture.md) a [odvozené zobrazení třídy dostupné v prostředí MFC](../../mfc/derived-view-classes-available-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CScrollView`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
##  <a name="checkscrollbars"></a>  CScrollView::CheckScrollBars  
 Volání této funkce člen k určení, zda posuňte zobrazení má vodorovného a svislého řádky.  
  
```  
void CheckScrollBars(
    BOOL& bHasHorzBar,  
    BOOL& bHasVertBar) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *bHasHorzBar*  
 Označuje, že aplikace má vodorovného posuvníku.  
  
 *bHasVertBar*  
 Označuje, že aplikace má svislého posuvníku.  
  
##  <a name="cscrollview"></a>  CScrollView::CScrollView  
 Vytvoří `CScrollView` objektu.  
  
```  
CScrollView();
```  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat buď `SetScrollSizes` nebo `SetScaleToFitSize` před posuňte zobrazení je možné použít.  
  
##  <a name="filloutsiderect"></a>  CScrollView::FillOutsideRect  
 Volání `FillOutsideRect` k vyplnění oblasti zobrazení, které se zobrazí mimo oblasti posouvání.  
  
```  
void FillOutsideRect(
    CDC* pDC,  
    CBrush* pBrush);
```  
  
### <a name="parameters"></a>Parametry  
 *primárního řadiče domény*  
 Kontext zařízení, ve kterém má být práce naplnění.  
  
 *pBrush*  
 Štětec, se kterou má být vyplněna oblasti.  
  
### <a name="remarks"></a>Poznámky  
 Použití `FillOutsideRect` ve svém posuňte zobrazení `OnEraseBkgnd` funkce obslužné rutiny, aby se zabránilo nadměrnému pozadí překreslení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]  
  
##  <a name="getdevicescrollposition"></a>  CScrollView::GetDeviceScrollPosition  
 Volání `GetDeviceScrollPosition` když potřebujete aktuální vodorovného a svislého polohy jezdcem ve posuvníky.  
  
```  
CPoint GetDeviceScrollPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vodorovného a svislého pozice (v jednotkách zařízení) jezdcem jako `CPoint` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato souřadnic pár odpovídá umístění v dokumentu, do které byl přešli levém horním rohu zobrazení. To je užitečné pro odsazení pozic zařízení myši na zobrazení posuňte pozic zařízení.  
  
 `GetDeviceScrollPosition` vrací hodnoty v jednotkách zařízení. Pokud chcete, aby logické jednotky, použijte `GetScrollPosition` místo.  
  
##  <a name="getdevicescrollsizes"></a>  CScrollView::GetDeviceScrollSizes  
 `GetDeviceScrollSizes` získá aktuální režim mapování, celková velikost a velikosti řádku a stránka posouvatelného zobrazení.  
  
```  
void GetDeviceScrollSizes(
    int& nMapMode,  
    SIZE& sizeTotal,  
    SIZE& sizePage,  
    SIZE& sizeLine) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nMapMode*  
 Vrátí aktuální režim mapování pro toto zobrazení. Seznam možných hodnot najdete v tématu `SetScrollSizes`.  
  
 *sizeTotal*  
 Vrátí aktuální celková velikost zobrazení, přejděte v jednotkách zařízení.  
  
 *sizePage*  
 Vrátí aktuální vodorovného a svislého objemy posun v každém směru v reakci na myši, klikněte na tlačítko v hřídel posuvníku. **Cx** člen obsahuje vodorovné velikost. **Cy** člen obsahuje vertikální velikost.  
  
 *sizeLine*  
 Vrátí aktuální vodorovného a svislého objemy posun v každém směru v reakci na myši, klikněte na tlačítko v posouvací šipky. **Cx** člen obsahuje vodorovné velikost. **Cy** člen obsahuje vertikální velikost.  
  
### <a name="remarks"></a>Poznámky  
 Velikosti jsou v jednotkách zařízení. Tato funkce člen je zřídka volána.  
  
##  <a name="getscrollposition"></a>  CScrollView::GetScrollPosition  
 Volání `GetScrollPosition` když potřebujete aktuální vodorovného a svislého polohy jezdcem ve posuvníky.  
  
```  
CPoint GetScrollPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vodorovného a svislého pozice (v logické jednotky) přejděte polí jako `CPoint` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato souřadnic pár odpovídá umístění v dokumentu, do které byl přešli levém horním rohu zobrazení.  
  
 `GetScrollPosition` vrací hodnoty v logické jednotky. Pokud chcete zařízení jednotky, použijte `GetDeviceScrollPosition` místo.  
  
##  <a name="gettotalsize"></a>  CScrollView::GetTotalSize  
 Volání `GetTotalSize` načíst aktuální velikosti vodorovného a svislého posouvacího zobrazení.  
  
```  
CSize GetTotalSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celková velikost posuňte zobrazení v logické jednotky. Vodorovné velikost **cx** členem `CSize` vrátit hodnotu. Svislé velikost **cy** člen.  
  
##  <a name="resizeparenttofit"></a>  CScrollView::ResizeParentToFit  
 Volání `ResizeParentToFit` umožníte velikost zobrazení určují velikost jeho rámce okna.  
  
```  
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bShrinkOnly*  
 Druh Změna velikosti k provedení. Výchozí hodnota **TRUE**, zmenší okně s rámečkem v případě potřeby. Pro zobrazení velké nebo malé rámce windows se však zobrazí posuvníky. Hodnota **FALSE** způsobí, že zobrazení vždy přesně změnit velikost rámce okna. To může být poněkud nebezpečná vzhledem k tomu může dojít okně s rámečkem příliš velká a nevejde se do okna rámce více rozhraní (MDI) dokumentu nebo na obrazovce.  
  
### <a name="remarks"></a>Poznámky  
 Toto nastavení se doporučuje jenom pro zobrazení v rámečku podřízených oken MDI. Použití `ResizeParentToFit` v `OnInitialUpdate` obslužné rutiny funkce vaší odvozené `CScrollView` třídy. Příklad této funkce člen, naleznete v části [CScrollView::SetScrollSizes](#setscrollsizes).  
  
 `ResizeParentToFit` předpokládá, že byla nastavena velikost okna zobrazení. Pokud velikost okna zobrazení nebyl nastaven při `ResizeParentToFit` je volána, budete mít kontrolní výrazy. Aby se zajistilo, že tato situace, použije toto volání před voláním `ResizeParentToFit`:  
  
 [!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="scrolltoposition"></a>  CScrollView::ScrollToPosition  
 Volání `ScrollToPosition` přesuňte k danému bodu v zobrazení.  
  
```  
void ScrollToPosition(POINT pt);
```  
  
### <a name="parameters"></a>Parametry  
 *PT*  
 Bod přesuňte, logické jednotky. **x** člena musí být kladné celé číslo (větší než nebo rovno 0 až celková velikost zobrazení). Totéž platí pro **y** člen, pokud je režim mapování `MM_TEXT`. **y** člen je záporný mapování režimy, jiné než `MM_TEXT`.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazení bude přesunut oblasti, takže tento bod je v levém horním rohu okna. Tato funkce člena nesmí být volána, pokud zobrazení přizpůsobí se.  
  
##  <a name="setscaletofitsize"></a>  CScrollView::SetScaleToFitSize  
 Volání `SetScaleToFitSize` když chcete automaticky škálovat na velikost zobrazení aktuální velikost okna.  
  
```  
void SetScaleToFitSize(SIZE sizeTotal);
```  
  
### <a name="parameters"></a>Parametry  
 *sizeTotal*  
 Vodorovného a svislého velikosti, na které se škálovat zobrazení. Posuňte zobrazení velikost se měří v logické jednotky. Je součástí vodorovné velikost **cx** člen. Svislé velikost je součástí **cy** člen. Obě **cx** a **cy** musí být větší než nebo rovna 0.  
  
### <a name="remarks"></a>Poznámky  
 S posuvníky může být pouze část logickém zobrazení viditelné kdykoli. Ale pomocí funkce škálování přizpůsobit zobrazení nemá žádné posuvníky a logickém zobrazení je roztažen tak nebo zmenšit, přesně podle okna klientské oblasti. Při změně velikosti okna zobrazení nevykresluje jeho data nové škálované na základě velikosti okna.  
  
 Budete obvykle umístit volání `SetScaleToFitSize` v přepsání zobrazení `OnInitialUpdate` – členská funkce. Pokud nechcete, aby automatické škálování, zavolejte `SetScrollSizes` členské funkce místo.  
  
 `SetScaleToFitSize` lze použít k provedení operace se "Zvětšení na vyhovující". Použití `SetScrollSizes` znovu inicializovat posouvání.  
  
 `SetScaleToFitSize` předpokládá, že byla nastavena velikost okna zobrazení. Pokud velikost okna zobrazení nebyl nastaven při `SetScaleToFitSize` je volána, budete mít kontrolní výrazy. Aby se zajistilo, že tato situace, použije toto volání před voláním `SetScaleToFitSize`:  
  
 [!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]  
  
##  <a name="setscrollsizes"></a>  CScrollView::SetScrollSizes  
 Volání `SetScrollSizes` po zobrazení Chystáte se aktualizovat.  
  
```  
void SetScrollSizes(
    int nMapMode,  
    SIZE sizeTotal,  
    const SIZE& sizePage = sizeDefault,  
    const SIZE& sizeLine = sizeDefault);
```  
  
### <a name="parameters"></a>Parametry  
 *nMapMode*  
 Režim mapování pro toto zobrazení. Možné hodnoty patří:  
  
|Mapování režimu|Logická jednotka|Kladné osy y Extends...|  
|------------------|------------------|---------------------------------|  
|`MM_TEXT`|1 pixel|Směrem dolů|  
|`MM_HIMETRIC`|0,01 mm|Nahoru|  
|`MM_TWIPS`|1/1440 v|Nahoru|  
|`MM_HIENGLISH`|0,001 in|Nahoru|  
|`MM_LOMETRIC`|0,1 mm|Nahoru|  
|`MM_LOENGLISH`|0,01 in|Nahoru|  
  
 Všechny tyto režimy jsou definovány v systému Windows. Dva režimy standardní mapování `MM_ISOTROPIC` a `MM_ANISOTROPIC`, nepoužívají se pro `CScrollView`. Poskytuje knihovny tříd `SetScaleToFitSize` – členská funkce škálování zobrazení tak, aby velikost okna. Tři sloupce v tabulce výše popisuje souřadnic orientaci.  
  
 *sizeTotal*  
 Celková velikost posuňte zobrazení. **Cx** člen obsahuje vodorovné rozsah. **Cy** člen obsahuje vertikální rozsah. Velikosti jsou v logické jednotky. Obě **cx** a **cy** musí být větší než nebo rovna 0.  
  
 *sizePage*  
 Posuňte se v každém směru v reakci na myši činí vodorovného a svislého klikněte v hřídel posuvníku. **Cx** člen obsahuje vodorovné velikost. **Cy** člen obsahuje vertikální velikost.  
  
 *sizeLine*  
 Posuňte se v každém směru v reakci na myši činí vodorovného a svislého klikněte v posouvací šipky. **Cx** člen obsahuje vodorovné velikost. **Cy** člen obsahuje vertikální velikost.  
  
### <a name="remarks"></a>Poznámky  
 Volání v přepsání z `OnUpdate` – členská funkce Upravit posouvání charakteristiky, když například původně zobrazení dokumentu nebo při změně velikosti.  
  
 Obvykle se získat informace o velikosti z dokumentu přidružené zobrazení voláním dokumentu členské funkce, třeba volat `GetMyDocSize`, který zadáte s odvození dokumentové třídy. Následující kód ukazuje tento přístup:  
  
 [!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]  
  
 Alternativně můžete někdy potřebovat nastavit pevnou velikost, jako v následujícím kódu:  
  
 [!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]  
  
 Je nutné nastavit režim mapování na všechny režimy mapování Windows s výjimkou `MM_ISOTROPIC` nebo `MM_ANISOTROPIC`. Pokud chcete použít mapování neomezeným režimu, zavolejte `SetScaleToFitSize` – členská funkce místo `SetScrollSizes`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC DIBLOOK](../../visual-cpp-samples.md)   
 [CView – třída](../../mfc/reference/cview-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CView – třída](../../mfc/reference/cview-class.md)   
 [CSplitterWnd – třída](../../mfc/reference/csplitterwnd-class.md)
