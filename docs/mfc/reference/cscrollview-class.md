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
ms.openlocfilehash: b89daaae4bb578d328e1468cc29470825e19c670
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502595"
---
# <a name="cscrollview-class"></a>CScrollView – třída

[CView](../../mfc/reference/cview-class.md) s možnostmi posouvání.

## <a name="syntax"></a>Syntaxe

```
class CScrollView : public CView
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name|Popis|
|----------|-----------------|
|[CScrollView::CScrollView](#cscrollview)|`CScrollView` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CScrollView::CheckScrollBars](#checkscrollbars)|Označuje, zda má zobrazení posuvníku vodorovné a svislé posuvníky.|
|[CScrollView::FillOutsideRect](#filloutsiderect)|Vyplní oblast zobrazení mimo oblast posouvání.|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Získá aktuální pozici posunutí v jednotkách zařízení.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Získá aktuální režim mapování, celkovou velikost a velikost řádku a stránky zobrazení s posuvníkem. Velikosti jsou v jednotkách zařízení.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Získá aktuální pozici posunutí v logických jednotkách.|
|[CScrollView:: GetTotalSize](#gettotalsize)|Získá celkovou velikost zobrazení posuvníku v logických jednotkách.|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|Způsobí, že velikost zobrazení nadiktují velikost svého rámečku.|
|[CScrollView::ScrollToPosition](#scrolltoposition)|Posune zobrazení na daný bod zadaný v logických jednotkách.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Přesune zobrazení posuvníku do režimu škálování na celou škálu.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Nastaví režim mapování zobrazení posuvníku, celkovou velikost a vodorovné a svislé posunutí.|

## <a name="remarks"></a>Poznámky

Můžete zpracovat standardní posun sami sebe v jakékoli třídě odvozené od `CView` přepsáním členských funkcí [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) a [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) mapované zprávy. Ale `CScrollView` na jeho `CView` funkce přidá tyto funkce:

- Spravuje velikosti oken a zobrazení a režimy mapování.

- Automaticky se posouvá v reakci na popruhové zprávy.

- Automaticky se posouvá v reakci na zprávy z klávesnice, nerolovací myš nebo kolečko myši.

Chcete-li se automaticky posouvat v reakci na zprávy z klávesnice, přidejte zprávu WM_KEYDOWN a otestujte VK_DOWN, VK_PREV a zavolejte [SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos).

Můžete zpracovat pohyb kolečka myši sami tím, že potlačuje členské funkce [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) a [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) mapované na zprávy. Vzhledem k `CScrollView`tomu, že tyto členské funkce podporují Doporučené chování pro [WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel), zprávu o rotaci kolečka.

Chcete-li využít výhod automatického posouvání, odvodit třídu zobrazení `CScrollView` z nástroje místo `CView`z. Při prvním vytvoření zobrazení, pokud chcete vypočítat velikost rolovacího zobrazení na základě velikosti dokumentu, zavolejte `SetScrollSizes` členskou funkci z vašeho přepsání buďto [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) nebo [CView:: inupdate](../../mfc/reference/cview-class.md#onupdate). (Pro dotaz na velikost dokumentu musíte napsat vlastní kód. Příklad najdete v [ukázce Klikyháky](../../overview/visual-cpp-samples.md).)

Volání `SetScrollSizes` členské funkce nastaví režim mapování zobrazení, celkové rozměry posunutého zobrazení a množství, které mají být posunuty vodorovně a svisle. Všechny velikosti jsou logické jednotky. Logická velikost zobrazení je obvykle počítána z dat uložených v dokumentu, ale v některých případech může být vhodné zadat pevnou velikost. Příklady obou přístupů naleznete v tématu [CScrollView:: SetScrollSizes](#setscrollsizes).

Určíte hodnoty pro posunutí vodorovně a svisle v logických jednotkách. Ve výchozím nastavení, pokud uživatel klikne na ovládací panel posuvníku mimo posuvné okno `CScrollView` , posuňte "stránku". Pokud uživatel klikne na šipku posuvníku na konci posuvníku, `CScrollView` posune se řádek. Ve výchozím nastavení je stránka 1/10 celkové velikosti zobrazení. čára je 1/10 velikosti stránky. Přepište tyto výchozí hodnoty předáním vlastních velikostí do `SetScrollSizes` členské funkce. Například můžete nastavit vodorovnou velikost na určitou část šířky celkové velikosti a výšku čáry v aktuálním písmu na výšku.

Místo posouvání `CScrollView` můžete zobrazení automaticky škálovat na velikost aktuálního okna. V tomto režimu zobrazení nemá žádné posuvníky a logické zobrazení je roztaženo nebo zmenšeno, aby se přesně vešlo na klientskou oblast okna. Chcete-li použít tuto možnost škálování na stránku, zavolejte [CScrollView:: SetScaleToFitSize](#setscaletofitsize). (Zavolejte buď `SetScaleToFitSize` nebo `SetScrollSizes`, ale ne obojí.)

Před voláním `CPaintDC` `OnDraw`členskéfunkcetřídy odvozeného zobrazení automatickyupravípočátekzobrazeníproobjektkontextuzařízení,kterýpředává.`CScrollView` `OnDraw`

Chcete-li upravit počátek zobrazení pro posuvné okno `CScrollView` , potlačí hodnoty [CView:: OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Tato úprava je automaticky nastavena pro `CPaintDC` kontext zařízení, `CScrollView` který předává `OnDraw`, ale je nutné `CScrollView::OnPrepareDC` zavolat pro všechny `CClientDC`ostatní kontexty zařízení, které používáte, například. Můžete přepsat `CScrollView::OnPrepareDC` , chcete-li nastavit pero, barvu pozadí a další atributy kreslení, ale zavolejte základní třídu pro provedení škálování.

Posuvníky se mohou zobrazit na třech místech vzhledem k zobrazení, jak je znázorněno v následujících případech:

- Standardní okna – posuvníky stylu lze nastavit pro zobrazení pomocí[stylů Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles)WS_HSCROLL a WS_VSCROLL.

- Ovládací prvky posuvníku lze také přidat do rámce obsahujícího zobrazení. v takovém případě rozhraní přepošle zprávy WM_HSCROLL a WM_VSCROLL z okna rámce do aktuálně aktivního zobrazení.

- Rozhraní také přepošle zprávy s `CSplitterWnd` posuvníky od ovládacího prvku Rozdělovač do aktuálně aktivního podokna rozdělení (zobrazení). Když umístíte do [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) se sdílenými posuvníky, `CScrollView` objekt bude používat sdílené místo pro vytváření vlastních panelů.

Další informace o použití `CScrollView`naleznete v tématu [Architektura Document/View](../../mfc/document-view-architecture.md) a [odvozené třídy zobrazení dostupné v knihovně MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="checkscrollbars"></a>CScrollView::CheckScrollBars

Voláním této členské funkce určíte, zda má rolovací zobrazení vodorovné a svislé pruhy.

```
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Parametry

