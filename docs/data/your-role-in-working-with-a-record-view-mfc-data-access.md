---
title: Vaše Role při práci se zobrazením záznamu (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
ms.openlocfilehash: 1f1361baafa5bb3dc884adcc464a3571aee04dd3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478634"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Vaše Role při práci se zobrazením záznamu (přístup k datům MFC)

Následující tabulka uvádí, co je obvykle nutné udělat pro práci se zobrazením záznamu a rozhraní udělá za vás.

### <a name="working-with-a-record-view-you-and-the-framework"></a>Práce se zobrazením záznamu: jste a rozhraní

|Vy|Rozhraní framework|
|---------|-------------------|
|Použití editoru dialogových oken Visual C++ pro návrh formuláře.|Vytvoří prostředek šablony dialogového okna s ovládacími prvky.|
|Použití [Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md) vytvoření třídy odvozené od [CRecordView](../mfc/reference/crecordview-class.md) a [CRecordset](../mfc/reference/crecordset-class.md).|Zapíše třídy za vás.|
|Mapování ovládací prvky zobrazení záznamu na pole data členů sady záznamů.|Poskytuje DDX mezi ovládacích prvků a polí záznamů.|
||Poskytuje výchozí obslužné rutiny příkazů pro **přesunout na první**, **přesunout na poslední**, **přesunout na další**, a **přesunout na předchozí** příkazy z nabídky nebo panelu nástrojů tlačítka.|
||Aktualizace změny do zdroje dat.|
|[Volitelné] Napište kód k vyplnění pole se seznamem nebo polí se seznamem nebo další ovládací prvky s daty z druhé sady záznamů.||
|[Volitelné] Napište kód pro žádné zvláštní ověření.||
|[Volitelné] Napsání kódu pro přidání nebo odstranění záznamů.||

Programování založené na formulářích je pouze jedním z přístupů k práci s databází. Informace o aplikacích pomocí některé jiné uživatelské rozhraní nebo žádné uživatelské rozhraní, naleznete v tématu [knihovny MFC: použití databázových tříd s dokumenty a zobrazeními](../data/mfc-using-database-classes-with-documents-and-views.md) a [knihovny MFC: použití třídy databáze bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md). Alternativní přístupy k zobrazení záznamů v databázi, naleznete v tématu třídy [CListView](../mfc/reference/clistview-class.md) a [CTreeView](../mfc/reference/ctreeview-class.md).

## <a name="see-also"></a>Viz také

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)