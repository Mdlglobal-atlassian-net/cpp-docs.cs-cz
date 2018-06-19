---
title: Zdroj dat (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 842a8bf3faadcf96b4f44441e45dc94d5679f9f4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33087871"
---
# <a name="data-source-odbc"></a>Zdroj dat (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Zdroj dat v databázi podmínky, je konkrétní sadu dat, informace požadované pro přístup k datům a umístění zdroje dat, který lze popsat pomocí názvu zdroje dat. Pro práci s třídou [CDatabase](../../mfc/reference/cdatabase-class.md), zdroj dat musí být ten, který jste nakonfigurovali prostřednictvím Správce připojení ODBC (Open Database). Mezi příklady zdroje dat patří vzdálené databáze systémem Microsoft SQL Server přes síť nebo souboru aplikace Microsoft Access do místního adresáře. Z vaší aplikace máte přístup k libovolný zdroj dat, pro které máte ovladače ODBC.  
  
 Může mít jeden nebo více zdrojů dat active v aplikaci najednou, každý reprezentován `CDatabase` objektu. Pro libovolný zdroj dat může mít i víc souběžných připojení. Připojením ke vzdálené a také pro místní zdroje dat, v závislosti na ovladače, které jste nainstalovali a možností vaší ovladačů ODBC. Další informace o zdrojích dat a správce rozhraní ODBC najdete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [správce rozhraní ODBC](../../data/odbc/odbc-administrator.md).  
  
 Následující témata popisují více o zdrojích dat:  
  
-   [Zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
-   [Zdroj dat: Stanovení schématu zdroje dat (rozhraní ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)