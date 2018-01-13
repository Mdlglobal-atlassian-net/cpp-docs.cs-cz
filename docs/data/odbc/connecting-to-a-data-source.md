---
title: "Připojení ke zdroji dat | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 08872f9e1034c50ca1468d6834f3a44dc06c1ebe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="connecting-to-a-data-source"></a>Připojení ke zdroji dat
Zdroje dat ODBC je konkrétní sadu dat, informace požadované pro přístup k datům a umístění zdroje dat, který lze popsat pomocí názvu zdroje dat. Zdroj dat z vašeho programu zahrnuje data, databázového systému, sítě (pokud existuje) a rozhraní ODBC.  
  
 Pro přístup k datům poskytuje zdroj dat, musí váš program nejprve navázat připojení ke zdroji dat. Všechny přístup k datům se spravuje přes toto připojení.  
  
 Připojení ke zdroji dat jsou zapouzdřené třídou [CDatabase](../../mfc/reference/cdatabase-class.md). Když `CDatabase` objekt je připojený ke zdroji dat, můžete:  
  
-   Vytvořit [sady záznamů](../../mfc/reference/crecordset-class.md), který vyberte záznamů z tabulek nebo dotazů.  
  
-   Spravovat [transakce](../../data/odbc/transaction-odbc.md), dávkování tak všechny aktualizace jsou ke zdroji dat najednou (nebo celá transakce vrácena zpět, takže se zdroji dat se neliší) – Pokud je zdroj dat podporuje požadované úrovni transakcí.  
  
-   Přímo spustit [SQL](../../data/odbc/sql.md) příkazy.  
  
 Po dokončení práce s připojení zdroje dat, zavřete `CDatabase` objekt a zničte jej nebo ji znovu použít pro nové připojení. Další informace o připojení ke zdroji dat najdete v tématu [datové zdroje (ODBC)](../../data/odbc/data-source-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)