---
title: 'MFC – ovládací prvky ActiveX: Vykreslování ovládacího prvku ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: fd98af90e86b6b98a856e633e50c5bf266cc466a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364587"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>MFC – ovládací prvky ActiveX: Vykreslování ovládacího prvku ActiveX

Tento článek popisuje proces malování ovládacího prvku ActiveX a jak můžete změnit kód malování pro optimalizaci procesu. (Viz [Optimalizace kreslicího výkresu](../mfc/optimizing-control-drawing.md) pro techniky optimalizace kreslení tím, že ovládací prvky nemají jednotlivě obnovit dříve vybrané objekty GDI. Po vylosované všechny ovládací prvky kontejneru můžete automaticky obnovit původní objekty.)

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

Příklady v tomto článku jsou z ovládacího prvku vytvořeného Průvodcem ovládacího prvku ActiveX knihovny MFC s výchozím nastavením. Další informace o vytvoření aplikace pro řízení kostry pomocí Průvodce řízením activex knihovny MFC naleznete v článku [Průvodce řízením ActiveX knihovny MFC](../mfc/reference/mfc-activex-control-wizard.md).

Jsou popsána následující témata:

- [Celkový proces malování ovládacího prvku a kód vytvořený Průvodcem ovládacím prvkem ActiveX pro podporu malování](#_core_the_painting_process_of_an_activex_control)

- [Jak optimalizovat proces malování](#_core_optimizing_your_paint_code)

- [Jak malovat ovládací prvek pomocí metasouborů](#_core_painting_your_control_using_metafiles)

## <a name="the-painting-process-of-an-activex-control"></a><a name="_core_the_painting_process_of_an_activex_control"></a>Proces malování ovládacího prvku ActiveX

Pokud jsou ovládací prvky ActiveX zpočátku zobrazeny nebo překresleny, postupujte podle procesu malování podobnému jiným aplikacím vyvinutým pomocí knihovny MFC s jedním důležitým rozdílem: Ovládací prvky ActiveX mohou být v aktivním nebo neaktivním stavu.

Aktivní ovládací prvek je reprezentován v kontejneru ovládacího prvku ActiveX podřízeným oknem. Stejně jako ostatní okna, je zodpovědný za malování sám, když je přijata WM_PAINT zpráva. Základní třída ovládacího prvku [COleControl](../mfc/reference/colecontrol-class.md)zpracovává tuto `OnPaint` zprávu ve své funkci. Tato výchozí implementace `OnDraw` volá funkci ovládacího prvku.

Neaktivní ovládací prvek je namalován odlišně. Pokud je ovládací prvek neaktivní, jeho okno je buď neviditelné nebo neexistující, takže nemůže přijímat zprávu o malování. Místo toho kontejner ovládacího `OnDraw` prvku přímo volá funkci ovládacího prvku. To se liší od procesu malování aktivní `OnPaint` ho ovládacího prvku v tom, že členské funkce je nikdy volána.

Jak je popsáno v předchozích odstavcích, jak je aktualizován ovládací prvek ActiveX závisí na stavu ovládacího prvku. Však protože rozhraní `OnDraw` volá členské funkce v obou případech, přidáte většinu kódu malování v této členské funkce.

Členská `OnDraw` funkce zpracovává řídicí malování. Pokud je ovládací prvek neaktivní, `OnDraw`řídicí kontejner volá , předávání kontextu zařízení kontejneru ovládacího prvku a souřadnice obdélníkové oblasti obsazené ovládacím prvkem.

Obdélník předaný rámci `OnDraw` členské funkce obsahuje oblast obsazené ovládacíprvek. Pokud je ovládací prvek aktivní, levý horní roh je (0, 0) a předané kontext zařízení je pro podřízené okno, které obsahuje ovládací prvek. Pokud je ovládací prvek neaktivní, souřadnice vlevo nahoře není nutně (0, 0) a předané kontextu zařízení je pro řídicí kontejner obsahující ovládací prvek.

> [!NOTE]
> Je důležité, aby `OnDraw` změny nezávisí na obdélníku levý horní bod se rovná (0, 0) a že `OnDraw`nakreslíte pouze uvnitř obdélníku předán . Neočekávané výsledky může dojít, pokud nakreslíte mimo oblast obdélníku.

Výchozí implementace poskytovaná Průvodcem ovládacího prvku ActiveX knihovny MFC v souboru implementace ovládacího prvku (. CPP), je uvedeno níže, maluje obdélník s bílou štětcem a vyplní elipsu s aktuální barvou pozadí.

[!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
> Při malování ovládacího prvku, neměli byste dělat předpoklady o stavu kontextu zařízení, `OnDraw` který je předán jako parametr *pdc* do funkce. V některých proto je kontext zařízení dodáván aplikací kontejneru a nemusí být nutně inicializován do výchozího stavu. Zejména explicitně vyberte pera, stopy, barvy, písma a další prostředky, na kterých závisí kód výkresu.

## <a name="optimizing-your-paint-code"></a><a name="_core_optimizing_your_paint_code"></a>Optimalizace kódu malování

Poté, co je ovládací prvek úspěšně malování sám, dalším krokem je optimalizace `OnDraw` funkce.

Výchozí implementace malování ovládacího prvku ActiveX vykresluje celou řídicí oblast. To je dostačující pro jednoduché ovládací prvky, ale v mnoha případech překreslování ovládacího prvku by bylo rychlejší, pokud pouze část, která potřebovala aktualizaci byla překreslena, namísto celého ovládacího prvku.

Funkce `OnDraw` poskytuje snadný způsob optimalizace předáním *rcInvalid*, obdélníkové oblasti ovládacího prvku, který potřebuje překreslení. Chcete-li proces malování urychlit, použijte tuto oblast, obvykle menší než celá kontrolní oblast.

## <a name="painting-your-control-using-metafiles"></a><a name="_core_painting_your_control_using_metafiles"></a>Malování ovládacího prvku pomocí metasouborů

Ve většině případů parametr *pdc* do `OnDraw` funkce odkazuje na kontext zařízení obrazovky (DC). Však při tisku obrázků ovládacího prvku nebo během relace náhledu tisku dc přijaté pro vykreslování je speciální typ nazývaný "metasoubor DC". Na rozdíl od řadiče domény obrazovky, který okamžitě zpracovává požadavky odeslané na něj, metafile DC ukládá požadavky, které mají být přehrávány později. Některé aplikace kontejneru může také zvolit vykreslení image ovládacího prvku pomocí metasouboru DC v režimu návrhu.

Požadavky na kreslení metasouborů mohou být prováděny kontejnerem prostřednictvím dvou funkcí rozhraní: `IViewObject::Draw` (tato `IDataObject::GetData`funkce může být také volána pro kreslení bez metasouborů) a . Pokud je řadič domény metasouboru předán jako jeden z parametrů, rozhraní MFC provede volání [cOleControl::OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile). Protože se jedná o virtuální členská funkce, přepsat tuto funkci v control class provést jakékoli speciální zpracování. Výchozí chování `COleControl::OnDraw`volá .

Chcete-li se ujistit, že ovládací prvek lze nakreslit v kontextu obrazovky i metasouboru zařízení, musíte použít pouze členské funkce, které jsou podporovány v obrazovce i v metasouboru DC. Uvědomte si, že souřadný systém nemusí být měřen v pixelech.

Vzhledem k `OnDrawMetafile` tomu, že `OnDraw` výchozí implementace volá funkci ovládacího prvku, používejte pouze členské funkce, které `OnDrawMetafile`jsou vhodné pro metasoubor i kontext zařízení obrazovky, pokud nepřepíšete . V následujícím seznamu je `CDC` uvedena podmnožina členských funkcí, které lze použít v metasouboru i v kontextu zařízení obrazovky. Další informace o těchto funkcích naleznete v tématu třídy [CDC](../mfc/reference/cdc-class.md) v *referenční knihovně knihovny mfc*.

|Arc|BibBlt|Chord|
|---------|------------|-----------|
|`Ellipse`|`Escape`|`ExcludeClipRect`|
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|
|`LineTo`|`MoveTo`|`OffsetClipRgn`|
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|
|`Pie`|`Polygon`|`Polyline`|
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|
|`SelectPalette`|`SetBkColor`|`SetBkMode`|
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|
|`StretchBlt`|`TextOut`||

Kromě `CDC` členských funkcí existuje několik dalších funkcí, které jsou kompatibilní v metasouboru DC. Patří mezi ně [CPalette::AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)a tři členské `CBrush`funkce : [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush)a [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).

Funkce, které nejsou zaznamenány v metasouboru, jsou: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc)a [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Vzhledem k tomu, že řadič domény metasouboru není ve skutečnosti přidružen k zařízení, nelze použít SetDIBits, GetDIBits a CreateDIBitmap s řadičem domény metasouboru. Můžete použít SetDIBitsToDevice a StretchDIBits s metafile mj. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap)a [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) nejsou smysluplné s řadičem domény metasouboru.

Dalším bodem, který je třeba vzít v úvahu při použití metasouboru DC, je, že souřadný systém nemusí být měřen v pixelech. Z tohoto důvodu by měl být veškerý kód výkresu `OnDraw` upraven tak, aby se vešel do obdélníku předaného v parametru *rcBounds.* Tím se zabrání náhodné malování mimo ovládací prvek, protože *rcBounds* představuje velikost okna ovládacího prvku.

Po implementaci vykreslování metasouborů pro ovládací prvek použijte testovací kontejner k testování metasouboru. Informace o tom, jak získat přístup k testovacímu kontejneru, najdete v tématu [Testování vlastností a událostí s testovacím kontejnerem.](../mfc/testing-properties-and-events-with-test-container.md)

#### <a name="to-test-the-controls-metafile-using-test-container"></a>Testování metasouboru ovládacího prvku pomocí testovacího kontejneru

1. V nabídce **Úpravy** testovacího kontejneru klepněte na **tlačítko Vložit nový ovládací prvek**.

1. V poli **Vložit nový ovládací prvek** vyberte ovládací prvek a klepněte na tlačítko **OK**.

   Ovládací prvek se zobrazí v kontejneru Test.

1. V nabídce **Control** klepněte na tlačítko **Kreslit metasoubor**.

   Zobrazí se samostatné okno, ve kterém je metasoubor zobrazen. Můžete změnit velikost tohoto okna a zjistit, jak změna měřítka ovlivní metasoubor ovládacího prvku. Toto okno můžete kdykoli zavřít.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
