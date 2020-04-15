---
title: Obslužné rutiny příkazů pro posouvání záznamů (přístup k datům knihovny MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 14ef845c3029f1d9a30d257f91c1b33017b6ec8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336932"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>Obslužné rutiny příkazů pro posouvání záznamů (přístup k datům knihovny MFC)

Třída [CRecordView](../mfc/reference/crecordview-class.md) poskytuje výchozí zpracování příkazů pro následující standardní příkazy:

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

Členská `OnMove` funkce poskytuje výchozí zpracování příkazů pro všechny čtyři příkazy, které se přesouvají ze záznamu na záznam. Při vydávání těchto příkazů načte RFX (nebo DFX) nový záznam do polí sady záznamů a DDX přesune hodnoty do ovládacích prvků formuláře záznamu. Informace o RFX naleznete v [tématu Record Field Exchange (RFX)](../data/odbc/record-field-exchange-rfx.md).

> [!NOTE]
> Ujistěte se, že tyto standardní ID příkazů použít pro všechny objekty uživatelského rozhraní spojené se standardními příkazy navigace záznamu.

## <a name="see-also"></a>Viz také

[Podpora navigace v zobrazení záznamů](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
