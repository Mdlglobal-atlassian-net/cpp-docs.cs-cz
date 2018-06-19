---
title: 'Zdroj dat: Stanovení schématu zdroje dat (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources [C++], schema
- schemas [C++], data sources
- data sources [C++], determining schema
ms.assetid: 17284acb-eb10-4f27-9944-ad1d973c0b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6da4067766eddab40bac75ee73d825dc5886dd0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33088274"
---
# <a name="data-source-determining-the-schema-of-the-data-source-odbc"></a>Zdroj dat: Stanovení schématu zdroje dat (rozhraní ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Nastavit datových členů v vaší `CRecordset` objekty, je nutné znát schématu zdroje dat, ke kterému se chcete připojit. Stanovení schématu zdroje dat zahrnuje získání seznamu tabulek ve zdroji dat, seznam sloupců v každé tabulce, datový typ jednotlivých sloupců a existenci žádné indexy.  
  
## <a name="see-also"></a>Viz také  
 [Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)   
 [Zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md)