*bHasHorzBar*<br/>
Určuje, že aplikace má vodorovný posuvník.

*bHasVertBar*<br/>
Určuje, že aplikace má svislý posuvník.

##  <a name="cscrollview"></a>CScrollView::CScrollView

`CScrollView` Vytvoří objekt.

```
CScrollView();
```

### <a name="remarks"></a>Poznámky

Je nutné volat buď `SetScrollSizes` nebo `SetScaleToFitSize` před tím, než je rolovací zobrazení použitelné.

##  <a name="filloutsiderect"></a>CScrollView::FillOutsideRect

Zavolejte `FillOutsideRect` k vyplnění oblasti zobrazení, které se zobrazí mimo oblast posouvání.

```
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Kontext zařízení, ve kterém má být vyplňování provedeno.

*pBrush*<br/>
Štětec, se kterým má být oblast vyplněna.

### <a name="remarks"></a>Poznámky

Použijte `FillOutsideRect` ve funkci `OnEraseBkgnd` obslužné rutiny posuvníku, abyste zabránili nadměrnému překreslení na pozadí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

##  <a name="getdevicescrollposition"></a>CScrollView::GetDeviceScrollPosition

Volá `GetDeviceScrollPosition` se, když budete potřebovat aktuální vodorovnou a svislou polohu rolovacích polí v posuvníkech.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Vodorovná a svislá pozice (v jednotkách zařízení) rolovacích polí jako `CPoint` objekt.

### <a name="remarks"></a>Poznámky

Tento dvojici souřadnic odpovídá umístění v dokumentu, na které bylo posunuto levý horní roh zobrazení. To je užitečné, když kompenzujete pozice zařízení myši, abyste se mohli posouvat a zobrazovat pozice zařízení.

`GetDeviceScrollPosition`Vrátí hodnoty v jednotkách zařízení. Pokud chcete použít logické jednotky, použijte `GetScrollPosition` místo toho.

##  <a name="getdevicescrollsizes"></a>CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes`Získá aktuální režim mapování, celkovou velikost a velikost řádku a stránky zobrazení s posuvníkem.

