---
title: 'Sada záznamů: Deklarování třídy pro předdefinovaný dotaz (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cbbb9202aaf56681a792e1acf2a0c02eff5636d9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Sada záznamů: Deklarování třídy pro předdefinovaný dotaz (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma vysvětluje, jak pro vytvoření sady záznamů třídy pro předdefinovaný dotaz (někdy nazývané uložené procedury, jako v systému Microsoft SQL Server).  
  
> [!NOTE]
>  Toto téma se vztahuje na objekty, které jsou odvozené z `CRecordset` v který řádek hromadné načítání se neimplementovala. Pokud se implementuje hromadné načítání řádků, je velmi podobné proces. Chcete-li pochopit rozdíly mezi sady záznamů, který implementuje hromadné načítání řádků a ty, které nechcete, přečtěte si téma [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Některé systémy správy databáze (systémy DBMS) umožňují vytvořit předdefinovaný dotaz a volat z aplikací jako funkce. Dotaz s názvem, může trvat parametry a může vrátit záznamy. Postup v tomto tématu popisuje, jak volat předdefinovaný dotaz, který vrací záznamy (a případně parametry).  
  
 Databázové třídy nepodporují aktualizaci předdefinované dotazy. Rozdíl mezi předdefinovaný dotaz snímku a dynamická sada předdefinovaný dotaz není aktualizovatelný, ale jestli změny provedené jiní uživatelé (nebo jiné sady záznamů v programu) jsou viditelné ve vaší sadě záznamů.  
  
> [!TIP]
>  Není nutné sadu záznamů pro volání předdefinovaný dotaz, který nevrací záznamy. Příprava příkaz jazyka SQL, jak je popsáno níže, ale provést voláním `CDatabase` – členská funkce [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).  
  
 Můžete vytvořit třídu jedné sady záznamů ke správě volání předdefinovaný dotaz, ale musíte udělat některé úkoly sami. Průvodci nepodporují vytvoření třídy speciálně pro tento účel.  
  
#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Pro vytvoření třídy pro volání předdefinovaný dotaz (uložené procedury)  
  
1.  Použití [průvodce příjemcem knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **přidat třídu** pro vytvoření sady záznamů třídy pro tabulku, která přispívá nejvíce sloupců vrácených dotazem. To vám dává začít.  
  
2.  Ručně přidejte pole datových členů pro všechny sloupce všech tabulek, které dotaz vrátí, ale tento průvodce vám nevytvořil.  
  
     Například pokud dotaz vrátí tři sloupce ze dvou dalších tabulek, přidejte do třídy šest pole datových členů (z příslušné datových typů).  
  
3.  Ručně přidejte [RFX](../../data/odbc/record-field-exchange-rfx.md) funkce volá [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) funkce člena třídy, jeden odpovídající datový typ jednotlivých přidat pole datového člena.  
  
    ```  
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:   
    pFX->SetFieldType( CFieldExchange::outputColumn );  
    ```  
  
    > [!NOTE]
    >  Datové typy a pořadí sloupců vrácených ve výsledku nastavit, musíte znát. Pořadí funkce RFX volání `DoFieldExchange` musí odpovídat pořadí sloupců sady výsledků dotazu.  
  
4.  Přidejte ručně inicializace pro nové pole datových členů v konstruktoru třídy sady záznamů.  
  
     Musíte také zvýšit hodnotu inicializace [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) – datový člen. Inicializace zapisuje průvodce, týká se však pouze pole datových členů, které přidá za vás. Příklad:  
  
    ```  
    m_nFields += 6;  
    ```  
  
     Některé datové typy by neměly inicializovat zde například `CLongBinary` nebo pole bajtů.  
  
5.  Pokud dotaz přebírá parametry, přidejte parametr datového člena pro každý parametr funkce RFX pro každou a inicializaci pro každý.  
  
6.  Musíte zvýšit `m_nParams` pro každý přidaný parametr, jako jste to udělali `m_nFields` pro přidat pole v kroku 4 tohoto postupu. Další informace najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
7.  Ručně zápisu příkaz SQL s následující tvar:  
  
    ```  
    {CALL proc-name [(? [, ?]...)]}  
    ```  
  
     kde **volání** je klíčové slovo rozhraní ODBC **proc-name** je název dotazu, protože je znám ve zdroji dat a "?" položky jsou zástupné hodnoty parametrů můžete zadat na sadu záznamů v době běhu (pokud existuje) . Následující příklad připraví zástupný symbol pro jeden parametr:  
  
    ```  
    CString mySQL = "{CALL Delinquent_Accts (?)}";  
    ```  
  
8.  V kódu, který otevře sadu záznamů, nastavte hodnoty parametru sady záznamů datové členy a pak zavolají **otevřete** – členská funkce, probíhá předání váš SQL **lpszSQL** parametr. Nebo místo toho nahraďte řetězec vrácený `GetDefaultSQL` členské funkce ve třídě.  
  
 Následující příklady ukazují postup pro volání předdefinovaný dotaz, s názvem `Delinquent_Accts`, které přijímá jeden parametr pro číslo oblasti prodeje. Tento dotaz vrací tři sloupce: `Acct_No`, `L_Name`, `Phone`. Jsou všechny sloupce z tabulky zákazníků.  
  
 Následující sada záznamů určuje pole datových členů pro sloupce dotaz vrací a parametr pro prodeje oblast požadovaný za běhu.  
  
```  
class CDelinquents : public CRecordset  
{  
// Field/Param Data  
    LONG m_lAcct_No;  
    CString m_strL_Name;  
    CString m_strPhone;  
    LONG m_lDistParam;  
    // ...  
};  
```  
  
 Tato deklarace třídy je jako průvodce provádí zápis, s výjimkou `m_lDistParam` člen přidat ručně. Jiní členové nejsou zobrazeny zde.  
  
 Další příklad ukazuje inicializací pro datové členy v `CDelinquents` konstruktor.  
  
```  
CDelinquents::CDelinquents(CDatabase* pdb)  
   : CRecordset(pdb)  
{  
    // Wizard-generated params:  
    m_lAcct_No = 0;  
    m_strL_Name = "";  
    m_strPhone = "";  
    m_nFields = 3;  
    // User-defined params:  
    m_nParams = 1;  
    m_lDistParam = 0;  
}  
```  
  
 Všimněte si inicializací pro [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) a [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Inicializuje průvodce `m_nFields`; inicializaci `m_nParams`.  
  
 Další příklad ukazuje funkce RFX v `CDelinquents::DoFieldExchange`:  
  
```  
void CDelinquents::DoFieldExchange(CFieldExchange* pFX)  
{  
    pFX->SetFieldType(CFieldExchange::outputColumn);  
    RFX_Long(pFX, "Acct_No", m_lAcct_No);  
    RFX_Text(pFX, "L_Name", m_strL_Name);  
    RFX_Text(pFX, "Phone", m_strPhone);  
    pFX->SetFieldType(CFieldExchange::param);  
    RFX_Long(pFX, "Dist_No", m_lDistParam);  
}  
```  
  
 Kromě vytvoření volání RFX pro tři vrácené sloupce, tento kód spravuje, vazbu parametru, který předáte za běhu. Parametr je nastaven na `Dist_No` sloupce (číslo oblasti).  
  
 Další příklad ukazuje, jak nastavit řetězec SQL a způsobu jeho použití k otevření sady záznamů.  
  
```  
// Construct a CDelinquents recordset object  
CDelinquents rsDel( NULL );  
CString strSQL = "{CALL Delinquent_Accts (?)}"  
// Specify a parameter value (obtained earlier from the user)  
rsDel.m_lDistParam = lDistrict;  
// Open the recordset and run the query  
if( rsDel.Open( CRecordset::snapshot, strSQL ) )  
    // Use the recordset ...  
```  
  
 Tento kód vytvoří snímek, předává je parametr dříve získali od uživatele a zavolá předdefinovaný dotaz. Při spuštění dotazu vrátí záznamy pro zadanou oblast prodeje. Každý záznam obsahuje sloupce pro číslo účtu, příjmení zákazníka a telefonní číslo zákazníka.  
  
> [!TIP]
>  Můžete chtít zpracovat návratovou hodnotu (výstupní parametr) z uložené procedury. Další informace a příklady naleznete v tématu [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)   
 [Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [Sada záznamů: Provedení spojení (rozhraní ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)