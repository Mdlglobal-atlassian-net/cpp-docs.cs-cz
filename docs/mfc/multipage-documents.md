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
ms.openlocfilehash: 87912c06a40740d25530235ee421c6c8bfa11aab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370738"
---
# <a name="multipage-documents"></a>Vícestránkové dokumenty

Tento článek popisuje tiskový protokol systému Windows a vysvětluje, jak tisknout dokumenty, které obsahují více než jednu stránku. Článek se zabývá následujícími tématy:

- [Tiskový protokol](#_core_the_printing_protocol)

- [Přepsání funkcí třídy zobrazení](#_core_overriding_view_class_functions)

- [Stránkování](#_core_pagination)

- [Stránky tiskárny vs. stránky dokumentu](#_core_printer_pages_vs.._document_pages)

- [Stránkování v době tisku](#_core_print.2d.time_pagination)

## <a name="the-printing-protocol"></a><a name="_core_the_printing_protocol"></a>Tiskový protokol

Chcete-li vytisknout vícestránkový dokument, rozhraní a zobrazení pracovat následujícím způsobem. Nejprve rozhraní framework zobrazí **tiskové** dialogové okno, vytvoří kontext zařízení pro tiskárnu a volá členská funkce [StartDoc](../mfc/reference/cdc-class.md#startdoc) objektu [CDC.](../mfc/reference/cdc-class.md) Potom pro každou stránku dokumentu framework volá [členskou](../mfc/reference/cdc-class.md#startpage) funkci `CDC` StartPage objektu, instruuje objekt zobrazení k tisku stránky a volá členskou funkci [EndPage.](../mfc/reference/cdc-class.md#endpage) Pokud je nutné před spuštěním určité stránky změnit režim tiskárny, volání zobrazení [ResetDC](../mfc/reference/cdc-class.md#resetdc), které aktualizuje strukturu [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) obsahující nové informace o režimu tiskárny. Po vytištění celého dokumentu framework volá členská funkce [EndDoc.](../mfc/reference/cdc-class.md#enddoc)

## <a name="overriding-view-class-functions"></a><a name="_core_overriding_view_class_functions"></a>Přepsání funkcí třídy zobrazení

[CView](../mfc/reference/cview-class.md) Třída definuje několik členských funkcí, které jsou volány rámci během tisku. Přepsáním těchto funkcí ve vaší třídě zobrazení poskytujete připojení mezi logikou tisku rozhraní frameworku a logikou tisku třídy zobrazení. V následující tabulce jsou uvedeny tyto členské funkce.

### <a name="cviews-overridable-functions-for-printing"></a>CView je overridable funkce pro tisk

|Name (Název)|Důvod pro přepsání|
|----------|---------------------------|
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|Vložení hodnot do tiskového dialogového okna, zejména délky dokumentu|
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|Přidělení písem nebo jiných prostředků GDI|
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|Úprava atributů kontextu zařízení pro danou stránku nebo stránkování v době tisku|
|[OnPrint](../mfc/reference/cview-class.md#onprint)|Tisk dané stránky|
|[OnendPrinting](../mfc/reference/cview-class.md#onendprinting)|Navrátit prostředky GDI|

Zpracování související s tiskem můžete provést i v jiných funkcích, ale tyto funkce jsou ty, které řídí proces tisku.

Následující obrázek znázorňuje kroky související s procesem `CView`tisku a ukazuje, kde jsou volány jednotlivé funkce tiskových členů. Zbytek tohoto článku vysvětluje většinu těchto kroků podrobněji. Další části tiskového procesu jsou popsány v článku [Přidělení zdrojů GDI](../mfc/allocating-gdi-resources.md).

![Proces tiskové smyčky](../mfc/media/vc37c71.gif "Proces tiskové smyčky") <br/>
Tisková smyčka

## <a name="pagination"></a><a name="_core_pagination"></a>Stránkování

Rozhraní framework ukládá většinu informací o tiskové úloze ve struktuře [CPrintInfo.](../mfc/reference/cprintinfo-structure.md) Několik hodnot v `CPrintInfo` části stránkování; tyto hodnoty jsou přístupné, jak je znázorněno v následující tabulce.

### <a name="page-number-information-stored-in-cprintinfo"></a>Informace o čísle stránky uložené v cprintinfo

|Členské proměnné nebo<br /><br /> název (názvy) funkcí|Číslo stránky, na které se odkazuje|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|První stránka dokumentu|
|`GetMaxPage`/`SetMaxPage`|Poslední stránka dokumentu|
|`GetFromPage`|První stránka, která má být vytištěna|
|`GetToPage`|Poslední stránka, která má být vytištěna|
|`m_nCurPage`|Právě se tiskne stránka|

Čísla stránek začínají na 1, to znamená, že první stránka je očíslovaná 1, ne 0. Další informace o těchto a dalších členech [cprintinfo](../mfc/reference/cprintinfo-structure.md)naleznete v *odkazu knihovny MFC*.

Na začátku procesu tisku framework volá zobrazení [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) členskou funkci, `CPrintInfo` předání ukazatele na strukturu. Průvodce aplikací poskytuje `OnPreparePrinting` implementaci, která volá [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting) `CView`, další členskou funkci . `DoPreparePrinting`je funkce, která zobrazuje tiskové dialogové okno a vytváří kontext zařízení tiskárny.

V tomto okamžiku aplikace neví, kolik stránek je v dokumentu. Používá výchozí hodnoty 1 a 0xFFFF pro čísla první a poslední stránky dokumentu. Pokud víte, kolik stránek dokument má, přepsat `OnPreparePrinting` a volat [SetMaxPage]--brokenlink--(reference/cprintinfo-class.md#setmaxpage) pro `CPrintInfo` strukturu před odesláním do `DoPreparePrinting`. To umožňuje určit délku dokumentu.

`DoPreparePrinting`pak se zobrazí tiskové dialogové okno. Když se vrátí, `CPrintInfo` struktura obsahuje hodnoty určené uživatelem. Pokud si uživatel přeje vytisknout pouze vybraný rozsah stránek, může v tiskovém dialogovém okně zadat počáteční a koncová čísla stránek. Rozhraní Framework načte tyto `GetFromPage` `GetToPage` hodnoty pomocí funkce [a CPrintInfo](../mfc/reference/cprintinfo-structure.md). Pokud uživatel nezadává rozsah stránek, rozhraní `GetMinPage` `GetMaxPage` framework volá a používá hodnoty vrácené k tisku celého dokumentu.

Pro každou stránku dokumentu, který má být vytištěn, framework volá dvě členské funkce ve vaší třídě [zobrazení, OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) a [OnPrint](../mfc/reference/cview-class.md#onprint)a `CPrintInfo` předá každou funkci dva parametry: ukazatel na objekt [CDC](../mfc/reference/cdc-class.md) a ukazatel na strukturu. Pokaždé, když `OnPrepareDC` framework `OnPrint`volá a , předá jinou `CPrintInfo` hodnotu v *m_nCurPage* člen struktury. Tímto způsobem rozhraní informuje zobrazení, která stránka by měla být vytištěna.

Členská funkce [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) se také používá pro zobrazení na obrazovce. Před zahájením kreslení provádí úpravy kontextu zařízení. `OnPrepareDC`slouží podobnou roli v tisku, ale existuje několik rozdílů: za prvé, `CDC` objekt představuje kontext zařízení tiskárny `CPrintInfo` namísto kontextu obrazovky zařízení a za druhé, objekt je předán jako druhý parametr. (Tento parametr je `OnPrepareDC` **null,** když je volána pro zobrazení na obrazovce.) Přepsáním `OnPrepareDC` provedete úpravy kontextu zařízení na základě toho, která stránka se tiskne. Můžete například přesunout počátek výřezu a oblast oříznutí, abyste zajistili, že se vytiskne příslušná část dokumentu.

Členská funkce [OnPrint](../mfc/reference/cview-class.md#onprint) provádí skutečný tisk stránky. Článek [Jak se provádí výchozí tisk,](../mfc/how-default-printing-is-done.md) ukazuje, jak rozhraní Framework volá [OnDraw](../mfc/reference/cview-class.md#ondraw) s kontextem zařízení tiskárny k provedení tisku. Přesněji řečeno, `OnPrint` rozhraní `CPrintInfo` framework volá se strukturou a kontext zařízení a `OnPrint` předá kontext zařízení . `OnDraw` Přepsáním `OnPrint` provedete jakékoli vykreslování, které by mělo být provedeno pouze během tisku a ne pro zobrazení na obrazovce. Další informace najdete například v článku [Záhlaví a zápatí).](../mfc/headers-and-footers.md) Pak `OnDraw` volání z přepsání provést vykreslování `OnPrint` společné pro zobrazení obrazovky a tisk.

Skutečnost, `OnDraw` že dělá vykreslování pro zobrazení obrazovky a tisk znamená, že vaše aplikace je WYSIWYG: "To, co vidíte, je to, co dostanete." Předpokládejme však, že nepíšete aplikaci WYSIWYG. Zvažte například textový editor, který používá tučné písmo pro tisk, ale zobrazuje řídicí kódy k označení tučného textu na obrazovce. V takové situaci se `OnDraw` používá výhradně pro zobrazení na obrazovce. Když přepíšete `OnPrint`, nahraďte volání `OnDraw` voláním samostatné funkce výkresu. Tato funkce nakreslí dokument tak, jak se zobrazuje na papíře, pomocí atributů, které nezobrazujete na obrazovce.

## <a name="printer-pages-vs-document-pages"></a><a name="_core_printer_pages_vs.._document_pages"></a>Stránky tiskárny vs. stránky dokumentů

Když odkazujete na čísla stránek, je někdy nutné rozlišovat mezi konceptem stránky tiskárnou a konceptem stránky dokumentu. Z hlediska tiskárny je stránka jeden list papíru. Jeden list papíru se však nemusí nutně rovnat jedné stránce dokumentu. Pokud například tisknete bulletin, kde mají být listy přeloženy, může jeden list papíru obsahovat první i poslední stránku dokumentu vedle sebe. Podobně, pokud tisknete tabulku, dokument se neskládá ze stránek vůbec. Místo toho může jeden list papíru obsahovat řádky 1 až 20, sloupce 6 až 10.

Všechna čísla stránek ve struktuře [CPrintInfo](../mfc/reference/cprintinfo-structure.md) odkazují na stránky tiskárny. Rámec volá `OnPrepareDC` `OnPrint` a jednou pro každý list papíru, který bude procházet tiskárnou. Když přepíšete funkci [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) a určíte délku dokumentu, musíte použít stránky tiskárny. Pokud existuje korespondence 1:1 (to znamená, že jedna stránka tiskárny se rovná jedné stránce dokumentu), je to snadné. Pokud na druhé straně stránky dokumentů a stránky tiskárny přímo neodpovídají, musíte mezi nimi překládat. Zvažte například tisk tabulky. Při přepsání `OnPreparePrinting`je nutné vypočítat, kolik listů papíru bude nutné vytisknout celou `SetMaxPage` tabulku, `CPrintInfo`a použít tuto hodnotu při volání členské funkce aplikace . Podobně při přepsání `OnPrepareDC`je nutné přeložit *m_nCurPage* do rozsahu řádků a sloupců, které se zobrazí na daném listu, a odpovídajícím způsobem upravit původ výřezu.

## <a name="print-time-pagination"></a><a name="_core_print.2d.time_pagination"></a>Stránkování v době tisku

V některých situacích nemusí vaše třída zobrazení předem vědět, jak dlouho je dokument, dokud nebyl skutečně vytištěn. Předpokládejme například, že vaše aplikace není WYSIWYG, takže délka dokumentu na obrazovce neodpovídá jeho délce při tisku.

To způsobí problém při přepsání [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) pro vaše zobrazení třídy: `SetMaxPage` nelze předat hodnotu funkce [CPrintInfo](../mfc/reference/cprintinfo-structure.md) struktury, protože neznáte délku dokumentu. Pokud uživatel nezadává číslo stránky, u které má přestat používat tiskové dialogové okno, rozhraní framework neví, kdy se má tisková smyčka zastavit. Jediný způsob, jak určit, kdy zastavit tiskovou smyčku, je vytisknout dokument a zjistit, kdy končí. Vaše třída zobrazení musí zkontrolovat konec dokumentu během tisku a potom informovat rozhraní, když je dosaženo konce.

Rozhraní framework spoléhá na funkci [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) vaší třídy zobrazení, která mu říká, kdy má být zastavit. Po každém `OnPrepareDC`volání , framework zkontroluje `CPrintInfo` člen struktury s názvem *m_bContinuePrinting*. Jeho výchozí hodnota je **TRUE.** Tak dlouho, jak to zůstane, rámec pokračuje tiskové smyčky. Pokud je nastavena na **hodnotu FALSE**, framework zastaví. Chcete-li provést stránkování v `OnPrepareDC` době tisku, přepište, zda bylo dosaženo konce dokumentu, a nastavte *m_bContinuePrinting* **na hodnotu FALSE,** pokud byla dosažena.

Výchozí implementace `OnPrepareDC` sad *m_bContinuePrinting* na **HODNOTU NEPRAVDA,** pokud je aktuální stránka větší než 1. To znamená, že pokud délka dokumentu nebyla zadána, rozhraní předpokládá, že dokument je jedna stránka dlouhá. Jedním z důsledků je, že musíte být opatrní, `OnPrepareDC`pokud zavoláte verzi základní třídy . Nepředpokládejte, že *m_bContinuePrinting* bude **true** po volání verze základní třídy.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Záhlaví a zápatí](../mfc/headers-and-footers.md)

- [Přidělování prostředků GDI](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Viz také

[Tisk](../mfc/printing.md)<br/>
[Třída CView](../mfc/reference/cview-class.md)<br/>
[Třída CDC](../mfc/reference/cdc-class.md)
