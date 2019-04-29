---
title: Funkce tříd zobrazení záznamu (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
ms.openlocfilehash: 5f8de956065571109c988bd2940d21822bba7cfd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397949"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Funkce tříd zobrazení záznamu (přístup k datům MFC)

Můžete provést programování založené na formulářích – přístup k datům s třídou [CFormView](../mfc/reference/cformview-class.md), ale [CRecordView](../mfc/reference/crecordview-class.md) je obecně lepší třídy odvozovat z. Kromě jeho `CFormView` funkce, `CRecordView`:

- Poskytuje výměna dat dialogových oken (DDX) mezi ovládací prvky formuláře a objekt přidružené sady záznamů.

- Zpracovává příkazy přesunout na první, přesunout na další, přesunout na předchozí a přesunout na poslední pro procházení záznamů v objektu přidružené sady záznamů.

- Když uživatel přesune na jiný záznam se aktualizace změní na aktuální záznam.

Další informace o navigaci v tématu [zobrazení záznamů: Podpora navigace v zobrazení záznamu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Viz také:

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)