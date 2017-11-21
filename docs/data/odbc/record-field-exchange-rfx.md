---
title: "Zaznamenejte pole (Exchange – RFX) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RFX (ODBC) [C++]
- data [MFC], moving between sources and recordsets
- database classes [C++], RFX
- data [MFC]
- ODBC [C++], RFX
ms.assetid: f5ddfbf0-2901-48d7-9848-4fb84de3c7ee
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6494773de5bd64e66c2031a618d7a8d899215c2d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="record-field-exchange-rfx"></a>Výměna pole záznamu (Record Field Exchange – RFX)
Databázové třídy MFC rozhraní ODBC automatizují přesunutí dat mezi zdroji dat a [sada záznamů](../../data/odbc/recordset-odbc.md) objektu. Pokud odvodíte třídu od [CRecordset](../../mfc/reference/crecordset-class.md) a nepoužívejte hromadné načítání řádků, data se přenáší přes mechanismus pole záznamu (exchange – RFX).  
  
> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků v odvozené `CRecordset` třídu rozhraní používá mechanismus exchange (Bulk RFX) pole záznamu k přenosu dat. Další informace najdete v tématu [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 RFX je podobná výměna dialogových dat (DDX). Přesun dat mezi zdrojem dat a pole datových členů sady záznamů vyžaduje několik volání do sady záznamů [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) funkce a značnou interakci mezi rozhraní a [ODBC](../../data/odbc/odbc-basics.md). Mechanismus RFX je bezpečnost typů a uloží je práci při volání funkcí rozhraní ODBC, jako **:: SQLBindCol**. Další informace o rozhraní DDX najdete v tématu [výměna dialogových dat a ověření](../../mfc/dialog-data-exchange-and-validation.md).  
  
 RFX je ve většině případů transparentní pro vás. Pokud je vaše třídy sady záznamů pomocí Průvodce aplikací MFC deklarovat nebo **přidat třídu** (jak je popsáno v [přidání příjemce rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)), je do nich RFX sestaveno automaticky. Třídu sady záznamů musí být odvozen od základní třídy `CRecordset` poskytl rozhraní. Průvodce aplikací MFC umožňuje vytvořit třídu počáteční sady záznamů. **Přidání třídy** můžete přidat další třídy sada záznamů je podle potřeby. Další informace a příklady naleznete v tématu [přidání příjemce rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Je třeba ručně přidat malé množství RFX kódu ve třech případech, pokud chcete:  
  
-   Použití parametrických dotazů. Další informace najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
-   Provedení spojení (použití jedné sady záznamů pro sloupce ze dvou nebo více tabulek). Další informace najdete v tématu [sada záznamů: provedení připojení (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
-   Dynamické vazby datových sloupců. To je běžné méně než parametrizace. Další informace najdete v tématu [sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
 Pokud potřebujete rozsáhlejšími znalostmi RFX, přečtěte si [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md).  
  
 Následující témata vysvětlují, podrobnosti o používání objektů sada záznamů:  
  
-   [Výměna polí záznamu: Použití funkce RFX](../../data/odbc/record-field-exchange-using-rfx.md)  
  
-   [Výměna polí záznamu: Použití funkcí RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)  
  
-   [Výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md)  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Podpora databáze, Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)