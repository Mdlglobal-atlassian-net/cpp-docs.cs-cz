---
title: CScrollView – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 5d0eb163fae2aa5fc63470e1c499311ab1a402a6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754417"
---
# <a name="cscrollview-class"></a>CScrollView – třída

[CView](../../mfc/reference/cview-class.md) s možností posouvání.

## <a name="syntax"></a>Syntaxe

```
class CScrollView : public CView
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CScrollView::CScrollView](#cscrollview)|Vytvoří `CScrollView` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CScrollView::Kontrola posuvníků](#checkscrollbars)|Označuje, zda má posuvníkové zobrazení vodorovné a svislé posuvníky.|
|[CScrollView::FillOutsideRect](#filloutsiderect)|Vyplní oblast pohledu mimo oblast posouvání.|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Získá aktuální pozici posouvání v jednotkách zařízení.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Získá aktuální režim mapování, celková velikost a velikost řádku a stránky posuvného zobrazení. Velikosti jsou v jednotkách zařízení.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Získá aktuální pozici posouvání v logických jednotkách.|
|[CScrollView::GetTotalSize](#gettotalsize)|Získá celkovou velikost zobrazení posouvání v logických jednotkách.|
|[CScrollView::Změna velikostiParentToFit](#resizeparenttofit)|Způsobí, že velikost zobrazení diktovat velikost jeho rámce.|
|[CScrollView::Scrolltopozice](#scrolltoposition)|Posune zobrazení do daného bodu určeného v logických jednotkách.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Přepne zobrazení posouvání do režimu přizpůsobení měřítku.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Nastaví režim mapování zobrazení posouvání, celkovou velikost a vodorovné a svislé množství posouvání.|

## <a name="remarks"></a>Poznámky

Můžete zpracovat standardní posouvání sami v `CView` libovolné třídě odvozené z přepsání maškarní zprávy [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) členské funkce. Ale `CScrollView` přidává následující funkce `CView` do svých schopností:

- Spravuje velikosti oken a výřezů a režimy mapování.

- To se posouvá automaticky v reakci na scroll-bar zpráv.

- Posouvá se automaticky v reakci na zprávy z klávesnice, myši bez posouvání nebo kolečka IntelliMouse.

Chcete-li se automaticky posouvat v reakci na zprávy z klávesnice, přidejte zprávu WM_KEYDOWN a otestujte VK_DOWN, VK_PREV a volejte [SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos).

Můžete zpracovat kolečko myši rolování sami přepsáním zprávy mapované [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) a [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) členské funkce. Tyto členské funkce podporují doporučené chování pro WM_MOUSEWHEEL , zprávu o otáčení kol. [WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel) `CScrollView`

Chcete-li využít výhod automatického posouvání, odvodit třídu zobrazení z `CScrollView` místa z `CView`. Pokud chcete při prvním vytvoření zobrazení vypočítat velikost posuvného zobrazení na základě velikosti `SetScrollSizes` dokumentu, zavolejte členskou funkci z přepsání [cview::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) nebo [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Musíte napsat vlastní kód pro dotaz na velikost dokumentu. Například viz [Ukázka klikyháky](../../overview/visual-cpp-samples.md).)

Volání `SetScrollSizes` členské funkce nastaví režim mapování zobrazení, celkové rozměry zobrazení posouvání a částky, které se mají posouvat vodorovně a svisle. Všechny velikosti jsou v logických jednotkách. Logická velikost zobrazení se obvykle vypočítá z dat uložených v dokumentu, ale v některých případech můžete chtít zadat pevnou velikost. Příklady obou přístupů naleznete v tématu [CScrollView::SetScrollSizes](#setscrollsizes).

Částky, které se mají posouvat vodorovně a svisle v logických jednotkách. Ve výchozím nastavení, pokud uživatel klepne na posuvník ový hřídel mimo posuvník, `CScrollView` posune "stránku". Pokud uživatel klepne na šipku posuvníku `CScrollView` na obou koncích posuvníku, posune "řádek". Ve výchozím nastavení je stránka 1/10 celkové velikosti zobrazení; řádek je 1/10 velikosti stránky. Tyto výchozí hodnoty přepište předáním `SetScrollSizes` vlastních velikostí v členské funkci. Můžete například nastavit vodorovnou velikost na určitý zlomek šířky celkové velikosti a svislé velikosti na výšku řádku v aktuálním písmu.

Místo posouvání `CScrollView` může automaticky změnit velikost zobrazení na aktuální velikost okna. V tomto režimu zobrazení nemá žádné posuvníky a logické zobrazení je roztaženo nebo zmenšeno tak, aby přesně odpovídalo klientské oblasti okna. Chcete-li použít tuto funkci přizpůsobit velikosti, zavolejte [CScrollView::SetScaleToFitSize](#setscaletofitsize). (Zavolejte `SetScaleToFitSize` `SetScrollSizes`buď nebo , ale ne obojí.)

Před `OnDraw` voláním členské funkce odvozené třídy zobrazení `CScrollView` automaticky upraví `CPaintDC` počátek výřezu pro `OnDraw`objekt kontextu zařízení, který předává .

Chcete-li upravit počátek výřezu `CScrollView` pro rolovací okno, přepíše [cview::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Tato úprava je `CPaintDC` automatická `CScrollView` pro `OnDraw`kontext zařízení, `CScrollView::OnPrepareDC` který přejde do aplikace , ale `CClientDC`musíte volat sami sebe pro všechny ostatní kontexty zařízení, které používáte, například . Přepsání `CScrollView::OnPrepareDC` můžete přepsat nastavením pera, barvy pozadí a dalších atributů výkresu, ale volání základní třídy pro změnu měřítka.

Posuvníky se mohou zobrazit na třech místech vzhledem k zobrazení, jak je znázorněno v následujících případech:

- Standardní posuvníky ve stylu okna lze nastavit pro zobrazení pomocí WS_HSCROLL a WS_VSCROLL[styly systému Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles).

- Posuvníkové ovládací prvky lze také přidat do rámce obsahujícího zobrazení, v takovém případě rozhraní vpřed WM_HSCROLL a WM_VSCROLL zprávy z okna rámce do aktuálně aktivního zobrazení.

- Rozhraní framework také předává `CSplitterWnd` zprávy posouvání z ovládacího prvku rozdělovače do aktuálně aktivního podokna rozdělovače (zobrazení). Při umístění do [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) se sdílenými `CScrollView` posuvníky, objekt bude používat sdílené ty spíše než vytvářet vlastní.

Další informace o `CScrollView`použití naleznete v [tématu Document/View Architecture](../../mfc/document-view-architecture.md) and [Derived View Classes Available in MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cscrollviewcheckscrollbars"></a><a name="checkscrollbars"></a>CScrollView::Kontrola posuvníků

Volání této členské funkce k určení, zda má zobrazení posouvání vodorovné a svislé pruhy.

```cpp
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Parametry

