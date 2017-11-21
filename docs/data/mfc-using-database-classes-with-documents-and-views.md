---
title: "MFC: Použití databázových tříd s dokumenty a zobrazeními | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b63e864b519dd55eedf96d525a25897c81f16ac0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: Použití databázových tříd s dokumenty a zobrazeními
Databázové třídy MFC můžete použít s nebo bez architektuře dokument/zobrazení. Toto téma klade důraz práce s dokumenty a zobrazení. Vysvětluje:  
  
-   [Tom, jak psát aplikace založené na formulářích](#_core_writing_a_form.2d.based_application) pomocí `CRecordView` objektu jako hlavní zobrazení v dokumentu.  
  
-   [Jak používat objekty sady záznamů ve své dokumenty a zobrazení](#_core_using_recordsets_in_documents_and_views).  
  
-   [Další důležité informace](#_core_other_factors).  
  
 Alternativy naleznete v tématu [MFC: použití třídy databáze bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
##  <a name="_core_writing_a_form.2d.based_application"></a>Zápis k aplikaci založené na formulářích  
 Mnoho aplikací přístup k datům jsou založené na formulářích. Uživatelské rozhraní je formulář obsahující ovládací prvky, ve kterých uživatel prověří, zadá nebo upravuje data. Aby aplikace formulář na základě použití třídy `CRecordView`. Po spuštění Průvodce aplikací knihovny MFC a vyberte **ODBC** typ klienta na **podpory databáze** stránka, projektu používá `CRecordView` pro třídu zobrazení.
  
 V aplikaci založené na formulářích, každý objekt zobrazení záznamu ukládá ukazatel na `CRecordset` objektu. V rámci pole záznamu (exchange – RFX) Frameworku výměny dat mezi sady záznamů a zdroj dat. Výměna dialogových dat (DDX) mechanismus výměnu dat mezi pole datových členů objektu sady záznamů a ovládací prvky na formuláři. `CRecordView`také poskytuje výchozí funkce obslužné rutiny příkazů pro navigaci mezi záznamy na formuláři.  
  
 Vytvoření aplikace založené na formulářích pomocí Průvodce aplikací, najdete v části [vytváření aplikací MFC založených na formulářích](../mfc/reference/creating-a-forms-based-mfc-application.md) a [Podpora databáze, Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
 Úplné informace o formulářích, najdete v části [zobrazení záznamů](../data/record-views-mfc-data-access.md).  
  
##  <a name="_core_using_recordsets_in_documents_and_views"></a>Použití sad záznamů v dokumentů a zobrazení  
 Mnoho jednoduché aplikace založené na formulářích nemusí dokumenty. Pokud vaše aplikace je složitější, budete pravděpodobně chtít použít dokument jako proxy server pro databázi, ukládání `CDatabase` objekt, který se připojuje ke zdroji dat. Aplikace založené na formulářích obvykle ukládají ukazatel na objekt sady záznamů v zobrazení. Jiné druhy databázových aplikací uložení sady záznamů a `CDatabase` objektu v dokumentu. Zde jsou některé možnosti pro použití v databázových aplikacích dokumentů:  
  
-   Pokud se připojujete záznamů v místní kontextu, vytvořte `CRecordset` objekt místně v členské funkce dokumentu nebo zobrazení, podle potřeby.  
  
     Objekt sady záznamů deklarujte jako místní proměnné ve funkci. Předat **NULL** do konstruktoru, což způsobí, že rozhraní k vytváření a otevírání dočasného `CDatabase` objektu za vás. Jako alternativu můžete předat ukazatel `CDatabase` objektu. Pomocí sady záznamů v rámci funkce a nechte jej ukončit automaticky při ukončení funkce.  
  
     Pokud předáte **NULL** do konstruktoru sady záznamů rozhraní používá informace vrácené sady záznamů `GetDefaultConnect` – členská funkce k vytvoření `CDatabase` objektu a otevřete ji. Průvodci implementují `GetDefaultConnect` za vás.  
  
-   Pokud přistupujete k sadě záznamů během platnosti dokumentu, vložte jeden nebo více `CRecordset` objekty v dokumentu.  
  
     Při inicializaci dokumentu nebo podle potřeby vytvořte objekty sady záznamů. Můžete napsat funkci, která vrací ukazatel na sadu záznamů, pokud již existuje nebo vytvoří a otevře sadu záznamů, pokud není ještě neexistuje. Zavřete, odstranit a znovu vytvořit sadu záznamů podle potřeby nebo volání jeho **Requery –** – členská funkce k aktualizaci záznamů.  
  
-   Při přístupu ke zdroji dat během platnosti dokumentu, Vložit `CDatabase` objektu nebo uložte ukazatel `CDatabase` objektu v ní.  
  
     `CDatabase` Připojení ke zdroji dat spravuje objektu. Objekt je automaticky vytvořen během vytváření dokumentu a volání jeho **otevřete** – členská funkce při inicializaci dokumentu. Když vytváříte objekty sady záznamů v dokumentu členské funkce, předáte ukazatel v dokumentu `CDatabase` objektu. To přidruží zdrojem dat pro každou sadu záznamů. Objekt databáze je obvykle zničen při zavření dokumentu. Objekty sady záznamů jsou obvykle zničený, když opustí rozsah funkce.  
  
##  <a name="_core_other_factors"></a>Další faktory  
 Aplikace založené na formulářích často nemají jakékoli použití pro rozhraní framework mechanismu serializace dokumentu, takže můžete chtít odebrat, zakázat nebo nahradit `New` a **otevřete** příkazy **soubor**nabídky. Najdete v článku [serializace: Serializace vs. Databáze vstupu a výstupu](../mfc/serialization-serialization-vs-database-input-output.md).  
  
 Můžete také provést použití mnoha možnosti uživatelského rozhraní, které podporují rozhraní. Například můžete použít více `CRecordView` objektů v rozděleném okně, otevřete více sad záznamů v různých více dokumentů (MDI) rozhraní podřízená okna a tak dále.  
  
 Můžete chtít implementovat tisk bez ohledu zobrazení, jestli je implementováno formuláře s `CRecordView` nebo něco jiného. Odvozené třídy z `CFormView`, `CRecordView` nemá nepodporuje tisk, ale můžete přepsat `OnPrint` – členská funkce má povolit tisk. Další informace najdete v tématu třídy [CFormView](../mfc/reference/cformview-class.md).  
  
 Možná budete chtít vůbec používat dokumentů a zobrazení. V takovém případě najdete v části [MFC: použití třídy databáze bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
## <a name="see-also"></a>Viz také  
 [Třídami databází MFC (.. / data/mfc-database-classes-odbc-and-dao.md)