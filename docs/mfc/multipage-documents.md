---
title: Vícestránkové dokumenty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d1d7835d2c0521495984a7534fd6fcf07216fd1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414833"
---
# <a name="multipage-documents"></a>Vícestránkové dokumenty

Tento článek popisuje protokol tisku Windows a vysvětluje, jak vytisknout dokumenty, které obsahují více než jednu stránku. Tento článek obsahuje následující témata:

- [Protokol tisku](#_core_the_printing_protocol)

- [Přepisování funkcí třídy zobrazení](#_core_overriding_view_class_functions)

- [Stránkování](#_core_pagination)

- [Stránkám tiskárny vs. stránky dokumentu](#_core_printer_pages_vs.._document_pages)

- [Tisk – čas stránkování](#_core_print.2d.time_pagination)

##  <a name="_core_the_printing_protocol"></a> Protokol tisku

Tisk vícestránkového dokumentu, rozhraní framework a zobrazení interakce následujícím způsobem. Nejprve zobrazí rozhraní **tisk** dialogové okno, vytvoří kontext zařízení pro tiskárnu a volání [zobrazující](../mfc/reference/cdc-class.md#startdoc) členskou funkci [CDC](../mfc/reference/cdc-class.md) objektu. Potom pro každou stránku dokumentu volá framework [StartPage](../mfc/reference/cdc-class.md#startpage) členskou funkci `CDC` objektu, nastaví objekt zobrazení k tisku stránky a volání [EndPage](../mfc/reference/cdc-class.md#endpage) členskou funkci. Pokud před zahájením konkrétní stránce musí změnit režim tiskárny, zavolá zobrazení [ResetDC](../mfc/reference/cdc-class.md#resetdc), jaké aktualizace [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) struktury obsahující nové informace o tiskárně režimu. Když vytisknutí celý dokument volá framework [EndDoc](../mfc/reference/cdc-class.md#enddoc) členskou funkci.

##  <a name="_core_overriding_view_class_functions"></a> Přepisování funkcí třídy zobrazení

[CView](../mfc/reference/cview-class.md) třída definuje několik členské funkce, které se volá se rozhraním při tisku. Přepsáním tyto funkce ve třídě zobrazení poskytuje připojení mezi tisk logiky rozhraní framework a zobrazit třídu tisk logiku. V následující tabulce jsou uvedeny tyto členské funkce.

### <a name="cviews-overridable-functions-for-printing"></a>CView na přepisovatelné funkce pro tisk

|Název|Důvod přepsání|
|----------|---------------------------|
|[OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting)|Chcete-li vložit hodnoty v dialogovém okně tisku, zejména délka dokumentu|
|[OnBeginPrinting –](../mfc/reference/cview-class.md#onbeginprinting)|Přidělit, písem nebo jiných prostředků GDI|
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|Aby se upravily atributy kontextu zařízení pro danou stránku nebo provádět stránkování čas tisku|
|[Při tisku](../mfc/reference/cview-class.md#onprint)|Chcete-li vytisknout danou stránku|
|[OnEndPrinting –](../mfc/reference/cview-class.md#onendprinting)|K uvolnění prostředků GDI|

Můžete provést zpracování i jiné funkce související s tiskem, ale tyto funkce jsou ty, které řídí proces tisku.

Následující obrázek znázorňuje proces tisku kroky a ukazuje, kde každý z `CView`je tisk členské funkce jsou volány. Zbývající část tohoto článku popisuje většina z těchto kroků podrobněji. Další části procesu tisku jsou popsané v článku [přidělování prostředků GDI](../mfc/allocating-gdi-resources.md).

![Tisk procesu smyčky](../mfc/media/vc37c71.gif "vc37c71") The smyčka tisku

##  <a name="_core_pagination"></a> Stránkování

Rozhraní framework ukládá většinu informací o tiskové úloze v [cprintinfo –](../mfc/reference/cprintinfo-structure.md) struktury. Některé hodnoty v `CPrintInfo` se týkají stránkování; tyto hodnoty jsou k dispozici, jak je znázorněno v následující tabulce.

### <a name="page-number-information-stored-in-cprintinfo"></a>Číslo stránky informací uložených v cprintinfo –

|Členské proměnné nebo<br /><br /> názvy – funkce|Číslo stránky, které odkazuje|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|První stránka dokumentu|
|`GetMaxPage`/`SetMaxPage`|Poslední stránka dokumentu|
|`GetFromPage`|První stránky k tisku|
|`GetToPage`|Poslední stránky k tisku|
|`m_nCurPage`|Právě tištěné stránky|

Počáteční stránka čísla na 1, to znamená, první stránka je číslované není 0, 1. Další informace o těchto a dalších členů [cprintinfo –](../mfc/reference/cprintinfo-structure.md), najdete v článku *odkaz knihovny MFC*.

Na začátku procesu tisku, volá framework zobrazení [OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting) členské funkci a předává ukazatel `CPrintInfo` struktury. Průvodce aplikací poskytuje implementaci `OnPreparePrinting` , která volá [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), jiné členské funkce `CView`. `DoPreparePrinting` je funkce, která se zobrazí dialogové okno Tisk a vytvoří kontext zařízení tiskárny.

Aplikace v tomto okamžiku nebude vědět, kolik stránek se v dokumentu. Použije výchozí hodnoty 1 a 0xFFFF čísla první a poslední stránky z dokumentu. Pokud víte, kolik stránek dokumentu, má přednost před `OnPreparePrinting` a volání [SetMaxPage]--brokenlink--(reference/cprintinfo-class.md#setmaxpage) pro `CPrintInfo` strukturu před jejím odesláním `DoPreparePrinting`. To vám umožní zadat délku dokumentu.

`DoPreparePrinting` Zobrazí dialogové okno Tisk. Když se vrátí, `CPrintInfo` struktura obsahuje hodnoty zadané uživatelem. Pokud si uživatel přeje tisk pouze vybrané oblasti stránek, nezíská zadat počáteční a koncovou čísla stránek v dialogovém okně tisku. Načte tyto hodnoty pomocí rozhraní `GetFromPage` a `GetToPage` funkce [cprintinfo –](../mfc/reference/cprintinfo-structure.md). Pokud uživatel nemá určenou stránku rozsah, zavolá rozhraní `GetMinPage` a `GetMaxPage` a používá hodnoty vrácené vytisknout celý dokument.

Pro každou stránku z dokumentu, které se mají vytisknout, volá framework dva členské funkce ve třídě zobrazení [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) a [OnPrint –](../mfc/reference/cview-class.md#onprint)a předá každý funkce dva parametry: ukazatel [ CDC](../mfc/reference/cdc-class.md) objektu a ukazatel `CPrintInfo` struktury. Pokaždé, když rámec volá `OnPrepareDC` a `OnPrint`, předá jinou hodnotu v *m_nCurPage* člena `CPrintInfo` struktury. Tímto způsobem rozhraní informuje zobrazení na stránce, které by měl vytisknout.

[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) členská funkce se také používá pro zobrazení na obrazovce. Umožňuje úpravy kontextu zařízení než kreslení. `OnPrepareDC` slouží podobné role v tisku, ale existuje několik rozdílů: nejprve je potřeba `CDC` objekt představuje kontextu zařízení tiskárny místo kontextu obrazovky zařízení a druhé, `CPrintInfo` objekt je předán jako druhý parametr. (Tento parametr je **NULL** při `OnPrepareDC` se volá pro zobrazení obrazovky.) Přepsat `OnPrepareDC` provést úpravy kontextu zařízení založené na stránce, které je tisk. Můžete například přesunout zobrazení zdroje a oblast ořezu zajistit, že získá odpovídající část dokumentu vytištěn.

[OnPrint –](../mfc/reference/cview-class.md#onprint) členská funkce provádí skutečné tisku stránky. Tento článek [jak výchozí tisk se provádí](../mfc/how-default-printing-is-done.md) znázorňuje, jakým způsobem volá framework [OnDraw](../mfc/reference/cview-class.md#ondraw) s kontextem zařízení tiskárny k provedení tisk. Přesněji řečeno, rámec volá `OnPrint` s `CPrintInfo` strukturu a kontext zařízení, a `OnPrint` předá kontext zařízení pro `OnDraw`. Přepsat `OnPrint` provádět jakékoli vykreslení, které by mělo být provedeno pouze během tisku a ne pro zobrazení obrazovky. Například pro tisk záhlaví a zápatí (přečtěte si článek [záhlaví a zápatí](../mfc/headers-and-footers.md) Další informace). Poté zavolejte `OnDraw` z přepsané `OnPrint` společná pro obě displejem vykreslování a tisk.

Fakt, který `OnDraw` nepodporuje vykreslování pro obě obrazovky zobrazení a tisk znamená, že je vaše aplikace WYSIWYG: "What you see is what you get." Nicméně Předpokládejme, že nejsou zápis WYSIWYG aplikace. Představte si třeba textový editor, který používá tučné písmo pro tisk, ale zobrazí řídicích kódů k označení tučným písmem na obrazovce. V takovém případě použijete `OnDraw` výhradně pro zobrazení na obrazovce. Při přepsání `OnPrint`, nahraďte volání `OnDraw` pomocí volání do samostatné funkce kreslení. Tuto funkci vykreslí dokument způsob, jakým se zobrazí na papír, pomocí atributů, které nechcete zobrazit na obrazovce.

##  <a name="_core_printer_pages_vs.._document_pages"></a> Tiskárny stránky vs. Stránky dokumentů

Když odkazujete na stránku čísla, je někdy potřeba rozlišovat mezi tiskárny koncept stránky a koncept dokumentu stránky. Z hlediska tiskárny na stránce je jeden list papíru. Jeden list papíru však není nutně roven jedné stránky z dokumentu. Například pokud tisknete bulletinu, kde mají listy složit, může obsahovat jeden list papíru první a poslední stránky dokumentu, vedle sebe. Podobně pokud tisknete tabulku, dokument nebude se skládají z stránky vůbec. Místo toho jeden list papíru může obsahovat řádky 1 až 20, 6 až 10 sloupce.

Na stránce v čísla [cprintinfo –](../mfc/reference/cprintinfo-structure.md) struktury odkazují na stránky tiskárny. Rámec volá `OnPrepareDC` a `OnPrint` s jednou registrací u každé list papíru, který se předá tiskárny. Při přepsání [OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting) funkce zadat délku dokumentu, je nutné použít stránkám tiskárny. Pokud je shoda (to znamená jedné stránky tiskárny se rovná jednu stránku dokumentu), pak je to snadné. Pokud na druhé straně stránky dokumentu a stránkám tiskárny neodpovídají přímo, je třeba převést mezi nimi. Představte si třeba Tisk tabulky. Při přepisování `OnPreparePrinting`, je nutné vypočítat, kolik listů, na které se bude vyžadovat vytisknout celou tabulku a potom tuto hodnotu použít při volání `SetMaxPage` členskou funkci `CPrintInfo`. Podobně při přepisování `OnPrepareDC`, musí překládat *m_nCurPage* do rozsahu řádků a sloupců, které se zobrazí na tento konkrétní seznam a odpovídajícím způsobem upravit zobrazení původu.

##  <a name="_core_print.2d.time_pagination"></a> Tisk – čas stránkování

V některých případech zobrazení třídy nemůže předem vědět, jak dlouho je dokument, dokud se ve skutečnosti byl vytištěn. Například předpokládejme, že vaše aplikace nebude WYSIWYG, takže délka dokumentu na obrazovce neodpovídá jeho délka po vytištění.

To způsobí, že k potížím při přepsání [OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting) pro zobrazení třídy: nemůžete předat hodnotu, která `SetMaxPage` funkce [cprintinfo –](../mfc/reference/cprintinfo-structure.md) struktury, protože si nejste jisti, délku dokument. Pokud uživatel nemá určenou číslo stránky k zastavení v dialogovém okně tisku, rozhraní nebude vědět, kdy se má zastavit tisku smyčky. Jediný způsob, jak určit, kdy zastavit tisku smyčky je vytisknout dokument a najdete v článku při jeho ukončení. Zobrazit třídu musíte hledat konec dokumentu, zatímco je tisku a potom informovat rozhraní, když je dosaženo konce.

Rozhraní využívá třídy zobrazení [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) funkce určit, kdy se má zastavit. Po každé volání `OnPrepareDC`, zkontroluje členem rozhraní `CPrintInfo` strukturu s názvem *m_bContinuePrinting*. Výchozí hodnota je **hodnotu TRUE.** Jak dlouho, dokud zůstává, smyčka tisku pokračuje v rozhraní. Pokud je nastavena na **FALSE**, zastaví framework. Provádět stránkování čas tisku přepsat `OnPrepareDC` ke kontrole, jestli konec dokumentu má bylo dosaženo a nastavte *m_bContinuePrinting* k **FALSE** po.

Výchozí implementace `OnPrepareDC` nastaví *m_bContinuePrinting* k **FALSE** Pokud aktuální stránka je větší než 1. To znamená, že pokud nebyla zadána délka dokumentu, rozhraní se předpokládá, že dokument je jedna stránka dlouho. Důsledkem tohoto je, že musíte být opatrní při volání základní třídy verzi `OnPrepareDC`. Nepředpokládejte, že *m_bContinuePrinting* bude **TRUE** po volání metody základní třídy verze.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Záhlaví a zápatí](../mfc/headers-and-footers.md)

- [Přidělování prostředků GDI](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Viz také

[Tisk](../mfc/printing.md)<br/>
[CView – třída](../mfc/reference/cview-class.md)<br/>
[CDC – třída](../mfc/reference/cdc-class.md)