---
title: Použití zobrazení záznamu (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
ms.openlocfilehash: 611ddfd755eec84d4f2572a50c18802f988c5c3d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209024"
---
# <a name="using-a-record-view--mfc-data-access"></a>Použití zobrazení záznamu (přístup k datům MFC)

V tomto tématu se dozvíte, jak často můžete přizpůsobit výchozí kód pro zobrazení záznamů, které vám průvodce zapisuje. Obvykle chcete omezit výběr záznamů pomocí [filtru](../data/odbc/recordset-filtering-records-odbc.md) nebo [parametrů](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), možná [Seřadit](../data/odbc/recordset-sorting-records-odbc.md) záznamy, přizpůsobit příkaz SQL.

Použití `CRecordView` je mnohem stejné jako použití [CFormView](../mfc/reference/cformview-class.md). Základní přístup je použití zobrazení záznamu k zobrazení a možná aktualizace záznamů jedné sady záznamů. Kromě toho můžete chtít použít i jiné sady záznamů, jak je popsáno v tématu [zobrazení záznamů: vyplnění seznamu z druhé sady záznamů](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

## <a name="see-also"></a>Viz také

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)
