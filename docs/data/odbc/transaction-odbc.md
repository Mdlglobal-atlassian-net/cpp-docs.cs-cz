---
title: Transakce (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
ms.openlocfilehash: 56629f8c5ff74aff4e0df589cda1e7b988fb5fd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376416"
---
# <a name="transaction-odbc"></a>Transakce (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Transakce je způsob, jak seskupit nebo dávkově seskupit řadu aktualizací [zdroje dat](../../data/odbc/data-source-odbc.md) tak, aby všechny potvrzené najednou nebo žádné nejsou potvrzeny, pokud vrátíte transakci zpět. Pokud nepoužijete transakci, změny zdroje dat jsou potvrzeny automaticky, nikoli potvrzeny na vyžádání.

> [!NOTE]
> Transakce nepodporují všechny ovladače databáze ROZHRANÍ ODBC. Volání `CanTransact` členské funkce [objektu CDatabase](../../mfc/reference/cdatabase-class.md) nebo [CRecordset](../../mfc/reference/crecordset-class.md) k určení, zda ovladač podporuje transakce pro danou databázi. Všimněte `CanTransact` si, že neříká, zda zdroj dat poskytuje plnou podporu transakcí. Musíte také `CDatabase::GetCursorCommitBehavior` volat `CDatabase::GetCursorRollbackBehavior` `CommitTrans` a `Rollback` po a zkontrolovat vliv transakce `CRecordset` na otevřený objekt.

Volání `AddNew` a `Edit` členské funkce `CRecordset` objektu ovlivní zdroj dat `Update`okamžitě při volání . `Delete`volání se projeví i okamžitě. Naproti tomu můžete použít transakci skládající se `AddNew`z `Edit` `Update`více `Delete`volání do , , a `CommitTrans` , které jsou prováděny, ale nejsou potvrzeny, dokud explicitně nezavoláte. Vytvořením transakce můžete provést řadu takových volání při zachování možnosti vrátit je zpět. Pokud kritický prostředek není k dispozici nebo některé jiné podmínky brání dokončení celé transakce, můžete vrátit zpět transakce namísto potvrzení. V takovém případě žádná ze změn, které patří k transakci, neovlivní zdroj dat.

> [!NOTE]
> V současné `CRecordset` době třída nepodporuje aktualizace zdroje dat, pokud jste implementovali hromadné načítání řádků. To znamená, že `AddNew`nelze `Edit` `Delete`volat `Update`do aplikace , , , nebo . Můžete však napsat vlastní funkce k provedení aktualizací a potom volat tyto funkce v rámci dané transakce. Další informace o hromadném načítání řádků naleznete v tématu [Recordset: Fetching Records in Bulk (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

> [!NOTE]
> Kromě ovlivnění sady záznamů ovlivňují transakce příkazy SQL, které provádíte přímo, pokud `CDatabase` používáte rozhraní ODBC **HDBC** přidružené k objektu nebo rozhraní **ODBC HSTMT** na základě tohoto **rozhraní HDBC**.

Transakce jsou užitečné zejména v případě, že máte více záznamů, které musí být aktualizovány současně. V takovém případě se chcete vyhnout napůl dokončené transakce, jako je například může dojít, pokud byla vyvolána výjimka před poslední aktualizace byla provedena. Seskupení těchto aktualizací do transakce umožňuje obnovení (vrácení zpět) ze změn a vrátí záznamy do stavu před transakcí. Pokud například banka převede peníze z účtu A na účet B, musí výběr z a i vklad do B úspěšně zpracovat prostředky správně nebo celá transakce musí selhat.

V databázových třídách provádíte `CDatabase` transakce prostřednictvím objektů. Objekt `CDatabase` představuje připojení ke zdroji dat a jedna nebo více `CDatabase` sad záznamů přidružených k tomuto objektu pracuje s tabulkami databáze prostřednictvím členských funkcí sady záznamů.

> [!NOTE]
> Je podporována pouze jedna úroveň transakcí. Nelze vnořit transakce ani transakce rozpětí více databázových objektů.

Následující témata poskytují další informace o způsobu provádění transakcí:

- [Transakce: Provádění transakcí v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transakce: Vliv transakcí na aktualizace (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Viz také

[Připojení k otevřené databázi (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
