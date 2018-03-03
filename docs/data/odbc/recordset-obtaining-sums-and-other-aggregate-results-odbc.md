---
title: "Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC) | Microsoft Docs"
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
- SQL, retrieving aggregate values from recordsets
- recordsets, retrieving SQL aggregate values
- retrieving SQL aggregate values from recordsets
- ODBC recordsets, retrieving SQL aggregate values
- SQL aggregate values
- SQL Server projects, retrieving aggregate values from recordsets
- SQL aggregate values, retrieving from recordsets
ms.assetid: 94500662-22a4-443e-82d7-acbe6eca447b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4753193789c95b726a8770cef9a153b041fa762c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-obtaining-sums-and-other-aggregate-results-odbc"></a>Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma vysvětluje, jak získat agregované výsledky pomocí následujících [SQL](../../data/odbc/sql.md) klíčová slova:  
  
-   **Součet** vypočítá celkové hodnoty ve sloupci s číselným datovým typem.  
  
-   **Minimální** extrahuje nejmenší hodnotu ve sloupci s číselným datovým typem.  
  
-   **Maximální počet** extrahuje největší hodnotu ve sloupci s číselným datovým typem.  
  
-   **PRŮMĚR** vypočítá průměrnou hodnotu ze všech hodnot ve sloupci s číselným datovým typem.  
  
-   **POČET** udává počet záznamů v sloupec jakéhokoli datového typu.  
  
 Použití těchto funkcí SQL k získání statistické informace o záznamech ve zdroji dat, a nikoli k extrakci záznamy ze zdroje dat. Sada záznamů, která se obvykle vytvoří se skládá z jednoho záznamu (pokud jsou všechny sloupce agregovány), který obsahuje hodnotu. (Může existovat více než jeden záznam pokud jste použili **GROUP BY** klauzule.) Tato hodnota je výsledek výpočtu nebo extrakce provádí funkce SQL.  
  
> [!TIP]
>  Chcete-li přidat SQL **GROUP BY** – klauzule (a případně **HAVING** klauzule) chcete příkazu jazyka SQL, připojte na konec **m_strFilter**. Příklad:  
  
```  
m_strFilter = "sales > 10 GROUP BY SALESPERSON_ID";  
```  
  
 Můžete omezit počet záznamů, které můžete použít k získání agregačních výsledků pomocí filtrování a řazení sloupců.  
  
> [!CAUTION]
>  Některé možné použít operátory agregace vrátit na jiný datový typ ze sloupce, po které jsou agregací.  
  
-   **Součet** a **průměr** může vrátit další větší datový typ (například volání s `int` vrátí **DLOUHO** nebo **dvojité**).  
  
-   **POČET** obvykle vrátí **DLOUHO** bez ohledu na typ cílového sloupce.  
  
-   **Maximální počet** a **MIN** vrátit stejný datový typ jako sloupce, které budou vypočítat.  
  
     Například **přidat třídu** Průvodce vytvoří `long` `m_lSales` pro přizpůsobení sloupec Prodej, ale je třeba nahraďte ho s `double m_dblSumSales` – datový člen k Sales. Podívejte se na téma v následujícím příkladu.  
  
#### <a name="to-obtain-an-aggregate-result-for-a-recordset"></a>Chcete-li získat agregační výsledek pro sady záznamů  
  
1.  Vytvoření sady záznamů, jak je popsáno v [přidání příjemce rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) obsahující sloupce, z nichž chcete získat agregované výsledky.  
  
2.  Změnit [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) funkce sady záznamů. Nahraďte řetězec reprezentující název sloupce (druhý argument [RFX](../../data/odbc/record-field-exchange-using-rfx.md) volání funkce) s řetězec představující agregační funkce na sloupec. Nahraďte například:  
  
    ```  
    RFX_Long(pFX, "Sales", m_lSales);  
    ```  
  
     Pomocí:  
  
    ```  
    RFX_Double(pFX, "Sum(Sales)", m_dblSumSales)  
    ```  
  
3.  Otevřete sadu záznamů. Výsledek operace agregace je ponechán v `m_dblSumSales`.  
  
> [!NOTE]
>  Průvodce přiřadí ve skutečnosti názvy datových členů bez Maďarská předpony. Například byste mohli vytvořit průvodce `m_Sales` pro sloupec Prodej, místo `m_lSales` název používaný dříve pro ilustraci.  
  
 Pokud používáte [CRecordView](../../mfc/reference/crecordview-class.md) třídy Pokud chcete zobrazit data, budete muset změnit funkce DDX zobrazíte nové hodnoty datového člena; v takovém případě změna z:  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_lSales, m_pSet);  
```  
  
 Do:  
  
```  
DDX_FieldText(pDX, IDC_SUMSALES, m_pSet->m_dblSumSales, m_pSet);  
```  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)