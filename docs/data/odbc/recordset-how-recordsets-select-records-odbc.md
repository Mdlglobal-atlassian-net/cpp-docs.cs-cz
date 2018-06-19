---
title: 'Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9ff2f1e9946eb32356eb09fa2ee216aa636a351
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093227"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma vysvětluje:  
  
-   [Vaše role a možnosti při výběru záznamy](#_core_your_options_in_selecting_records).  
  
-   [Jak sady záznamů příkazy SQL a vybere záznamy](#_core_how_a_recordset_constructs_its_sql_statement).  
  
-   [Co můžete dělat pro přizpůsobení výběru](#_core_customizing_the_selection).  
  
 Sady záznamů vybírají záznamy ze zdroje dat prostřednictvím ovladače ODBC odesláním příkazů SQL ovladače. SQL odešle závisí na tom, jak navrhnout a otevřete třídu sady záznamů.  
  
##  <a name="_core_your_options_in_selecting_records"></a> Možnosti při výběru záznamů  
 Následující tabulka uvádí možnosti při výběru záznamů.  
  
### <a name="how-and-when-you-can-affect-a-recordset"></a>Jak a kdy může ovlivnit sady záznamů  
  
|Pokud jste|Můžeš|  
|--------------|-------------|  
|Deklarovat třídu sady záznamů s **přidat třídu** Průvodce|Zadejte které tabulky vybírat.<br /><br /> Zadejte sloupce, které chcete zahrnout.<br /><br /> V tématu [přidání příjemce knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|  
|Dokončení implementaci třídy sady záznamů|Přepsat členské funkce, jako `OnSetOptions` (rozšířené), chcete-li nastavit možnosti specifické pro aplikaci nebo změnit výchozí nastavení. Zadejte parametry datových členů, pokud chcete, aby parametrizované sady záznamů.|  
|Vytvořte objekt sady záznamů (před voláním **otevřete**)|Zadejte podmínku vyhledávání (případně složenou) pro použití v **kde** klauzuli, která filtruje záznamy. V tématu [sada záznamů: filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Určit pořadí řazení pro použití v **Order** klauzuli, která řadí záznamy. V tématu [sada záznamů: řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Zadejte hodnoty parametrů pro všechny parametry, které jste přidali do třídy. V tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|  

| Spusťte dotaz sady záznamů voláním **otevřete**| Zadejte vlastní řetězec SQL nahradit výchozí řetězec SQL nastavit tak, že v průvodci. V tématu [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) v *třídy referenční příručka knihovny* a [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |  

| Volání **Requery** k Requery – sady záznamů s nejnovější hodnoty ve zdroji dat | Zadejte nové parametry, filtr nebo řazení. V tématu [sada záznamů: opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |  
  
##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> Jak sady záznamů příkazy SQL  
 Při volání objektu sady záznamů [otevřete](../../mfc/reference/crecordset-class.md#open) – členská funkce **otevřete** vytvoří příkazu SQL pomocí některé nebo všechny následující složky:  
  
-   **LpszSQL** byl předán parametr **otevřete**. Není-li **NULL**, tento parametr určuje vlastní řetězec SQL nebo jeho část. Rozhraní framework analyzuje řetězec. Pokud je řetězec SQL **vyberte** příkaz nebo ODBC **volání** příkaz, rozhraní používá řetězec jako příkaz SQL sady záznamů. Pokud řetězec nezačíná "Vyberte" nebo "{CALL", systém použije, co je součástí konstrukce SQL **FROM** klauzule.  
  
-   Řetězec vrácený [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). Ve výchozím nastavení to je název tabulky, kterou jste zadali pro sady záznamů v průvodci, ale můžete změnit návratovou hodnotu. Volání framework `GetDefaultSQL` – Pokud řetězec nezačíná "Vyberte" nebo "{CALL", předpokládá se název tabulky, který se používá pro konstrukci řetězec SQL.  
  

-   Pole datových členů sady záznamů, které mají být vázána na konkrétní sloupce tabulky. Rozhraní framework sváže záznam sloupců s adresami těchto členů, jejich použití jako vyrovnávací paměti. Rozhraní framework určuje korelaci pole datových členů sloupců tabulky z [RFX](../../data/odbc/record-field-exchange-using-rfx.md) nebo Bulk RFX funkce volá v sadě záznamů [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange ](../../mfc/reference/crecordset-class.md#dofieldexchange) – členská funkce.  
  
-   [Filtru](../../data/odbc/recordset-filtering-records-odbc.md) sady záznamů, pokud existuje, obsažené v [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) – datový člen. Rozhraní framework tento řetězec používá k vytvoření SQL **kde** klauzule.  
  
-   [Řazení](../../data/odbc/recordset-sorting-records-odbc.md) pořadí sady záznamů, pokud existuje, obsažené v [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) – datový člen. Rozhraní framework tento řetězec používá k vytvoření SQL **Order** klauzule.  

  
    > [!TIP]
    >  Používat SQL **GROUP BY** – klauzule (a případně **HAVING** klauzule), připojte na konec vaší řetězec filtru klauzule.  
  
-   Hodnoty všech [parametry datových členů](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) zadáte pro třídu. Hodnoty parametru nastavíte těsně před voláním **otevřete** nebo **Requery –**. Rozhraní framework váže hodnot parametrů, které "?" zástupné symboly v řetězci SQL. Při kompilaci můžete zadat řetězec se zástupnými symboly. V době běhu rozhraní vyplní podle hodnoty parametrů, které předat podrobnosti.  
  
 **Otevřete** vytvoří SQL **vyberte** příkaz z těchto složek. V tématu [přizpůsobení výběru](#_core_customizing_the_selection) podrobnosti o tom, jak rozhraní používá složky.  
  
 Po vytváření příkaz **otevřete** odešle SQL správce ovladačů ODBC (a knihovna kurzorů rozhraní ODBC, pokud se nachází v paměti), který jej odešle ovladač ODBC pro konkrétní databázového systému. Ovladač komunikuje s databázového systému provádět výběr ve zdroji dat a načte první záznam. Rozhraní framework načte záznam do pole datových členů sady záznamů.  
  
 Můžete použít kombinaci těchto postupů otevřete [tabulky](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) a k vytvoření dotazu na základě [spojení](../../data/odbc/recordset-performing-a-join-odbc.md) více tabulek. Pomocí dalších úprav můžete volat [předdefinované dotazy](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (uložené procedury), vyberte tabulky, sloupce není známý v době návrhu a [vazby](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) jejich polí záznamů, nebo můžete provést většiny ostatních přístup k datům úlohy. Nelze provádět přizpůsobením sad záznamů úlohy můžete provést stále [volání funkcí rozhraní API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) nebo přímo spuštěním příkazů SQL s [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).  
  
##  <a name="_core_customizing_the_selection"></a> Přizpůsobení výběru  
 Kromě toho poskytuje filtr, pořadí řazení nebo parametry, můžete provést následující akce pro přizpůsobení výběr sady záznamů:  
  
-   Předat vlastní řetězec SQL v **lpszSQL** při volání [otevřete](../../mfc/reference/crecordset-class.md#open) sady záznamů. Nic předáte v **lpsqSQL** co má přednost před [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) – členská funkce vrátí.  
  
     Další informace najdete v tématu [SQL: přizpůsobení vaše SQL příkazu záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), která popisuje typy příkazů SQL (nebo částečné příkazy) můžete předat do **otevřete** a co systém s nimi.  
  
    > [!NOTE]
    >  Pokud vlastní řetězec, který můžete předat nezačíná "Vyberte" nebo "{CALL", MFC předpokládá, že obsahuje název tabulky. To platí také pro další položky s odrážkami.  
  
-   Příkaz ALTER řetězec, který průvodce zapíše do sady záznamů `GetDefaultSQL` – členská funkce. Upravte kód funkce změnit návratovou hodnotu. Ve výchozím nastavení, zapisuje průvodce `GetDefaultSQL` funkci, která vrací jeden název tabulky.  
  
     Můžete mít `GetDefaultSQL` vrátit některou z položek, které mohou uplynout v **lpszSQL** parametru **otevřete**. Pokud jste nepředávejte vlastní řetězec SQL v **lpszSQL**, rozhraní použije řetězec, který `GetDefaultSQL` vrátí. Minimálně `GetDefaultSQL` musí vracet jeden název tabulky. Ale může mít vrátí více názvů tabulek, úplnou **vyberte** příkaz ODBC **volání** příkaz a tak dále. Seznam můžete předat do **lpszSQL** – nebo mít `GetDefaultSQL` vrátit – najdete v části [SQL: přizpůsobení vaše SQL příkazu záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
     Pokud provádíte spojení dvou nebo více tabulek, přepište `GetDefaultSQL` k přizpůsobení seznamu tabulka použita v SQL **FROM** klauzule. Další informace najdete v tématu [sada záznamů: provedení připojení (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  

-   Ručně vytvořit vazbu další pole datových členů, případně na základě informací, které můžete získat o schématu zdroje dat za běhu. Přidat pole datových členů do třídy sady záznamů [RFX](../../data/odbc/record-field-exchange-using-rfx.md) nebo Bulk RFX funkce volá, aby [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) – členská funkce a inicializacích datových členů v konstruktoru třídy. Další informace najdete v tématu [sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Členské funkce sady záznamů, například přepsání `OnSetOptions`, chcete-li nastavit možnosti specifické pro aplikaci a přepsat výchozí hodnoty.  
  
 Pokud chcete založit na komplexní příkazu SQL sady záznamů, budete muset použít kombinaci těchto technik. Například můžete potřebovat použít klauzuli SQL a klíčová slova nejsou přímo podporována sady záznamů, nebo možná chcete spojit více tabulek.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [ODBC – základy](../../data/odbc/odbc-basics.md)   
 [SQL](../../data/odbc/sql.md)   
 [Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)