---
title: Návrh a vytváření zobrazení záznamů (přístup k datům MFC) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- designing forms
- record views, creating
- forms [C++], designing
- record views, designing
- application wizards [C++], creating record view classes
- designing record views
ms.assetid: 1d6f5439-754f-4b8b-a19d-841a4657827b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c03b85538a795142f5085c93df3a60f4c60481ab
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065847"
---
# <a name="designing-and-creating-a-record-view--mfc-data-access"></a>Návrh a vytváření zobrazení záznamů (přístup k datům MFC)

Můžete vytvořit vaší třídy zobrazení záznamu s [Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md). Pokud použijete Průvodce aplikací, vytvoří tříd zobrazení záznamu a prostředku šablony dialogového okna pro něj (bez ovládací prvky). Přidání ovládacích prvků do šablony prostředku dialogového okna, je nutné použít editor dialogového okna Visual C++. Na druhou stranu, pokud používáte **přidat třídu**, musíte nejprve vytvořit prostředku šablony dialogového okna v okně editor a pak vytvořte tříd zobrazení záznamu.

#### <a name="to-create-your-record-view-with-the-mfc-application-wizard"></a>Chcete-li vytvořit zobrazení záznamu pomocí Průvodce aplikací MFC

1. Zobrazit [Podpora databáze, Průvodce aplikací knihovny MFC](../mfc/reference/database-support-mfc-application-wizard.md).

#### <a name="to-design-your-form"></a>Návrh formuláře

1. Zobrazit [editoru dialogového okna](../windows/dialog-editor.md).

#### <a name="to-create-your-record-view-class"></a>Chcete-li vytvořit třídu zobrazení záznamu

1. Zobrazit [přidání příjemce ODBC knihovny MFC](../mfc/reference/adding-an-mfc-odbc-consumer.md).

Následující témata vysvětlují, další podrobnosti o použití zobrazení záznamů:

- [Zobrazení záznamů: Podpora navigace v zobrazení záznamu](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)

- [Zobrazení záznamu: Použití zobrazení záznamů](../data/using-a-record-view-mfc-data-access.md)

- [Zobrazení záznamů: Naplnění seznamu druhou sadou záznamů](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)

## <a name="see-also"></a>Viz také

[Zobrazení záznamů (přístup k datům MFC)](../data/record-views-mfc-data-access.md)<br/>
[Sada záznamů (ODBC)](../data/odbc/recordset-odbc.md)<br/>
[Seznam ovladačů ODBC](../data/odbc/odbc-driver-list.md)