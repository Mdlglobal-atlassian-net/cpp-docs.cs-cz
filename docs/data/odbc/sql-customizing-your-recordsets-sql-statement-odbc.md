---
title: 'SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c6562689450aab15a766d315f9a948772613c5dd
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39209245"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)
Toto téma vysvětluje:  
  
-   Jak rozhraní sestavuje příkaz SQL  
  
-   Jak lze přepsat příkaz jazyka SQL  
  
> [!NOTE]
>  Tyto informace platí pro třídy knihovny MFC rozhraní ODBC. Pokud pracujete s tříd DAO knihovny MFC, naleznete v tématu "Porovnání z Microsoft Jet databáze modul SQL a ANSI SQL" v nápovědě k DAO.  
  
## <a name="sql-statement-construction"></a>Vytvoření příkazu SQL  
 Výběr záznamů primárně na SQL databází sady záznamů **vyberte** příkazu. Při deklaraci vaší třídy pomocí Průvodce zapíše přepsání verze `GetDefaultSQL` členskou funkci, která vypadá přibližně takto (pro třídu sady záznamů volána `CAuthors`).  
  
```  
CString CAuthors::GetDefaultSQL()  
{  
    return "AUTHORS";  
}  
```  
  
 Ve výchozím nastavení vrátí toto přepsání název tabulky, který jste zadali v průvodci. V tomto příkladu je název tabulky "Autoři." Při později volání sady záznamů **otevřít** členskou funkci **otevřít** sestaví finální **vyberte** příkazu ve formátu:  
  
```  
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]   
       [ORDER BY m_strSort]  
```  
  
 kde `table-name` je získán voláním `GetDefaultSQL` a `rfx-field-list` získaný z volání funkcí RFX v `DoFieldExchange`. To se dá dosáhnout pro **vyberte** příkazu není-li nahradit ho záznamem přepsání verze za běhu, i když můžete také upravit výchozí příkaz s parametry nebo filtru.  
  
> [!NOTE]
>  Pokud zadáte název sloupce, který obsahuje (nebo by mohly obsahovat) mezery, uzavřete název do hranatých závorek. Název "Jméno" by měl být například "[jméno]".  
  
 Přepsat výchozí nastavení **vyberte** prohlášení, vložte řetězec obsahující úplný **vyberte** příkaz při volání **otevřít**. Místo vytváření vlastní výchozí řetězec, používá sadu záznamů řetězec, který zadáte. Pokud váš příkaz nahrazení obsahuje **kde** klauzule, nezadávejte filtru v **m_strFilter** protože by pak máte dvě filtrování příkazů. Podobně pokud váš příkaz nahrazení obsahuje **klauzule ORDER BY** klauzule, nezadávejte řazení v `m_strSort` tak, že nebudete mít dva příkazy seřadit.  
  
> [!NOTE]
>  Pokud používáte řetězcových literálů v filtry (nebo jiné části příkazu jazyka SQL), budete muset "nabídka" (uzavřete do zadaných oddělovačů) tyto řetězce literálu předpona specifická pro DBMS a literálu přípony znak (nebo znaky).  
  
 Speciální syntaktickými požadavky pro operace, jako je vnější spojení, může dojít také v závislosti na vaší DBMS. Funkce ODBC pro získání těchto informací z vašich ovladače pro správce databáze. Například volání **:: SQLGetTypeInfo** pro konkrétní datový typ, jako například **SQL_VARCHAR**, požádat o **LITERAL_PREFIX** a **LITERAL_SUFFIX** znaků. Pokud píšete kód nezávislý na databázi, naleznete v dodatku C *ODBC SDK ** referenční informace pro programátory* na disku CD knihovny MSDN, pro podrobné informace o syntaxi.  
  
 Objekt sady záznamů sestavuje příkaz SQL, který se používá k výběru záznamů, pokud nepředáte vlastní příkaz jazyka SQL. Jak se to závisí hlavně na hodnotu můžete předat `lpszSQL` parametr **otevřít** členskou funkci.  
  
 Obecný tvar SQL **vyberte** příkaz je:  
  
```  
SELECT [ALL | DISTINCT] column-list FROM table-list  
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]  
```  
  
 Jeden ze způsobů, jak přidat **DISTINCT** – klíčové slovo do příkazu SQL sady záznamů, je vložit – klíčové slovo v prvním volání funkce RFX v `DoFieldExchange`. Příklad:  
  
```  
...  
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);  
...  
```  
  
> [!NOTE]
>  Tento postup lze používejte pouze se sadou záznamů otevřené s oprávněními jen pro čtení.  
  
## <a name="overriding-the-sql-statement"></a>Přepsání příkaz jazyka SQL  
 V následující tabulce jsou uvedeny možnosti `lpszSQL` parametr **otevřít**. Případy v tabulce jsou vysvětlené v následující tabulce.  
  
 **Výsledný řetězec SQL a parametru Ipszsql**  
  
