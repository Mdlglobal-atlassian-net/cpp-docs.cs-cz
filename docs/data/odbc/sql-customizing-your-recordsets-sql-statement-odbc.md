---
title: "SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cae8862dd8fc10dd117b07414ab00a34117f5e10
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)
Toto téma vysvětluje:  
  
-   Jak rozhraní framework vytvoří příkazu jazyka SQL  
  
-   Jak lze přepsat příkaz jazyka SQL  
  
> [!NOTE]
>  Tyto informace platí pro třídy MFC rozhraní ODBC. Pokud pracujete s tříd MFC rozhraní DAO, naleznete v tématu "Porovnání z Microsoft Jet databáze stroj SQL a ANSI SQL" v nápovědě rozhraní DAO.  
  
## <a name="sql-statement-construction"></a>Konstrukce příkazu SQL  
 Sady záznamů základny výběr záznamů hlavně na SQL **vyberte** příkaz. Je-li vaše třídu deklarovat s průvodce, zapíše přepsání verzi `GetDefaultSQL` – členská funkce, která vypadá přibližně takto (u třídy sady záznamů označuje `CAuthors`).  
  
```  
CString CAuthors::GetDefaultSQL()  
{  
    return "AUTHORS";  
}  
```  
  
 Ve výchozím nastavení toto přepsání vrátí název tabulky, který jste zadali v průvodci. V příkladu je název tabulky "AUTHORS." Při později volání sady záznamů **otevřete** – členská funkce **otevřete** sestaví finální **vyberte** příkaz ve tvaru:  
  
```  
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]   
       [ORDER BY m_strSort]  
```  
  
 kde `table-name` se získá voláním `GetDefaultSQL` a `rfx-field-list` se získávají z volání funkce RFX v `DoFieldExchange`. Toto je získáte pro **vyberte** příkaz Pokud nahrazena přepsání verze za běhu, i když můžete také upravit výchozí příkaz pomocí parametrů nebo filtru.  
  
> [!NOTE]
>  Pokud zadáte název sloupce, který obsahuje (nebo by mohly obsahovat) mezery, je nutné uzavřít název do hranatých závorek. Název "Jméno" musí být například "[jméno]".  
  
 Přepsat výchozí nastavení **vyberte** příkaz, vložte řetězec obsahující úplný **vyberte** příkaz při volání **otevřete**. Místo vytváření vlastní výchozí řetězec, používá sada záznamů řetězec, který zadáte. Pokud nahrazující příkaz obsahuje **kde** klauzule, nezadávejte filtr ve funkci **m_strFilter** protože by pak máte dva filtrování příkazů. Podobně pokud nahrazující příkaz obsahuje **Order** klauzule, nezadávejte řazení v `m_strSort` tak, že nebudete mít dva příkazy seřadit.  
  
> [!NOTE]
>  Pokud používáte literály filtry (nebo dalších částí příkaz jazyka SQL), možná budete muset "nabídka" (uzavřít do zadaných oddělovačů) tyto řetězce s předponou literálu specifické databázového systému a literálu přípona znak (nebo znaků).  
  
 Zvláštní požadavky syntaxi pro operace, jako je například vnější spojení, může dojít také v závislosti na vaší databázového systému. Pomocí funkcí rozhraní ODBC získat tyto informace z vašeho ovladače databázového systému. Například volání **:: SQLGetTypeInfo** pro konkrétní datový typ, jako například **SQL_VARCHAR**, k vyžádání **LITERAL_PREFIX** a **LITERAL_SUFFIX** znaků. Pokud vytváříte kód nezávislý na databázi, naleznete v dodatku C *ODBC SDK**referenční informace pro programátory* na disku CD knihovny MSDN pro podrobné informace o syntaxi.  
  
 Objekt sady záznamů vytvoří příkaz jazyka SQL, která slouží k výběru záznamů, pokud předáte vlastní příkaz SQL. Způsob provedení závisí hlavně na hodnotě, kterou předáte `lpszSQL` parametr **otevřete** – členská funkce.  
  
 Obecná forma SQL **vyberte** příkaz je:  
  
```  
SELECT [ALL | DISTINCT] column-list FROM table-list  
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]  
```  
  
 Jeden ze způsobů, jak přidat **DISTINCT** – klíčové slovo příkazu SQL sady záznamů je vložit klíčové slovo v první volání funkce RFX v `DoFieldExchange`. Příklad:  
  
```  
...  
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);  
...  
```  
  
> [!NOTE]
>  Tento postup použijte pouze v sadě záznamů otevřít jen pro čtení.  
  
## <a name="overriding-the-sql-statement"></a>Přepsání příkazu SQL  
 V následující tabulce jsou uvedeny možnosti pro `lpszSQL` parametru **otevřete**. V případech v tabulce jsou vysvětlené v následující tabulce.  
  
 **Parametr lpszSQL a výsledný řetězec SQL**  
  
