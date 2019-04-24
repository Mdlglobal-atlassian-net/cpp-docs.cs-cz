---
title: Použití zobrazení záznamů (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
ms.openlocfilehash: 9d64fc26e1c78bad0431bc9b10dd5117c4866159
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152914"
---
# <a name="using-a-record-view--mfc-data-access"></a>Použití zobrazení záznamů (přístup k datům MFC)

Toto téma vysvětluje, jak může často přizpůsobit výchozí kód pro zobrazení záznamů, které průvodce zapíše za vás. Obvykle je vhodné omezit výběr záznamu [filtr](../data/odbc/recordset-filtering-records-odbc.md) nebo [parametry](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), možná [řazení](../data/odbc/recordset-sorting-records-odbc.md) záznamy, přizpůsobení příkazu SQL.

Pomocí `CRecordView` je skoro stejné jako při použití [CFormView](../mfc/reference/cformview-class.md). Základní přístupem je použití zobrazení záznamů pro zobrazení a případně k aktualizaci záznamů z jedné sady záznamů. Kromě toho můžete chtít použít jiné sady záznamů také, jak je popsáno v [zobrazení záznamů: Naplnění seznamu druhou sadou záznamů](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

## <a name="see-also"></a>Viz také:

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)