*bHasHorzBar*<br/>
Označuje, že aplikace má vodorovný posuvník.

*bHasVertBar*<br/>
Označuje, že aplikace má svislý posuvník.

## <a name="cscrollviewcscrollview"></a><a name="cscrollview"></a>CScrollView::CScrollView

Vytvoří `CScrollView` objekt.

```
CScrollView();
```

### <a name="remarks"></a>Poznámky

Musíte zavolat `SetScrollSizes` `SetScaleToFitSize` buď nebo před zobrazení posouvání je použitelný.

## <a name="cscrollviewfilloutsiderect"></a><a name="filloutsiderect"></a>CScrollView::FillOutsideRect

Volání `FillOutsideRect` k vyplnění oblasti zobrazení, která se zobrazí mimo oblast posouvání.

```cpp
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Kontext zařízení, ve kterém má být plnění provedeno.

*pŠtětec*<br/>
Kartáč, kterým má být oblast vyplněna.

### <a name="remarks"></a>Poznámky

Použijte `FillOutsideRect` ve funkci obslužné rutiny `OnEraseBkgnd` zobrazení posouvání, abyste zabránili nadměrnému překreslení pozadí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

## <a name="cscrollviewgetdevicescrollposition"></a><a name="getdevicescrollposition"></a>CScrollView::GetDeviceScrollPosition

Volání, `GetDeviceScrollPosition` když potřebujete aktuální vodorovné a svislé pozice posuvníku v posuvníku.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Vodorovné a svislé polohy (v jednotkách zařízení) posuvných polí jako objektu. `CPoint`

### <a name="remarks"></a>Poznámky

Tato dvojice souřadnic odpovídá umístění v dokumentu, do kterého byl posunut levý horní roh zobrazení. To je užitečné pro vyrovnání polohy myši zařízení pro zobrazení polohy zařízení.

`GetDeviceScrollPosition`vrátí hodnoty v jednotkách zařízení. Pokud chcete logické jednotky, použijte `GetScrollPosition` místo toho.

## <a name="cscrollviewgetdevicescrollsizes"></a><a name="getdevicescrollsizes"></a>CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes`získá aktuální režim mapování, celkovou velikost a velikost řádků a stránek posuvného zobrazení.

