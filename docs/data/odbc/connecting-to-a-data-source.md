---
title: Připojení ke zdroji dat | Dokumentace Microsoftu
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
ms.openlocfilehash: 4be8214ad036d67a02ce4b9c5935d3deb92252c1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061094"
---
# <a name="connecting-to-a-data-source"></a>Připojení ke zdroji dat

Zdroje dat ODBC je konkrétní sady dat, informace požadované pro přístup k datům a umístění zdroje dat, které mohou být popsány pomocí názvu zdroje dat. Z vašeho programu zdroj dat obsahuje data, správce databáze, sítě (pokud existuje) a rozhraní ODBC.  
  
Pro přístup k datům, které jsou k dispozici ve zdroji dat, musí váš program nejprve navázat připojení ke zdroji dat. Veškerý datový přístup je spravována prostřednictvím tohoto připojení.  
  
Připojení ke zdroji dat jsou zapouzdřena objektem třídy [CDatabase](../../mfc/reference/cdatabase-class.md). Když `CDatabase` objektu je připojený ke zdroji dat, můžete:  
  
- Vytvořit [sady záznamů](../../mfc/reference/crecordset-class.md), které výběr záznamů z tabulky nebo dotazů.  
  
- Správa [transakce](../../data/odbc/transaction-odbc.md), proto všechny dávkování aktualizace usilujeme o to ke zdroji dat najednou (nebo celá transakce vrácena zpět, takže se zdrojem dat je beze změny) – Pokud zdroj dat podporuje požadované úrovni transakcí.  
  
- Přímé spuštění [SQL](../../data/odbc/sql.md) příkazy.  
  
Po dokončení práce s připojením zdroje dat, zavřete `CDatabase` objektu a odstranit ji nebo ji znovu použít pro nová připojení. Další informace o připojení ke zdroji dat, naleznete v tématu [datové zdroje (ODBC)](../../data/odbc/data-source-odbc.md).  
  
## <a name="see-also"></a>Viz také  

[Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)