```
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>Parametry

*nMapMode*<br/>
Vrátí aktuální režim mapování pro toto zobrazení. Seznam možných hodnot naleznete v tématu `SetScrollSizes`.

*sizeTotal*<br/>
Vrátí aktuální celkovou velikost posunutého zobrazení v jednotkách zařízení.

*sizePage*<br/>
Vrátí aktuální vodorovnou a svislou částku pro posouvání v každém směru v reakci na kliknutí myší v hřídeli posuvníku. `cx` Člen obsahuje vodorovnou částku. `cy` Člen obsahuje svislou částku.

*sizeLine*<br/>
Vrátí aktuální vodorovnou a svislou hodnotu pro posouvání v každém směru v reakci na kliknutí myší na šipku posuvníku. `cx` Člen obsahuje vodorovnou částku. `cy` Člen obsahuje svislou částku.

### <a name="remarks"></a>Poznámky

Velikosti jsou v jednotkách zařízení. Tato členská funkce je volána zřídka.

##  <a name="getscrollposition"></a>CScrollView::GetScrollPosition

Volá `GetScrollPosition` se, když budete potřebovat aktuální vodorovnou a svislou polohu rolovacích polí v posuvníkech.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Vodorovná a svislá pozice (v logických jednotkách) rolovacích polí jako `CPoint` objekt.

### <a name="remarks"></a>Poznámky

Tento dvojici souřadnic odpovídá umístění v dokumentu, na které bylo posunuto levý horní roh zobrazení.

`GetScrollPosition`Vrátí hodnoty v logických jednotkách. Pokud chcete použít jednotky zařízení, použijte `GetDeviceScrollPosition` místo toho.

##  <a name="gettotalsize"></a>CScrollView:: GetTotalSize

Zavolejte `GetTotalSize` k načtení aktuální vodorovné a svislé velikosti zobrazení s posuvníkem.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Celková velikost zobrazení posuvníku v logických jednotkách. Vodorovná velikost je v `cx` členu `CSize` návratové hodnoty. Svislá velikost je v `cy` členu.

##  <a name="resizeparenttofit"></a>CScrollView::ResizeParentToFit

Zavolejte `ResizeParentToFit` , pokud chcete, aby velikost zobrazení nadiktuja velikost okna rámce.

```
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bShrinkOnly*<br/>
Druh změny velikosti, která má být provedena. Výchozí hodnota TRUE, zmenšuje okno rámce, pokud je to vhodné. Posuvníky se budou pořád zobrazovat u velkých zobrazení nebo malých oken s rámečkem. Hodnota FALSE způsobí, že zobrazení vždy změní velikost okna rámce přesně. To může být poněkud nebezpečné, protože okno rámce může být příliš velké, aby se vešlo do okna rámce MDI (Multiple Document Interface) nebo na obrazovku.

### <a name="remarks"></a>Poznámky

