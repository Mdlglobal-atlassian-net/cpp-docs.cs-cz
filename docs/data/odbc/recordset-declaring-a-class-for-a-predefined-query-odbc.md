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
ms.openlocfilehash: 9d19328fb82503519fd8eca083e0dd11e10883ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212950"
---
# <a name="recordset-declaring-a-class-for-a-predefined-query-odbc"></a>Sada záznamů: Deklarování třídy pro předdefinovaný dotaz (ODBC)

> [!NOTE]
> Průvodce příjemcem knihovny MFC rozhraní ODBC není dostupný v aplikaci Visual Studio 2019 a novějším. Příjemce můžete přesto vytvořit ručně.

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje, jak vytvořit třídu sady záznamů pro předdefinovaný dotaz (někdy označované jako uložená procedura, jako v Microsoft SQL Server).

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Pokud je implementováno hromadné načítání řádků, je proces velmi podobný. Pro pochopení rozdílů mezi sadami záznamů, které implementují hromadné načítání řádků a těch, které nejsou, viz [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Některé systémy správy databáze (DBMS) umožňují vytvořit předdefinovaný dotaz a volat ho z vašich programů, jako je funkce. Dotaz má název, může přebírat parametry a může vracet záznamy. Postup v tomto tématu popisuje, jak volat předdefinovaný dotaz, který vrací záznamy (a případně přebírá parametry).

Databázové třídy nepodporují aktualizaci předdefinovaných dotazů. Rozdíl mezi předdefinovaným dotazem snímku a předdefinovaným dynamická sadou nelze aktualizovat, ale zda jsou změny provedené jinými uživateli (nebo jinými sadami záznamů v programu) viditelné v sadě záznamů.

> [!TIP]
>  Nepotřebujete sadu záznamů pro volání předdefinovaného dotazu, který nevrací záznamy. Připravte příkaz SQL, jak je popsáno níže, ale spusťte ho voláním členské funkce `CDatabase` [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

Můžete vytvořit jednu třídu sady záznamů pro správu volání předdefinovaného dotazu, ale musíte provést nějakou práci sami. Průvodci nepodporují vytváření tříd speciálně pro tento účel.

#### <a name="to-create-a-class-for-calling-a-predefined-query-stored-procedure"></a>Vytvoření třídy pro volání předdefinovaného dotazu (uložená procedura)

1. Pomocí [Průvodce příjemcem knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z **Přidat třídu** vytvořte třídu sady záznamů pro tabulku, která bude mít nejvíce sloupců vrácených dotazem. To vám dává začátek.

1. Ručně přidejte datové členy pole pro všechny sloupce všech tabulek, které dotaz vrátí, ale průvodce pro vás nevytvořil.

   Například pokud dotaz vrátí tři sloupce každý ze dvou dalších tabulek, přidejte do třídy šest datových členů pole (z odpovídajících datových typů).

1. Ručně přidejte volání funkce [RFX](../../data/odbc/record-field-exchange-rfx.md) v členské funkci [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) třídy, jednu odpovídající datovému typu každého přidaného datového člena pole.

    ```cpp
    Immediately before these RFX calls, call <MSHelp:link keywords="_mfc_CFieldExchange.3a3a.SetFieldType" TABINDEX="0">SetFieldType</MSHelp:link>, as shown here:
    pFX->SetFieldType( CFieldExchange::outputColumn );
    ```

    > [!NOTE]
    >  Musíte znát datové typy a pořadí sloupců vrácených v sadě výsledků dotazu. Pořadí volání funkce RFX v `DoFieldExchange` musí odpovídat pořadí sloupců sady výsledků.

1. Ručně přidejte inicializace pro nové datové členy pole v konstruktoru třídy sady záznamů.

   Také je nutné zvýšit inicializační hodnotu datového členu [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) . Průvodce zapíše inicializaci, ale vztahuje se pouze na pole datových členů, které pro vás přidá. Příklad:

    ```cpp
    m_nFields += 6;
    ```

   Některé typy dat by se tady neměly inicializovat, například `CLongBinary` nebo Bajtová pole.

1. Pokud dotaz přebírá parametry, přidejte datový člen parametru pro každý parametr, volání funkce RFX pro každou a inicializaci každého.

1. Je nutné zvýšit `m_nParams` pro každý přidaný parametr, protože jste `m_nFields` pro přidaná pole v kroku 4 tohoto postupu. Další informace naleznete v tématu [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Ručně napište řetězec příkazu SQL s následujícím formulářem:

    ```
    {CALL proc-name [(? [, ?]...)]}
    ```

   kde **Call** je klíčové slovo ODBC, **proc-Name** je název dotazu, který je známý ve zdroji dat, a položky "?" jsou zástupné symboly pro hodnoty parametrů, které zadáte do sady záznamů v době běhu (pokud existuje). Následující příklad připraví zástupný symbol pro jeden parametr:

    ```
    CString mySQL = "{CALL Delinquent_Accts (?)}";
    ```

1. V kódu, který otevře sadu záznamů, nastavte hodnoty datových členů parametru sady záznamů a potom zavolejte `Open` členské funkce a předejte řetězec SQL pro parametr *lpszSQL* . Nebo místo toho nahraďte řetězec vrácený `GetDefaultSQL` členskou funkcí ve vaší třídě.

Následující příklady znázorňují postup pro volání předdefinovaného dotazu s názvem `Delinquent_Accts`, který přijímá jeden parametr pro číslo oblasti prodeje. Tento dotaz vrátí tři sloupce: `Acct_No`, `L_Name``Phone`. Všechny sloupce jsou z tabulky Customers.

Následující sada záznamů Určuje datové členy pole pro sloupce, které dotaz vrátí, a parametr pro číslo oblasti prodeje požadované v době běhu.

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

Tato deklarace třídy je jako průvodce zapisuje, s výjimkou člena `m_lDistParam` přidaných ručně. Další členové zde nejsou zobrazeni.

Následující příklad ukazuje inicializace pro datové členy v konstruktoru `CDelinquents`.

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

Poznamenejte si inicializace pro [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) a [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams). Průvodce inicializuje `m_nFields`; inicializujete `m_nParams`.

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

Kromě vytvoření volání RFX pro tři vrácené sloupce tento kód spravuje vazbu parametru, který jste předali za běhu. Parametr je nastaven na sloupec `Dist_No` (číslo oblasti).

Další příklad ukazuje, jak nastavit řetězec SQL a jak ho použít k otevření sady záznamů.

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

Tento kód vytvoří snímek, předá mu parametr získaný dříve od uživatele a zavolá předdefinovaný dotaz. Při spuštění dotazu vrátí záznamy pro zadanou oblast prodeje. Každý záznam obsahuje sloupce pro číslo účtu, příjmení zákazníka a telefonní číslo zákazníka.

> [!TIP]
>  Je možné, že budete chtít zpracovat návratovou hodnotu (výstupní parametr) z uložené procedury. Další informace a příklad naleznete v tématu [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)<br/>
[Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Sada záznamů: Provedení spojení (rozhraní ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)
