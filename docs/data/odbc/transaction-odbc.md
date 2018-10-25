---
title: Transakce (ODBC) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ba77eb5289dcd2bd169b85fe9a595c231a86cf4c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056168"
---
# <a name="transaction-odbc"></a>Transakce (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Transakce je způsob, jak seskupit nebo dávka, řadu aktualizací služby [zdroj dat](../../data/odbc/data-source-odbc.md) tak, aby byly všechny najednou, nebo žádná není potvrzena, pokud vrátíte zpět transakce. Pokud nepoužijete transakce, změny do zdroje dat. usilujeme o to automaticky místo potvrzuje na vyžádání.

> [!NOTE]
>  Ne všechny ovladače rozhraní ODBC databáze podporu transakcí. Volání `CanTransact` členskou funkci vaše [CDatabase](../../mfc/reference/cdatabase-class.md) nebo [CRecordset](../../mfc/reference/crecordset-class.md) objektem pro určení, jestli ovladač podporuje transakce pro danou databázi. Všimněte si, že `CanTransact` není zjistíte, zda zdroj dat obsahuje plnou podporu transakcí. Musíte také zavolat `CDatabase::GetCursorCommitBehavior` a `CDatabase::GetCursorRollbackBehavior` po `CommitTrans` a `Rollback` chcete zkontrolovat dopad transakce na otevřený `CRecordset` objektu.

Volání `AddNew` a `Edit` členské funkce `CRecordset` ovlivní zdroj dat okamžitě při volání objektu `Update`. `Delete` volání také projeví okamžitě. Naproti tomu můžete použít transakci, který se skládá z více volání `AddNew`, `Edit`, `Update`, a `Delete`, které jsou prováděny, ale nikoli potvrdit až do okamžiku volání `CommitTrans` explicitně. Tím, že transakce, můžete provést řadu těchto volání při zachování možnost vrátit zpět změny. Pokud kritické prostředek není dostupný nebo některých jiných podmínek brání celá transakce nebránily dokončení, můžete místo jeho potvrzení transakce vrátit zpět. V takovém případě žádná ze změn, které patří k transakci ovlivní zdroj dat.

> [!NOTE]
>  V současné době třídy `CRecordset` nepodporuje aktualizace ke zdroji dat, pokud jste implementovali hromadné načítání řádků. To znamená, že nemůžete provádět volání `AddNew`, `Edit`, `Delete`, nebo `Update`. Můžete je ale napsat vlastní funkce pro provádění aktualizací a potom volání těchto funkcí v rámci dané transakce. Další informace o hromadném načítání řádků naleznete v tématu [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Kromě by to ovlivnilo sady záznamů, transakce ovlivňují příkazy SQL, které můžete provést přímo za předpokladu, použijte rozhraní ODBC **HDBC** přidružené k vaší `CDatabase` objektu nebo ODBC **HSTMT** na základě který **HDBC**.

Transakce jsou zvláště užitečné v případě, že máte více záznamů, které musí být aktualizovány současně. V tomto případě chcete se vyhnout transakce napůl dokončený, například může dojít, pokud došlo k výjimce předtím, než byla provedena poslední aktualizace. Seskupení těchto aktualizací do transakce umožňuje obnovení změny (vrácení zpět) a vrátí záznamy do stavu před transakcí. Například pokud banka přenese peníze z účtu A k účtu B, stažení zálohy A a B musí být správně zpracovat fondů i musí selhat, celá transakce.

V databázové třídy provádět transakce prostřednictvím `CDatabase` objekty. A `CDatabase` objekt představuje připojení ke zdroji dat, a přidruženou jednu nebo více sad záznamů s `CDatabase` objekt pracovat v tabulkách databáze pomocí členské funkce sady záznamů.

> [!NOTE]
>  Je podporován pouze jednu úroveň transakce. Nelze vnořovat transakce ani může zahrnovat více databázových objektů.

Další informace o tom, jak se transakce provádějí v následujících tématech:

- [Transakce: Provádění transakcí v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transakce: Vliv transakcí na aktualizace (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)