---
title: 'Transakce: Vliv transakcí na aktualizace (rozhraní ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
ms.openlocfilehash: 8a87176ecb20beaf46583e1190b0ad458d508b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376421"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transakce: Vliv transakcí na aktualizace (rozhraní ODBC)

Aktualizace [zdroje dat](../../data/odbc/data-source-odbc.md) jsou spravovány během transakcí pomocí vyrovnávací paměti pro úpravy (stejná metoda používaná mimo transakce). Datové členy pole sady záznamů společně slouží jako vyrovnávací paměť pro úpravy, která obsahuje aktuální `AddNew` záznam, který sada záznamů dočasně zálohuje během nebo . `Edit` Během `Delete` operace není aktuální záznam zálohován v rámci transakce. Další informace o vyrovnávací paměti pro úpravy a způsobu ukládání aktualizací aktuálního záznamu naleznete v tématu [Recordset: How Recordsets Update Records (ODBC).](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

> [!NOTE]
> Pokud jste implementovali hromadné načítání řádků, `Edit`nelze `Delete`volat `AddNew`, nebo . Místo toho je nutné napsat vlastní funkce k provedení aktualizací zdroje dat. Další informace o hromadném načítání řádků naleznete v tématu [Recordset: Fetching Records in Bulk (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Během transakcí, `AddNew` `Edit`, `Delete` a operace mohou být potvrzeny nebo vráceny zpět. Účinky `CommitTrans` a `Rollback` může způsobit aktuální záznam nelze obnovit do vyrovnávací paměti úprav. Chcete-li se ujistit, že aktuální záznam je správně `CommitTrans` `Rollback` obnoven, `CDatabase` je důležité pochopit, `CRecordset`jak a členské funkce práce s funkcemi aktualizace .

## <a name="how-committrans-affects-updates"></a><a name="_core_how_committrans_affects_updates"></a>Jak CommitTrans ovlivňuje aktualizace

Následující tabulka vysvětluje účinky `CommitTrans` na transakce.

### <a name="how-committrans-affects-updates"></a>Jak CommitTrans ovlivňuje aktualizace

|Operace|Stav zdroje dat|
|---------------|---------------------------|
|`AddNew`a `Update`, a pak`CommitTrans`|Do zdroje dat se přidá nový záznam.|
|`AddNew`(bez `Update`) a poté`CommitTrans`|Nový rekord je ztracen. Záznam nebyl přidán do zdroje dat.|
|`Edit`a `Update`, a pak`CommitTrans`|Úpravy potvrzené ke zdroji dat.|
|`Edit`(bez `Update`) a poté`CommitTrans`|Úpravy záznamu budou ztraceny. Záznam zůstane ve zdroji dat nezměněn.|
|`Delete`Pak`CommitTrans`|Záznamy odstraněné ze zdroje dat.|

## <a name="how-rollback-affects-transactions"></a><a name="_core_how_rollback_affects_updates"></a>Jak vrácení zpět ovlivňuje transakce

Následující tabulka vysvětluje účinky `Rollback` na transakce.

### <a name="how-rollback-affects-transactions"></a>Jak vrácení zpět ovlivňuje transakce

|Operace|Stav aktuálního záznamu|Musíte také|Stav zdroje dat|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew`a `Update`, pak`Rollback`|Obsah aktuálního záznamu je dočasně uložen, aby se uvolnilo místo pro nový záznam. Nový záznam je zadán do vyrovnávací paměti pro úpravy. Po `Update` volání je aktuální záznam obnoven do vyrovnávací paměti pro úpravy.||Přidání ke zdroji `Update` dat provedenému je obráceno.|
|`AddNew`(bez), `Update`pak`Rollback`|Obsah aktuálního záznamu je dočasně uložen, aby se uvolnilo místo pro nový záznam. Upravit vyrovnávací paměť obsahuje nový záznam.|Volání `AddNew` znovu obnovit upravit vyrovnávací paměti do prázdné, nový záznam. Nebo `Move`volání (0) obnovit staré hodnoty upravit vyrovnávací paměti.|Protože `Update` nebylvolán, nebyly provedeny žádné změny ve zdroji dat.|
|`Edit`a `Update`, pak`Rollback`|Dočasně je uložena neupravená verze aktuálního záznamu. Úpravy jsou provedeny k obsahu vyrovnávací paměti úprav. Po `Update` volání je neupravená verze záznamu stále dočasně uložena.|*Dynaset*: Posunutím z aktuálního záznamu pak zpět obnovit neupravenou verzi záznamu do vyrovnávací paměti pro úpravy.<br /><br /> *Snímek* `Requery` : Volání aktualizace sady záznamů ze zdroje dat.|Změny zdroje dat `Update` provedené pomocí jsou stornovány.|
|`Edit`(bez), `Update`pak`Rollback`|Dočasně je uložena neupravená verze aktuálního záznamu. Úpravy jsou provedeny k obsahu vyrovnávací paměti úprav.|Volání `Edit` znovu obnovit neupravenou verzi záznamu do vyrovnávací paměti pro úpravy.|Protože `Update` nebylvolán, nebyly provedeny žádné změny ve zdroji dat.|
|`Delete`Pak`Rollback`|Obsah aktuálního záznamu bude odstraněn.|Volání `Requery` obnovení obsahu aktuálního záznamu ze zdroje dat.|Odstranění dat ze zdroje dat je obráceno.|

## <a name="see-also"></a>Viz také

[Transakce (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transakce: Provádění transakcí v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
