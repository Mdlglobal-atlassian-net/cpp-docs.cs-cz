---
title: Obslužné rutiny příkazů pro posouvání záznamů (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 8bbacd6625e846381d2bafc8133e8b36efe51b1a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213444"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Obslužné rutiny příkazů pro posouvání záznamů (přístup k datům MFC)

Třída [CRecordView](../mfc/reference/crecordview-class.md) poskytuje výchozí zpracování příkazů pro následující standardní příkazy:

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

Členská funkce `OnMove` poskytuje výchozí zpracování příkazů pro všechny čtyři příkazy, které se pohybují ze záznamu na záznam. Jak jsou tyto příkazy vydány, RFX (nebo DFX) načte nový záznam do polí sady záznamů a DDX přesune hodnoty do ovládacích prvků formuláře záznamu. Informace o RFX naleznete v tématu [Výměna pole záznamu (RFX)](../data/odbc/record-field-exchange-rfx.md).

> [!NOTE]
>  Nezapomeňte použít tato standardní ID příkazů pro všechny objekty uživatelského rozhraní přidružené k standardním příkazům pro navigaci v záznamu.

## <a name="see-also"></a>Viz také

[Podpora navigace v zobrazení záznamu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
