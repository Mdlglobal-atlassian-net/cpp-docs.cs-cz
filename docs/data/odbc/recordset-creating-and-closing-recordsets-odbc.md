---
title: 'Sada záznamů: Vytváření a uzavírání sad záznamů (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bbf020e12151e666aa8f88098865b1624403b828
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Sada záznamů: Vytváření a uzavírání sad záznamů (rozhraní ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Pokud chcete použít sadu záznamů, vytvořte objekt sady záznamů a potom volejte jeho **otevřete** – členská funkce Spustit dotaz sady záznamů a vybrat záznamy. Když skončíte s sadu záznamů, zavřete a odstraňte objekt.  
  
 Toto téma vysvětluje:  
  
-   [Kdy a jak vytvořit objekt sady záznamů](#_core_creating_recordsets_at_run_time).  
  
-   [Kdy a jak kvalifikovat chování sady záznamů jako parametrizování, filtrování, řazení nebo zamykání](#_core_setting_recordset_options).  
  
-   [Kdy a jak zavřít objekt sady záznamů](#_core_closing_a_recordset).  
  
##  <a name="_core_creating_recordsets_at_run_time"></a> Vytvoření sady záznamů v době běhu  
 Před vytvořením objektů sady záznamů v programu, obvykle zápisu třídy sady záznamů specifické pro aplikaci. Další informace o tomto předběžném kroku najdete v tématu [přidání příjemce rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Pokud je nutné vybrat záznamy ze zdroje dat, otevřete objekt dynamická sada nebo snímek. Typ objektu k vytvoření závisí na co musíte udělat s daty v aplikaci a na co ovladač ODBC podporuje. Další informace najdete v tématu [dynamická sada](../../data/odbc/dynaset.md) a [snímku](../../data/odbc/snapshot.md).  
  
#### <a name="to-open-a-recordset"></a>Chcete-li otevřít sady záznamů  
  
1.  Sestavte objekt vaší `CRecordset`-odvozené třídy.  
  
     Můžete vytvořit objekt v haldě nebo na rámec zásobníku funkce.  
  
2.  Volitelně můžete změňte výchozí chování sady záznamů. Dostupné možnosti najdete v tématu [nastavení možností sady záznamů](#_core_setting_recordset_options).  
  
3.  Volání objektu [otevřete](../../mfc/reference/crecordset-class.md#open) – členská funkce.  
  
 V konstruktoru, můžete předat ukazatel `CDatabase` objektu nebo předejte **NULL** pomocí dočasného databázového objektu, který rozhraní framework vytvoří a otevře na základě připojovací řetězec vrácený [GetDefaultConnect – ](../../mfc/reference/crecordset-class.md#getdefaultconnect) – členská funkce. `CDatabase` Objekt již může být připojen ke zdroji dat.  
  
 Volání **otevřete** použije k výběru záznamy ze zdroje dat SQL. Na první záznam vybrané (pokud existuje) je aktuální záznam. Hodnoty polí tento záznam jsou uložené v objektu sady záznamů pole datových členů. Pokud nebyly vybrány žádné záznamy, jak `IsBOF` a `IsEOF` členské funkce vrátí 0.  
  
 Ve vašem [otevřete](../../mfc/reference/crecordset-class.md#open) volání, můžete:  
  
-   Zadejte, zda je záznamů dynamická sada nebo snímek. Sady záznamů otevřete jako snímky ve výchozím nastavení. Nebo můžete zadat dopředné sady záznamů, které umožňují pouze posouvání vpřed, jeden záznam současně.  
  
     Ve výchozím nastavení, používá výchozí typ uložené v sada záznamů `CRecordset` – datový člen **m_nDefaultType**. Průvodci napsat kód pro inicializaci **m_nDefaultType** typ sady záznamů, vyberte v průvodci. Místo přijetí toto výchozí nastavení, můžete nahradit jinou sadu záznamů typu.  
  
-   Zadejte řetězec, která nahradí výchozí SQL **vyberte** příkaz, který vytváří sadu záznamů.  
  
-   Zadejte, zda je jen pro čtení, nebo pouze připojení záznamů. Sady záznamů povolit úplnou aktualizaci ve výchozím nastavení, ale můžete omezit, které k přidávání nových záznamů pouze nebo zakážete všechny aktualizace.  
  
 Následující příklad ukazuje, jak otevřít objekt snímek jen pro čtení třídy `CStudentSet`, třídu specifické pro aplikaci:  
  
```  
// Construct the snapshot object  
CStudentSet rsStudent( NULL );  
// Set options if desired, then open the recordset  
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))  
    return FALSE;  
// Use the snapshot to operate on its records...  
```  
  
 Po zavolání metody **otevřete**, použít členské funkce a data členů objekt pro práci se záznamy. V některých případech můžete chtít requery nebo aktualizovat sadu záznamů o změnách, k nimž došlo na datovém zdroji. Další informace najdete v tématu [sada záznamů: opětovné spuštění dotazu sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).  
  
> [!TIP]
>  Připojovací řetězec, který použijete při vývoji nemusí být stejný řetězec připojení, který případné uživatelé potřebovat. Zobecňování vaší aplikace v tomto ohledu, najdete v části [zdroj dat: Správa připojení (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).  
  
##  <a name="_core_setting_recordset_options"></a> Nastavení možností sady záznamů  
 Po sestavení objektu sady záznamů, ale před voláním **otevřete** vybrat záznamy, můžete chtít nastavit některé možnosti řízení chování sady záznamů. Pro všechny sady záznamů můžete:  
  
-   Zadejte [filtru](../../data/odbc/recordset-filtering-records-odbc.md) omezit výběr záznamů.  
  
-   Zadejte [řazení](../../data/odbc/recordset-sorting-records-odbc.md) pořadí záznamů.  
  
-   Zadejte [parametry](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) , můžete vybrat záznamů pomocí informací získaných nebo vypočtených za běhu.  
  
 Můžete také nastavit následující možnost splnění podmínek:  
  
-   Pokud sada záznamů je aktualizovat a podporuje možnosti uzamčení, zadejte [uzamčení](../../data/odbc/recordset-locking-records-odbc.md) metodu používanou pro aktualizace.  
  
> [!NOTE]
>  Pokud chcete ovlivnit výběr záznamů, musíte nastavit tyto možnosti před voláním **otevřete** – členská funkce.  
  
##  <a name="_core_closing_a_recordset"></a> Zavírání sady záznamů  
 Až skončíte s sady záznamů, musíte dispose ho a navrátit její paměť.  
  
#### <a name="to-close-a-recordset"></a>Zavřete sady záznamů  
  
1.  Volání jeho [Zavřít](../../mfc/reference/crecordset-class.md#close) – členská funkce.  
  
2.  Zničte objekt sady záznamů.  
  
     Pokud deklarovaný na rámec zásobníku funkce, objekt automaticky zničen při opuštění oboru. Jinak použijte **odstranit** operátor.  
  
 **Zavřít** uvolní sady záznamů **HSTMT** zpracování. Toto nezničí objekt jazyka C++.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)   
 [Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)