```cpp
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>Parametry

*nRežim Mapy*<br/>
Vrátí aktuální režim mapování pro toto zobrazení. Seznam možných hodnot naleznete `SetScrollSizes`v tématu .

*sizeTotal*<br/>
Vrátí aktuální celkovou velikost zobrazení posouvání v jednotkách zařízení.

*sizePage*<br/>
Vrátí aktuální vodorovné a svislé částky, aby se posouvala v každém směru v reakci na klepnutí myší v posuvníku. Člen `cx` obsahuje vodorovnou částku. Člen `cy` obsahuje svislou částku.

*velikostČára*<br/>
Vrátí aktuální vodorovné a svislé částky, aby se posouvala v každém směru v reakci na klepnutí myší na šipku posuvníku. Člen `cx` obsahuje vodorovnou částku. Člen `cy` obsahuje svislou částku.

### <a name="remarks"></a>Poznámky

Velikosti jsou v jednotkách zařízení. Tato členská funkce je zřídka volána.

## <a name="cscrollviewgetscrollposition"></a><a name="getscrollposition"></a>CScrollView::GetScrollPosition

Volání, `GetScrollPosition` když potřebujete aktuální vodorovné a svislé pozice posuvníku v posuvníku.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Vodorovné a svislé polohy (v logických jednotkách) posuvných polí jako objektu. `CPoint`

### <a name="remarks"></a>Poznámky

Tato dvojice souřadnic odpovídá umístění v dokumentu, do kterého byl posunut levý horní roh zobrazení.

`GetScrollPosition`vrátí hodnoty v logických jednotkách. Pokud chcete jednotky zařízení, použijte `GetDeviceScrollPosition` místo toho.

## <a name="cscrollviewgettotalsize"></a><a name="gettotalsize"></a>CScrollView::GetTotalSize

Volání `GetTotalSize` načíst aktuální vodorovné a svislé velikosti zobrazení posouvání.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Celková velikost zobrazení posouvání v logických jednotkách. Vodorovná velikost je `cx` v `CSize` členu vrácené hodnoty. Svislá `cy` velikost je v členu.

## <a name="cscrollviewresizeparenttofit"></a><a name="resizeparenttofit"></a>CScrollView::Změna velikostiParentToFit

Volání, `ResizeParentToFit` které umožní velikost zobrazení, určuje velikost okna rámce.

```cpp
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bShrinkOnly*<br/>
Druh změna velikosti provést. Výchozí hodnota TRUE zmenší okno rámce, pokud je to vhodné. Posuvníky se stále zobrazují pro velká zobrazení nebo okna s malými rámečky. Hodnota FALSE způsobí, že zobrazení vždy změnit velikost okna rámce přesně. To může být poněkud nebezpečné, protože okno rámce může být příliš velké, aby se vešlo do okna rámce rozhraní více dokumentů (MDI) nebo obrazovky.

### <a name="remarks"></a>Poznámky

