---
title: CScrollView Class
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
ms.openlocfilehash: d60082092bd42fbe220eee08953ad5fda0ff0a85
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774150"
---
# <a name="cscrollview-class"></a>CScrollView Class

A [CView](../../mfc/reference/cview-class.md) s možností posouvání.

## <a name="syntax"></a>Syntaxe

```
class CScrollView : public CView
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name|Popis|
|----------|-----------------|
|[CScrollView::CScrollView](#cscrollview)|Vytvoří `CScrollView` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CScrollView::CheckScrollBars](#checkscrollbars)|Označuje, jestli se posuvníky zobrazení vodorovného a svislého posuvníku.|
|[CScrollView::FillOutsideRect](#filloutsiderect)|Vyplní oblast zobrazení mimo oblast posouvání.|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Získá aktuální pozici posunutí v jednotkách zařízení.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Získá aktuální režim mapování, celková velikost a velikost řádku a stránky posuvný zobrazení. Velikosti nejsou v jednotkách zařízení.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Získá aktuální pozici posunutí v logických jednotkách.|
|[CScrollView::GetTotalSize](#gettotalsize)|Získá celková velikost posouvání zobrazení v logických jednotkách.|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|Způsobí, že velikost zobrazení tak, aby určovat velikost jeho rámce.|
|[CScrollView::ScrollToPosition](#scrolltoposition)|Posune zobrazení k danému bodu, zadaný v logických jednotkách.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Posuvníky zobrazení přepne do režimu měřítka přizpůsobit.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Nastaví režim mapování posuvníky zobrazení, celková velikost a množství vodorovné a svislé posouvání.|

## <a name="remarks"></a>Poznámky

Dokáže zpracovat standardní sami posouvání v libovolné třídě odvozené z `CView` tak, že přepíšete mapované zpráva [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) členské funkce. Ale `CScrollView` přidá následující funkce, které její `CView` možnosti:

- Spravuje mapování režimů a velikosti oken a zobrazení.

- V reakci na posuvníku zprávy posouvá automaticky.

- V reakci na zprávy z klávesnice, myš neposouvaných nebo kolečkem posouvá automaticky.

V reakci na zprávy z klávesnice, posouvání automaticky, přidejte je zpráva WM_KEYDOWN a test pro VK_DOWN, VK_PREV a volání [SetScrollPos](/windows/desktop/api/winuser/nf-winuser-setscrollpos).

Dokáže zpracovat kolečko myši posouvání sami tak, že přepíšete mapované zpráva [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) a [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) členské funkce. Protože jde o pro `CScrollView`, tyto členské funkce podporují doporučené chování pro [WM_MOUSEWHEEL](/windows/desktop/inputdev/wm-mousewheel), zpráva otočení kolečka.

Abyste mohli využívat automatické posouvání, odvodit třídu vaše zobrazení z `CScrollView` namísto z `CView`. Když je zobrazení nejprve vytvořit, pokud chcete vypočítat velikost zobrazení posuvný na základě velikosti dokumentu, volání `SetScrollSizes` členskou funkci ze přepsání buď [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) nebo [ CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Musíte napsat vlastní kód pro dotazování velikost dokumentu. Příklad najdete v tématu [ukázky Scribble](../../overview/visual-cpp-samples.md).)

Volání `SetScrollSizes` členská funkce nastaví režim mapování zobrazení, celkový počet rozměrů posuvníky zobrazení a množství posouvat vodorovně a svisle. Všechny velikosti jsou v logických jednotkách. Logická velikost zobrazení se obvykle počítá z dat uložených v dokumentu, ale v některých případech můžete chtít určit pevnou velikost. Příklady oba přístupy poskytují, naleznete v tématu [CScrollView::SetScrollSizes](#setscrollsizes).

Zadáte částky posouvat vodorovně a svisle v logických jednotkách. Ve výchozím nastavení, když uživatel klikne posuvníku panelu šachty mimo posuvníku `CScrollView` posune "stránky". Pokud uživatel klikne na jednom konci posuvník, posouvací šipky `CScrollView` posune "řádek". Ve výchozím nastavení je stránka 1/10 celkové velikosti zobrazení. řádek je 1/10 velikosti stránky. Tyto výchozí hodnoty přepsání předáním vlastní velikosti v `SetScrollSizes` členskou funkci. Vodorovná velikost může například nastavit na část šířky celková velikost a velikost svislé výšku řádku v aktuálním písmem.

Místo posouvání, `CScrollView` může automaticky škálovat zobrazení tak, aby velikost aktuálního okna. V tomto režimu zobrazení nemá žádné posuvníky a logické zobrazení je vyčerpávat nebo zmenšit přesně podle klientské oblasti okna. Chcete-li použít tuto funkci škálování přizpůsobit, zavolejte [CScrollView::SetScaleToFitSize](#setscaletofitsize). (Volání buď `SetScaleToFitSize` nebo `SetScrollSizes`, ale ne obojí.)

Před `OnDraw` členské funkce třídy odvozené zobrazení je volána, `CScrollView` automaticky přizpůsobí zobrazení počátek `CPaintDC` objekt kontextu zařízení, který předá do `OnDraw`.

Chcete-li upravit zobrazení zdroje pro okno umožňující posouvání `CScrollView` přepíše [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Toto nastavení je automatické `CPaintDC` kontextu zařízení, která `CScrollView` předá `OnDraw`, ale musí volat `CScrollView::OnPrepareDC` sami pro jiné kontexty zařízení použijete, jako například `CClientDC`. Můžete přepsat `CScrollView::OnPrepareDC` nastavit pera, barvu pozadí a další atributy kreslení, ale volání základní třídy provést škálování.

Posuvníky se může zobrazit na třech místech vzhledem k zobrazení, jak je znázorněno v následujících případech:

- Posuvníky standardní styl okna můžete nastavit pro zobrazení pomocí WS_HSCROLL a WS_VSCROLL[styly Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles).

- Ovládací prvky posuvníku lze také přidat do rámce obsahující zobrazení, v takovém případě rozhraní předává WM_HSCROLL a WM_VSCROLL zprávy z okna rámce k aktuálně aktivnímu zobrazení.

- Rozhraní také předá posuňte zprávy z `CSplitterWnd` rozdělovač – ovládací prvek do aktuálně aktivní rozdělovač podokna (zobrazení). Při umístění v [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) s sdílené posuvníky, `CScrollView` objektu bude používat sdílený ty namísto vytváření vlastní.

Další informace o používání `CScrollView`, naleznete v tématu [architekturu Document/View](../../mfc/document-view-architecture.md) a [odvozené zobrazení tříd k dispozici v knihovně MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="checkscrollbars"></a>  CScrollView::CheckScrollBars

Voláním této členské funkce k určení, zda posuvníky zobrazení má vodorovné a svislé pruhy.

```
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Parametry

