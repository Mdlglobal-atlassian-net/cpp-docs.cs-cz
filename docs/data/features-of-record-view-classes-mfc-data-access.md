---
title: Funkce záznamu zobrazení tříd (přístup k datům MFC) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 524fd0ac48c0f26f8621c074f5460e55d7690761
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074654"
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>Funkce tříd zobrazení záznamu (přístup k datům MFC)

Můžete provést programování založené na formulářích – přístup k datům s třídou [CFormView](../mfc/reference/cformview-class.md), ale [CRecordView](../mfc/reference/crecordview-class.md) je obecně lepší třídy odvozovat z. Kromě jeho `CFormView` funkce, `CRecordView`:

- Poskytuje výměna dat dialogových oken (DDX) mezi ovládací prvky formuláře a objekt přidružené sady záznamů.

- Zpracovává příkazy přesunout na první, přesunout na další, přesunout na předchozí a přesunout na poslední pro procházení záznamů v objektu přidružené sady záznamů.

- Když uživatel přesune na jiný záznam se aktualizace změní na aktuální záznam.

Další informace o navigaci v tématu [zobrazení záznamů: Podpora navigace v zobrazení záznamu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md).

## <a name="see-also"></a>Viz také

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)