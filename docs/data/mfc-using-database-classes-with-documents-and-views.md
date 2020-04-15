---
title: 'MFC: Použití databázových tříd s dokumenty a zobrazeními'
ms.date: 11/04/2016
helpviewer_keywords:
- documents [C++], database applications
- recordsets [C++], documents and views
- CRecordView class, using in database forms
- views [C++], database applications
- forms [C++], database applications
- record views [C++], form-based applications
- document/view architecture [C++], in databases
- database applications [C++], forms
- database classes [C++], MFC
- ODBC recordsets [C++], documents and views
- ODBC [C++], forms
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
ms.openlocfilehash: 9e071e0cc25492073cd74ed517284476b6e49ef8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368900"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: Použití databázových tříd s dokumenty a zobrazeními

Databázové třídy knihovny MFC můžete použít s architekturou dokumentu nebo zobrazení nebo bez ní. Toto téma klade důraz na práci s dokumenty a zobrazeními. Vysvětluje:

- [Jak napsat formulářovou aplikaci](#_core_writing_a_form.2d.based_application) `CRecordView` pomocí objektu jako hlavního zobrazení dokumentu.

- [Použití objektů sady záznamů v dokumentech a zobrazeních](#_core_using_recordsets_in_documents_and_views).

- [Další úvahy](#_core_other_factors).

Alternativy naleznete v tématu [Knihovna MFC: Použití tříd databáze bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>Psaní formulářové aplikace

Mnoho aplikací pro přístup k datům je založeno na formulářích. Uživatelské rozhraní je formulář obsahující ovládací prvky, ve kterých uživatel zkoumá, zadá nebo uvede data. Chcete-li formulář žádosti na `CRecordView`základě, použijte třídu . Když spustíte Průvodce aplikací knihovny MFC a vyberete typ klienta **ROZHRANÍ ODBC** na stránce **Podpora databáze,** projekt použije `CRecordView` pro třídu zobrazení.

V aplikaci založené na formuláři každý objekt `CRecordset` zobrazení záznamu ukládá ukazatel na objekt. Mechanismus výměny pole záznamu rozhraní (RFX) rozhraní si vyměňuje data mezi sadou záznamů a zdrojem dat. Mechanismus výměny dat dialogu (DDX) vyměňuje data mezi datovými členy pole objektu sady záznamů a ovládacími prvky ve formuláři. `CRecordView`Poskytuje také výchozí funkce obslužné rutiny příkazů pro navigaci ze záznamu do záznamu ve formuláři.

Informace o vytvoření formulářové aplikace pomocí Průvodce aplikací naleznete [v tématu Vytvoření aplikace knihovny MFC založené na formulářích,](../mfc/reference/creating-a-forms-based-mfc-application.md) [Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md).

Úplnou diskusi o formulářích naleznete v [tématu Zobrazení záznamů](../data/record-views-mfc-data-access.md).

## <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>Použití sad záznamů v dokumentech a zobrazeních

Mnoho jednoduchých aplikací založených na formulářích nepotřebuje dokumenty. Pokud je aplikace složitější, pravděpodobně budete chtít použít dokument jako proxy pro `CDatabase` databázi, ukládání objektu, který se připojuje ke zdroji dat. Aplikace založené na formulářích obvykle ukládají ukazatel na objekt sady záznamů v zobrazení. Jiné druhy databázových aplikací `CDatabase` ukládají sady záznamů a objekt v dokumentu. Zde jsou některé možnosti pro použití dokumentů v databázových aplikacích:

- Pokud přistupujete k sadě záznamů `CRecordset` v místním kontextu, vytvořte objekt místně v členských funkcích dokumentu nebo zobrazení podle potřeby.

   Deklarujte objekt sady záznamů jako místní proměnnou ve funkci. Předat NULL konstruktoru, který způsobí, že rozhraní `CDatabase` vytvořit a otevřít dočasný objekt pro vás. Jako alternativu předaj `CDatabase` ukazatel na objekt. Použijte sadu záznamů v rámci funkce a nechte ji automaticky zničit při ukončení funkce.

   Když předáte null konstruktoru sady záznamů, rozhraní framework používá `GetDefaultConnect` informace vrácené `CDatabase` členská funkce sady záznamů k vytvoření objektu a jeho otevření. Průvodci implementovat `GetDefaultConnect` za vás.

- Pokud přistupujete k sadě záznamů během doby platnosti dokumentu, vložte do dokumentu jeden nebo více `CRecordset` objektů.

   Vytvořte objekty sady záznamů buď při inicializaci dokumentu, nebo podle potřeby. Můžete napsat funkci, která vrátí ukazatel na sadu záznamů, pokud již existuje nebo vytvoří a otevře sadu záznamů, pokud ještě neexistuje. Podle potřeby zavřete, odstraňte a znovu vytvořte sadu záznamů nebo zavolejte její členská `Requery` funkci a aktualizujte záznamy.

- Pokud přistupujete ke zdroji dat během doby `CDatabase` platnosti dokumentu, `CDatabase` vložte objekt nebo uložte ukazatel na objekt.

   Objekt `CDatabase` spravuje připojení ke zdroji dat. Objekt je vytvořen automaticky během konstrukce dokumentu `Open` a při inicializaci dokumentu voláte jeho člennou funkci. Když vytváříte objekty sady záznamů v členských funkcích dokumentu, předáte ukazatel `CDatabase` objektu dokumentu. Tím přidružíte každou sadu záznamů ke zdroji dat. Databázový objekt je obvykle zničen při zavření dokumentu. Objekty sady záznamů jsou obvykle zničeny při ukončení oboru funkce.

## <a name="other-factors"></a><a name="_core_other_factors"></a>Další faktory

Aplikace založené na formulářích často nemají žádné použití pro mechanismus serializace dokumentů v rámci, takže můžete chtít odebrat, zakázat nebo nahradit **příkazy New** a **Open** v nabídce **Soubor.** Viz článek [Serializace: Serializace vs. Vstup/výstup databáze](../mfc/serialization-serialization-vs-database-input-output.md).

Můžete také chtít využít mnoho možností uživatelského rozhraní, které může podporovat rozhraní. Můžete například použít `CRecordView` více objektů v okně rozdělovače, otevřít více sad záznamů v různých podřízených oknech rozhraní více dokumentů (MDI) a tak dále.

Možná budete chtít implementovat tisk, co je podle vašeho `CRecordView` názoru, ať už se jedná o formulář implementovaný s nebo něco jiného. Jako třídy `CFormView`odvozené z aplikace `CRecordView` nepodporuje tisk, `OnPrint` ale můžete přepsat členskou funkci a povolit tisk. Další informace naleznete v tématu [cformview](../mfc/reference/cformview-class.md)třídy .

Dokumenty a zobrazení pravděpodobně nebudete chtít používat vůbec. V takovém případě naleznete v tématu [Knihovna MFC: Použití tříd databáze bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Viz také

[Třídy databáze knihovny MFC](../data/mfc-database-classes-odbc-and-dao.md)
