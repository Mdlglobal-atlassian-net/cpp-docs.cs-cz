---
title: "Zdroj dat: Stanovení schématu zdroje dat (ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 54a596ce7821d89096836a0edbaf810d6c3f4a2e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Zdroj dat: Stanovení schématu zdroje dat (rozhraní ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Nastavit datových členů v vaší `CRecordset` objekty, je nutné znát schématu zdroje dat, ke kterému se chcete připojit. Stanovení schématu zdroje dat zahrnuje získání seznamu tabulek ve zdroji dat, seznam sloupců v každé tabulce, datový typ jednotlivých sloupců a existenci žádné indexy.  
  
## <a name="see-also"></a>Viz také  
 [Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)   
 [Zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)