---
title: 'MFC – ovládací prvky ActiveX: Vykreslování ovládacího prvku ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: b90aa331c289caf827785af2eeba037e70f686ab
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281927"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>MFC – ovládací prvky ActiveX: Vykreslování ovládacího prvku ActiveX

Tento článek popisuje proces vykreslování ovládacího prvku ActiveX a jak je možné změnit kód barvy k optimalizaci procesu. (Viz [optimalizace vykreslování ovládacího prvku](../mfc/optimizing-control-drawing.md) pro techniky o tom, jak optimalizovat tím, že jednotlivě ovládacích prvků výkresu Obnovte dříve vybrané objekty GDI. Po vykreslení všechny ovládací prvky kontejneru můžete automaticky obnovit původní objekty.)

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

Příklady v tomto článku jsou z ovládacího prvku vytvořený pomocí průvodce ovládací prvek ActiveX knihovny MFC s výchozím nastavením. Další informace o vytvoření aplikace kostru ovládacího prvku pomocí Průvodce ovládacím prvkem ActiveX knihovny MFC naleznete v článku [Průvodce ovládacím prvkem MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md).

Jsou pokryta následující témata:

- [Celkový proces vykreslování ovládacího prvku a kód vytvořený pomocí průvodce ovládací prvek ActiveX pro podporu Malování](#_core_the_painting_process_of_an_activex_control)

- [K optimalizaci procesu Malování](#_core_optimizing_your_paint_code)

- [Jak se má Vymalovat ovládacího prvku pomocí metasoubory](#_core_painting_your_control_using_metafiles)

##  <a name="_core_the_painting_process_of_an_activex_control"></a> Proces vykreslování ovládacího prvku ActiveX

Ovládací prvky ActiveX jsou primárně zobrazen nebo se měl překreslit, následují podobně jako ostatní aplikace vyvinuté pomocí knihovny MFC, jeden zásadním Malování proces: Ovládací prvky ActiveX, může být aktivní nebo neaktivní stav.

Aktivní ovládací prvek je vyjádřena v kontejneru ovládacího prvku ActiveX podle podřízené okno. Stejně jako ostatní okna je zodpovědný za samotný Malování při doručení zprávy do WM_PAINT. Základní třída ovládacího prvku, [COleControl](../mfc/reference/colecontrol-class.md), zpracovává tuto zprávu v jeho `OnPaint` funkce. Tato výchozí implementace volá `OnDraw` funkce ovládacího prvku.

Ovládací prvek neaktivní vymalováním odlišně. Když ovládací prvek je neaktivní, jeho okno je neviditelný nebo neexistující, proto ji nelze přijmout zprávu malby. Místo toho přímo volá kontejnerem ovládacího prvku `OnDraw` funkce ovládacího prvku. Tím se liší od procesu Malování aktivní řízení, která `OnPaint` nikdy volána členská funkce.

Jak je popsáno v předchozích odstavcích, jak aktualizovat ovládacího prvku ActiveX závisí na stavu ovládacího prvku. Ale vzhledem k tomu rozhraní volá `OnDraw` členské funkce v obou případech přidávat většinu kódu vykreslování v tato členská funkce.

`OnDraw` Členská funkce zpracovává barvení ovládacích prvků. Když je ovládací prvek neaktivní, kontejnerem ovládacího prvku volá `OnDraw`, předání kontextu zařízení kontejnerem ovládacího prvku a souřadnice obdélníkového zabraná ovládacího prvku.

Obdélník předaný rozhraním, aby `OnDraw` členskou funkci obsahuje zabraná ovládacího prvku. Pokud je aktivní ovládací prvek, levém horním rohu je (0, 0) a kontext zařízení předaný je pro podřízené okno, která obsahuje ovládací prvek. Pokud je neaktivní, není nutně souřadnice levého horního (0, 0) a je kontext zařízení předaný kontejnerem ovládacího prvku obsahujícího ovládací prvek.

> [!NOTE]
>  Je důležité, který úprav `OnDraw` nezávisí na horní levé bodu obdélníku je rovna (0, 0) a kreslení pouze uvnitř obdélníku předán `OnDraw`. Pokud si nakreslíte mimo oblast obdélníku, můžete dojít k neočekávaným výsledkům.

Výchozí implementace poskytuje průvodce ovládací prvek ActiveX knihovny MFC v souboru implementace ovládacího prvku (. CPP), je znázorněno níže, jsou vykreslovány obdélníku s bílým štětce a vyplní se třemi tečkami aktuální barvou pozadí.

[!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
>  Při vykreslování ovládacího prvku, by neměl vytvářet předpoklady o stav kontextu zařízení, který je předán jako *primárního řadiče domény* parametr `OnDraw` funkce. V některých případech kontextu zařízení získáte ho od aplikace typu kontejner a nutně nelze inicializovat do výchozího stavu. Konkrétně se explicitně vyberte per, štětce, barvy, písma a další prostředky, které závisí váš kód výkresu.

##  <a name="_core_optimizing_your_paint_code"></a> Optimalizace kódu Malování

Poté, co ovládací prvek se úspěšně Malování samotné, dalším krokem je k optimalizaci `OnDraw` funkce.

Výchozí implementace vykreslování ovládacího prvku ActiveX jsou vykreslovány oblasti celý ovládací prvek. To je dostatečné pro jednoduché ovládací prvky, ale v mnoha případech překreslení ovládacího prvku by být rychleji, pokud pouze překreslit části potřebné aktualizace, ale místo celý ovládací prvek.

`OnDraw` Funkce poskytuje snadný způsob optimalizace předáním *rcInvalid*, obdélníkovou oblast, která potřebuje překreslení ovládacího prvku. Pomocí této oblasti obvykle menší než celý ovládací prvek oblasti, ke zrychlení procesu vykreslování.

##  <a name="_core_painting_your_control_using_metafiles"></a> Malování pomocí metasoubory ovládacího prvku

Ve většině případů *primárního řadiče domény* parametr `OnDraw` funkce odkazuje na obrazovce kontextu zařízení (DC). Ale při tisku imagí ovládacího prvku nebo během relace náhledu tisku, řadič domény byl přijat pro vykreslování je speciální typ s názvem "metasoubor řadiče domény". Na rozdíl od obrazovky řadiče domény, která okamžitě zpracovává požadavky odeslané, úložišť metasoubor DC žádosti o přehrání později. Některé aplikace typu kontejner si také můžou k vykreslení ovládacího prvku image pomocí metasoubor řadiče domény v režimu návrhu.

Metafile kreslení žádostí je možné provádět pomocí kontejneru, přistoupit přes dvě funkce rozhraní: `IViewObject::Draw` (této funkce lze také volat pro jiné metasoubor kreslení) a `IDataObject::GetData`. Když řadič domény je předán jako jeden z parametrů metasoubor rozhraní MFC zavolá [COleControl::OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile). Protože se jedná virtuální členskou funkci, přepište tuto funkci ve třídě ovládacího prvku provést žádné speciální zpracování. Výchozí chování volání `COleControl::OnDraw`.

Pokud chcete mít jistotu, že ovládací prvek lze vykreslit v kontextech zařízení obrazovky a metasoubor, je nutné použít pouze členské funkce, které jsou podporovány v obrazovce a metasoubor řadiče domény. Mějte na paměti, že nemusí být systém souřadnic měřená v pixelech.

Protože výchozí implementace `OnDrawMetafile` volání ovládacího prvku `OnDraw` funkci, použijte jenom členské funkce, které jsou vhodné pro metasoubor a kontext zařízení obrazovky, pokud přepíšete `OnDrawMetafile`. Následující seznam obsahuje podmnožinu `CDC` členské funkce, které lze použít v metasoubor a kontext zařízení obrazovky. Další informace o těchto funkcích naleznete v tématu třídy [CDC](../mfc/reference/cdc-class.md) v *odkaz knihovny MFC*.

|Oblouk|BibBlt|Ctr|
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

Kromě `CDC` členské funkce k dispozici je několik funkcí, které jsou kompatibilní se metasoubor řadiče domény. Patří mezi ně [CPalette::AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)a tři členské funkce `CBrush`: [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush), a [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).

Funkce, které nejsou zaznamenávány do metasouboru jsou: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect ](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc), a [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Protože metasoubor řadič domény není ve skutečnosti přiřazený k zařízení, nemůžete použít SetDIBits GetDIBits a CreateDIBitmap s metasoubor řadiče domény. SetDIBitsToDevice a StretchDIBits s metasoubor řadiče domény můžete použít jako cíl. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap), a [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) nejsou smysluplné s metasoubor řadiče domény.

Jiné vzít v úvahu při použití metasoubor řadič domény je, že nemusí být systém souřadnic měřená v pixelech. Z tohoto důvodu všechny výkresu kódu by měla být přizpůsobena podle střed v obdélníku předaný `OnDraw` v *rcBounds* parametru. To zabrání náhodnému Malování mimo ovládací prvek, protože *rcBounds* představuje velikost okna ovládacího prvku.

Po dokončení implementace metasoubor vykreslování ovládacího prvku k otestování metasoubor použijte kontejner testu. Zobrazit [testování vlastností a událostí pomocí testování kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak získat přístup ke kontejneru testů.

#### <a name="to-test-the-controls-metafile-using-test-container"></a>K otestování metasoubor ovládacího prvku pomocí Test kontejneru

1. Test kontejneru **upravit** nabídky, klikněte na tlačítko **vložte nový ovládací prvek**.

1. V **vložte nový ovládací prvek** pole, vyberte ovládací prvek a klikněte na tlačítko **OK**.

   Ovládací prvek se zobrazí v kontejneru testů.

1. Na **ovládací prvek** nabídky, klikněte na tlačítko **nakreslit metasoubor**.

   Samostatném okně se zobrazí, ve kterém je tento metasoubor zobrazovat. Můžete změnit velikost tohoto okna naleznete v tématu Jak škálování ovlivňuje metasoubor ovládacího prvku. Kdykoli můžete toto okno zavřít.

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
