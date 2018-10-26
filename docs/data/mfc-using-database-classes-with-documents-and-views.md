---
title: 'MFC: Použití databázových tříd s dokumenty a zobrazeními | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 94dbb1b91d52a84172dabc635db6745109b8c4a4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059962"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: Použití databázových tříd s dokumenty a zobrazeními

MFC – databázové třídy můžete použít i bez architekturu document/view. Toto téma zvýrazňuje práci s dokumenty a zobrazeními. Vysvětluje:

- [Postup při psaní aplikace založené na formulářích](#_core_writing_a_form.2d.based_application) pomocí `CRecordView` objektu jako hlavní zobrazení v dokumentu.

- [Jak používat objekty sady záznamů v dokumentů a zobrazení](#_core_using_recordsets_in_documents_and_views).

- [Ostatní úvahy](#_core_other_factors).

Alternativy, naleznete v tématu [knihovny MFC: použití třídy databáze bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md).

##  <a name="_core_writing_a_form.2d.based_application"></a> Zápis aplikace založené na formulářích

Mnoho přístup k datům aplikací jsou založené na formulářích. Uživatelské rozhraní je formulář obsahující ovládací prvky, ve kterých uživatel prověří, zadá nebo upravuje data. Chcete-li vaše založené na formuláři aplikace, použijte třídu `CRecordView`. Když spustíte Průvodce aplikací knihovny MFC a vyberete **ODBC** typu klienta na **Podpora databáze** stránky, že projekt používá `CRecordView` pro danou třídu zobrazení.

V aplikaci založené na formulářích, každý objekt zobrazení záznamu ukládá ukazatel `CRecordset` objektu. V rámci pole záznamu (RFX) systému exchange Frameworku vyměňuje data mezi sady záznamů a zdrojem dat. Výměna dialogových dat (DDX) mechanismus výměnu dat mezi datové členy polí objekt sady záznamů a ovládacích prvků na formuláři. `CRecordView` také poskytuje výchozí funkce obslužné rutiny příkazů pro navigaci mezi záznam ve formuláři.

Vytvoření aplikace založené na formulářích pomocí Průvodce aplikací najdete v tématu [vytvoření aplikace MFC založené na formulářích](../mfc/reference/creating-a-forms-based-mfc-application.md) a [Podpora databáze, Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md).

Úplnou diskusi o formuláře, naleznete v tématu [zobrazení záznamů](../data/record-views-mfc-data-access.md).

##  <a name="_core_using_recordsets_in_documents_and_views"></a> Použití sad záznamů v dokumentů a zobrazení

Mnoho jednoduché aplikace založené na formulářích nemusí dokumenty. Pokud vaše aplikace je složitější, budete pravděpodobně chtít použít dokumentu jako proxy server pro databázi, ukládání `CDatabase` objekt, který se připojuje ke zdroji dat. Aplikace založené na formulářích obvykle ukládají ukazatel na objekt sady záznamů v zobrazení. Uložení sady záznamů jiných typů databázových aplikací a `CDatabase` objektu v dokumentu. Zde jsou některé možnosti pro práci s dokumenty v databázové aplikace:

- Při přístupu k sadě záznamů v rámci místní, vytvořit `CRecordset` objektu místně v členské funkce dokumentu nebo zobrazení, podle potřeby.

   Objekt sady záznamů deklarujte jako místní proměnná ve funkci. Předat hodnotu NULL do konstruktoru, což způsobí, že rozhraní k vytváření a otevírání dočasný `CDatabase` objekt za vás. Jako alternativu můžete předat ukazatel `CDatabase` objektu. Pomocí sady záznamů v rámci této funkce a ten automaticky zničeny při ukončení funkce.

   Při předání hodnoty NULL do konstruktoru sady záznamů rozhraní používá informace o vrácené sady záznamů `GetDefaultConnect` členské funkci, která vytvoří `CDatabase` objektu a otevřete ho. Průvodci implementují `GetDefaultConnect` za vás.

- Při přístupu k sadě záznamů po celou dobu životnosti dokumentu, vložit jeden nebo více `CRecordset` objektů v dokumentu.

   Objekty sady záznamů je možné vytvořte při inicializaci dokumentu nebo podle potřeby. Můžete například napsat funkci, která vrací ukazatel na sadu záznamů, pokud již existuje nebo vytvoří a otevře sadu záznamů, pokud ho ještě neexistuje. Zavřete, odstranit a podle potřeby znovu vytvořit sadu záznamů nebo volat jeho `Requery` členskou funkci k aktualizaci záznamů.

- Při přístupu ke zdroji dat po celou dobu životnosti dokumentu, vložení `CDatabase` objekt nebo ukazatel na ukládání `CDatabase` objektu v něm.

   `CDatabase` Spravuje připojení ke zdroji dat objektu. Objekt je vytvořen automaticky při vytváření dokumentu a volání jeho `Open` členské funkce při inicializaci dokumentu. Při vytváření objektů sady záznamů v dokumentu členské funkce předat ukazatel dokument `CDatabase` objektu. To spojí každá sada záznamů s jeho zdrojovými daty. Databázový objekt je zničen obvykle při zavření dokumentu. Objekty sady záznamů jsou obvykle zničeny, když opustí rozsah funkce.

##  <a name="_core_other_factors"></a> Další faktory

Aplikace založené na formulářích často nemají jakékoli použití pro mechanismus serializace v rámci dokumentu, proto je vhodné k odebrání, zakázání nebo nahradit **nový** a **otevřít** příkazy na **Souboru** nabídky. Přečtěte si článek [serializace: Serializace vs. Databáze vstupní a výstupní](../mfc/serialization-serialization-vs-database-input-output.md).

Můžete také provést mnoho možností uživatelského rozhraní, které může podporovat rozhraní framework. Například můžete použít více `CRecordView` objekty v okno s rozdělovačem, otevřete více sad záznamů v různých více dokumentů (MDI) interface podřízená okna a tak dále.

Může být potřeba implementovat tisk cokoli, co je v zobrazení, ať už jde o formulář implementuje pomocí `CRecordView` nebo něco jiného. Odvozené třídy z `CFormView`, `CRecordView` nemá nepodporuje tisk, ale můžete přepsat `OnPrint` členské funkce má povolit tisk. Další informace najdete v tématu třídy [CFormView](../mfc/reference/cformview-class.md).

Možná budete chtít vůbec používat dokumentů a zobrazení. V takovém případě naleznete v tématu [knihovny MFC: použití třídy databáze bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Viz také

[MFC – databázové třídy (.. / data/mfc-database-classes-odbc-and-dao.md)