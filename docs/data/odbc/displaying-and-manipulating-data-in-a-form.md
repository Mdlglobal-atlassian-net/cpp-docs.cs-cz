---
title: Zobrazení dat ve formuláři a manipulace s nimi
ms.date: 11/04/2016
helpviewer_keywords:
- forms [C++], displaying data
- displaying data [C++], forms
- ODBC [C++], forms
- record views [C++], displaying data
- data [MFC]
- data [MFC], displaying in a form
ms.assetid: c56185c4-12cb-40b1-b499-02b29ea83e3a
ms.openlocfilehash: 6b663fabd0c87d9a2773e6f5a2796bcc8f57ce29
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213249"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Zobrazení dat ve formuláři a manipulace s nimi

Mnoho aplikací pro přístup k datům vybere data a zobrazí je v polích ve formuláři. Třída Database [CRecordView](../../mfc/reference/crecordview-class.md) poskytuje objekt [CFormView](../../mfc/reference/cformview-class.md) přímo připojený k objektu sady záznamů. Zobrazení záznamu používá [výměnu dat dialogových oken (DDX)](../../mfc/dialog-data-exchange-and-validation.md) k přesunutí hodnot polí aktuálního záznamu ze sady záznamů do ovládacích prvků ve formuláři a k přesunutí aktualizovaných informací zpět do sady záznamů. Sada záznamů zase používá výměnu pole záznamu (RFX) k přesunu dat mezi poli datových členů a odpovídajících sloupců v tabulce ve zdroji dat.

Můžete použít Průvodce aplikací knihovny MFC nebo **Přidat třídu** (jak je popsáno v tématu [Přidání příjemce knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) k vytvoření třídy zobrazení a její přidružené třídy sady záznamů ve spojení.

Zobrazení záznamu a jeho sada záznamů jsou zničeny při zavření dokumentu. Další informace o zobrazení záznamů naleznete v tématu [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Další informace o RFX naleznete v tématu [Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Viz také

[Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)
