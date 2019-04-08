---
title: 'Recordset: Informace o aktualizacích (ODBC)'
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
ms.openlocfilehash: c29ff110fc507c4e449b2f3d082d98c159a35107
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040765"
---
# <a name="recordset-more-about-updates-odbc"></a>Recordset: Informace o aktualizacích (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje:

- [Vliv na jiné operace, jako je například transakce, aktualizace](#_core_how_transactions_affect_updates).

- [Vaše aktualizace i u jiných uživatelů](#_core_your_updates_and_the_updates_of_other_users).

- [Další informace o členské funkce Update a Delete](#_core_more_about_update_and_delete).

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené z `CRecordset` v který řádek hromadné načítání není implementovaná. Pokud jste implementovali hromadné načítání řádků, některé informace se nevztahují. Například nelze volat `AddNew`, `Edit`, `Delete`, a `Update` členské funkce; však může provádět transakce. Další informace o hromadném načítání řádků naleznete v tématu [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="_core_how_other_operations_affect_updates"></a> Vliv na ostatní operace aktualizace

Vaše aktualizace jsou ovlivněny transakce v platnosti v době aktualizace po zavření sady záznamů před dokončením transakce a posuňte před dokončením transakce.

###  <a name="_core_how_transactions_affect_updates"></a> Vliv transakcí na aktualizace

Kromě pochopení jak `AddNew`, `Edit`, a `Delete` práce, je důležité pochopit, jak `BeginTrans`, `CommitTrans`, a `Rollback` členské funkce [CDatabase](../../mfc/reference/cdatabase-class.md) fungují s aktualizace funkcí [CRecordset](../../mfc/reference/crecordset-class.md).

Ve výchozím nastavení, volání `AddNew` a `Edit` ovlivní zdroj dat okamžitě při volání `Update`. `Delete` volání se projeví okamžitě. Ale můžete vytvořit transakci a spusťte dávku těchto volání. Aktualizace nejsou trvalé, dokud je nepotvrdíte. Pokud změníte své rozhodnutí, můžete místo potvrzení transakce vrátit zpět.

Další informace o transakcích najdete v tématu [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

###  <a name="_core_how_closing_the_recordset_affects_updates"></a> Uzavření sady záznamů vliv aktualizace

Pokud zavřete sadě záznamů nebo jeho přidružené `CDatabase` objektu s transakcí v průběhu (nebyla volána [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) nebo [CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback)), transakce je vrácena. jenom automaticky (Pokud back-endu databáze je databázový stroj Microsoft Jet).

> [!CAUTION]
>  Pokud používáte databázový stroj Microsoft Jet, zavření sady záznamů v explicitní transakci nemá za následek uvolnění všech řádků, které byly změněny na zámků, které byly umístěny, dokud je explicitní transakce potvrzena nebo vrácena zpět. Doporučujeme tuto je vždy otevřít i zavřít sady záznamů uvnitř nebo vně explicitní Jet transakce.

###  <a name="_core_how_scrolling_affects_updates"></a> Posouvání vliv aktualizace

Pokud jste [sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) v sadě záznamů vyrovnávací paměť pro úpravu zaplněný s každým novým záznamem (předchozí záznam není uložen). Posouvání přeskakuje dříve odstraněné záznamy. Pokud se posunete za `AddNew` nebo `Edit` volání bez volání `Update`, `CommitTrans`, nebo `Rollback` nejprve, všechny změny budou ztraceny (bez upozornění) jako nový záznam přenese do vyrovnávací paměti pro úpravy. Vyrovnávací paměť pro úpravu je vyplněn záznam přechod na uložený záznam je uvolněn a nedošlo k žádné změně ve zdroji dat. To platí pro obě `AddNew` a `Edit`.

##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> Vaše aktualizace a aktualizace jiných uživatelů

Pokud používáte sadu záznamů k aktualizaci dat, vaše aktualizace ovlivnit jiné uživatele. Podobně aktualizací po celou dobu životnosti sady záznamů jiných uživatelů vás týkají.

V prostředí ostatní uživatelé mohou otevřít sady záznamů, které obsahují některé stejné záznamy, které jste vybrali ve vaší sadě záznamů. Změny v záznamu před jeho načtení se projeví v sady záznamů. Protože dynamické sady načíst záznam pokaždé, když posunutí, dynamické změny projeví pokaždé, když přejděte k záznamu. Snímky načíst záznam poprvé posun, tak snímky odrážejí pouze ty změny, ke kterým dojde před přejděte na tento záznam původně.

Záznamy přidané další uživatele po otevření sady záznamů se nezobrazí ve vaší sadě záznamů, není-li se znovu spustí dotaz. Pokud sady záznamů je dynamická sada, úpravy existujících záznamů jinými uživateli zobrazí ve vašich dynamických sad při posouvání na daný záznam. Pokud sady záznamů je snímek, úpravy se nezobrazí, dokud requery snímku. Pokud chcete zobrazit záznamy přidali nebo volání odstraněné jinými uživateli ve vaší snímku, nebo přidat jinými uživateli ve vaší dynamických sad záznamů [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) znovu vytvořit sadu záznamů. (Všimněte si, že odstranění ostatním uživatelům zobrazit na vaší dynamických sad.) Můžete také volat `Requery` zobrazíte záznamy přidáte, ale nejsou vidět vaše odstranění.

> [!TIP]
>  Chcete-li vynutit, ukládání do mezipaměti pro celou najednou snímku, zavolejte `MoveLast` okamžitě po otevření snímku. Poté zavolejte `MoveFirst` začít pracovat s záznamy. `MoveLast` je ekvivalentní k posouvání přes všechny záznamy, ale získává je všechny najednou. Upozorňujeme, že to může snížit výkon a nemusí být nutná pro některé ovladače.

Účinky aktualizace pro ostatní uživatele jsou podobné jejich dopadu na vás.

##  <a name="_core_more_about_update_and_delete"></a> Další informace o aktualizace a odstranění

Tato část obsahuje další informace, které vám pomohou při práci s `Update` a `Delete`.

### <a name="update-success-and-failure"></a>Aktualizace úspěchy a chyby

Pokud `Update` proběhne úspěšně, `AddNew` nebo `Edit` ukončením režimu. Chcete-li začít `AddNew` nebo `Edit` režimu znovu, volání `AddNew` nebo `Edit`.

Pokud `Update` selže (vrátí hodnotu FALSE nebo vyvolá výjimku), zůstanou v `AddNew` nebo `Edit` režim, v závislosti na funkci, která jste volali poslední. Potom můžete provést jednu z následujících:

- Upravit pole datového člena a zkuste `Update` znovu.

- Volání `AddNew` obnovit datové členy polí na hodnotu Null, nastavte hodnoty datové členy polí a poté zavolejte `Update` znovu.

- Volání `Edit` k opětovnému načtení hodnoty, které byly v sadě záznamů před prvním volání `AddNew` nebo `Edit`, nastavte hodnoty datové členy polí a poté zavolejte `Update` znovu. Po úspěšném `Update` volání (s výjimkou po `AddNew` volání), datové členy polí zachovat nové hodnoty.

- Volání `Move` (včetně `Move` s parametrem AFX_MOVE_REFRESH nebo 0), která vyprázdní všechny změny a ukončí všechny `AddNew` nebo `Edit` režimu platná.

### <a name="update-and-delete"></a>Update a Delete

Tato část se týká obou `Update` a `Delete`.

Na `Update` nebo `Delete` operace, je třeba aktualizovat jenom jeden záznam. Tento záznam je aktuální záznam, který odpovídá datových hodnot v polích záznamů. Pokud z nějakého důvodu nejsou ovlivněny žádné záznamy vliv na jeden nebo více než jeden záznam je, je vyvolána výjimka, obsahující jednu z následujících **RETCODE** hodnoty:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Při vyvolání těchto výjimek, zůstanou v `AddNew` nebo `Edit` stavu byly jste volali `Update` nebo `Delete`. Tady jsou nejběžnějších scénářů, ve kterých uvidíte tyto výjimky. Budete nejpravděpodobněji naleznete v tématu:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED při použití režimu optimistického zamykání a jiný uživatel upravil záznam způsobem, který brání rozhraní identifikace správný záznam, aktualizovat nebo odstranit.

- Při aktualizaci tabulky AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED, která nemá primární klíč nebo jedinečný index a nemáte dostatek sloupců v sadě záznamů k jedinečné identifikaci řádků tabulky.

## <a name="see-also"></a>Viz také:

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Výměna pole záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md)