*bHasHorzBar*<br/>
Označuje, že aplikace má vodorovný posuvník.

*bHasVertBar*<br/>
Označuje, že aplikace má svislý posuvník.

##  <a name="cscrollview"></a>  CScrollView::CScrollView

Vytvoří `CScrollView` objektu.

```
CScrollView();
```

### <a name="remarks"></a>Poznámky

Je nutné volat buď `SetScrollSizes` nebo `SetScaleToFitSize` před posuvníku zobrazení je použitelný.

##  <a name="filloutsiderect"></a>  CScrollView::FillOutsideRect

Volání `FillOutsideRect` k vyplnění oblasti zobrazení, které se objeví mimo posuvné oblasti.

```
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Kontext zařízení, ve kterém má být provedeno naplnění.

*pBrush*<br/>
Štětec, se kterou má být vyplněny oblasti.

### <a name="remarks"></a>Poznámky

Použití `FillOutsideRect` v posuvníky zobrazení `OnEraseBkgnd` funkci obslužné rutiny, aby se zabránilo nadměrnému pozadí překreslení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

##  <a name="getdevicescrollposition"></a>  CScrollView::GetDeviceScrollPosition

Volání `GetDeviceScrollPosition` když potřebujete aktuální vodorovné a svislé polohy posuvníku polí ve posuvníky.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Vodorovné a svislé polohy (v jednotkách zařízení) posuvníku polí jako `CPoint` objektu.

### <a name="remarks"></a>Poznámky

Tento pár souřadnic odpovídá místo v dokumentu, do které se levém horním rohu zobrazení posunul. To je užitečné pro vyrovnání pozice myši zařízení na zařízení místo zobrazení s posuvníkem.

`GetDeviceScrollPosition` Vrátí hodnoty v jednotkách zařízení. Pokud chcete logické jednotky, použijte `GetScrollPosition` místo.

##  <a name="getdevicescrollsizes"></a>  CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes` Získá aktuální režim mapování, celková velikost a velikost řádku a stránky posuvný zobrazení.

