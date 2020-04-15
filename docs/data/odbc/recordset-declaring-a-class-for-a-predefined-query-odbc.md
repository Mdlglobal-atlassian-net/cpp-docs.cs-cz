---
title: 'Sada záznamů: Deklarování třídy pro předdefinovaný dotaz (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, queries
- predefined queries and recordsets
- stored procedures, and recordsets
- recordsets, predefined queries
- recordsets, stored procedures
ms.assetid: d27c4df9-dad2-4484-ba72-92ab0c8ff928
ms.openlocfilehash: f9618f25d738c092ab1818ef7c4ea52928e2ea60
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367044"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Sada záznamů: Deklarování třídy pro předdefinovaný dotaz (ODBC)

> [!NOTE]
> Průvodce příjemcem knihovny MFC ODBC není k dispozici v sadě Visual Studio 2019 a novějších. Stále můžete vytvořit příjemce ručně.

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Toto téma vysvětluje, jak vytvořit třídu sady záznamů pro předdefinovaný dotaz (někdy se nazývá uložená procedura, jako v Microsoft SQL Server).

> [!NOTE]
> Toto téma se vztahuje `CRecordset` na objekty odvozené od, ve kterém hromadné načítání řádků nebyla implementována. Pokud hromadné načítání řádků je implementováno, proces je velmi podobný. Informace o rozdílech mezi sadami záznamů, které implementují hromadné načítání řádků, a těmi, které je neprovádějí, naleznete v tématu [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Některé systémy správy databází (DBMS) umožňují vytvořit předdefinovaný dotaz a volat jej z programů jako funkce. Dotaz má název, může mít parametry a může vrátit záznamy. Postup v tomto tématu popisuje, jak volat předdefinovaný dotaz, který vrací záznamy (a možná přebírá parametry).

Třídy databáze nepodporují aktualizaci předdefinovaných dotazů. Rozdíl mezi předdefinovaným dotazem snímku a předdefinovaným dotazem dynasady není aktualizovatelnost, ale zda jsou změny provedené jinými uživateli (nebo jinými sadami záznamů v programu) viditelné ve vaší sadě záznamů.

> [!TIP]
> K volání předdefinovaného dotazu, který nevrací záznamy, nepotřebujete sadu záznamů. Připravte příkaz SQL, jak je popsáno `CDatabase` níže, ale spusťte jej voláním členské funkce [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

Můžete vytvořit jednu třídu sady záznamů pro správu volání předdefinovaného dotazu, ale některé práce musíte provést sami. Průvodci nepodporují vytváření třídy speciálně pro tento účel.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Vytvoření třídy pro volání předdefinovaného dotazu (uložená procedura)

1. Pomocí [Průvodce spotřebitele knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **přidat třídu** vytvořte třídu sady záznamů pro tabulku, která přispívá nejvíce sloupců vrácených dotazem. To vám dává náskok.

1. Ručně přidejte datové členy pole pro všechny sloupce všech tabulek, které dotaz vrátí, ale které pro vás průvodce nevytvořil.

   Například pokud dotaz vrátí tři sloupce každý ze dvou dalších tabulek, přidejte šest členů dat pole (příslušných datových typů) do třídy.

1. Ručně přidejte volání funkce [RFX](../../data/odbc/record-field-exchange-rfx.md) do členské funkce [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) třídy, která odpovídá datovému typu každého přidaného datového člena pole.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  Musíte znát datové typy a pořadí sloupců vrácených v sadě výsledků. Pořadí volání funkce RFX `DoFieldExchange` v musí odpovídat pořadí sloupců sady výsledků.

1. Ručně přidejte inicializace pro nové členy dat pole v konstruktoru třídy sady záznamů.

   Je také nutné zintálčit hodnotu inicializace pro datový člen [m_nFields.](../../mfc/reference/crecordset-class.md#m_nfields) Průvodce zapíše inicializaci, ale zahrnuje pouze datové členy pole, které za vás přidá. Příklad:

    ```cpp
    m_nFields += 6;
    ```

   Některé datové typy by zde neměly `CLongBinary` být inicializovány, například nebo bajtová pole.

1. Pokud dotaz přebírá parametry, přidejte datový člen parametru pro každý parametr, volání funkce RFX pro každý a inicializaci pro každý.

1. Je nutné zvýšit `m_nParams` pro každý přidaný `m_nFields` parametr, stejně jako u přidaných polí v kroku 4 tohoto postupu. Další informace naleznete v [tématu Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Ručně napište řetězec příkazu SQL s následujícím formulářem:

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   kde **CALL** je klíčové slovo ODBC, **proc-name** je název dotazu, jak je známý ve zdroji dat, a položky "?" jsou zástupné symboly pro hodnoty parametrů, které zadáte do sady záznamů za běhu (pokud existuje). Následující příklad připraví zástupný symbol pro jeden parametr:

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. V kódu, který otevře sadu záznamů, nastavte hodnoty datových členů parametru `Open` sady záznamů a pak zavolejte členská funkci a předejte řetězec SQL pro parametr *lpszSQL.* Nebo místo toho nahraďte `GetDefaultSQL` řetězec vrácený členovou funkcí ve vaší třídě.

Následující příklady ukazují postup pro volání předdefinovaného dotazu s názvem `Delinquent_Accts`, který má jeden parametr pro číslo prodejní oblasti. Tento dotaz vrátí `Acct_No`tři `L_Name` `Phone`sloupce: , , . Všechny sloupce jsou z tabulky Zákazníci.

Následující sada záznamů určuje členy dat polí pro sloupce, které dotaz vrátí, a parametr pro číslo prodejní oblasti požadované za běhu.

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

Tato deklarace třídy je jako průvodce `m_lDistParam` píše, s výjimkou člena přidaného ručně. Ostatní členové zde nejsou zobrazeni.

Následující příklad ukazuje inicializace pro datové `CDelinquents` členy v konstruktoru.

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

Poznamenejte si inicializace [pro m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) a [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Průvodce inicializuje `m_nFields`; inicializujete `m_nParams`.

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

Kromě provádění Volání RFX pro tři vrácené sloupce tento kód spravuje vazby parametr, který předáte v době běhu. Parametr je zakódován do sloupce (číslo okresu). `Dist_No`

Následující příklad ukazuje, jak nastavit řetězec SQL a jak jej použít k otevření sady záznamů.

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

Tento kód vytvoří snímek, předá mu parametr získaný dříve od uživatele a zavolá předdefinovaný dotaz. Při spuštění dotazu vrátí záznamy pro zadanou prodejní oblast. Každý záznam obsahuje sloupce pro číslo účtu, příjmení zákazníka a telefonní číslo zákazníka.

> [!TIP]
> Můžete chtít zpracovat vrácenou hodnotu (výstupní parametr) z uložené procedury. Další informace a příklad naleznete v tématu [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Sada záznamů: Provedení spojení (rozhraní ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)
