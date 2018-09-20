---
title: 'TN068: Provádění transakcí pomocí ovladače ODBC Microsoft Access 7 | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/28/2018
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
ms.openlocfilehash: 4006ee6953342fd55b644eeb2a8e8f30c1d80285
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395840"
---
# <a name="tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver"></a>TN068: Provádění transakcí pomocí ovladače ODBC Microsoft Access 7

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato poznámka popisuje, jak k provádění transakcí, při použití databázové třídy MFC rozhraní ODBC a ovladači Microsoft Access 7.0 ODBC součástí Microsoft ODBC Desktop ovladač Pack verze 3.0.

## <a name="overview"></a>Přehled

Pokud vaše databáze aplikace provádí transakce, musíte být opatrní a volat `CDatabase::BeginTrans` a `CRecordset::Open` tak správné pořadí ve vaší aplikaci. Databázový stroj Microsoft Jet používá ovladač Microsoft Access 7.0 a Jet vyžaduje, že vaše aplikace není spustit transakci na všechny databáze, které se má otevřít kurzor. Pro databázové třídy MFC rozhraní ODBC, otevřít kurzor odpovídá otevřenou `CRecordset` objektu.

Pokud otevřete záznamů před zavoláním funkce `BeginTrans`, nezobrazí žádné chybové zprávy. Nicméně všechny sady záznamů aktualizuje vaše aplikace využívá trvalý po volání `CRecordset::Update`, a aktualizace nebudou vrácena zpět voláním `Rollback`. Chcete-li tomuto problému vyhnout, musíte volat `BeginTrans` první a pak otevřít sadu záznamů.

MFC zkontroluje funkci ovladače pro kurzor chování potvrzení změn a vrácení zpět. Třída `CDatabase` poskytuje dva členské funkce `GetCursorCommitBehavior` a `GetCursorRollbackBehavior`, účinnosti jakékoli transakce na vaše open `CRecordset` objektu. Pro ovladače Microsoft Access 7.0 ODBC tyto členské funkce vrátí `SQL_CB_CLOSE` protože přístup ovladač nepodporuje zachovávání s rozlišením kurzoru. Proto je nutné volat `CRecordset::Requery` následující `CommitTrans` nebo `Rollback` operace.

Pokud je třeba provést více transakcí, jeden po druhém, nejde volat `Requery` po první transakce a poté spusťte další příkaz. Je nutné zavřít záznamů před dalším voláním `BeginTrans` splníte Jet pro požadavek. Tato technická Poznámka popisuje dva způsoby zpracování této situaci:

- Uzavření sady záznamů po každém z nich `CommitTrans` nebo `Rollback` operace.

- Pomocí funkce ODBC API `SQLFreeStmt`.

## <a name="closing-the-recordset-after-each-committrans-or-rollback-operation"></a>Po každé operaci vrácení zpět nebo CommitTrans uzavření sady záznamů

Před spuštěním transakce, ujistěte se, že objekt sady záznamů je zavřené. Po volání `BeginTrans`, volání sady záznamů `Open` členskou funkci. Zavřete sadu záznamů ihned po volání `CommitTrans` nebo `Rollback`. Všimněte si, že opakovaného otevírání a zavírání záznamů může zpomalit výkon vaší aplikace.

## <a name="using-sqlfreestmt"></a>Pomocí SQLFreeStmt

Můžete také použít – funkce rozhraní API ODBC `SQLFreeStmt` explicitně zavřít kurzor po ukončení transakce. Chcete-li spustit jinou transakci, zavolejte `BeginTrans` následovaný `CRecordset::Requery`. Při volání metody `SQLFreeStmt`, HSTMT sady záznamů je nutné zadat jako první parametr a *SQL_CLOSE* jako druhý parametr. Tato metoda je rychlejší než zavřením a otevřením sady záznamů na začátku každé transakci. Následující kód ukazuje, jak implementovat tento postup:

```cpp
CMyDatabase db;
db.Open("MYDATASOURCE");
CMyRecordset rs(&db);

// start transaction 1 and
// open the recordset
db.BeginTrans();
rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans(); // or Rollback()

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

Dalším způsobem, jak implementovat tato technika se zapsat novou funkci, `RequeryWithBeginTrans`, které můžete volat a spusťte další transakce po potvrzení nebo vrácení zpět první z nich. Zapsat takové funkce, proveďte následující kroky:

1. Zkopírujte kód pro `CRecordset::Requery( )` na tuto novou funkci.

2. Přidejte následující řádek bezprostředně po volání `SQLFreeStmt`:

   `m_pDatabase->BeginTrans( );`

Nyní můžete voláním této funkce mezi každý pár transakce:

```cpp
// start transaction 1 and
// open the recordset
db.BeginTrans();

rs.Open();

// manipulate data

// end transaction 1
db.CommitTrans();   // or Rollback()

// close the cursor, start new transaction,
// and get the result set
rs.RequeryWithBeginTrans();

// manipulate data

// end transaction 2
db.CommitTrans();   // or Rollback()
```

> [!NOTE]
> Nepoužívejte tento postup, pokud potřebujete změnit proměnné členů sady záznamů *m_strFilter* nebo *m_strSort* mezi transakcemi. V takovém případě by měla zavřít sadu záznamů po každém z nich `CommitTrans` nebo `Rollback` operace.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
