---
title: "ODBC: Volání rozhraní API ODBC funkce přímo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51fde2bb7ea73a2655c0b771dabfe14d2c833fb5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: Přímé volání funkcí rozhraní API ODBC
Databázové třídy poskytují jednodušší rozhraní k [zdroj dat](../../data/odbc/data-source-odbc.md) než rozhraní ODBC. Třídy v důsledku toho není zapouzdření rozhraní API ODBC. Pro všechny funkce, která spadá mimo schopnosti tříd musí volat funkce rozhraní API ODBC přímo. Například musí volat funkce katalogu rozhraní ODBC (**:: SQLColumns**, **:: SQLProcedures**, **:: SQLTables**a jiné) přímo.  
  
> [!NOTE]
>  Zdroje dat ODBC jsou přístupné prostřednictvím třídy knihovny MFC rozhraní ODBC, jak je popsáno v tomto tématu nebo třídy MFC objekt DAO (Data Access).  
  
 K volání funkce rozhraní API ODBC přímo, je nutné provést stejné kroky, které bude trvat, pokud jste volali bez rozhraní. Tyto kroky:  
  
-   Přidělení úložiště pro výsledky, které vrátí volání.  
  
-   Předat ODBC **HDBC** nebo **HSTMT** zpracování, v závislosti na parametru signatury funkce. Použití [AFXGetHENV](../../mfc/reference/database-macros-and-globals.md#afxgethenv) makro pro načtení popisovače ODBC.  
  
     Členské proměnné **CDatabase::m_hdbc** a **CRecordset::m_hstmt** jsou k dispozici, takže není nutné přidělit a inicializovat sami.  
  
-   Možné volání dalších funkcí rozhraní ODBC se připravit nebo následnou akci hlavní volání.  
  
-   Po dokončení zrušit přidělení úložiště.  
  
 Další informace o těchto krocích najdete v tématu [připojení ODBC (Open Database)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) SDK v dokumentaci k webu MSDN.  
  
 Kromě těchto kroků budete muset udělat dodatečné kroky, chcete-li zkontrolovat návratové hodnoty funkce, ujistěte se, že váš program není čekání na asynchronní volání dokončit a tak dále. Tyto poslední kroky můžete zjednodušit pomocí `AFX_SQL_ASYNC` a `AFX_SQL_SYNC` makra. Další informace najdete v tématu [makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md) v *odkaz knihovny MFC*.  

  
## <a name="see-also"></a>Viz také  
 [ODBC – základy](../../data/odbc/odbc-basics.md)
