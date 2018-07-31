---
title: 'Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC) | Dokumentace Microsoftu'
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
ms.openlocfilehash: 4082153c87867e0ade989234999fd1d9f5b6ec66
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338269"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)
Toto téma platí pro třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma vysvětluje:  
  
-   [Vaše role a možnosti při výběru záznamů](#_core_your_options_in_selecting_records).  
  
-   [Jak sada záznamů sestavuje příkaz SQL a vybírá záznamy](#_core_how_a_recordset_constructs_its_sql_statement).  
  
-   [Co můžete dělat přizpůsobit výběr](#_core_customizing_the_selection).  
  
 Sady záznamů vybírají záznamy ze zdroje dat prostřednictvím ovladače rozhraní ODBC odesláním příkazů SQL pro ovladač. SQL odeslána závisí na návrh a otevřete třídu sady záznamů.  
  
##  <a name="_core_your_options_in_selecting_records"></a> Možnosti při výběru záznamů  
 V následující tabulce jsou uvedeny možnosti při výběru záznamů.  
  
### <a name="how-and-when-you-can-affect-a-recordset"></a>Jak a kdy může mít vliv na sadu záznamů  
  
|Pokud jste|Můžeš|  
|--------------|-------------|  
|Deklarujete třídu sady záznamů s **přidat třídu** Průvodce|Zadejte které tabulky vybírat.<br /><br /> Zadejte sloupce, které chcete zahrnout.<br /><br /> Zobrazit [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|  
|Dokončení implementaci třídy sady záznamů|Členské funkce přepsat jako `OnSetOptions` (Upřesnit) nastavit možnosti specifické pro aplikace nebo chcete změnit výchozí hodnoty. Zadejte parametry datových členů, pokud chcete parametrizovanou sadu záznamů.|  
|Vytvořte objekt sady záznamů (před voláním `Open`)|Zadejte podmínky vyhledávání (může být složené) pro použití v **kde** klauzuli, která filtruje záznamy. Zobrazit [sada záznamů: filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Určit pořadí řazení pro použití v **klauzule ORDER BY** klauzuli, která seřadí záznamy. Zobrazit [sada záznamů: řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Zadejte hodnoty parametrů pro všechny parametry, které jste přidali do třídy. Zobrazit [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|  

| Sady záznamů dotaz spustíte voláním `Open`| Zadejte vlastní řetězec SQL, chcete-li nahradit řetězec SQL výchozí nastavení průvodce. Zobrazit [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) v *tříd – referenční dokumentace ke knihovně* a [SQL: Přizpůsobení příkazu SQL sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |  

| Volání `Requery` do sady záznamů s nejnovějšími hodnotami ve zdroji dat. requery | Zadejte nové parametry, filtr nebo řazení. Zobrazit [sada záznamů: opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |  
  
##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> Jak sada záznamů sestavuje příkaz SQL  
 Při volání objektu sady záznamů [otevřít](../../mfc/reference/crecordset-class.md#open) členskou funkci `Open` sestavuje příkaz SQL pomocí některé nebo všechny z následujících složek:  
  
-   *Ipszsql* byl předán parametr `Open`. Pokud není NULL, tento parametr určuje vlastní řetězec SQL nebo členem jedné. Rozhraní analyzuje řetězec. Pokud je řetězec SQL **vyberte** příkazu nebo ODBC **volání** prohlášení, rozhraní se použije jako příkazu SQL sady záznamů. Pokud řetězec nemá na začátku "Vyberte" nebo "{volání", systém použije co je součástí konstrukce SQL **FROM** klauzuli.  
  
-   Řetězec vrácený funkcí [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). Ve výchozím nastavení toto je název tabulky, ve které jste zadali pro sady záznamů v průvodci, ale můžete změnit, funkce vrátí. Rámec volá `GetDefaultSQL` – Pokud řetězec nemá na začátku "Vyberte" nebo "{volání", předpokládá se bude název tabulky, který se používá ke konstrukci řetězec SQL.  
  

-   Pole datových členů sady záznamů, které mají být vázaný na konkrétní sloupce v tabulce. Rozhraní framework sváže záznam sloupců adresy tyto členy, jejich použití jako vyrovnávací paměť. Rozhraní určuje korelace pole datových členů na sloupce tabulky z [RFX](../../data/odbc/record-field-exchange-using-rfx.md) nebo Bulk RFX funkce se volá v sadě záznamů [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange ](../../mfc/reference/crecordset-class.md#dofieldexchange) členskou funkci.  
  
-   [Filtr](../../data/odbc/recordset-filtering-records-odbc.md) sady záznamů, pokud existuje, součástí [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) datový člen. Rozhraní tento řetězec používá k vytvoření SQL **kde** klauzuli.  
  
-   [Řazení](../../data/odbc/recordset-sorting-records-odbc.md) pořadí záznamů, pokud existuje, součástí [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) datový člen. Rozhraní tento řetězec používá k vytvoření SQL **klauzule ORDER BY** klauzuli.  

  
    > [!TIP]
    >  Použití SQL **Group** klauzuli (a případně **HAVING** klauzule), připojte na konec řetězce filtru klauzule.  
  
-   Hodnot ve všech [parametry datových členů](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) zadáte pro třídu. Nastavit hodnoty parametrů těsně před voláním `Open` nebo `Requery`. Rozhraní vazby hodnoty parametru "?" zástupné texty v řetězci SQL. V době kompilace můžete zadat řetězec se zástupnými symboly. V době běhu vyplní rozhraní podrobnosti na základě hodnot parametrů, které můžete předat.  
  
 `Open` vytvoří SQL **vyberte** příkaz z těchto složek. Zobrazit [přizpůsobení výběr](#_core_customizing_the_selection) podrobnosti o tom, jak rozhraní používá složek.  
  
 Po vytvoření příkazu, `Open` odešle SQL správce ovladačů ODBC (a knihovna kurzorů rozhraní ODBC, pokud se v paměti), který ho odešle ovladač ODBC pro konkrétní systém DBMS. Ovladač komunikuje s DBMS pro provedení výběru ve zdroji dat a načte první záznam. Rozhraní načte záznam do pole data členů sady záznamů.  
  
 Kombinace těchto postupů můžete otevřít [tabulky](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) a k vytvoření dotazu na základě [spojení](../../data/odbc/recordset-performing-a-join-odbc.md) z více tabulek. Pomocí dalších úprav lze volat [předdefinované dotazy](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (uložené procedury), vyberte tabulku sloupce není známý v době návrhu a [svázat](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) je sada záznamů pole nebo je můžete provádět většiny ostatních přístup k datům úlohy. Nelze provést přizpůsobením sady záznamů úlohy můžete provést i nadále [volání funkcí rozhraní API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) nebo přímo provádění příkazů SQL s [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).  
  
##  <a name="_core_customizing_the_selection"></a> Přizpůsobení výběru  
 Kromě zadání filtru, pořadí řazení nebo parametry, můžete provést následující akce pro přizpůsobení sady záznamů výběr:  
  
-   Zadat vlastní řetězec SQL v *Ipszsql* při volání [otevřít](../../mfc/reference/crecordset-class.md#open) sady záznamů. Nic předáním *lpsqSQL* co má přednost před [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) členská funkce vrátí.  
  
     Další informace najdete v tématu [SQL: SQL příkazu přizpůsobení sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), který popisuje typy příkazů SQL (nebo částečné výpisy) můžete předat `Open` a systém provádí s nimi.  
  
    > [!NOTE]
    >  Pokud vlastní řetězec, který předáte nezačíná "Vyberte" nebo "{volání", MFC předpokládá, že obsahuje název tabulky. To platí i pro další položky seznamu s odrážkami.  
  
-   Příkaz ALTER řetězec, který průvodce zapíše do sady záznamů `GetDefaultSQL` členskou funkci. Upravte kód funkce, chcete-li změnit jej vrátí. Ve výchozím nastavení, Průvodce provádí zápis `GetDefaultSQL` funkce, která vrací jeden název tabulky.  
  
     Můžete mít `GetDefaultSQL` vrátit žádnou z položek, které můžete předat *Ipszsql* parametr `Open`. Pokud nepředáte vlastní řetězec SQL v *Ipszsql*, systém použije řetězec, který `GetDefaultSQL` vrátí. Minimálně `GetDefaultSQL` musí vracet název jedné tabulky. Ale můžete ho vrátit více názvy tabulek, úplné máte **vyberte** příkaz ODBC **volání** příkazu a tak dále. Seznam můžete předat do *Ipszsql* – nebo mít `GetDefaultSQL` vrátit – naleznete v tématu [SQL: SQL příkazu přizpůsobení sady záznamů (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
     Pokud provádíte spojení dvou nebo více tabulek, přepište `GetDefaultSQL` přizpůsobení seznamu tabulka použita v SQL **FROM** klauzuli. Další informace najdete v tématu [sada záznamů: provedení do připojení (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  

-   Ruční svázání datové členy další pole, možná na základě informací, které získáte o schématu zdroje dat v době běhu. Přidejte datové členy polí třídy sady záznamů [RFX](../../data/odbc/record-field-exchange-using-rfx.md) nebo Bulk RFX funkce se volá, aby [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) nebo [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) členská funkce, a Inicializace datových členů v konstruktoru třídy. Další informace najdete v tématu [sada záznamů: dynamické vazby dat sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Přepsat záznamů členské funkce, jako například `OnSetOptions`, chcete-li nastavit možnosti specifické pro aplikaci nebo přepsat výchozí nastavení.  
  
 Pokud chcete založit komplexního příkazu SQL sady záznamů, budete muset použít kombinaci těchto technik. Například možná chcete použít klauzuli SQL a klíčová slova nejsou přímo podporována sady záznamů, nebo možná chcete se připojit se k více tabulek.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [ODBC – základy](../../data/odbc/odbc-basics.md)   
 [SQL](../../data/odbc/sql.md)   
 [Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)