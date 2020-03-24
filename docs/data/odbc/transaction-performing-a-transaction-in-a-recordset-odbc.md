---
title: 'Transakce: Provádění transakcí v sadě záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
ms.openlocfilehash: 94177a27a1f99a8c9c37b7fce3f697fd0088b7c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212586"
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transakce: Provádění transakcí v sadě záznamů (ODBC)

Toto téma vysvětluje, jak provést transakci v sadě záznamů.

> [!NOTE]
>  Je podporována pouze jedna úroveň transakcí; Nemůžete vnořovat transakce.

#### <a name="to-perform-a-transaction-in-a-recordset"></a>Provedení transakce v sadě záznamů

1. Zavolejte členskou funkci objektu `CDatabase` `BeginTrans`.

1. Pokud jste neimplementovali hromadné načítání řádků, zavolejte `AddNew/Update`, `Edit/Update`a `Delete` členské funkce jednoho nebo více objektů sady záznamů ve stejné databázi, kolikrát je potřeba. Další informace naleznete v tématu [Sada záznamů: Přidání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Pokud jste implementovali hromadné načítání řádků, musíte napsat vlastní funkce pro aktualizaci zdroje dat.

1. Nakonec zavolejte členskou funkci `CommitTrans` objektu `CDatabase`. Pokud dojde k chybě v jedné z aktualizací nebo se rozhodnete změny zrušit, zavolejte její členskou funkci `Rollback`.

Následující příklad používá dvě sady záznamů k odstranění registrace studenta z registrační databáze školy a odebírá studenta ze všech tříd, ve kterých je student zaregistrovaný. Protože volání `Delete` v obou sadách záznamů musí být úspěšné, je požadována transakce. Příklad předpokládá existenci `m_dbStudentReg`, členská proměnná typu `CDatabase` již připojená ke zdroji dat a třídy sady záznamů `CEnrollmentSet` a `CStudentSet`. Proměnná `strStudentID` obsahuje hodnotu získanou od uživatele.

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
>  Volání `BeginTrans` bez volání `CommitTrans` nebo `Rollback` je chyba.

## <a name="see-also"></a>Viz také

[Transakce (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transakce: Vliv transakcí na aktualizace (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)<br/>
[CDatabase – třída](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
