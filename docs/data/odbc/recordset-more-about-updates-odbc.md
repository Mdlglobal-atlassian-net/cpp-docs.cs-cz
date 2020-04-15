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
ms.openlocfilehash: 955b26137ce976514d84f95f4d819779b93bd78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368677"
---
# <a name="recordset-more-about-updates-odbc"></a>Sada záznamů: Další informace o aktualizacích (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Toto téma vysvětluje:

- [Jak ostatní operace, například transakce, ovlivňují aktualizace](#_core_how_transactions_affect_updates).

- [Vaše aktualizace a aktualizace ostatních uživatelů](#_core_your_updates_and_the_updates_of_other_users).

- [Další informace o členských funkcích Aktualizovat a odstranit](#_core_more_about_update_and_delete).

> [!NOTE]
> Toto téma se vztahuje `CRecordset` na objekty odvozené od, ve kterém hromadné načítání řádků nebyla implementována. Pokud jste implementovali hromadné načítání řádků, některé informace se nevztahují. Nelze například volat `AddNew`, `Edit` `Delete`, `Update` a členské funkce; můžete však provádět transakce. Další informace o hromadném načítání řádků naleznete v tématu [Recordset: Fetching Records in Bulk (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>Jak ostatní operace ovlivňují aktualizace

Vaše aktualizace jsou ovlivněny transakcemi, které jsou platné v době aktualizace, uzavřením sady záznamů před dokončením transakce a posouváním před dokončením transakce.

### <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>Jak transakce ovlivňují aktualizace

Kromě `AddNew`pochopení, `Edit`jak `Delete` , , a práce, `BeginTrans` `CommitTrans`je `Rollback` důležité pochopit, jak , a členské funkce [CDatabase](../../mfc/reference/cdatabase-class.md) pracovat s funkcemi aktualizace [CRecordset](../../mfc/reference/crecordset-class.md).

Ve výchozím nastavení `AddNew` `Edit` volá a ovlivňuje zdroj `Update`dat okamžitě při volání . `Delete`volání se projeví okamžitě. Ale můžete vytvořit transakci a provést dávku těchto volání. Aktualizace nejsou trvalé, dokud je nepotvrdíte. Pokud změníte názor, můžete transakci vrátit zpět namísto potvrzení.

Další informace o transakcích naleznete v [tématu Transakce (ODBC).](../../data/odbc/transaction-odbc.md)

### <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>Jak zavření sady záznamů ovlivňuje aktualizace

Pokud zavřete sadu záznamů nebo `CDatabase` její přidružený objekt s probíhající transakcí (nevolali jste [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) nebo [CDatabase::Rollback),](../../mfc/reference/cdatabase-class.md#rollback)bude transakce vrácena zpět automaticky (pokud back-end databáze databáze Microsoft Jet).

> [!CAUTION]
> Pokud používáte databázový stroj Microsoft Jet, zavření sady záznamů uvnitř explicitní transakce nemá za následek uvolnění žádné řádky, které byly změněny nebo zámky, které byly umístěny, dokud explicitní transakce je potvrzena nebo vrácena zpět. Doporučujeme vždy otevřít a zavřít sady záznamů uvnitř nebo vně explicitní transakce Jet.

### <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>Jak posouvání ovlivňuje aktualizace

Při [sadě záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) v sadě záznamů je vyrovnávací paměť pro úpravy vyplněna každým novým aktuálním záznamem (předchozí záznam není uložen jako první). Posouvání přeskočí záznamy, které byly dříve odstraněny. Pokud se posunete za `Update` `CommitTrans`voláním `Rollback` `AddNew` nebo `Edit` zavoláte bez volání , nebo nejprve dojde ke ztrátě všech změn (bez upozornění) při převedení nového záznamu do vyrovnávací paměti pro úpravy. Vyrovnávací paměť pro úpravy je vyplněna záznamem posouvaným na, uložený záznam je uvolněn a ve zdroji dat nedojde k žádné změně. To platí pro `AddNew` `Edit`obě a .

## <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>Vaše aktualizace a aktualizace ostatních uživatelů

Při aktualizaci dat pomocí sady záznamů ovlivní aktualizace ostatní uživatele. Podobně vás ovlivní aktualizace ostatních uživatelů během doby životnosti sady záznamů.

Ve víceuživatelském prostředí mohou ostatní uživatelé otevírat sady záznamů, které obsahují některé ze stejných záznamů, které jste vybrali v sadě záznamů. Změny záznamu před jeho načtením se projeví v sadě záznamů. Vzhledem k tomu, že dynasady načítají záznam při každém přecvaknutí, projeví se změny při každém přechodu na záznam. Snímky načíst záznam při prvním přejděte na něj, takže snímky odrážejí pouze ty změny, ke kterým dojde před přejděte na záznam zpočátku.

Záznamy přidané jinými uživateli po otevření sady záznamů se v sadě záznamů nezobrazí, pokud se znovu nedotazujete. Pokud je vaše sada záznamů dynaset, úpravy existujících záznamů jinými uživateli se zobrazí v dynasetě při přechodu na ovlivněný záznam. Pokud je vaše sada záznamů snímek, úpravy se nezobrazí, dokud znovu dotaz na snímek. Pokud chcete zobrazit záznamy přidané nebo odstraněné jinými uživateli ve snímku nebo záznamy přidané jinými uživateli v dynasetě, zavolejte [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) pro opětovné sestavení sady záznamů. (Všimněte si, že odstranění ostatních uživatelů se zobrazí ve vaší dynasetě.) Můžete také `Requery` volat, abyste viděli záznamy, které přidáte, ale neabyste viděli odstranění.

> [!TIP]
> Chcete-li vynutit ukládání celého `MoveLast` snímku do mezipaměti najednou, volejte ihned po otevření snímku. Pak `MoveFirst` volání začít pracovat se záznamy. `MoveLast`je ekvivalentní posouvání přes všechny záznamy, ale načte je všechny najednou. Všimněte si však, že to může snížit výkon a nemusí být vyžadováno pro některé ovladače.

Účinky vašich aktualizací na ostatní uživatele jsou podobné jejich účinkům na vás.

## <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>Další informace o aktualizaci a odstranění

Tato část obsahuje další informace, `Update` `Delete`které vám pomohou pracovat s a .

### <a name="update-success-and-failure"></a>Aktualizovat úspěch a neúspěch

Pokud `Update` je úspěšná, `AddNew` režim nebo `Edit` končí. Chcete-li `AddNew` `Edit` znovu zahájit `AddNew` `Edit`nebo režim, zavolejte nebo .

Pokud `Update` selže (vrátí FALSE nebo vyvolá výjimku), zůstanete v `AddNew` režimu nebo `Edit` režimu, v závislosti na funkci, kterou voláte poslední. Poté můžete provést jednu z následujících akcí:

- Upravte datový člen pole `Update` a akci opakujte.

- Volání `AddNew` obnovit datové členy pole na hodnotu Null, nastavit hodnoty `Update` datových členů pole a pak znovu zavolat.

- Volání `Edit` znovu načíst hodnoty, které byly v sadě `AddNew` `Edit`záznamů před prvním voláním nebo , `Update` nastavte hodnoty datových členů pole a pak znovu volat. Po úspěšném `Update` volání (s výjimkou po `AddNew` volání) si členové dat pole zachovávají své nové hodnoty.

- Volání `Move` (včetně `Move` s parametrem AFX_MOVE_REFRESH nebo 0), který vyprázdní všechny změny a ukončí všechny `AddNew` nebo `Edit` režim v platnosti.

### <a name="update-and-delete"></a>Aktualizovat a odstranit

Tato část se `Update` vztahuje `Delete`na obě a .

V `Update` operaci `Delete` nebo by měl být aktualizován jeden a pouze jeden záznam. Tento záznam je aktuální záznam, který odpovídá datovým hodnotám v polích sady záznamů. Pokud z nějakého důvodu nejsou ovlivněny žádné záznamy nebo je ovlivněnvíce než jeden záznam, je vyvolána výjimka obsahující jednu z následujících hodnot **RETCODE:**

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Při vyvolání těchto výjimek zůstanete `AddNew` `Edit` ve stavu nebo, `Update` ve `Delete`které jste byli při volání nebo . Zde jsou nejběžnější scénáře, ve kterých by se tyto výjimky zoašili. S největší pravděpodobností uvidíte:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED, pokud používáte optimistický režim zamykání a jiný uživatel upravil záznam způsobem, který brání rozhraní framework u identifikace správného záznamu aktualizovat nebo odstranit.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED, pokud aktualizace tabulky nemá žádný primární klíč nebo jedinečný index a nemáte v sadě záznamů dostatek sloupců, které by jednoznačně identifikovaly řádek tabulky.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md)
