---
title: "Přístup k rozhraní ODBC a jazyku SQL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 666c0d0b3d358360426a7cf1184917b524a7030a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="access-to-odbc-and-sql"></a>Přístup k rozhraní ODBC a jazyku SQL
Knihovny Microsoft Foundation Class zapouzdří mnoha volání rozhraní API systému Windows a umožňuje stále přímo volat jakékoli funkce rozhraní API systému Windows. Databázové třídy poskytují flexibilitu stejné s ohledem na rozhraní API ODBC. Když vás od velkou část složitosti ODBC třídy databáze chrání, bude možné volat rozhraní API ODBC funkce přímo z libovolného místa v programu.  
  
 Podobně databázové třídy vás chrání před nutností pracovat příliš s [SQL](../../data/odbc/sql.md), ale pokud chcete, můžete jej přímo používat. Objekty sady záznamů můžete přizpůsobit předáním vlastní příkazu jazyka SQL (nebo nastavíte části výchozího příkazu) při otevření sady záznamů. Můžete také provést volání SQL přímo pomocí [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) funkce člena třídy [CDatabase](../../mfc/reference/cdatabase-class.md).  
  
 Další informace najdete v tématu [ODBC: volání rozhraní ODBC API funkce přímo](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) a [SQL: provedení přímé SQL volání (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [ODBC a MFC](../../data/odbc/odbc-and-mfc.md)