To se doporučuje pouze pro zobrazení v podřízených oknech rámů MDI. Použití `ResizeParentToFit` ve `OnInitialUpdate` funkci obslužné rutiny odvozené `CScrollView` třídy. Příklad této členské funkce naleznete v tématu [CScrollView::SetScrollSizes](#setscrollsizes).

`ResizeParentToFit`předpokládá, že byla nastavena velikost okna zobrazení. Pokud velikost okna zobrazení nebyla `ResizeParentToFit` nastavena při volání, získáte kontrolní výraz. Chcete-li zajistit, aby k tomu nedošlo, proveďte před voláním `ResizeParentToFit`následující hovor :

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewscrolltoposition"></a><a name="scrolltoposition"></a>CScrollView::Scrolltopozice

Volání `ScrollToPosition` pro posun k danému bodu v zobrazení.

```cpp
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Bod, ke které se má posunout v logických jednotkách. Člen `x` musí mít kladnou hodnotu (větší nebo rovnou 0, až do celkové velikosti zobrazení). Totéž platí pro `y` člen při MM_TEXT režimmapování. Člen `y` je negativní v jiných režimech mapování než MM_TEXT.

### <a name="remarks"></a>Poznámky

Zobrazení bude posunuto tak, aby tento bod byl v levém horním rohu okna. Tato členská funkce nesmí být volána, pokud je měřítko zobrazení přizpůsobit.

## <a name="cscrollviewsetscaletofitsize"></a><a name="setscaletofitsize"></a>CScrollView::SetScaleToFitSize

Volání, `SetScaleToFitSize` pokud chcete automaticky změnit velikost výřezu na aktuální velikost okna.

```cpp
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Parametry

*sizeTotal*<br/>
Vodorovné a svislé velikosti, na které má být měřítko pohledu. Velikost zobrazení posouvání se měří v logických jednotkách. Vodorovná velikost je obsažena v členu. `cx` Svislá velikost `cy` je obsažena v členu. Oba `cx` `cy` a musí být větší nebo rovna 0.

### <a name="remarks"></a>Poznámky

U posuvníků může být kdykoli viditelná pouze část logického zobrazení. Ale s možností škálování přizpůsobit, zobrazení nemá žádné posuvníky a logické zobrazení je roztaženo nebo zmenšeno tak, aby přesně odpovídalo klientské oblasti okna. Při změně velikosti okna zobrazení nakreslí svá data v novém měřítku na základě velikosti okna.

Obvykle umístíte volání do `SetScaleToFitSize` přepsání `OnInitialUpdate` členské funkce zobrazení. Pokud nechcete automatické škálování, `SetScrollSizes` zavolejte místo toho členovou funkci.

`SetScaleToFitSize`lze použít k implementaci operace "Zoom to Fit". Slouží `SetScrollSizes` k opětovné inicializaci posouvání.

`SetScaleToFitSize`předpokládá, že byla nastavena velikost okna zobrazení. Pokud velikost okna zobrazení nebyla `SetScaleToFitSize` nastavena při volání, získáte kontrolní výraz. Chcete-li zajistit, aby k tomu nedošlo, proveďte před voláním `SetScaleToFitSize`následující hovor :

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewsetscrollsizes"></a><a name="setscrollsizes"></a>CScrollView::SetScrollSizes

Volání, `SetScrollSizes` když se má zobrazení aktualizovat.

```cpp
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Parametry

*nRežim Mapy*<br/>
Režim mapování, který chcete nastavit pro toto zobrazení. Možné hodnoty zahrnují:

|Režim mapování|Logická jednotka|Kladná osa y se prodlužuje...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 pixel|Dolů|
|MM_HIMETRIC|0,01 mm|Nahoru|
|MM_TWIPS|1/1440 v|Nahoru|
|MM_HIENGLISH|0,001 v|Nahoru|
|MM_LOMETRIC|0,1 mm|Nahoru|
|MM_LOENGLISH|0,01 palců|Nahoru|

Všechny tyto režimy jsou definovány systémem Windows. Dva standardní režimy mapování, MM_ISOTROPIC a `CScrollView`MM_ANISOTROPIC, se nepoužívají pro . Knihovna tříd `SetScaleToFitSize` poskytuje členovou funkci pro změnu velikosti zobrazení na velikost okna. Sloupec tři ve výše uvedené tabulce popisuje orientaci souřadnic.

*sizeTotal*<br/>
Celková velikost zobrazení posouvání. Člen `cx` obsahuje horizontální rozsah. Člen `cy` obsahuje svislý rozsah. Velikosti jsou v logických jednotkách. Oba `cx` `cy` a musí být větší nebo rovna 0.

*sizePage*<br/>
Vodorovná a svislá částka se posouvá v každém směru v reakci na kliknutí myší v hřídeli posuvníku. Člen `cx` obsahuje vodorovnou částku. Člen `cy` obsahuje svislou částku.

*velikostČára*<br/>
Vodorovná a svislá částka se posouvá v každém směru v reakci na kliknutí myší v posuvníku. Člen `cx` obsahuje vodorovnou částku. Člen `cy` obsahuje svislou částku.

### <a name="remarks"></a>Poznámky

Volání v přepsání `OnUpdate` členské funkce upravit charakteristiky posouvání, když například dokument je zpočátku zobrazen nebo když se změní velikost.

Obvykle získáte informace o velikosti z přidruženého dokumentu zobrazení voláním `GetMyDocSize`členské funkce dokumentu, případně volané , které zadáte s odvozenou třídou dokumentu. Následující kód ukazuje tento přístup:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Případně může být někdy nutné nastavit pevnou velikost, jako v následujícím kódu:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Režim mapování je nutné nastavit na libovolný režim mapování systému Windows s výjimkou MM_ISOTROPIC nebo MM_ANISOTROPIC. Pokud chcete použít režim mapování bez omezení, `SetScaleToFitSize` zavolejte namísto `SetScrollSizes`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Třída CView](../../mfc/reference/cview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CView](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd – třída](../../mfc/reference/csplitterwnd-class.md)
