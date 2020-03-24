---
title: Zobrazení záznamů (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], record views
- ODBC recordsets [C++], record views
- databases [C++], record views
- record views [C++]
- forms [C++], data access tasks
ms.assetid: 562122d9-01d8-4284-acf6-ea109ab0408d
ms.openlocfilehash: 31dbd92219f263c625050524279b97ef38ba9ba1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209128"
---
# <a name="record-views--mfc-data-access"></a>Zobrazení záznamů (přístup k datům MFC)

Tato část se vztahuje pouze na třídy knihovny MFC rozhraní ODBC. Informace o OLE DB zobrazení záznamů naleznete v tématu [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) a [using OLE DB Record views](../data/oledb/using-ole-db-record-views.md).

Pro podporu formulářové aplikace pro přístup k datům poskytuje knihovna tříd třídu [CRecordView](../mfc/reference/crecordview-class.md). Zobrazení záznamu je objekt zobrazení formuláře, jehož ovládací prvky jsou mapovány přímo k poli datových členů objektu [Recordset](../data/odbc/recordset-odbc.md) (a nepřímo k odpovídajícím sloupcům ve výsledku dotazu nebo tabulce ve zdroji dat). Podobně jako jeho základní třída [CFormView](../mfc/reference/cformview-class.md)je `CRecordView` založena na prostředku šablony dialogového okna.

## <a name="form-uses"></a>Formulář používá

Formuláře jsou užitečné pro nejrůznější úlohy přístupu k datům:

- Zadávání dat

- Provádění zkoumání dat jen pro čtení

- Aktualizace dat

## <a name="further-reading-about-record-views"></a>Další informace o zobrazení záznamů

Materiály v tématech se vztahují na třídy založené na rozhraní ODBC i na rozhraní DAO. Pro rozhraní DAO použijte `CRecordView` pro rozhraní ODBC a `CDaoRecordView`.

Témata:

- [Funkce tříd zobrazení záznamu](../data/features-of-record-view-classes-mfc-data-access.md)

- [Výměna dat pro zobrazení záznamů](../data/data-exchange-for-record-views-mfc-data-access.md)

- [Vaše role při práci se zobrazením záznamu](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)

- [Návrh a vytvoření zobrazení záznamu](../data/designing-and-creating-a-record-view-mfc-data-access.md)

- [Používání zobrazení záznamu](../data/using-a-record-view-mfc-data-access.md)

## <a name="see-also"></a>Viz také

[Programování přístupu k datům (MFC/ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)
