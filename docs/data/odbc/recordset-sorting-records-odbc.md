---
title: "Sada záznamů: Řazení záznamů (ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6ca9e8547149ae36722c40e146392085e6ccf08e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-sorting-records-odbc"></a>Sada záznamů: Řazení záznamů (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma vysvětluje, jak řadit sady záznamů. Můžete zadat jeden nebo více sloupců, na jejichž základě řadíte a můžete určit vzestupném nebo sestupném pořadí (`ASC` nebo **DESC**; `ASC` je výchozí nastavení) pro každý zadaný sloupec. Například pokud zadáte dva sloupce, záznamy jsou seřazeny nejprve na první sloupec s názvem a pak na druhý sloupec s názvem. SQL **Order** klauzule definuje řazení. Pokud systém připojí **Order** dotaz klauzule SQL sady záznamů, klauzule ovládacích prvků výběr je řazení.  
  
 Po vytvoření objektu, ale před voláním musíte vytvořit pořadí řazení sady záznamů jeho **otevřete** – členská funkce (nebo před voláním **Requery –** – členská funkce pro existující objekt sady záznamů jejichž **otevřete** – členská funkce byla volána dříve).  
  
#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Chcete-li určit pořadí řazení pro objekt sady záznamů  
  
1.  Vytvořte nový objekt sady záznamů (nebo připravte volání **Requery** pro některý ze stávajících).  
  
2.  Nastavte hodnotu objektu [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) – datový člen.  
  
     Řazení je řetězce ukončené hodnotou null. Obsahuje obsah **Order** klauzule, ale nikoli klíčové slovo **Order**. Například použijte:  
  
    ```  
    recordset.m_strSort = "LastName DESC, FirstName DESC";  
    ```  
  
     not  
  
    ```  
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";  
    ```  
  
3.  Nastavte další možnosti, které potřebujete, jako je například filtr, režim uzamčení nebo parametry.  
  
4.  Volání **otevřete** nového objektu (nebo **Requery** pro existující objekt).  
  
 Vybrané záznamy jsou řazeny uvedené. Například seřadit sadu záznamy studentů v sestupném pořadí podle příjmení, pak křestní jméno, postupujte takto:  
  
```  
// Construct the recordset  
CStudentSet rsStudent( NULL );  
// Set the sort  
rsStudent.m_strSort = "LastName DESC, FirstName DESC";  
// Run the query with the sort in place  
rsStudent.Open( );  
```  
  
 Sada záznamů obsahuje všechny záznamy studenty, seřazené v sestupném pořadí (Z až A) podle příjmení a pak podle křestní jméno.  
  
> [!NOTE]
>  Pokud se rozhodnete přepsat výchozí řetězec SQL sady záznamů předáním svůj vlastní řetězec SQL k **otevřete**, nenastavujte řazení, pokud má váš vlastní řetězec **Order** klauzule.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [Sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)