|Případ|Co můžete předat lpszSQL|Výsledný příkaz SELECT|  
|----------|------------------------------|------------------------------------|  
|1|**HODNOTU NULL**|**Vyberte** *seznam polí rfx* **FROM** *název tabulky*<br /><br /> `CRecordset::Open`volání `GetDefaultSQL` získat název tabulky. Výsledný řetězec je jedním z případů 2 až 5, v závislosti na tom, co `GetDefaultSQL` vrátí.|  
|2|Název tabulky|**Vyberte** *seznam polí rfx* **FROM** *název tabulky*<br /><br /> Seznam polí jsou převzaty z příkazů RFX v `DoFieldExchange`. Pokud **m_strFilter** a `m_strSort` nejsou prázdné, přidá **kde** nebo **Order** klauzule.|  
|3 *|Úplná **vyberte** příkaz ale bez **kde** nebo **Order** – klauzule|Jak je předán. Pokud **m_strFilter** a `m_strSort` nejsou prázdné, přidá **kde** nebo **Order** klauzule.|  
|4 *|Úplná **vyberte** příkaz s **kde** nebo **Order** – klauzule|Jak je předán. **m_strFilter** nebo `m_strSort` musí zůstat prázdná, nebo dvě filtru nebo vytváří příkazy řazení.|  
|5 *|Volání uložené procedury|Jak je předán.|  
  
 \*`m_nFields` musí být menší než počet sloupců zadaný v **vyberte** příkaz. Datový typ zadaný v každý sloupec **vyberte** příkaz musí být stejný jako datový typ odpovídající RFX výstupního sloupce.  
  
### <a name="case-1---lpszsql--null"></a>Případ 1 lpszSQL = NULL  
 Výběr sady záznamů závisí na co `GetDefaultSQL` vrátí, když `CRecordset::Open` nazve je. Případů 2 až 5 popisují možné řetězce.  
  
### <a name="case-2---lpszsql--a-table-name"></a>Případ 2 lpszSQL = Název tabulky  
 Sady záznamů výměna pole záznamu (RFX) používá k vytvoření seznamu sloupců z názvů sloupců zadaný v RFX funkce volá v třídě sady záznamů přepsání `DoFieldExchange`. Pokud jste použili Průvodce deklarovat třídu sady záznamů, má tento případ stejný výsledek jako případ 1 (za předpokladu, že předáváte stejný název tabulky, který jste zadali v průvodci). Pokud použijete průvodce k zápisu třídě, případ 2 je nejjednodušší způsob, jak vytvořit příkaz jazyka SQL.  
  
 Následující příklad vytvoří příkaz SQL, který vybere z databázové aplikace MFC záznamy. Když volá framework `GetDefaultSQL` – členská funkce, funkce vrátí název tabulky, `SECTION`.  
  
```  
CString CEnrollSet::GetDefaultSQL()  
{  
    return "SECTION";  
}  
```  
  
 Získat názvy sloupců SQL **vyberte** prohlášení, volání framework `DoFieldExchange` – členská funkce.  
  
```  
void CEnrollSet::DoFieldExchange(CFieldExchange* pFX)  
{  
    pFX->SetFieldType(CFieldExchange::outputColumn);  
    RFX_Text(pFX, "CourseID", m_strCourseID);  
    RFX_Text(pFX, "InstructorID", m_strInstructorID);  
    RFX_Text(pFX, "RoomNo", m_strRoomNo);  
    RFX_Text(pFX, "Schedule", m_strSchedule);  
    RFX_Text(pFX, "SectionNo", m_strSectionNo);  
}  
```  
  
 Po dokončení příkazu SQL vypadá takto:  
  
```  
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo   
    FROM SECTION  
```  
  
### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Případ 3 lpszSQL = vyberte možnost z příkazu  
 Nespoléhá se na RFX automatické vytvoření ručně zadáte seznamu sloupců. Můžete chtít provést při:  
  
-   Chcete určit **DISTINCT** – klíčové slovo následující **vyberte**.  
  
     Váš seznam sloupců by měl odpovídat názvy sloupců a typy ve stejném pořadí, v jakém jsou uvedené v `DoFieldExchange`.  
  
-   Máte důvod ručně načíst hodnoty ve sloupcích pomocí funkce rozhraní ODBC **:: SQLGetData** nespoléhá se na RFX sváže a načte sloupce za vás.  
  
     Můžete například umístit nové sloupce, které zákazník aplikace přidat tabulkách databáze po byla distribuována aplikace. Je nutné přidat tyto další pole datových členů, které nebyly známé v době deklarovali třídu pomocí průvodce.  
  
     Váš seznam sloupců by měl odpovídat názvy sloupců a typy ve stejném pořadí, v jakém jsou uvedené v `DoFieldExchange`, za nímž následují názvy ručně vázaných sloupců. Další informace najdete v tématu [sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Chcete spojit tabulky zadáním několika tabulkám ve **FROM** klauzule.  
  
     Informace a příklady naleznete v tématu [sada záznamů: provedení připojení (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Případ 4 lpszSQL = vyberte / FROM Plus WHERE nebo ORDER BY  
 Všechno, co zadáte: seznam sloupců (podle RFX v `DoFieldExchange`), seznam tabulek a obsah **kde** nebo **Order** klauzule. Pokud zadáte vaše **kde** nebo **Order** klauzule tímto způsobem, nepoužívejte **m_strFilter** nebo `m_strSort`.  
  
### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Případ 5 lpszSQL = volání uložené procedury  
 Pokud je třeba volat předdefinovaný dotaz (například uloženou proceduru v databázi Microsoft SQL Server), musíte napsat **volání** příkaz v řetězci je předat do `lpszSQL`. Průvodci nepodporují deklarování třídy pro předdefinovaný dotaz volání sady záznamů. Ne všechny předdefinované dotazy vrátí záznamy.  
  
 Pokud předdefinovaný dotaz nevrátí záznamy, můžete použít `CDatabase` – členská funkce `ExecuteSQL` přímo. Pro předdefinovaný dotaz vracející záznamy, musíte taky ručně napsat volání RFX v `DoFieldExchange` pro všechny sloupce postup vrátí. Volání RFX musí být ve stejném pořadí a vrátí stejné typy jako předdefinovaný dotaz. Další informace najdete v tématu [sada záznamů: deklarování třídy pro předdefinovaný dotaz (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [SQL: SQL a datové typy C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)   
 [SQL: Provedení přímá volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
