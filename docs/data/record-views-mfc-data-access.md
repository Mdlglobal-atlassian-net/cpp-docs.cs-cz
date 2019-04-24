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
ms.openlocfilehash: 199f51f20dd42ee9105b4e09f579c1f48948745f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161365"
---
# <a name="record-views--mfc-data-access"></a>Zobrazení záznamů (přístup k datům MFC)

Tato část platí jenom pro třídy knihovny MFC rozhraní ODBC. Informace o zobrazení záznamů technologie OLE DB najdete v tématu [COleDBRecordView](../mfc/reference/coledbrecordview-class.md) a [pomocí OLE DB zobrazení záznamů](../data/oledb/using-ole-db-record-views.md).

Podpora aplikací založené na formulářích – přístup k datům, knihovny tříd poskytuje třída [CRecordView](../mfc/reference/crecordview-class.md). Zobrazení záznamů je objekt zobrazení formuláře, jehož ovládací prvky, mapují přímo na pole datové členy [záznamů](../data/odbc/recordset-odbc.md) objektu (a nepřímo odpovídající sloupce ve výsledku dotazu nebo tabulky zdroje dat). Její základní třídě, jako jsou [CFormView](../mfc/reference/cformview-class.md), `CRecordView` je založen na šabloně prostředek dialogového okna.

## <a name="form-uses"></a>Formulář používá

Formuláře jsou užitečné pro řadu úloh přístup k datům:

- Zadávání dat

- Provádí se ověření dat jen pro čtení

- Aktualizace dat

## <a name="further-reading-about-record-views"></a>Další informace o zobrazení záznamů

Materiál témata se vztahuje na základě rozhraní ODBC a třídy založené na rozhraní DAO. Použití `CRecordView` pro rozhraní ODBC a `CDaoRecordView` pro rozhraní DAO.

Mezi témata patří:

- [Funkce tříd zobrazení záznamu](../data/features-of-record-view-classes-mfc-data-access.md)

- [Výměna dat pro zobrazení záznamů](../data/data-exchange-for-record-views-mfc-data-access.md)

- [Vaše Role při práci se zobrazením záznamu](../data/your-role-in-working-with-a-record-view-mfc-data-access.md)

- [Návrh a vytváření zobrazení záznamů](../data/designing-and-creating-a-record-view-mfc-data-access.md)

- [Použití zobrazení záznamů](../data/using-a-record-view-mfc-data-access.md)

## <a name="see-also"></a>Viz také:

[Přístup k datům programování knihovny MFC nebo ATL)](../data/data-access-programming-mfc-atl.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)