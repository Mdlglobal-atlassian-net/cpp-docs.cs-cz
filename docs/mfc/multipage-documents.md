---
title: "Vícestránkové dokumenty | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 43bc9bbe4653e34c37ae46439baa1e649d6d8042
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="multipage-documents"></a>Vícestránkové dokumenty
Tento článek popisuje protokol tisku Windows a vysvětluje, jak tisk dokumentů, které obsahují více než jednu stránku. Článek obsahuje následující témata:  
  
-   [Protokol tisku](#_core_the_printing_protocol)  
  
-   [Přepsání zobrazit funkce tříd](#_core_overriding_view_class_functions)  
  
-   [Stránkování](#_core_pagination)  
  
-   [Stránky tiskáren oproti stránky dokumentu](#_core_printer_pages_vs.._document_pages)  
  
-   [Tisk čas stránkování](#_core_print.2d.time_pagination)  
  
##  <a name="_core_the_printing_protocol"></a>Protokol tisku  
 Tisk vícestránkového dokumentu, framework a zobrazení komunikovat následujícím způsobem. První rozhraní zobrazí **tiskových** dialogové okno, vytvoří kontext zařízení pro tiskárny a volání [zobrazující](../mfc/reference/cdc-class.md#startdoc) členské funkce [CDC](../mfc/reference/cdc-class.md) objektu. Potom pro každou stránku dokumentu volá framework [StartPage](../mfc/reference/cdc-class.md#startpage) členské funkce `CDC` objektu, dá pokyn objekt zobrazení k tisku stránky a volání [EndPage](../mfc/reference/cdc-class.md#endpage) – členská funkce. Pokud před zahájením konkrétní stránky, je třeba změnit režim tiskárny, zavolá zobrazení [ResetDC](../mfc/reference/cdc-class.md#resetdc), které aktualizace [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struktura obsahujícího informace o novém režim tiskárny. Pokud byl vytištěn celý dokument, volá framework [EndDoc](../mfc/reference/cdc-class.md#enddoc) – členská funkce.  
  
##  <a name="_core_overriding_view_class_functions"></a>Přepsání zobrazit funkce tříd  
 [CView](../mfc/reference/cview-class.md) třída definuje několik členské funkce, které jsou volány prostřednictvím rozhraní během tisku. Přepsáním tyto funkce ve třídě zobrazení poskytnete připojení mezi tisk logiku rozhraní framework a tisk logiku třídy zobrazení. Následující tabulka uvádí tyto členské funkce.  
  
### <a name="cviews-overridable-functions-for-printing"></a>CView na přepisovatelné funkce pro tisk  
  
|Název|Důvod pro přepsání|  
|----------|---------------------------|  
|[OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting)|Chcete-li vložit hodnoty v dialogovém okně tisku, zejména délka dokumentu|  
|[OnBeginPrinting –](../mfc/reference/cview-class.md#onbeginprinting)|Přidělit písem nebo jiných prostředků GDI|  
|[Onpreparedc –](../mfc/reference/cview-class.md#onpreparedc)|Chcete-li upravit atributy kontext zařízení pro danou stránku, nebo provést stránkování čas tisku|  
|[Při tisku](../mfc/reference/cview-class.md#onprint)|Tisknout danou stránku|  
|[OnEndPrinting –](../mfc/reference/cview-class.md#onendprinting)|Chcete-li zrušit přidělení prostředků GDI|  
  
 Můžete provést související s tiskem zpracování v také další funkce, ale tyto funkce jsou ty, které jednotka proces tisku.  
  
 Následující obrázek ukazuje kroky v procesu tisku a ukazuje, kde každý z `CView`je tisk člen se označují jako funkce. Zbývající část tohoto článku popisuje většinu těchto kroků podrobněji. Další části procesu tisku jsou popsané v článku [přidělování prostředků GDI](../mfc/allocating-gdi-resources.md).  
  
 ![Tisk procesu smyčky](../mfc/media/vc37c71.gif "vc37c71")  
Tisk smyčky  
  
##  <a name="_core_pagination"></a>Stránkování  
 Rozhraní framework ukládá většinu informací o tiskovou úlohu ve [cprintinfo –](../mfc/reference/cprintinfo-structure.md) struktura. Několik hodnot v `CPrintInfo` týkají stránkování; tyto hodnoty jsou k dispozici, jak je znázorněno v následující tabulce.  
  
### <a name="page-number-information-stored-in-cprintinfo"></a>Číslo stránky informace uložené v cprintinfo –  
  
|Členské proměnné nebo<br /><br /> názvy – funkce|Číslo stránky, které odkazuje|  
|-----------------------------------------------|----------------------------|  
|`GetMinPage`/`SetMinPage`|První stránka dokumentu|  
|`GetMaxPage`/`SetMaxPage`|Poslední stránku dokumentu|  
|`GetFromPage`|První stránky k tisku|  
|`GetToPage`|Poslední stránky k tisku|  
|`m_nCurPage`|Právě tištěné stránky|  
  
 Úvodní stránka čísla na 1, to znamená, první stránka je číslované 1, není 0. Další informace o těchto a dalších členy [cprintinfo –](../mfc/reference/cprintinfo-structure.md), najdete v článku *odkaz knihovny MFC*.  
  
 Na začátku procesu tisku, volá framework zobrazení [OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting) – členská funkce, předávání ukazatel na `CPrintInfo` struktury. Poskytuje implementaci pro Průvodce aplikací `OnPreparePrinting` , který volá [doprepareprinting –](../mfc/reference/cview-class.md#doprepareprinting), jiné členské funkce `CView`. `DoPreparePrinting`je funkce, která se zobrazí dialogové okno tisku a vytvoří kontextu zařízení tiskárny.  
  
 V tomto okamžiku aplikace neví, kolik stránek se v dokumentu. Použije výchozí hodnoty 1 a 0xFFFF pro čísla první a poslední stránky z dokumentu. Pokud víte, kolik stránek dokumentu, mají přednost před `OnPreparePrinting` a volání [SetMaxPage]--brokenlink--(reference/cprintinfo-class.md#setmaxpage) pro `CPrintInfo` struktury před jejím odesláním `DoPreparePrinting`. To umožňuje zadat délku dokumentu.  
  
 `DoPreparePrinting`potom zobrazí dialogové okno tisku. Až se obnoví, `CPrintInfo` struktura obsahuje hodnoty zadané uživatelem. Pokud uživatel chce tisku vybraný rozsah stránek, potvrdí můžete zadat počáteční a koncovou čísla stránek v dialogovém okně tisku. Rozhraní framework načte tyto hodnoty pomocí `GetFromPage` a `GetToPage` funkce [cprintinfo –](../mfc/reference/cprintinfo-structure.md). Pokud uživatel není zadat rozsahu stránek, volá framework `GetMinPage` a `GetMaxPage` a používá hodnot vrácených tisknout celý dokument.  
  
 Pro každou stránku dokumentu pro tisk volá framework dva členské funkce ve třídě zobrazení [onpreparedc –](../mfc/reference/cview-class.md#onpreparedc) a [při tisku](../mfc/reference/cview-class.md#onprint)a předá jednotlivé funkce dva parametry: ukazatel na [ CDC](../mfc/reference/cdc-class.md) objekt a odkazy `CPrintInfo` struktura. Pokaždé, když volání framework `OnPrepareDC` a `OnPrint`, předává jinou hodnotu v `m_nCurPage` členem `CPrintInfo` struktura. Tímto způsobem rozhraní informuje zobrazení stránky, která by měla být vytisknout.  
  
 [Onpreparedc –](../mfc/reference/cview-class.md#onpreparedc) – členská funkce se také používá pro zobrazení na obrazovce. Umožňuje úpravy kontextu zařízení před vykreslením probíhá. `OnPrepareDC`funguje podobně jako role v tisku, ale existuje několik rozdílů: nejdřív `CDC` objekt představuje kontextu zařízení tiskárny místo kontextu obrazovky zařízení a druhé, `CPrintInfo` jako druhý parametr je předán objekt. (Tento parametr je **NULL** při `OnPrepareDC` je volána pro zobrazení na obrazovce.) Přepsání `OnPrepareDC` provádět úpravy kontextu zařízení, podle které se tisknout. Můžete například přesunout bod zobrazení a zajistit, že odpovídající část dokumentu načte vytištěn oblast ořezu.  
  
 [Při tisku](../mfc/reference/cview-class.md#onprint) provede – členská funkce skutečného tisku stránky. Článek [jak výchozí tisk probíhá](../mfc/how-default-printing-is-done.md) znázorňuje, jakým způsobem volá rámec [OnDraw –](../mfc/reference/cview-class.md#ondraw) s kontextu zařízení tiskárny k tisku. Přesněji řečeno, volání framework `OnPrint` s `CPrintInfo` strukturu a kontext zařízení, a `OnPrint` předá kontext zařízení, který má `OnDraw`. Přepsání `OnPrint` k provedení jakékoli vykreslování, které by mělo být provedeno pouze během tisku a ne pro zobrazení na obrazovce. Například pro tisk záhlaví a zápatí (najdete v článku [záhlaví a zápatí](../mfc/headers-and-footers.md) informace). Potom zavolejte `OnDraw` z přepis metody `OnPrint` udělat společné pro obě obrazovky zobrazení vykreslování a tisk.  
  
 Fakt, na který `OnDraw` nepodporuje vykreslování pro obě obrazovky zobrazení a tisk znamená, že vaše aplikace se WYSIWYG: "What you see is what you get." Ale Předpokládejme, že nejsou zápis WYSIWYG aplikace. Představte si třeba textový editor, který používá tučné písmo pro tisk, ale zobrazí kódy ovládacího prvku k označení tučně na obrazovce. V takovém případě použijete `OnDraw` výhradně pro zobrazení na obrazovce. Při přepsání `OnPrint`, nahraďte volání `OnDraw` pomocí volání kreslení funkci. Tuto funkci nevykresluje dokumentu způsob, jakým se zobrazí na dokument, pomocí atributů, které se nezobrazí na obrazovce.  
  
##  <a name="_core_printer_pages_vs.._document_pages"></a>Tiskárny stránky vs. Stránky dokumentu  
 Když odkazujete na stránce čísla, je někdy nutné rozlišit tiskárny koncept stránky a koncept dokumentu stránky. Z hlediska tiskárny stránka má jeden list papíru. Jeden list papíru však není nutně rovnat jednu stránku dokumentu. Například při tisku bulletinů, kde mají listy nástroje přeložena, může obsahovat jeden list papíru první a poslední stránky do dokumentu vedle sebe. Podobně při tisku tabulkou, dokument není obsahovat stránky vůbec. Místo toho listů dokumentu může obsahovat řádky 1 až 20, sloupce 6 až 10.  
  
 Všechny stránky v čísla [cprintinfo –](../mfc/reference/cprintinfo-structure.md) struktura odkazují na stránky tiskárny. Volání framework `OnPrepareDC` a `OnPrint` jednou pro každý z nich dokumentu, který bude předávat tiskárny. Při přepsání [OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting) funkce zadat délku dokumentu, je nutné použít stránky tiskáren. Pokud je souvislosti (tedy jedné stránky tiskárny se rovná jednu stránku dokumentu), pak je to snadné. Pokud na druhé straně dokumentu stránky a stránky tiskáren neodpovídají přímo, musí překládat mezi nimi. Představte si třeba tisk tabulkou. Při přepsání `OnPreparePrinting`, je nutné vypočítat, kolik listů, na které bude potřeba tiskových celou tabulku a potom tuto hodnotu použít při volání metody `SetMaxPage` členské funkce `CPrintInfo`. Podobně při přepisování `OnPrepareDC`, musí překládat `m_nCurPage` do rozsah řádků a sloupců, které se zobrazí na tuto konkrétní listu a odpovídajícím způsobem upravit bod zobrazení.  
  
##  <a name="_core_print.2d.time_pagination"></a>Tisk čas stránkování  
 V některých situacích třídě zobrazení nemusí předem vědět, jak dlouho je dokument, dokud ve skutečnosti vytištění. Například předpokládejme, že vaše aplikace není WYSIWYG, takže délka dokumentu na obrazovce neodpovídá jeho délka při tisku.  
  
 To způsobí, že problém při přepsání [OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting) pro zobrazení třídy: nemůžete předat hodnotu na `SetMaxPage` funkce [cprintinfo –](../mfc/reference/cprintinfo-structure.md) struktury, protože nevíte, délku dokument. Pokud uživatel není zadat číslo stránky kdykoli zastavit pomocí dialogového okna Tisk, rozhraní neví, kdy zastavit tiskové smyčky. Jediný způsob, jak určit, kdy zastavit tiskové smyčky je vytiskněte dokument a zobrazit při jeho ukončení. Zobrazení třídy musí zkontrolovat tohoto dokumentu je tisku, a potom informovat rozhraní, když je dosaženo konce.  
  
 Rozhraní využívá třídy zobrazení [onpreparedc –](../mfc/reference/cview-class.md#onpreparedc) funkce mu sdělit, kdy bude ukončeno. Po každé volání `OnPrepareDC`, rozhraní kontroluje členem `CPrintInfo` strukturu s názvem `m_bContinuePrinting`. Výchozí hodnota je **hodnotu TRUE.** Tak dlouho, dokud zůstává tak, pokračuje v rozhraní framework tiskové smyčky. Pokud je nastaven na hodnotu **FALSE**, zastaví framework. Chcete-li provést čas tisku stránkování, přepište `OnPrepareDC` ke kontrole, jestli na konec dokumentu má bylo dosaženo a nastavte `m_bContinuePrinting` k **FALSE** po.  
  
 Výchozí implementaci `OnPrepareDC` nastaví `m_bContinuePrinting` k **FALSE** Pokud aktuální stránky je větší než 1. To znamená, že pokud nebyla zadána délka dokumentu, rozhraní předpokládá, že dokument je jednu stránku dlouho. Důsledkem tohoto je, že musí být opatrní při volání základní třída verzi `OnPrepareDC`. Nepředpokládejte, který `m_bContinuePrinting` bude **TRUE** po volání metody verze základní třídy.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Záhlaví a zápatí](../mfc/headers-and-footers.md)  
  
-   [Přidělování prostředků GDI](../mfc/allocating-gdi-resources.md)  
  
## <a name="see-also"></a>Viz také  
 [Tisk](../mfc/printing.md)   
 [CView – třída](../mfc/reference/cview-class.md)   
 [CDC – třída](../mfc/reference/cdc-class.md)