---
title: Transakce (ODBC) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 38348bb2c1e78111e996cf84ae4bc81aceb96895
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="transaction-odbc"></a>Transakce (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Transakce je způsob, jak skupinu nebo dávky, řadu aktualizací [zdroj dat](../../data/odbc/data-source-odbc.md) tak, aby byly všechny najednou, nebo žádná není potvrzena, pokud je vrácení transakce. Pokud nepoužijete transakce, jsou změny ke zdroji dat potvrzeny automaticky místo se potvrzovanou na požádání.  
  
> [!NOTE]
>  Ne všechny ovladače ODBC databáze podporovat transakce. Volání `CanTransact` členské funkce vaše [CDatabase](../../mfc/reference/cdatabase-class.md) nebo [CRecordset](../../mfc/reference/crecordset-class.md) objektem pro určení, zda ovladač podporuje transakce pro danou databázi. Všimněte si, že `CanTransact` nezjistíte zda zdroj dat poskytuje plnou podporu transakcí. Musíte také zavolat `CDatabase::GetCursorCommitBehavior` a `CDatabase::GetCursorRollbackBehavior` po **CommitTrans** a **vrácení zpět** chcete zkontrolovat dopad transakce na open `CRecordset` objektu.  
  
 Volání `AddNew` a **upravit** členské funkce `CRecordset` vliv zdroj dat okamžitě při volání objektu **aktualizace**. **Odstranit** volání také se projeví okamžitě. Naproti tomu můžete použít transakce, který se skládá z více volání `AddNew`, **upravit**, **aktualizace**, a **odstranit**, které jsou prováděny, ale nikoli potvrdit až volání **CommitTrans** explicitně. Vytvořením transakce, můžete provést řadu těchto volání při zachování možnost vrátit je zpátky. Pokud je kritický zdroj není dostupný nebo jiné podmínky zabraňují dokončení celé transakce, můžete transakci místo potvrzení vrátit zpět. V takovém případě žádná ze změn, které patří do transakce ovlivní zdroj dat.  
  
> [!NOTE]
>  V současné době třídy `CRecordset` nepodporuje aktualizace ke zdroji dat, pokud jste implementovali hromadné načítání řádků. To znamená, že nemůžete provádět volání `AddNew`, **upravit**, **odstranit**, nebo **aktualizace**. Můžete je však napsat vlastní funkce pro provádění aktualizací a pak zavolají tyto funkce v rámci dané transakci. Další informace o hromadné načítání řádků najdete v tématu [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Kromě toho, které mají vliv na sady záznamů, transakce ovlivňují příkazy SQL, které můžete přímo provádět také pomocí rozhraní ODBC **HDBC** přidružené k vaší `CDatabase` objekt nebo ODBC **HSTMT** na základě který **HDBC**.  
  
 Transakce jsou zvláště užitečné, když máte více záznamů, které musí být aktualizovány současně. V takovém případě budete chtít vyhnout půl dokončit transakci, například jako může dojít, pokud předtím, než byla provedena poslední aktualizace došlo k výjimce. Seskupení těchto aktualizací do transakce umožňuje obnovení (vrácení) změny a vrátí záznamy do stavu před transakcí. Například pokud bankovní převod peněz z účtu A k účtu B, jak odstoupení od uložení A a b musí být zpracován fondů správně nebo celá transakce selhat.  
  
 V databázové třídy provádět transakce prostřednictvím `CDatabase` objekty. A `CDatabase` objekt představuje připojení ke zdroji dat a který přidružený jeden nebo více sad záznamů `CDatabase` objekt pracovat v tabulkách databáze pomocí členské funkce sady záznamů.  
  
> [!NOTE]
>  Je podporována pouze jedna úroveň transakcí. Nelze vnořit transakce ani zahrnovat více databázové objekty.  
  
 Následující témata obsahují další informace o tom, jak se provádí transakce:  
  
-   [Transakce: Provádění transakcí v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)  
  
-   [Transakce: Vliv transakcí na aktualizace (rozhraní ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)