```
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>Parametry

*nMapMode*<br/>
Vrátí aktuální režim mapování pro toto zobrazení. Seznam možných hodnot najdete v tématu `SetScrollSizes`.

*sizeTotal*<br/>
Vrátí aktuální celková velikost posouvání zobrazení v jednotkách zařízení.

*sizePage*<br/>
Vrátí aktuální částky vodorovného a svislého posouvání v každém směru v reakci na myš, klikněte na tlačítko v šachty posuvníku. `cx` Člena obsahuje vodorovný částku. `cy` Člena obsahuje vertikální částku.

*sizeLine*<br/>
Vrátí aktuální částky vodorovného a svislého posouvání v každém směru v reakci na myš, klikněte na tlačítko v posouvací šipky. `cx` Člena obsahuje vodorovný částku. `cy` Člena obsahuje vertikální částku.

### <a name="remarks"></a>Poznámky

Velikosti nejsou v jednotkách zařízení. Tato členská funkce je volána jen zřídka.

##  <a name="getscrollposition"></a>  CScrollView::GetScrollPosition

Volání `GetScrollPosition` když potřebujete aktuální vodorovné a svislé polohy posuvníku polí ve posuvníky.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Vodorovné a svislé polohy (v logických jednotkách) posuvníku polí jako `CPoint` objektu.

### <a name="remarks"></a>Poznámky

Tento pár souřadnic odpovídá místo v dokumentu, do které se levém horním rohu zobrazení posunul.

`GetScrollPosition` Vrátí hodnoty v logických jednotkách. Pokud chcete zařízení jednotky, použijte `GetDeviceScrollPosition` místo.

##  <a name="gettotalsize"></a>  CScrollView::GetTotalSize

Volání `GetTotalSize` načíst aktuální velikosti vodorovného a svislého posouvání zobrazení.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Celková velikost posouvání zobrazení v logických jednotkách. Vodorovná velikost je v `cx` člena `CSize` návratovou hodnotu. Výška probíhá `cy` člena.

##  <a name="resizeparenttofit"></a>  CScrollView::ResizeParentToFit

Volání `ResizeParentToFit` chcete, aby velikost zobrazení určovat velikost okna rámce.

```
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bShrinkOnly*<br/>
Druh provádět změny velikosti. Výchozí hodnota TRUE, zmenší okno rámce v případě potřeby. Pro zobrazení velké nebo malé okna s rámečkem bude stále zobrazovat posuvníky. Hodnota FALSE způsobí, že zobrazení vždy přesně velikost okna rámce. To může být trochu nebezpečné, protože okno rámce může získat nevejdou uvnitř okna rámce (MDI interface) více dokumentu nebo na obrazovce.

### <a name="remarks"></a>Poznámky

