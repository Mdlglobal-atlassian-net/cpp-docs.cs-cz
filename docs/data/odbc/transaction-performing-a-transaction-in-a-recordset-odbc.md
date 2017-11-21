---
title: "Transakce: Provádění transakcí v sadě záznamů (ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: transactions, updating recordsets
ms.assetid: cf1d6b48-7fb8-4903-84f7-a1822054534d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1451775374b94bbefb6396e7afeda2396df84ba4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="transaction-performing-a-transaction-in-a-recordset-odbc"></a>Transakce: Provádění transakcí v sadě záznamů (ODBC)
Toto téma vysvětluje, jak k provádění transakcí v sadě záznamů.  
  
> [!NOTE]
>  Je podporován pouze jedna úroveň transakce; transakce nelze vnořit.  
  
#### <a name="to-perform-a-transaction-in-a-recordset"></a>K provedení transakcí v sadě záznamů  
  
1.  Volání `CDatabase` objektu **metody BeginTrans** – členská funkce.  
  
2.  Nemáte-li hromadné načítání řádků, volání **AddNew/Update**, **upravit nebo aktualizovat**, a **odstranit** jeden nebo více objektů sady záznamů ze stejné členské funkce databáze tolikrát, kolikrát podle potřeby. Další informace najdete v tématu [sada záznamů: přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md). Pokud jste implementovali hromadné načítání řádků, musí se napsat vlastní funkce se aktualizovat zdroj dat.  
  
3.  Nakonec zavolejte `CDatabase` objektu **CommitTrans** – členská funkce. Pokud dojde k chybě v jedné aktualizace nebo jste se rozhodli zrušit změny, zavolejte jeho **vrácení zpět** – členská funkce.  
  
 Následující příklad používá dvě sady záznamů odstranit Studentova registrace z registrační databáze školy, student odebráním všechny třídy, ve kterých je student zapsán. Protože **odstranit** volání v obou sadách záznamů musí proběhnout úspěšně, je požadována transakce. Příklad předpokládá existenci `m_dbStudentReg`, členské proměnné typu `CDatabase` již připojen ke zdroji dat a tříd sady záznamů `CEnrollmentSet` a `CStudentSet`. `strStudentID` Proměnná obsahuje hodnotu získaný od uživatele.  
  
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
>  Volání metody **metody BeginTrans** znovu bez volání **CommitTrans** nebo **vrácení zpět** chybu.  
  
## <a name="see-also"></a>Viz také  
 [Transakce (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transakce: Vliv transakcí na aktualizace (rozhraní ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)   
 [CDatabase – třída](../../mfc/reference/cdatabase-class.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)