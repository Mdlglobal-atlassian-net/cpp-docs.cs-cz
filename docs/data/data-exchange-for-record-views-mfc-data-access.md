---
title: Výměna dat pro zobrazení záznamů (přístup k datům MFC)
ms.date: 11/19/2018
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: f9f460305b55a2313b64effdf4d1dbbfd9823def
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213466"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Výměna dat pro zobrazení záznamů (přístup k datům MFC)

Použijete-li [Přidat třídu](../mfc/reference/adding-an-mfc-odbc-consumer.md) pro mapování ovládacích prvků v dialogovém okně šablony zobrazení záznamu na pole sady záznamů, rozhraní spravuje výměnu dat v obou směrech – ze sady záznamů do ovládacích prvků a z ovládacích prvků do sady záznamů. Použití DDX mechanismu znamená, že nemusíte psát kód pro přenos dat sami a zpátky.

DDX pro zobrazení záznamů funguje ve spojení s [RFX](../data/odbc/record-field-exchange-rfx.md) pro sady záznamů třídy `CRecordset` (ODBC).  RFX přesouvá data mezi aktuálním záznamem zdroje dat a poli datových členů objektu sady záznamů. DDX přesune data z datových členů pole do ovládacích prvků ve formuláři. Tato kombinace zpočátku naplní ovládací prvky formuláře a uživatel přejde ze záznamu na záznam. Může také přesunout aktualizovaná data zpět do sady záznamů a následně do zdroje dat.

Následující obrázek znázorňuje vztah mezi DDX a RFX pro zobrazení záznamů.

![Výměna&#45;dat dialogových oken&#45;a výměna pole záznamu](../data/media/vc37xt1.gif "Výměna&#45;dat dialogových oken&#45;a výměna pole záznamu")<br/>
Výměna dat dialogových oken a výměna pole záznamu

Další informace o DDX naleznete v tématu [Výměna a ověřování dat dialogových oken](../mfc/dialog-data-exchange-and-validation.md). Další informace o RFX naleznete v tématu [Výměna pole záznamu (RFX)](../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Viz také

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)
