---
title: 'Transakce: Provádění transakcí v sadě záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 45ae414c318376b2c4d787498e9a288a0037af83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358098"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transakce: Provádění transakcí v sadě záznamů (ODBC)

Toto téma vysvětluje, jak provést transakci v sadě záznamů.

> [!NOTE]
> Je podporována pouze jedna úroveň transakcí; nelze vnořit transakce.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>Provedení transakce v sadě záznamů

1. Volání `CDatabase` `BeginTrans` členské funkce objektu.

1. Pokud jste neimplementovali hromadné načítání `AddNew/Update`řádků, volejte , `Edit/Update`a `Delete` členské funkce jednoho nebo více objektů sady záznamů stejné databáze tolikrát, kolikrát je potřeba. Další informace naleznete v [tématu Recordset: Přidání, aktualizace a odstranění záznamů (ODBC).](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md) Pokud jste implementovali hromadné načítání řádků, musíte napsat vlastní funkce pro aktualizaci zdroje dat.

1. Nakonec volání `CDatabase` `CommitTrans` členské funkce objektu. Pokud dojde k chybě v jedné z aktualizací nebo se `Rollback` rozhodnete zrušit změny, zavolejte její členské funkce.

Následující příklad používá dvě sady záznamů k odstranění zápisu studenta z databáze školní registrace a odebrání studenta ze všech tříd, ve kterých je student zapsán. Vzhledem `Delete` k tomu, že volání v obou sadách záznamů musí být úspěšné, je vyžadována transakce. Příklad `m_dbStudentReg`předpokládá existenci , členské proměnné typu, `CDatabase` který je již připojen ke `CEnrollmentSet` zdroji `CStudentSet`dat, a tříd sady záznamů a . Proměnná `strStudentID` obsahuje hodnotu získanou od uživatele.

```
BOOL CEnrollDoc::RemoveStudent( CString strStudentID )
{
    // remove student from all the classes
    // the student is enrolled in

    if ( !m_dbStudentReg.BeginTrans( ) )
        return FALSE;

    CEnrollmentSet rsEnrollmentSet(&m_dbStudentReg);
    rsEnrollmentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsEnrollmentSet.Open(CRecordset::dynaset) )
        return FALSE;

    CStudentSet rsStudentSet(&m_dbStudentReg);
    rsStudentSet.m_strFilter = "StudentID = " + strStudentID;

    if ( !rsStudentSet.Open(CRecordset::dynaset) )
        return FALSE;

    TRY
    {
        while ( !rsEnrollmentSet.IsEOF( ) )
        {
            rsEnrollmentSet.Delete( );
            rsEnrollmentSet.MoveNext( );
        }

        // delete the student record
        rsStudentSet.Delete( );

        m_dbStudentReg.CommitTrans( );
    }

    CATCH_ALL(e)
    {
        m_dbStudentReg.Rollback( );
        return FALSE;
    }
    END_CATCH_ALL

    rsEnrollmentSet.Close( );
    rsStudentSet.Close( );

    return TRUE;

}
```

> [!NOTE]
> Volání `BeginTrans` znovu `CommitTrans` bez `Rollback` volání nebo je chyba.

## <a name="see-also"></a>Viz také

[Transakce (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transakce: Vliv transakcí na aktualizace (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