|případ|Předáno Ipszsql|Výsledný příkaz SELECT|  
|----------|------------------------------|------------------------------------|  
|1|**HODNOTU NULL**|**Vyberte** *seznamu polí rfx* **FROM** *název tabulky*<br /><br /> `CRecordset::Open` volání `GetDefaultSQL` a získat tak název tabulky. Výsledný řetězec je jedním z případů 2 až 5, v závislosti na tom, co `GetDefaultSQL` vrátí.|  
|2|Název tabulky|**Vyberte** *seznamu polí rfx* **FROM** *název tabulky*<br /><br /> V seznamu polí jsou převzaty ze příkazů RFX v `DoFieldExchange`. Pokud **m_strFilter** a `m_strSort` nejsou prázdné, přidá **kde** a/nebo **klauzule ORDER BY** klauzule.|  
|3 \*|Kompletní **vyberte** příkaz ale bez **kde** nebo **klauzule ORDER BY** – klauzule|Jako úspěšný. Pokud **m_strFilter** a `m_strSort` nejsou prázdné, přidá **kde** a/nebo **klauzule ORDER BY** klauzule.|  
|4 \*|Kompletní **vyberte** příkazem **kde** a/nebo **klauzule ORDER BY** – klauzule|Jako úspěšný. **m_strFilter** a/nebo `m_strSort` musí zůstat prázdná, nebo dvě filtr nebo řazení příkazy se budou vytvářet.|  
|5 \*|Volání uložené procedury|Jako úspěšný.|  
  
 \* `m_nFields` musí být menší než počet sloupců zadaný v **vyberte** příkazu. Typ dat každého sloupce zadané v **vyberte** příkaz musí být stejný jako datový typ odpovídající RFX výstupního sloupce.  
  
### <a name="case-1---lpszsql--null"></a>Případ 1 Ipszsql = NULL  
 Výběr sady záznamů, závisí na co `GetDefaultSQL` vrátí, když `CRecordset::Open` jej volá. V případech 2 až 5 popisují možné řetězce.  
  
### <a name="case-2---lpszsql--a-table-name"></a>Případ 2 Ipszsql = název tabulky  
 Sada záznamů používá výměna pole záznamu (RFX) k vytvoření seznamu sloupců z názvů sloupců zadaný v RFX volá funkci v přepsání třídy sady záznamů `DoFieldExchange`. Pokud použijete průvodce k deklaraci vaší třídy sady záznamů, tento případ má stejný výsledek jako případ 1 (za předpokladu, že předáte stejný název tabulky, který jste zadali v průvodci). Pokud použijete průvodce k zápisu vaší třídy, případ 2 je nejjednodušší způsob, jak vytvořit příkaz SQL.  
  
 Následující příklad vytvoří příkaz SQL, který vybírá záznamy z databázových aplikacích MFC. Když volá framework `GetDefaultSQL` členská funkce, funkce vrátí název tabulky, `SECTION`.  
  
```  
CString CEnrollSet::GetDefaultSQL()  
{  
    return "SECTION";  
}  
```  
  
 Získat názvy sloupců pro SQL **vyberte** prohlášení, rámec volá `DoFieldExchange` členskou funkci.  
  
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
  
 Jakmile budete hotovi, příkaz jazyka SQL vypadá takto:  
  
```  
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo   
    FROM SECTION  
```  
  
### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Případ 3 Ipszsql = SELECT / z příkazu  
 Seznam sloupců je zadat ručně nespoléhat se na funkce RFX vytvořit automaticky. Můžete chtít provést při:  
  
-   Chcete zadat **DISTINCT** – klíčové slovo následující **vyberte**.  
  
     Sloupec seznamu by měl odpovídat názvy sloupců a typy ve stejném pořadí, jak jsou uvedeny v `DoFieldExchange`.  
  
-   Máte důvod pro ruční načtení hodnoty ve sloupcích pomocí funkce ODBC **:: SQLGetData** nespoléhat se na funkce RFX svázat a načíst sloupce za vás.  
  
     Můžete například umístit nové sloupce, které zákazník vaší aplikace přidat do tabulky databáze po byla distribuována aplikace. Budete muset přidat tyto dodatečné datové členy, kterých se ví, v době deklarována třída pomocí průvodce.  
  
     Sloupec seznamu by měl odpovídat názvy sloupců a typy ve stejném pořadí, jak jsou uvedeny v `DoFieldExchange`následovaný názvy ručně svázané sloupce. Další informace najdete v tématu [sada záznamů: dynamické vazby dat sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Chcete-li tabulky mají spojit, tak, že zadáte více tabulek v **FROM** klauzuli.  
  
     Informace a příklad najdete v tématu [sada záznamů: provedení do připojení (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Případ 4 Ipszsql = vyberte / z Plus WHERE a ORDER BY  
 Všechno, co zadáte: seznam sloupců (podle RFX v `DoFieldExchange`), seznam tabulek a obsah **kde** a/nebo **klauzule ORDER BY** klauzuli. Pokud zadáte vaši **kde** a/nebo **klauzule ORDER BY** klauzule tímto způsobem, nepoužívejte **m_strFilter** a/nebo `m_strSort`.  
  
### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Případ 5 Ipszsql = volání uložené procedury  
 Pokud je potřeba volat předdefinovaný dotaz (jako jsou uložené procedury v databázi Microsoft SQL Server), je nutné napsat **volání** příkaz v řetězci, který předáte `lpszSQL`. Průvodci nepodporují deklarace třídy sady záznamů pro volání předdefinovaného dotazu. Ne všechny předdefinované dotazy vrací záznamy.  
  
 Je-li předdefinovaný dotaz nevrací záznamy, můžete použít `CDatabase` členskou funkci `ExecuteSQL` přímo. Pro předdefinovaný dotaz, který vrátí záznamy, je nutné také ručně napsat volání RFX v `DoFieldExchange` pro všechny sloupce postup vrátí. Volání funkce RFX musí být ve stejném pořadí a vrátí stejné typy, jako předdefinovaný dotaz. Další informace najdete v tématu [sada záznamů: deklarování třídy pro předdefinovaný dotaz (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [SQL: SQL a datové typy C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)   
 [SQL: Přímá volání SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
