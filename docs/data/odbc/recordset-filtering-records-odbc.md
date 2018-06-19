---
title: 'Sada záznamů: Filtrování záznamů (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4b4860726fa77d7b852290d8ea4680fe1bbbd86f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091800"
---
# <a name="recordset-filtering-records-odbc"></a>Sada záznamů: Filtrování záznamů (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma vysvětluje, jak filtrovat sadu záznamů tak, aby vybral pouze konkrétní podmnožinu dostupných záznamů. Můžete například vybrat pouze oddíly třídy pro konkrétní kurz, jako je například MATH101. Filtr je podmínka vyhledávání definované obsah SQL **kde** klauzule. Pokud systém připojí k příkazu SQL sady záznamů, **kde** klauzule omezí výběr.  
  
 Je nutné vytvořit filtr objekt sady záznamů, co vytvoříte objekt, ale před voláním jeho **otevřete** – členská funkce (nebo před voláním **Requery –** – členská funkce pro existující sady záznamů objekt, jehož **otevřete** – členská funkce byla volána dříve).  
  
#### <a name="to-specify-a-filter-for-a-recordset-object"></a>K zadání filtru pro objekt sady záznamů  
  
1.  Vytvořte nový objekt sady záznamů (nebo připravte volání **Requery** pro existující objekt).  
  
2.  Nastavte hodnotu objektu [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) – datový člen.  
  
     Filtr je řetězec ukončené hodnotou null, který obsahuje obsah SQL **kde** klauzule, ale nikoli klíčové slovo **kde**. Například použijte:  
  
    ```  
    m_pSet->m_strFilter = "CourseID = 'MATH101'";  
    ```  
  
     not  
  
    ```  
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";  
    ```  
  
    > [!NOTE]
    >  Řetězcový literál "MATH101" se zobrazí s apostrofech výše. Ve specifikaci ODBC SQL jednoduchých uvozovek a slouží k označení znak řetězcový literál. Podívejte se do dokumentace ovladač ODBC pro požadavky z hlediska stylu citací vaší databázového systému v této situaci. Tato syntaxe je také popsána dále téměř na konci tohoto tématu.  
  
3.  Nastavte další možnosti, které potřebujete, například pořadí řazení, režim uzamčení nebo parametry. Zadání parametru je obzvláště užitečná. Informace o parametrizaci filtru najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
4.  Volání **otevřete** nového objektu (nebo **Requery** pro objekt, který dříve otevřen).  
  
> [!TIP]
>  Pomocí parametrů do filtru je možná nejefektivnější metoda pro načtení záznamů.  
  
> [!TIP]
>  Sada záznamů filtry jsou užitečné pro [připojení](../../data/odbc/recordset-performing-a-join-odbc.md) tabulky a pro používání [parametry](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) na základě informací získaných nebo vypočtených za běhu.  
  
 Sada záznamů vybere pouze záznamy, které splňují podmínku vyhledávání, které zadáte. Můžete například zadat filtr kurzu popsané výše (za předpokladu, že proměnné `strCourseID` nastaveno, například na "MATH101"), postupujte takto:  
  
```  
// Using the recordset pointed to by m_pSet  
  
// Set the filter  
m_pSet->m_strFilter = "CourseID = " + strCourseID;   
  
// Run the query with the filter in place  
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )  
  
// Use the recordset  
```  
  
 Sada záznamů obsahuje záznamy pro všechny oddíly tříd pro MATH101.  
  
 Všimněte si, jak byl nastaven řetězec filtru v příkladu výše, používá proměnnou string. Toto je typické použití. Ale Předpokládejme, že chcete zadat hodnotu literálu 100 pro ID kurzu. Následující kód ukazuje, jak nastavit řetězec filtru správně s literálovou hodnotou:  
  
```  
m_strFilter = "StudentID = '100'";   // correct  
```  
  
 Všimněte si použití jednoduchých uvozovkách znaků; Pokud jste nastavili řetězec filtru přímo, je řetězec filtru **není**:  
  
```  
m_strFilter = "StudentID = 100";   // incorrect for some drivers  
```  
  
 Použití uvozovek výše odpovídá specifikaci ODBC, ale některé DBMS mohou vyžadovat další znaky uvozovek za sebou. Další informace najdete v tématu [SQL: přizpůsobení vaše SQL příkazu záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
> [!NOTE]
>  Pokud se rozhodnete přepsat výchozí řetězec SQL sady záznamů předáním svůj vlastní řetězec SQL k **otevřete**, by neměl nastavit filtr, pokud má váš vlastní řetězec **kde** klauzule. Další informace o přepsání výchozího SQL najdete v tématu [SQL: přizpůsobení vaše SQL příkazu záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)   
 [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)