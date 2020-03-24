---
title: Vaše role při práci se zobrazením záznamu (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
ms.openlocfilehash: 351aa2d5ce950017aa8c1b3d99c8d297a423ad9f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208998"
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Vaše role při práci se zobrazením záznamu (přístup k datům MFC)

Následující tabulka ukazuje, co se obvykle provádí pro práci se zobrazením záznamů a k čemu pro vás architektura.

### <a name="working-with-a-record-view-you-and-the-framework"></a>Práce se zobrazením záznamu: vy a rozhraní

|Vy|Rozhraní .NET Framework|
|---------|-------------------|
|Pro návrh formuláře C++ použijte Editor dialogových oken Visual.|Vytvoří prostředek šablony dialogového okna s ovládacími prvky.|
|Pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md) vytvořte třídy odvozené z [CRecordView](../mfc/reference/crecordview-class.md) a [CRecordset](../mfc/reference/crecordset-class.md).|Zapisuje třídy za vás.|
|Ovládací prvky zobrazení záznamu mapování na datové členy pole sady záznamů.|Poskytuje DDX mezi ovládacími prvky a poli sady záznamů.|
||Poskytuje výchozí obslužné rutiny příkazů pro příkaz **Přesunout první**, **Přesunout poslední**, **přesunout na další**a **přesunout předchozí** příkazy z nabídek nebo tlačítek na panelu nástrojů.|
||Aktualizuje změny ve zdroji dat.|
|Volitelné Napíšete kód, který vyplní pole seznamu nebo pole se seznamem nebo jiné ovládací prvky s daty z druhé sady záznamů.||
|Volitelné Napište kód pro jakékoli zvláštní ověřování.||
|Volitelné Napíšete kód pro přidání nebo odstranění záznamů.||

Programování založené na formulářích je pouze jedním z přístupů k práci s databází. Informace o aplikacích, které používají jiné uživatelské rozhraní nebo žádné uživatelské rozhraní, naleznete v tématu [MFC: použití databázových tříd s dokumenty a zobrazeními](../data/mfc-using-database-classes-with-documents-and-views.md) a [MFC: použití databázových tříd bez dokumentů a zobrazení](../data/mfc-using-database-classes-without-documents-and-views.md). Alternativní přístupy k zobrazení záznamů databáze naleznete v tématu třídy [CListView –](../mfc/reference/clistview-class.md) a [CTreeView –](../mfc/reference/ctreeview-class.md).

## <a name="see-also"></a>Viz také

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)
