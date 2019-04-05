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
ms.openlocfilehash: e50c433e701fbae2e607d79d7abb34efe8eba5b5
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033745"
---
# <a name="displaying-and-manipulating-data-in-a-form"></a>Zobrazení dat ve formuláři a manipulace s nimi

Mnoho aplikací přístup k datům vyberte data a zobrazit je pole ve formuláři. Třída database [CRecordView](../../mfc/reference/crecordview-class.md) vám [CFormView](../../mfc/reference/cformview-class.md) objektu přímo připojen k objektu sady záznamů. Zobrazení záznamu používá [výměna dat dialogových oken (DDX)](../../mfc/dialog-data-exchange-and-validation.md) přesunout hodnoty polí aktuální záznam ze záznamů pro ovládací prvky ve formuláři a přesuňte aktualizované informace zpět do sady záznamů. Sady záznamů pro přesun dat mezi její datové členy a odpovídající sloupce v tabulce ve zdroji dat. pak dále používá výměna pole záznamu (RFX).

Můžete použít Průvodce aplikací knihovny MFC nebo **přidat třídu** (jak je popsáno v [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) Chcete-li vytvořit třídu zobrazení a jeho přidružené třídy sady záznamů ve spojení.

Zobrazení záznamu a jeho sady záznamů jsou zničeny při zavření dokumentu. Další informace o zobrazení záznamů najdete v tématu [zobrazení záznamů](../../data/record-views-mfc-data-access.md). Další informace o RFX najdete v tématu [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Viz také:

[Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)