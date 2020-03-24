---
title: 'Sada záznamů: Další informace o aktualizacích (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
ms.openlocfilehash: f11c723e4589cb28a3f38100050a69a78fc0809e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212846"
---
# <a name="recordset-more-about-updates-odbc"></a>Sada záznamů: Další informace o aktualizacích (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje:

- [Jak jiné operace, například transakce, ovlivňují aktualizace](#_core_how_transactions_affect_updates).

- [Vaše aktualizace a jiní uživatelé](#_core_your_updates_and_the_updates_of_other_users).

- [Další informace o funkcích aktualizace a odstranění členů](#_core_more_about_update_and_delete).

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, některé informace se nevztahují. Například nemůžete volat `AddNew`, `Edit`, `Delete`a `Update` členské funkce; Můžete však provádět transakce. Další informace o hromadném načítání řádků naleznete v tématu [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>Jak jiné operace ovlivňují aktualizace

Aktualizace jsou ovlivněny transakcemi platnými v době aktualizace, zavřením sady záznamů před dokončením transakce a posouváním před dokončením transakce.

###  <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>Jak transakce ovlivňují aktualizace

Nad rámec pochopení, jak `AddNew`, `Edit`a `Delete` fungují, je důležité pochopit, jak `BeginTrans`, `CommitTrans`a `Rollback` členské funkce [CDatabase](../../mfc/reference/cdatabase-class.md) pracují s funkcemi Update v [CRecordset](../../mfc/reference/crecordset-class.md).

Ve výchozím nastavení volání `AddNew` a `Edit` ovlivňují zdroj dat okamžitě při volání `Update`. `Delete` volání se projeví okamžitě. Můžete ale vytvořit transakci a spustit dávku takových volání. Aktualizace nejsou trvalé, dokud je nepotvrdíte. Pokud si to rozmyslíte, můžete transakci místo potvrzení vrátit zpátky.

Další informace o transakcích naleznete v tématu [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

###  <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>Jak zavírání sady záznamů ovlivňuje aktualizace

Pokud zavřete sadu záznamů nebo její přidružený `CDatabase` objekt s probíhající transakcí (nevolali jste volání [CDatabase:: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) nebo [CDatabase:: Rollback](../../mfc/reference/cdatabase-class.md#rollback)), transakce je vrácena zpět automaticky (Pokud je back-end databáze strojem Microsoft Jet).

> [!CAUTION]
>  Pokud používáte databázový stroj Microsoft Jet, ukončení sady záznamů uvnitř explicitní transakce nevede k uvolnění žádného z řádků, které byly upraveny nebo uzamčeny, dokud se explicitní transakce nepotvrdí nebo nevrátí zpět. Doporučuje se, abyste vždy otevírali i zavřeli sady záznamů uvnitř nebo vně explicitní transakce jet.

###  <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>Jak posouvání ovlivňuje aktualizace

Při [záznamu sady záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) v sadě záznamů je vyrovnávací paměť pro úpravy vyplněna každým novým záznamem (předchozí záznam není uložen jako první). Posouvání přeskočí dříve odstraněné záznamy. Pokud se posunete po `AddNew` nebo `Edit` volání bez volání `Update`, `CommitTrans`nebo `Rollback` jako první, všechny změny se ztratí (bez upozornění), protože nový záznam se načte do vyrovnávací paměti úprav. Upravená vyrovnávací paměť je vyplněna záznamem, na který se přechází, uložený záznam je uvolněn a ve zdroji dat nedochází k žádné změně. To platí pro `AddNew` i `Edit`.

##  <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>Vaše aktualizace a aktualizace dalších uživatelů

Při použití sady záznamů k aktualizaci dat mají aktualizace vliv na ostatní uživatele. Podobně budou aktualizace dalších uživatelů během života vaší sady záznamů ovlivněny.

Ve víceuživatelském prostředí mohou jiní uživatelé otevřít sady záznamů, které obsahují některé ze stejných záznamů, které jste vybrali v sadě záznamů. Změny záznamu před jeho načtením se projeví ve vaší sadě záznamů. Vzhledem k tomu, že dynamické sady načítají záznam pokaždé, když se na něj posouvají, dynamické sady odrážejí změny pokaždé, když se posunete na záznam. Snímky načtou záznam při prvním procházení, takže snímky odrážejí pouze ty změny, ke kterým došlo před přechodem na záznam na začátku.

Záznamy přidané ostatními uživateli po otevření sady záznamů se nezobrazí ve vaší sadě záznamů, pokud se znovu nespustí dotaz. Pokud vaše sada záznamů je dynamická sada, úpravy stávajících záznamů ostatními uživateli se zobrazí ve vaší dynamické sadě při posouvání na ovlivněný záznam. Pokud je vaše sada záznamů snímkem, úpravy se neprojeví, dokud se snímek znovu nespustí. Chcete-li zobrazit záznamy přidané nebo odstraněné jinými uživateli ve vašem snímku nebo záznamy přidané ostatními uživateli v dynamické sadě, zavolejte metodu [CRecordset:: Requery](../../mfc/reference/crecordset-class.md#requery) pro opětovné sestavení sady záznamů. (Všimněte si, že odstranění dalších uživatelů se zobrazí ve vaší dynamické sadě.) Můžete také volat `Requery` pro zobrazení záznamů, které přidáte, ale ne k zobrazení vašich odstranění.

> [!TIP]
>  Chcete-li vynutit ukládání celého snímku do mezipaměti, zavolejte `MoveLast` hned po otevření snímku. Potom zavolejte `MoveFirst` pro zahájení práce se záznamy. `MoveLast` je ekvivalentní posouvání všech záznamů, ale načítá je všechny najednou. Upozorňujeme ale, že to může snížit výkon a nemusí být pro některé ovladače nutné.

Účinky vašich aktualizací na jiné uživatele se podobají jejich efektům.

##  <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>Další informace o Update a DELETE

V této části najdete další informace, které vám pomůžou pracovat s `Update` a `Delete`.

### <a name="update-success-and-failure"></a>Úspěšná aktualizace a chyba

Pokud `Update` úspěšné, `AddNew` nebo `Edit` režim skončí. Chcete-li spustit `AddNew` nebo režim `Edit` znovu, zavolejte `AddNew` nebo `Edit`.

Pokud `Update` selžou (vrátí hodnotu FALSE nebo vyvolá výjimku), zůstanete v režimu `AddNew` nebo `Edit`, a to v závislosti na funkci, kterou jste volali jako poslední. Pak můžete provést jednu z následujících akcí:

- Upravte datový člen pole a zkuste `Update` znovu.

- Zavolejte `AddNew` pro resetování datových členů pole na hodnotu null, nastavte hodnoty datových členů pole a poté zavolejte `Update` znovu.

- Zavolejte `Edit` pro opětovné načtení hodnot, které byly v sadě záznamů před prvním voláním `AddNew` nebo `Edit`, nastavte hodnoty datových členů pole a poté zavolejte `Update` znovu. Po úspěšném `Update` volání (kromě po volání `AddNew`) pole datové členy uchovávají své nové hodnoty.

- Zavolejte `Move` (včetně `Move` s parametrem AFX_MOVE_REFRESH nebo 0), který vyprázdní všechny změny a ukončí jakýkoli `AddNew` nebo `Edit` režim.

### <a name="update-and-delete"></a>Aktualizovat a odstranit

Tato část se týká `Update` i `Delete`.

U operace `Update` nebo `Delete` by se měl aktualizovat jeden a jenom jeden záznam. Tento záznam je aktuální záznam, který odpovídá hodnotám dat v polích sady záznamů. Pokud z nějakého důvodu nejsou ovlivněny žádné záznamy nebo je ovlivněn více než jeden záznam, je vyvolána výjimka obsahující jednu z následujících hodnot **RETCODE** :

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Pokud jsou tyto výjimky vyvolány, zůstanete ve `AddNew` nebo `Edit` stavu, ke kterému jste byli při volání `Update` nebo `Delete`. Tady jsou nejběžnější scénáře, ve kterých tyto výjimky vidíte. Pravděpodobně se zobrazí:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED, když používáte režim optimistického zamykání a jiný uživatel změnil záznam způsobem, který brání architektuře v identifikaci správného záznamu, který se má aktualizovat nebo odstranit.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED, když tabulka, kterou aktualizujete, nemá žádný primární klíč nebo jedinečný index a v sadě záznamů nemáte dost sloupců k jednoznačné identifikaci řádku tabulky.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md)
