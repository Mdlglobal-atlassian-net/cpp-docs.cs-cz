---
title: Připojení ke zdroji dat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b6a33f1e2421c56f89184d26185903b4ec7859e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088388"
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