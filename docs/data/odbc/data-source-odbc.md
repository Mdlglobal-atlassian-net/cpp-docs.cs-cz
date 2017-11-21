---
title: Zdroj dat (ODBC) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC data sources, configuring
- CDatabase class, data source connections
- ODBC data sources
- configuring ODBC data sources
- ODBC data sources, represented by CDatabase
ms.assetid: b246721f-b9e1-49bd-a6c7-f348b8c3d537
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e0236c8684c37b0378dd7ebead37d2c9c44cf1d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="data-source-odbc"></a>Zdroj dat (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Zdroj dat v databázi podmínky, je konkrétní sadu dat, informace požadované pro přístup k datům a umístění zdroje dat, který lze popsat pomocí názvu zdroje dat. Pro práci s třídou [CDatabase](../../mfc/reference/cdatabase-class.md), zdroj dat musí být ten, který jste nakonfigurovali prostřednictvím Správce připojení ODBC (Open Database). Mezi příklady zdroje dat patří vzdálené databáze systémem Microsoft SQL Server přes síť nebo souboru aplikace Microsoft Access do místního adresáře. Z vaší aplikace máte přístup k libovolný zdroj dat, pro které máte ovladače ODBC.  
  
 Může mít jeden nebo více zdrojů dat active v aplikaci najednou, každý reprezentován `CDatabase` objektu. Pro libovolný zdroj dat může mít i víc souběžných připojení. Připojením ke vzdálené a také pro místní zdroje dat, v závislosti na ovladače, které jste nainstalovali a možností vaší ovladačů ODBC. Další informace o zdrojích dat a správce rozhraní ODBC najdete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [správce rozhraní ODBC](../../data/odbc/odbc-administrator.md).  
  
 Následující témata popisují více o zdrojích dat:  
  
-   [Zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)  
  
-   [Zdroj dat: Stanovení schématu zdroje dat (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)