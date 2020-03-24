---
title: Funkce tříd zobrazení záznamu (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 62597a3eb3f7a7e779ca57c9781565176df568d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213431"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Funkce tříd zobrazení záznamu (přístup k datům MFC)

Můžete provádět programování pro přístup k datům na základě formulářů s třídou [CFormView](../mfc/reference/cformview-class.md), ale [CRecordView](../mfc/reference/crecordview-class.md) je všeobecně lepší třídou odvozenou od. Kromě funkcí `CFormView` `CRecordView`:

- Poskytuje výměnu dat dialogových oken (DDX) mezi ovládacími prvky formuláře a přidruženým objektem sady záznamů.

- Obslužné rutiny se přesunou jako první, přesunout další, přesunout předchozí a přesunout poslední příkazy pro procházení záznamů v přidruženém objektu sady záznamů.

- Aktualizuje změny aktuálního záznamu, když se uživatel přesune na jiný záznam.

Další informace o navigaci naleznete v tématu [zobrazení záznamů: podpora navigace v zobrazení záznamu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Viz také

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)