Tato položka se doporučuje jenom pro zobrazení v podřízených oknech snímků MDI. Použijte `ResizeParentToFit` `CScrollView` ve funkci obslužné rutiny vaší odvozené třídy. `OnInitialUpdate` Příklad této členské funkce naleznete v tématu [CScrollView:: SetScrollSizes](#setscrollsizes).

`ResizeParentToFit`předpokládá, že byla nastavena velikost okna zobrazení. Pokud velikost okna zobrazení není nastavena při `ResizeParentToFit` volání, zobrazí se kontrolní výraz. Chcete-li zajistit, aby k tomu nedocházelo, proveďte následující volání `ResizeParentToFit`před voláním:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="scrolltoposition"></a>CScrollView::ScrollToPosition

Voláním `ScrollToPosition` posuňte se k danému bodu v zobrazení.

```
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Parametry

*bodů*<br/>
Bod, na který se má přejít, v logických jednotkách. `x` Člen musí být kladná hodnota (větší než nebo rovna 0, až do celkové velikosti zobrazení). Totéž platí pro `y` člena, pokud je režim mapování MM_TEXT. `y` Člen je záporný v jiných režimech mapování než MM_TEXT.

### <a name="remarks"></a>Poznámky

Zobrazení se posune tak, aby byl v levém horním rohu okna. Tato členská funkce nesmí být volána, je-li zobrazení upraveno podle měřítka.

##  <a name="setscaletofitsize"></a>CScrollView::SetScaleToFitSize

Volá `SetScaleToFitSize` se, když chcete automaticky škálovat velikost zobrazení na aktuální velikost okna.

```
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Parametry

*sizeTotal*<br/>
Vodorovné a svislé velikosti, na které se má zobrazení škálovat Velikost zobrazení posuvníku se měří v logických jednotkách. Vodorovná velikost je obsažena v `cx` členu. Svislá velikost je obsažena v `cy` členu. `cx` A`cy` musí být větší než nebo rovna 0.

### <a name="remarks"></a>Poznámky

Pomocí posuvníků může být kdykoli vidět pouze část logického zobrazení. Ale s možností škálování na místo, zobrazení nemá žádné posuvníky a logické zobrazení se roztáhne nebo zmenší tak, aby se přesně vešlo na klientskou oblast okna. Když se změní velikost okna, zobrazení nakreslí jeho data v novém měřítku na základě velikosti okna.

Obvykle zadáte volání do `SetScaleToFitSize` svého přepsání `OnInitialUpdate` členské funkce zobrazení. Pokud nechcete automatické škálování, zavolejte `SetScrollSizes` místo toho členskou funkci.

`SetScaleToFitSize`dá se použít k implementaci operace přiblížení k přizpůsobení. Použijte `SetScrollSizes` k opětovné inicializaci posouvání.

`SetScaleToFitSize`předpokládá, že byla nastavena velikost okna zobrazení. Pokud velikost okna zobrazení není nastavena při `SetScaleToFitSize` volání, zobrazí se kontrolní výraz. Chcete-li zajistit, aby k tomu nedocházelo, proveďte následující volání `SetScaleToFitSize`před voláním:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="setscrollsizes"></a>CScrollView::SetScrollSizes

Volá `SetScrollSizes` se, když se bude aktualizovat zobrazení.

```
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Parametry

*nMapMode*<br/>
Režim mapování, který má být nastaven pro toto zobrazení. Možné hodnoty:

|Režim mapování|Logická jednotka|Kladná osa y rozšiřuje...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 pixel|Úhlopříčn|
|MM_HIMETRIC|0,01 mm|Šikm|
|MM_TWIPS|1/1440 v|Šikm|
|MM_HIENGLISH|0,001 v|Šikm|
|MM_LOMETRIC|0,1 mm|Šikm|
|MM_LOENGLISH|0,01 v|Šikm|

Všechny tyto režimy jsou definovány systémem Windows. Dva standardní režimy mapování, MM_ISOTROPIC a MM_ANISOTROPIC, se nepoužívají pro `CScrollView`. Knihovna tříd poskytuje `SetScaleToFitSize` členskou funkci pro škálování zobrazení na velikost okna. Sloupec 3 v tabulce výše popisuje orientaci souřadnic.

*sizeTotal*<br/>
Celková velikost zobrazení posouvání `cx` Člen obsahuje vodorovný rozsah. `cy` Člen obsahuje vertikální rozsah. Velikosti jsou v logických jednotkách. `cx` A`cy` musí být větší než nebo rovna 0.

*sizePage*<br/>
Vodorovná a svislá vzdálenost pro posouvání v každém směru v reakci na kliknutí myší v hřídeli posuvníku. `cx` Člen obsahuje vodorovnou částku. `cy` Člen obsahuje svislou částku.

*sizeLine*<br/>
Vodorovná a svislá vzdálenost pro posouvání v každém směru v reakci na kliknutí myší na šipku posuvníku. `cx` Člen obsahuje vodorovnou částku. `cy` Člen obsahuje svislou částku.

### <a name="remarks"></a>Poznámky

Zavolejte ji v přepsání `OnUpdate` členské funkce pro úpravu vlastností posouvání, když je například dokument zpočátku zobrazen nebo když se změní velikost.

Obvykle budete získávat informace o velikosti z přidruženého dokumentu zobrazení voláním členské funkce dokumentu, která je pravděpodobně volána `GetMyDocSize`, kterou zadáte do odvozené třídy dokumentu. Následující kód ukazuje tento přístup:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Případně může být někdy nutné nastavit pevnou velikost, jak je uvedeno v následujícím kódu:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Režim mapování je nutné nastavit na libovolný režim mapování systému Windows s výjimkou MM_ISOTROPIC nebo MM_ANISOTROPIC. Pokud chcete použít neomezený režim mapování, zavolejte `SetScaleToFitSize` členskou funkci `SetScrollSizes`namísto.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Viz také:

[DIBLOOK Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CView – třída](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd – třída](../../mfc/reference/csplitterwnd-class.md)
