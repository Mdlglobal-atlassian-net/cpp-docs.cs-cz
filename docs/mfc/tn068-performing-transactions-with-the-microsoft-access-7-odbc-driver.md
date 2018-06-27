---
title: 'TN068: Provádění transakcí pomocí ovladače ODBC Microsoft Access 7 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data.odbc
dev_langs:
- C++
helpviewer_keywords:
- TN068 [MFC]
- transactions [MFC], calling BeginTrans
- transactions [MFC], Microsoft Access
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 653e1cf29ff2b2e2338df7e8e3a1e74d73a7d6fe
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950224"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068: Provádění transakcí pomocí ovladače ODBC Microsoft Access 7
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato poznámka popisuje provádění transakcí, při použití databázové třídy MFC rozhraní ODBC a ovladač Microsoft Access 7.0 ODBC součástí Microsoft ODBC Desktop Driver Pack verze 3.0.  
  
## <a name="overview"></a>Přehled  
 Pokud aplikace databáze provádí transakce, musí být opatrní při volání `CDatabase::BeginTrans` a `CRecordset::Open` ve správném pořadí ve vaší aplikaci. Ovladač Microsoft Access 7.0 používá databázový stroj Microsoft Jet a Jet vyžaduje, aby vaše aplikace není spustit transakci na všechny databáze, který má otevřít kurzor. Pro databázové třídy MFC rozhraní ODBC, otevřete kurzoru rovná otevřenou `CRecordset` objektu.  
  
 Pokud otevřete sadu záznamů před voláním `BeginTrans`, nemusí zobrazit chybové zprávy. Ale všechny sady záznamů aktualizuje vaše aplikace má po volání stane trvalé `CRecordset::Update`, a aktualizace nebude vrácena voláním `Rollback`. K tomuto problému nedošlo, je třeba volat `BeginTrans` první a pak otevřete sadu záznamů.  
  
 MFC kontroluje ovladače funkce pro potvrzení a vrácení chování kurzoru. Třída `CDatabase` poskytuje dva členské funkce `GetCursorCommitBehavior` a `GetCursorRollbackBehavior`, pro ověření účinnosti jakékoli transakce na vaše otevřete `CRecordset` objektu. Ovladače Microsoft Access 7.0 ODBC, který se vrátí tyto funkce člen `SQL_CB_CLOSE` protože ovladače Access nepodporuje písmen a zachovávání kurzoru. Proto musí volat `CRecordset::Requery` následující `CommitTrans` nebo `Rollback` operaci.  
  
 Pokud potřebujete provést více transakcí, jedna po druhé, nelze volat `Requery` po první transakce a poté spusťte následující. Je třeba nejprve zavřít záznamů před dalším voláním `BeginTrans` za účelem splnění požadavků na Jet. Tato technická Poznámka popisuje dvě metody zpracování této situaci:  
  
-   Uzavření sady záznamů po každém z nich `CommitTrans` nebo `Rollback` operaci.  
  
-   Pomocí funkce rozhraní API ODBC `SQLFreeStmt`.  
  
## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>Po každé CommitTrans nebo operaci vrácení zpět uzavření sady záznamů  
 Před zahájením transakce, zkontrolujte, zda že objekt sady záznamů je uzavřený. Po volání `BeginTrans`, volání sady záznamů `Open` – členská funkce. Zavřete sadu záznamů ihned po volání `CommitTrans` nebo `Rollback`. Všimněte si, že opakovaně otvírání a zavírání sady záznamů můžou způsobit snížení výkonu aplikace.  
  
## <a name="using-sqlfreestmt"></a>Pomocí SQLFreeStmt  
 Můžete také použít funkce rozhraní API ODBC `SQLFreeStmt` explicitně zavřete kurzor po ukončení transakce. Chcete-li spustit jinou transakcí, volejte `BeginTrans` následuje `CRecordset::Requery`. Při volání metody `SQLFreeStmt`, je nutné zadat jako první parametr HSTMT sady záznamů a *SQL_CLOSE* jako druhý parametr. Tato metoda je rychlejší než zavřením a otevřením sada záznamů na začátku každé transakci. Následující kód ukazuje, jak implementovat tento postup:  
  
```  
CMyDatabase db;  
db.Open("MYDATASOURCE");

CMyRecordset rs(&db);

 
// start transaction 1 and   
// open the recordset  
db.BeginTrans();

rs.Open();

 
// manipulate data  
 
// end transaction 1  
db.CommitTrans();
*// or Rollback()  
 
// close the cursor  
::SQLFreeStmt(rs.m_hstmt, SQL_CLOSE);

 
// start transaction 2  
db.BeginTrans();

 
// now get the result set  
rs.Requery();

 
// manipulate data  
 
// end transaction 2  
db.CommitTrans();

 
rs.Close();

db.Close();
```  
  
 Jiný způsob, jak implementovat tato technika je napsat nové funkce, `RequeryWithBeginTrans`, můžete volat před zahájením další transakci po potvrzení nebo vrácení změn první z nich. Zápis takové funkce, proveďte následující kroky:  
  
1.  Zkopírujte kód pro `CRecordset::Requery( )` nové funkce.  
  
2.  Přidejte následující řádek hned po volání `SQLFreeStmt`:  
  
 `m_pDatabase->BeginTrans( );`  
  
 Nyní můžete volat tuto funkci mezi každý pár transakcí:  
  
```  
// start transaction 1 and   
// open the recordset  
db.BeginTrans();

rs.Open();

 
// manipulate data  
 
// end transaction 1  
db.CommitTrans();
*// or Rollback()  
 
// close the cursor,
    start new transaction,  
// and get the result set  
rs.RequeryWithBeginTrans();

 
// manipulate data  
 
// end transaction 2  
db.CommitTrans();
*// or Rollback()  
```  
  
> [!NOTE]
>  Nepoužívejte tato technika, pokud potřebujete změnit proměnné členů sady záznamů *m_strFilter* nebo *m_strSort* mezi transakce. V takovém případě by měl zavřít sadu záznamů po každém z nich `CommitTrans` nebo `Rollback` operaci.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

