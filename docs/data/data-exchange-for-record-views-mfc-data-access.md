---
title: Výměna dat pro zobrazení záznamů (přístup k datům MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: d3b1c5b997baa0938c532c7a2806d5e65eb125a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546463"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Výměna dat pro zobrazení záznamů (přístup k datům MFC)

Při použití [přidat třídu](../mfc/reference/adding-an-mfc-odbc-consumer.md) do mapování ovládacích prvků v prostředku šablony dialogového okna zobrazení záznamu na pole sady záznamů, že rozhraní spravuje výměny dat v obou směrech – ze záznamů pro ovládací prvky a z ovládacích prvků do sady záznamů. Pomocí mechanismu DDX znamená, že není potřeba psát kód pro přenos dat vpřed a zpět, sami.

DDX pro zobrazení záznamu funguje ve spojení s [RFX](../data/odbc/record-field-exchange-rfx.md) pro sady záznamů třídy `CRecordset` (ODBC).  RFX přesouvá data mezi aktuální záznam zdroje dat a datové členy polí objektu sady záznamů. DDX přesouvá data z datové členy polí na ovládací prvky ve formuláři. Tato kombinace vyplní ovládací prvky formuláře zpočátku a jak se uživatel přesune mezi záznamy. Může to také přesunout aktualizovaná data zpět do sady záznamů a poté ke zdroji dat.

Následující obrázek ukazuje vztah mezi DDX a funkce RFX pro zobrazení záznamů.

![Dialogové okno&#45;výměny dat a záznam&#45;pole exchange](../data/media/vc37xt1.gif "vc37xt1")<br/>
Výměna dat dialogových oken a výměna pole záznamu

Další informace o rozhraní DDX najdete v tématu [výměna dat dialogových oken a ověření](../mfc/dialog-data-exchange-and-validation.md). Další informace o RFX najdete v tématu [výměna pole záznamu (RFX)](../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Viz také

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)