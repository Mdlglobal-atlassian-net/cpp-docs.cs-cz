---
title: Vícestránkové dokumenty
ms.date: 11/19/2018
helpviewer_keywords:
- pagination [MFC]
- overriding [MFC], View class functions for printing
- OnPrepareDC method [MFC]
- CPrintInfo structure [MFC], multipage documents
- OnEndPrinting method [MFC]
- protocols [MFC], printing protocol
- document pages vs. printer pages [MFC]
- printer mode [MFC]
- printing [MFC], multipage documents
- printers [MFC], printer mode
- documents [MFC], printing
- OnPreparePrinting method [MFC]
- OnPrint method [MFC]
- DoPreparePrinting method and pagination [MFC]
- OnDraw method [MFC], printing
- pagination [MFC], printing multipage documents
- printing [MFC], protocol
- pages [MFC], printing
- OnBeginPrinting method [MFC]
- multipage documents [MFC]
- printing [MFC], pagination
- documents [MFC], paginating
ms.assetid: 69626b86-73ac-4b74-b126-9955034835ef
ms.openlocfilehash: 7ef4267c311c1de516f75c3b54677adfbfaba5c9
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916443"
---
# <a name="multipage-documents"></a>Vícestránkové dokumenty

Tento článek popisuje protokol tiskového systému Windows a vysvětluje, jak tisknout dokumenty, které obsahují více než jednu stránku. Článek se zabývá následujícími tématy:

