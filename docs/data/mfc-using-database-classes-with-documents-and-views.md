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
ms.openlocfilehash: e2b073b20b9518667b43c30e7ee3199a84a3ad38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213379"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: Použití databázových tříd s dokumenty a zobrazeními

Můžete použít třídy databáze knihovny MFC s architekturou Document/View nebo bez ní. Toto téma zvýrazňuje práci s dokumenty a zobrazeními. Vysvětluje:

- [Zápis aplikace založené na formulářích](#_core_writing_a_form.2d.based_application) pomocí objektu `CRecordView` jako hlavního zobrazení dokumentu.

- [Jak používat objekty sady záznamů ve svých dokumentech a zobrazeních](#_core_using_recordsets_in_documents_and_views).

- [Další požadavky](#_core_other_factors).

Pro alternativy viz [MFC: použití databázových tříd bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md).

##  <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>Zápis aplikace založené na formulářích

Řada aplikací pro přístup k datům je založena na formulářích. Uživatelské rozhraní je formulář obsahující ovládací prvky, ve kterých uživatel prověřuje, zadá nebo upravuje data. Chcete-li vytvořit formulář aplikace na základě, použijte třídu `CRecordView`. Když spustíte Průvodce aplikací knihovny MFC a vyberete typ klienta **rozhraní ODBC** na stránce **Podpora databáze** , projekt používá `CRecordView` pro třídu zobrazení.

V aplikaci založené na formulářích ukládá každý objekt zobrazení záznamu ukazatel na objekt `CRecordset`. Mechanismus výměny pole záznamu (RFX) rozhraní vyměňuje data mezi sadou záznamů a zdrojem dat. Mechanismus pro výměnu dat dialogových oken (DDX) vyměňuje data mezi datovými členy objektu Recordset a ovládacími prvky ve formuláři. `CRecordView` také nabízí výchozí obslužné rutiny příkazu pro navigaci ze záznamu na záznam ve formuláři.

Chcete-li vytvořit formulářovou aplikaci pomocí Průvodce aplikací, přečtěte si téma [Vytvoření aplikace MFC založené na formulářích](../mfc/reference/creating-a-forms-based-mfc-application.md) a [Podpora databáze, Průvodce aplikací MFC](../mfc/reference/database-support-mfc-application-wizard.md).

Úplnou diskuzi o formulářích naleznete v tématu [zobrazení záznamů](../data/record-views-mfc-data-access.md).

##  <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>Použití sad záznamů v dokumentech a zobrazeních

Mnohé jednoduché aplikace založené na formulářích nepotřebují dokumenty. Pokud je vaše aplikace složitější, budete pravděpodobně chtít použít dokument jako proxy databáze a uložit objekt `CDatabase`, který se připojuje ke zdroji dat. Formulářové aplikace obvykle ukládají ukazatel na objekt sady záznamů v zobrazení. Jiné druhy databázových aplikací ukládají sady záznamů a objekt `CDatabase` v dokumentu. Tady je několik možností použití dokumentů v databázových aplikacích:

- Pokud přistupujete k sadě záznamů v místním kontextu, vytvořte objekt `CRecordset` lokálně v členských funkcích dokumentu nebo zobrazení podle potřeby.

   Deklarujte objekt sady záznamů jako místní proměnnou ve funkci. Předat hodnotu NULL konstruktoru, který způsobí, že rozhraní vytvoří a otevře dočasný objekt `CDatabase` za vás. Jako alternativu předejte ukazatel na objekt `CDatabase`. Použijte sadu záznamů v rámci funkce a umožněte její zničení automaticky při ukončení funkce.

   Při předání hodnoty NULL konstruktoru sady záznamů používá rozhraní informace vrácené členskou funkcí `GetDefaultConnect` sady záznamů k vytvoření objektu `CDatabase` a jeho otevření. Průvodci implementují `GetDefaultConnect` za vás.

- Pokud přistupujete k sadě záznamů během životnosti dokumentu, vložte jeden nebo více `CRecordset` objektů do dokumentu.

   Sestavte objekty sady záznamů buď při inicializaci dokumentu, nebo podle potřeby. Můžete napsat funkci, která vrátí ukazatel na sadu záznamů, pokud již existuje, nebo vytvořit a otevřít sadu záznamů, pokud ještě neexistuje. Zavřete, odstraňte a znovu vytvořte sadu záznamů podle potřeby, nebo zavolejte jeho členskou funkci `Requery` pro aktualizaci záznamů.

- Pokud přistupujete ke zdroji dat během životnosti dokumentu, vložte objekt `CDatabase` nebo uložte ukazatel na objekt `CDatabase` v něm.

   Objekt `CDatabase` spravuje připojení ke zdroji dat. Objekt je vytvořen automaticky během vytváření dokumentu a při inicializaci dokumentu voláte jeho `Open` členskou funkci. Při vytváření objektů sady záznamů v členských funkcích dokumentu předáte ukazatel na objekt `CDatabase` dokumentu. Tím spojíte každou sadu záznamů se zdrojem dat. Databázový objekt je obvykle zničen při zavření dokumentu. Objekty sady záznamů jsou obvykle zničeny při opuštění oboru funkce.

##  <a name="other-factors"></a><a name="_core_other_factors"></a>Jiné faktory

Formulářové aplikace často nemají žádné použití pro mechanizmus serializace dokumentu rozhraní, takže možná budete chtít odebrat, zakázat nebo nahradit **nové** a **otevřené** příkazy v nabídce **soubor** . Viz článek [serializace: serializace vs. vstup/výstup databáze](../mfc/serialization-serialization-vs-database-input-output.md).

Můžete také využít mnoho možností uživatelského rozhraní, které může architektura podporovat. Můžete například použít více objektů `CRecordView` v okně s rozdělovačem, otevřít více sad záznamů v různých podřízených oknech MDI (Multiple Document Interface) a tak dále.

Je možné, že budete chtít implementovat tisk bez ohledu na to, jestli se jedná o formulář implementovaný pomocí `CRecordView` nebo něco jiného. Jako třídy odvozené od `CFormView``CRecordView` nepodporuje tisk, ale můžete přepsat `OnPrint` členské funkce pro povolení tisku. Další informace naleznete v tématu Třída [CFormView](../mfc/reference/cformview-class.md).

Možná nebudete chtít používat dokumenty a zobrazení vůbec. V takovém případě viz [MFC: použití databázových tříd bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Viz také

[MFC – databázové třídy](../data/mfc-database-classes-odbc-and-dao.md)
