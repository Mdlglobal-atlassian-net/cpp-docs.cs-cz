---
title: 'Transakce: Provádění transakcí v sadě záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: df7c28ebfbb68f3e0163368247b90ff69058726d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659580"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transakce: Provádění transakcí v sadě záznamů (ODBC)

Toto téma vysvětluje, jak k provádění transakcí v sadě záznamů.

> [!NOTE]
>  Je podporován pouze jednu úroveň transakce; nelze vnořovat transakce.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>K provedení transakcí v sadě záznamů

1. Volání `CDatabase` objektu `BeginTrans` členskou funkci.

1. Pokud jste neimplementovali hromadné načítání řádků, zavolejte `AddNew/Update`, `Edit/Update`, a `Delete` členské funkce jeden nebo více objektů sady záznamů ze stejné databáze tolikrát, kolikrát podle potřeby. Další informace najdete v tématu [sada záznamů: přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Pokud jste implementovali hromadné načítání řádků, musíte napsat vlastní funkce k aktualizaci zdroje dat.

1. Nakonec proveďte volání `CDatabase` objektu `CommitTrans` členskou funkci. Pokud dojde k chybě v jedné aktualizace nebo se rozhodnete zrušit změny, zavolejte jeho `Rollback` členskou funkci.

Dvě sady záznamů z registrační databáze školy, odebrání všechny třídy, ve kterých se zaregistruje studenta studenta odstranit registrace student získal v následujícím příkladu. Vzhledem k tomu, `Delete` volání v obou sadách záznamů musí proběhnout úspěšně, je požadována transakce. Příklad předpokládá existenci `m_dbStudentReg`, členské proměnné typu `CDatabase` již připojen ke zdroji dat a tříd sady záznamů `CEnrollmentSet` a `CStudentSet`. `strStudentID` Proměnná obsahuje hodnotu získaný od uživatele.

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
>  Volání `BeginTrans` znovu bez volání `CommitTrans` nebo `Rollback` chybu.

## <a name="see-also"></a>Viz také

[Transakce (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transakce: Vliv transakcí na aktualizace (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)