To se doporučuje jenom pro zobrazení v podřízených oken rámce MDI. Použití `ResizeParentToFit` v `OnInitialUpdate` funkci obslužné rutiny z vaší odvozené `CScrollView` třídy. Příklad tato členská funkce, najdete v části [CScrollView::SetScrollSizes](#setscrollsizes).

`ResizeParentToFit` předpokládá, že byla nastavena velikost okna zobrazení. Pokud velikost okna zobrazení nebyl nastaven při `ResizeParentToFit` se volá, zobrazí se kontrolní výraz. Aby bylo zajištěno, že to nestalo, použije následující volání před voláním `ResizeParentToFit`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="scrolltoposition"></a>  CScrollView::ScrollToPosition

Volání `ScrollToPosition` přejděte k danému bodu v zobrazení.

```
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Parametry

*pt*<br/>
Bod tak, aby přejděte v logických jednotkách. `x` Člena musí být kladné číslo (větší než nebo rovna 0 až do celkové velikosti zobrazení). Totéž platí pro `y` člen MM_TEXT po režim mapování. `y` Člen je v režimech mapování než MM_TEXT záporné.

### <a name="remarks"></a>Poznámky

Zobrazení se posouvat tak, aby tento bod v levém horním rohu okna. Tato členská funkce nesmí volat, pokud zobrazení se přizpůsobí.

##  <a name="setscaletofitsize"></a>  CScrollView::SetScaleToFitSize

Volání `SetScaleToFitSize` když chcete automaticky škálovat, velikosti zobrazovacího okna aktuální velikosti okna.

```
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Parametry

*sizeTotal*<br/>
Vodorovné a svislé velikosti, ke kterým je možné škálovat zobrazení. Velikost posouvání zobrazení se měří v logických jednotkách. Vodorovná velikost je součástí `cx` člena. Velikost svislé je součástí `cy` člena. Obě `cx` a `cy` musí být větší než nebo rovna 0.

### <a name="remarks"></a>Poznámky

S posuvníky mohou být pouze část logické zobrazení viditelná v každém okamžiku. Ale s možností škálování přizpůsobit zobrazení nemá žádné posuvníky a logické zobrazení je vyčerpávat nebo zmenšit přesně podle klientské oblasti okna. Při změně velikosti okna zobrazení kreslení svá data na nový škálování na základě velikosti okna.

Obvykle budete umístit volání `SetScaleToFitSize` v přepsání metody zobrazení `OnInitialUpdate` členskou funkci. Pokud nechcete, aby automatické škálování, zavolejte `SetScrollSizes` členské funkce místo.

`SetScaleToFitSize` slouží k implementaci operace "Přiblížení na vyhovující". Použití `SetScrollSizes` opětovnou inicializaci posouvání.

`SetScaleToFitSize` předpokládá, že byla nastavena velikost okna zobrazení. Pokud velikost okna zobrazení nebyl nastaven při `SetScaleToFitSize` se volá, zobrazí se kontrolní výraz. Aby bylo zajištěno, že to nestalo, použije následující volání před voláním `SetScaleToFitSize`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="setscrollsizes"></a>  CScrollView::SetScrollSizes

Volání `SetScrollSizes` při zobrazení se chystáte aktualizovat.

```
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Parametry

*nMapMode*<br/>
Režim mapování nastavení pro toto zobrazení. Možné hodnoty:

|Režim mapování|Logické jednotky|Osa y pozitivní rozšiřuje...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 pixelu|Dolů|
|MM_HIMETRIC|0,01 mm|Nahoru|
|MM_TWIPS|1/1 440 v|Nahoru|
|MM_HIENGLISH|0,001 Indie|Nahoru|
|MM_LOMETRIC|0,1 mm|Nahoru|
|MM_LOENGLISH|0,01 Indie|Nahoru|

Všechny tyto režimy jsou definovány ve Windows. Dva režimy standardní mapování MM_ISOTROPIC a MM_ANISOTROPIC, nejsou použity pro `CScrollView`. Poskytuje knihovna tříd `SetScaleToFitSize` členskou funkci pro změnu velikosti zobrazení tak, aby velikost okna. Tři sloupce v tabulce výše popisuje souřadnic orientace.

*sizeTotal*<br/>
Celková velikost zobrazení s posuvníkem. `cx` Člena obsahuje vodorovný rozsahu. `cy` Člena obsahuje vertikální rozsahu. Velikosti nejsou v logických jednotkách. Obě `cx` a `cy` musí být větší než nebo rovna 0.

*sizePage*<br/>
Částky vodorovné a svislé posouvání v každém směru v reakci na myš, klikněte na tlačítko v šachty posuvníku. `cx` Člena obsahuje vodorovný částku. `cy` Člena obsahuje vertikální částku.

*sizeLine*<br/>
Částky vodorovné a svislé posouvání v každém směru v reakci na myš, klikněte na tlačítko v posouvací šipky. `cx` Člena obsahuje vodorovný částku. `cy` Člena obsahuje vertikální částku.

### <a name="remarks"></a>Poznámky

Volání v přepsání metody `OnUpdate` členská funkce, chcete-li upravit vlastnosti umožňující posouvání při, například je primárně zobrazen dokumentu nebo při změně velikosti.

Obvykle se získat informace o velikosti ze zobrazení přidružený dokument voláním členské funkce dokumentu, třeba volat `GetMyDocSize`, který zadáte s vaší třídy odvozené dokumentu. Tento přístup je znázorněný na následujícím kódem:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Alternativně můžete někdy potřebovat k nastavení pevné velikosti, stejně jako v následujícím kódu:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Režim mapování musí nastavit na některou z mapování režimy Windows s výjimkou MM_ISOTROPIC nebo MM_ANISOTROPIC. Pokud chcete použít režim neomezeným mapování, zavolejte `SetScaleToFitSize` členskou funkci místo `SetScrollSizes`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd – třída](../../mfc/reference/csplitterwnd-class.md)
