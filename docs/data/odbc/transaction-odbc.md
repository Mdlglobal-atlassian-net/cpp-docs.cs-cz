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
ms.openlocfilehash: 49fc0e244dd4f63bd7a69d963ff2a9fbc00ddb6c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212599"
---
# <a name="transaction-odbc"></a>Transakce (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Transakce je způsob, jak seskupit nebo dávkovat série aktualizací do [zdroje dat](../../data/odbc/data-source-odbc.md) tak, aby všechny byly potvrzeny najednou, nebo žádný, pokud transakci vrátíte zpět. Pokud transakci nepoužíváte, změny ve zdroji dat se přiřadí automaticky místo toho, aby je bylo možné zapsat na vyžádání.

> [!NOTE]
>  Ne všechny ovladače ODBC Database podporují transakce. Zavolejte členskou funkci `CanTransact` vašeho [CDatabase](../../mfc/reference/cdatabase-class.md) nebo [CRecordset](../../mfc/reference/crecordset-class.md) objektu, abyste zjistili, jestli váš ovladač podporuje transakce pro danou databázi. Všimněte si, že `CanTransact` vám neřekne, zda zdroj dat poskytuje plnou podporu transakcí. Je také nutné volat `CDatabase::GetCursorCommitBehavior` a `CDatabase::GetCursorRollbackBehavior` po `CommitTrans` a `Rollback` pro kontrolu účinku transakce na otevřeném objektu `CRecordset`.

Volání `AddNew` a `Edit` členské funkce objektu `CRecordset` ovlivňují zdroj dat okamžitě při volání `Update`. `Delete` volání se projeví také okamžitě. Naopak můžete použít transakci skládající se z více volání `AddNew`, `Edit`, `Update`a `Delete`, které jsou provedeny, ale nejsou potvrzeny, dokud nebudete volat `CommitTrans` explicitně. Vytvořením transakce můžete spustit sérii takových volání a přitom zachovat schopnost je vrátit zpět. Pokud není důležitý prostředek k dispozici nebo některá jiná podmínka brání dokončení celé transakce, můžete transakci místo potvrzení změn vrátit zpátky. V takovém případě žádné změny patřící k transakci neovlivňují zdroj dat.

> [!NOTE]
>  Třída `CRecordset` v současné době nepodporuje aktualizace zdroje dat, pokud jste implementovali hromadné načítání řádků. To znamená, že nemůžete provádět volání `AddNew`, `Edit`, `Delete`nebo `Update`. Můžete však napsat vlastní funkce pro provádění aktualizací a pak tyto funkce volat v rámci dané transakce. Další informace o hromadném načítání řádků naleznete v tématu [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Kromě ovlivnění vaší sady záznamů mají transakce vliv na příkazy SQL, které jsou spouštěny přímo, pokud použijete rozhraní ODBC **HDBC** přidružené k vašemu objektu `CDatabase` nebo rozhraní ODBC **HSTMT** založené na tomto **HDBC**.

Transakce jsou zvláště užitečné v případě, že máte více záznamů, které je třeba aktualizovat současně. V takovém případě se chcete vyhnout nedokončené transakci, například může nastat, pokud byla vyvolána výjimka před provedením Poslední aktualizace. Seskupení těchto aktualizací do transakce umožňuje obnovení (vrácení zpět) ze změn a vrátí záznamy do stavu před transakcemi. Pokud například banka přenáší peníze z účtu A na účet B, stažení z a a vklad do B musí úspěšně zpracovat prostředky nebo celá transakce musí selhat.

V databázových třídách provádíte transakce prostřednictvím `CDatabase` objektů. Objekt `CDatabase` představuje připojení ke zdroji dat a jedna nebo více sad záznamů přidružených k danému objektu `CDatabase` pracuje na tabulkách databáze prostřednictvím členských funkcí sady záznamů.

> [!NOTE]
>  Podporovaná je jenom jedna úroveň transakcí. Nemůžete vnořovat transakce, ani nemůže transakce zahrnovat více databázových objektů.

Následující témata obsahují další informace o tom, jak se provádí transakce:

- [Transakce: Provádění transakcí v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transakce: Vliv transakcí na aktualizace (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