- [Protokol tisku](#_core_the_printing_protocol)

- [Přepisování funkcí třídy zobrazení](#_core_overriding_view_class_functions)

- [Stránkování](#_core_pagination)

- [Stránky tiskárny vs. stránky dokumentů](#_core_printer_pages_vs.._document_pages)

- [Stránkování tiskového času](#_core_print.2d.time_pagination)

##  <a name="_core_the_printing_protocol"></a>Protokol tisku

Pro tisk vícestránkového dokumentu rozhraní a zobrazení komunikuje následujícím způsobem. Nejprve rozhraní zobrazí dialogové okno **Tisk** , vytvoří kontext zařízení pro tiskárnu a zavolá členskou funkci [StartDoc](../mfc/reference/cdc-class.md#startdoc) objektu [CDC](../mfc/reference/cdc-class.md) . Pak pro každou stránku dokumentu rozhraní volá členskou funkci `CDC` [StartPage](../mfc/reference/cdc-class.md#startpage) objektu, instruuje objekt zobrazení, aby vytiskl stránku, a zavolá členskou funkci [EndPage](../mfc/reference/cdc-class.md#endpage) . Pokud je nutné před spuštěním konkrétní stránky změnit režim tiskárny, zobrazení volá [ResetDC](../mfc/reference/cdc-class.md#resetdc), které aktualizuje strukturu [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) obsahující informace o novém režimu tiskárny. Po vytištění celého dokumentu rozhraní volá členskou funkci [EndDoc](../mfc/reference/cdc-class.md#enddoc) .

##  <a name="_core_overriding_view_class_functions"></a>Přepisování funkcí třídy zobrazení

Třída [CView](../mfc/reference/cview-class.md) definuje několik členských funkcí, které jsou volány rozhraním během tisku. Přepsáním těchto funkcí ve třídě zobrazení zadáte propojení mezi logikou tisku rozhraní a tiskovou logikou vaší třídy zobrazení. Následující tabulka uvádí tyto členské funkce.

### <a name="cviews-overridable-functions-for-printing"></a>Přepsatelné funkce prvku CView pro tisk

|Name|Důvod přepsání|
|----------|---------------------------|
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|Pro vložení hodnot do dialogového okna Tisk, zejména na délku dokumentu|
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|Přidělení písem nebo jiných prostředků GDI|
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|Postup úpravy atributů kontextu zařízení pro danou stránku nebo provádění stránkování tiskového času|
|[OnPrint](../mfc/reference/cview-class.md#onprint)|Tisk dané stránky|
|[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)|Zrušení přidělení prostředků GDI|

Zpracování související s tiskem můžete provádět i v jiných funkcích, ale tyto funkce jsou ty, které řídí proces tisku.

Následující obrázek znázorňuje kroky, které jsou součástí procesu tisku, a ukazuje, kde jsou `CView`volány jednotlivé členské funkce tisku. Zbývající část tohoto článku vysvětluje většinu těchto kroků podrobněji. Další části procesu tisku jsou popsány v článku [přidělování prostředků GDI](../mfc/allocating-gdi-resources.md).

![Proces smyčky tisku](../mfc/media/vc37c71.gif "Proces smyčky tisku") <br/>
Cyklus tisku

##  <a name="_core_pagination"></a>Stránkování

Rozhraní ukládá většinu informací o tiskové úloze ve struktuře [CPrintInfo –](../mfc/reference/cprintinfo-structure.md) . Několik hodnot v `CPrintInfo` souvislosti se stránkováním; tyto hodnoty jsou přístupné, jak je znázorněno v následující tabulce.

### <a name="page-number-information-stored-in-cprintinfo"></a>Informace o číslech stránek uložených v CPrintInfo –

|Členské proměnné nebo<br /><br /> názvy funkcí|Odkazované číslo stránky|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|První stránka dokumentu|
|`GetMaxPage`/`SetMaxPage`|Poslední stránka dokumentu|
|`GetFromPage`|První stránka, která se má vytisknout|
|`GetToPage`|Poslední stránka, která se má vytisknout|
|`m_nCurPage`|Právě tištěná stránka|

Čísla stránek začínají na 1, to znamená, že první stránka je očíslována 1, ne 0. Další informace o těchto a dalších členech [CPrintInfo –](../mfc/reference/cprintinfo-structure.md)naleznete v tématu *MFC Reference*.

Na začátku procesu tisku volá rozhraní členskou funkci [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) zobrazení, která předává ukazatel do `CPrintInfo` struktury. Průvodce aplikací poskytuje implementaci `OnPreparePrinting` , která volá [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), `CView`jinou členskou funkci. `DoPreparePrinting`je funkce, která zobrazí dialogové okno Tisk a vytvoří kontext zařízení tiskárny.

V tomto okamžiku aplikace neví, kolik stránek je v dokumentu. Pro čísla první a poslední stránky dokumentu používá výchozí hodnoty 1 a 0xFFFF. Pokud víte, kolik stránek váš dokument obsahuje, přepište `OnPreparePrinting` a zavolejte [SetMaxPage]--brokenlink--(Reference/CPrintInfo –-Class. MD # SetMaxPage) `CPrintInfo` pro strukturu předtím, než ji odešlete `DoPreparePrinting`do. To vám umožní zadat délku dokumentu.

`DoPreparePrinting`pak se zobrazí dialogové okno Tisk. Když se vrátí, `CPrintInfo` struktura obsahuje hodnoty určené uživatelem. Pokud si uživatel přeje vytisknout pouze vybraný rozsah stránek, může v dialogovém okně Tisk zadat počáteční a koncovou číslo stránky. Rozhraní načítá tyto hodnoty pomocí `GetFromPage` funkcí a [](../mfc/reference/cprintinfo-structure.md) `GetToPage` CPrintInfo –. Pokud uživatel nezadá rozsah stránky, rozhraní zavolá `GetMinPage` a `GetMaxPage` použije hodnoty vracené k vytištění celého dokumentu.

Pro každou stránku dokumentu, který má být vytištěn, rozhraní volá dvě členské funkce ve třídě zobrazení, [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) a [Print](../mfc/reference/cview-class.md#onprint)a předá jednotlivé funkce dva parametry: ukazatel na objekt [CDC](../mfc/reference/cdc-class.md) `CPrintInfo` a ukazatel na strukturované. Pokaždé, když rozhraní `OnPrepareDC` volá `OnPrint`a, předává jiné hodnotě v *m_nCurPage* členu `CPrintInfo` struktury. Tímto způsobem rozhraní oznamuje zobrazení, které stránky by se měly vytisknout.

Členská funkce [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) se používá také pro zobrazení obrazovky. Provede úpravy kontextu zařízení před tím, než se provede vykreslování. `OnPrepareDC`obsluhuje podobnou roli při tisku, ale existuje několik rozdílů: nejprve `CDC` objekt představuje kontext zařízení tiskárny namísto kontextu zařízení obrazovky a druhý `CPrintInfo` , objekt je předán jako druhý parametr. (Tento parametr má **hodnotu null** , pokud `OnPrepareDC` je volána pro zobrazení obrazovky.) Přepište `OnPrepareDC` , aby se provedly úpravy kontextu zařízení na základě tištěné stránky. Například můžete přesunout počátek zobrazení a oblast oříznutí, aby se zajistilo, že bude vytištěna příslušná část dokumentu.

Členská funkce pro [Tisk](../mfc/reference/cview-class.md#onprint) provede skutečný tisk stránky. Článek [o tom, jak se provádí výchozí tisk](../mfc/how-default-printing-is-done.md) , ukazuje, [](../mfc/reference/cview-class.md#ondraw) jak se v rozhraní nakreslí při vykreslení pomocí kontextu zařízení tiskárny k provedení tisku. Rozhraní .NET Framework je přesnější `OnPrint` , volá `CPrintInfo` se strukturou a kontextem zařízení `OnPrint` a předá kontext `OnDraw`zařízení. Přepište `OnPrint` pro provedení všech vykreslení, které by se mělo provést pouze během tisku, a ne pro zobrazení obrazovky. Například pro tisk záhlaví nebo zápatí (Další informace naleznete v [záhlavích a zápatí](../mfc/headers-and-footers.md) článků). Pak zavolejte `OnDraw` z `OnPrint` přepsání pro, aby bylo vykreslování společné při zobrazení a tisku obrazovky.

Fakt, který `OnDraw` provádí vykreslování pro zobrazení a tisk obrazovky znamená, že vaše aplikace je WYSIWYG: "Co vidíte, co dostanete." Předpokládejme však, že nepíšete aplikaci WYSIWYG. Zvažte například textový editor, který používá tučné písmo pro tisk, ale zobrazuje řídicí kódy pro indikaci tučného textu na obrazovce. V takové situaci použijete `OnDraw` výhradně pro zobrazení obrazovky. Pokud přepíšete `OnPrint`, nahraďte `OnDraw` volání samostatnou funkcí kreslení voláním. Tato funkce nakreslí dokument tak, jak se zobrazí na papíře, a to pomocí atributů, které se nezobrazí na obrazovce.

##  <a name="_core_printer_pages_vs.._document_pages"></a>Stránky tiskárny vs. Stránky dokumentu

Když odkazujete na čísla stránek, někdy je potřeba odlišit koncept stránky a koncept dokumentu stránky. Z hlediska tiskárny je stránka jedním listem papíru. Jeden list papíru ale nemusí nutně odpovídat jedné stránce dokumentu. Pokud například tisknete bulletin, kde jsou listy přeloženy, jeden list papíru může obsahovat první i poslední stránku dokumentu vedle sebe. Podobně platí, že pokud tisknete tabulku, dokument se vůbec neskládá ze stránek. Místo toho může obsahovat jeden list papíru řádky 1 až 20, sloupce 6 až 10.

Všechna čísla stránek ve struktuře [CPrintInfo –](../mfc/reference/cprintinfo-structure.md) odkazují na stránky tiskárny. Rozhraní Framework `OnPrepareDC` a `OnPrint` jednou pro každý list papíru, který projde tiskárnou. Pokud přepíšete funkci [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) a zadáte délku dokumentu, je nutné použít stránky tiskárny. Pokud existuje korespondence 1:1 (tj. jedna stránka tiskárny se rovná jedné stránce dokumentu), je to snadné. Pokud na druhé straně stránky dokumentu a stránky tiskárny neodpovídají přímo, je nutné překládat mezi nimi. Zvažte například tisk tabulky. Při přepisování `OnPreparePrinting`musíte vypočítat, kolik listů papíru bude nutné pro vytištění celé tabulky a pak použít tuto hodnotu při `SetMaxPage` volání členské funkce `CPrintInfo`. Podobně při přepsání `OnPrepareDC`je nutné přeložit *m_nCurPage* do rozsahu řádků a sloupců, které se zobrazí na daném listu, a následně upravit původní zobrazení podle potřeby.

##  <a name="_core_print.2d.time_pagination"></a>Stránkování tiskového času

V některých situacích vaše třída zobrazení nemusí předem znát dobu, po kterou je dokument skutečně vytištěn. Předpokládejme například, že vaše aplikace není WYSIWYG, takže délka dokumentu na obrazovce neodpovídá délce při tisku.

To způsobí problém při přepsání [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) pro vaši třídu zobrazení: hodnotu `SetMaxPage` nelze předat funkci struktury [CPrintInfo –](../mfc/reference/cprintinfo-structure.md) , protože neznáte délku dokumentu. Pokud uživatel nezadá číslo stránky, které se má zastavit při použití dialogového okna Tisk, rozhraní neví, kdy zastaví tiskovou smyčku. Jediným způsobem, jak určit, kdy zastavit smyčku tisku, je vytisknout dokument a zjistit, kdy skončí. Vaše třída zobrazení musí během tisku kontrolovat konec dokumentu a po dosažení konce informovat rozhraní.

Rozhraní spoléhá na funkci [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) vaší třídy zobrazení, která říká, kdy se má zastavit. Po každém volání `OnPrepareDC`rozhraní ověří architektura člen `CPrintInfo` struktury s názvem *m_bContinuePrinting*. Jeho výchozí hodnota je **true.** Dokud to zůstane, rozhraní pokračuje ve smyčce tisku. Pokud je nastaveno na **false**, rozhraní se zastaví. Chcete-li provést tiskovou stránkování, přepište `OnPrepareDC` , abyste zkontrolovali, zda byl dosažen konec dokumentu, a nastavte *m_bContinuePrinting* na **hodnotu false** , pokud má.

Výchozí implementace `OnPrepareDC` sad *m_bContinuePrinting* na **hodnotu false** , pokud je aktuální stránka větší než 1. To znamená, že pokud se délka dokumentu nezadala, rozhraní předpokládá, že dokument je o jednu stránku dlouhou. Jedním z nich je, že musíte být opatrní při volání verze `OnPrepareDC`základní třídy. Nepředpokládat, že *m_bContinuePrinting* bude po volání verze základní třídy **true** .

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Záhlaví a zápatí](../mfc/headers-and-footers.md)

- [Přidělování prostředků GDI](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Viz také:

[Tisk](../mfc/printing.md)<br/>
[CView – třída](../mfc/reference/cview-class.md)<br/>
[CDC – třída](../mfc/reference/cdc-class.md)
