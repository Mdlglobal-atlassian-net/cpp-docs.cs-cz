---
title: 'Recordset: Deklarování třídy pro předdefinovaný dotaz (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: d4ae9f21c4bd53a8050d6f8c3765bb9823d077ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395596"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Recordset: Deklarování třídy pro předdefinovaný dotaz (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje, jak vytvořit sadu záznamů třídy pro předdefinovaný dotaz (říká se jim uložené procedury, stejně jako v systému Microsoft SQL Server).

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené z `CRecordset` v který řádek hromadné načítání není implementovaná. Pokud hromadné načítání řádků je implementováno, je velmi podobné. Rozdíly mezi sadách záznamů implementujících hromadné načítání řádků a ty, které nejsou najdete v tématu [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Některé systémy správy databáze (DBMS) umožňují vytvořit předdefinovaný dotaz a jeho volání z aplikace jako funkce. Dotaz s názvem, mohou mít parametry a může vrátit záznamů. Postup v tomto tématu popisuje, jak volat předdefinovaný dotaz, který vrací záznamy (a možná parametry).

Databázové třídy nepodporují aktualizaci předdefinované dotazy. Rozdíl mezi předdefinovaný dotaz snímku a dynamická sada předdefinovaného dotazu není aktualizovatelný, ale Určuje, zda jsou viditelné ve vaší sadě záznamů změny provedené jinými uživateli (nebo jiné sady záznamů ve svém programu).

> [!TIP]
>  Není nutné sadu záznamů pro předdefinovaný dotaz, který nevrací záznamy volání. Příprava příkaz jazyka SQL, jak je popsáno níže, ale provést voláním `CDatabase` členskou funkci [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

Můžete vytvořit třídu jedné sady záznamů ke správě volání předdefinovaného dotazu, ale musíte udělat některé úkoly sami. Průvodce nepodporuje vytvoření třídy speciálně pro tento účel.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Chcete-li vytvořit třídu pro volání předdefinovaného dotazu (uložené procedury)

1. Použití [průvodce příjemcem MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **přidat třídu** pro vytvoření sady záznamů třídy pro tabulku, jež přispívají nejvíce sloupců vrácených dotazem. To vám začít.

1. Ručně přidejte pole datových členů pro všechny sloupce všech tabulek, které dotaz vrátí hodnotu, ale tento průvodce se nevytvořil za vás.

   Například pokud dotaz vrací tři sloupce ze dvou dalších tabulek, přidejte do třídy šesti pole datové členy (příslušné datové typy).

1. Ruční přidání [RFX](../../data/odbc/record-field-exchange-rfx.md) volání funkce [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) členské funkce třídy, jeden odpovídající typ dat každého z nich přidá pole datového člena.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  Musíte znát datové typy a pořadí sloupců ve výsledku nastavit. Pořadí funkcí RFX volání `DoFieldExchange` musí odpovídat pořadí sloupců sady výsledků dotazu.

1. Ručně přidejte inicializace pro nové pole datových členů v konstruktoru třídy sady záznamů.

   Také musíte zvýšit hodnotu inicializace [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) datový člen. Průvodce provádí zápis inicializace, ale zahrnuje pouze datové členy polí, které přidá za vás. Příklad:

    ```cpp
    m_nFields += 6;
    ```

   Některé typy dat by neměl být inicializovány tady, například `CLongBinary` nebo pole bajtů.

1. Pokud parametry dotazu, přidejte parametr datový člen pro každý parametr, volání funkce RFX pro každou a inicializace pro každou.

1. Musíte zvýšit hodnotu `m_nParams` pro každý přidaný parametr, jako jste to udělali `m_nFields` pro přidání polí v kroku 4 tohoto postupu. Další informace najdete v tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Ručně napište řetězec příkazu SQL s následující tvar:

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   kde **volání** je klíčové slovo rozhraní ODBC **proc název** je název dotazu, který je znám na zdroji dat a "?" položky jsou zástupné symboly pro hodnoty parametrů zadat do sady záznamů v době běhu (pokud existuje) . V následujícím příkladu připraví zástupný symbol pro jeden parametr:

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. V kódu, který otevře sadu záznamů, nastavte hodnoty parametru sady záznamů datové členy a následně zavolat `Open` členskou funkci předání řetězce jazyka SQL *Ipszsql* parametru. Nebo místo toho nahradit řetězec vrácený funkcí `GetDefaultSQL` členské funkce ve své třídě.

Následující příklady ukazují postup volání předdefinovaný dotaz s názvem `Delinquent_Accts`, která přijímá jeden parametr pro číslo prodejní oblasti. Tento dotaz vrátí tři sloupce: `Acct_No`, `L_Name`, `Phone`. Jsou všechny sloupce z tabulky Zákazníci.

Následující sada záznamů určuje pole datových členů pro sloupce, které vrátí dotaz a parametrů pro prodej po oblastech číslo, které se požaduje za běhu.

```cpp
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

Tato deklarace třídy je jako průvodce provádí zápis, s výjimkou `m_lDistParam` člena přidat ručně. Ostatní členové se tady nezobrazují.

Následující příklad znázorňuje tyto inicializace pro datové členy v `CDelinquents` konstruktoru.

```cpp
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

Mějte na paměti tyto inicializace pro [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) a [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Inicializuje průvodce `m_nFields`; inicializaci `m_nParams`.

Následující příklad ukazuje funkce RFX v `CDelinquents::DoFieldExchange`:

```cpp
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

Kromě volání funkce RFX pro tři vrácené sloupce, tento kód slouží ke správě vazbu parametru, který předáte v době běhu. Parametr je nastaven na `Dist_No` sloupec (číslo oblasti).

Následující příklad ukazuje, jak vytvořit řetězec SQL a jak ji používat k otevření sady záznamů.

```cpp
// Construct a CDelinquents recordset object
CDelinquents rsDel( NULL );
CString strSQL = "{CALL Delinquent_Accts (?)}"
// Specify a parameter value (obtained earlier from the user)
rsDel.m_lDistParam = lDistrict;
// Open the recordset and run the query
if( rsDel.Open( CRecordset::snapshot, strSQL ) )
    // Use the recordset ...
```

Tento kód vytvoří snímek, předává je parametr, který jste dříve získali z uživatele a zavolá předdefinovaný dotaz. Při spuštění dotazu se vrátí záznamy pro zadanou prodejní oblast. Každý záznam obsahuje sloupce pro číslo účtu, Příjmení odběratele a telefonní číslo zákazníka.

> [!TIP]
>  Můžete chtít zpracovat návratovou hodnotu (výstupní parametr) z uložené procedury. Další informace a příklad najdete v tématu [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

## <a name="see-also"></a>Viz také:

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Sada záznamů: Provedení spojení (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)