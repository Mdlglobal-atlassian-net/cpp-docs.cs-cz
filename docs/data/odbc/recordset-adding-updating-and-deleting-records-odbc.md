---
title: 'Seznam záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC).'
ms.date: 11/04/2016
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- records [C++], deleting
- AddNew method
- ODBC recordsets [C++], deleting records
- data in recordsets [C++]
- record editing [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
ms.openlocfilehash: 14fc26709541135e80a2e0fe4de872cc75221874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213002"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Seznam záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC).

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

> [!NOTE]
>  Nyní můžete přidávat záznamy efektivněji. Další informace naleznete v tématu [Sada záznamů: hromadné přidávání záznamů (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Používáte-li hromadné načítání řádků, přečtěte si téma [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Aktualizovatelné snímky a dynamické sady umožňují přidávat, upravovat (aktualizovat) a odstraňovat záznamy. Toto téma vysvětluje:

- [Jak zjistit, jestli je vaše sada záznamů aktualizovatelná](#_core_determining_whether_your_recordset_is_updatable).

- [Postup přidání nového záznamu](#_core_adding_a_record_to_a_recordset)

- [Jak upravit existující záznam](#_core_editing_a_record_in_a_recordset).

- [Postup odstranění záznamu](#_core_deleting_a_record_from_a_recordset)

Další informace o tom, jak se provádí aktualizace a jak se budou aktualizace zobrazovat ostatním uživatelům, najdete v tématu [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). V normálním případě když přidáte, upravíte nebo odstraníte záznam, sada záznamů okamžitě změní zdroj dat. Místo toho je možné do transakcí Batch seskupovat související aktualizace. Pokud transakce probíhá, aktualizace se nestane finální, dokud transakci nepotvrdíte. To vám umožní vzít zpět nebo vrátit zpět změny. Informace o transakcích naleznete v tématu [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

Následující tabulka shrnuje možnosti, které jsou k dispozici pro sady záznamů s různými charakteristikami aktualizace.

### <a name="recordset-readupdate-options"></a>Možnosti čtení a aktualizace sady záznamů

|Typ|Číst|Upravit záznam|Odstranit záznam|Přidat novou (připojit)|
|----------|----------|-----------------|-------------------|------------------------|
|Jen pro čtení|Ano|N|N|N|
|Pouze připojení|Ano|N|N|Ano|
|Plně aktualizovatelná|Ano|Ano|Ano|Ano|

##  <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>Určení, jestli je vaše sada záznamů aktualizovatelná

Objekt sady záznamů je možné aktualizovat, pokud je zdroj dat aktualizovatelný a Vy jste otevřeli sadu záznamů jako aktualizovatelnou. Jeho aktualizace také závisí na příkazu SQL, který používáte, na možnostech ovladače ODBC a na tom, jestli je knihovna kurzorů rozhraní ODBC v paměti. Nelze aktualizovat sadu záznamů nebo zdroj dat jen pro čtení.

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Určení, zda je vaše sada záznamů aktualizovatelná

1. Zavolejte členskou funkci [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) objektu sady záznamů.

   `CanUpdate` vrací nenulovou hodnotu, pokud je sada záznamů aktualizovatelná.

Ve výchozím nastavení jsou sady záznamů plně aktualizovatelné (můžete provádět `AddNew`, `Edit`a `Delete` operace). Můžete ale také použít možnost [AppendOnly](../../mfc/reference/crecordset-class.md#open) a otevřít aktualizovatelné sady záznamů. Sada záznamů otevřená tímto způsobem umožňuje pouze přidávání nových záznamů s `AddNew`. Existující záznamy nelze upravovat ani odstraňovat. Můžete otestovat, zda je sada záznamů otevřena pouze pro připojení voláním členské funkce [CanAppend](../../mfc/reference/crecordset-class.md#canappend) . `CanAppend` vrátí nenulovou hodnotu, pokud je sada záznamů buď plně aktualizovatelná, nebo otevřená pouze pro připojení.

Následující kód ukazuje, jak je možné použít `CanUpdate` pro objekt sady záznamů s názvem `rsStudentSet`:

```cpp
if( !rsStudentSet.Open( ) )
    return FALSE;
if( !rsStudentSet.CanUpdate( ) )
{
    AfxMessageBox( "Unable to update the Student recordset." );
    return;
}
```

> [!CAUTION]
>  Při přípravě na aktualizaci sady záznamů voláním `Update`se ujistěte, že vaše sada záznamů obsahuje všechny sloupce, které tvoří primární klíč tabulky (nebo všechny sloupce libovolného jedinečného indexu v tabulce). V některých případech může rozhraní použít pouze sloupce vybrané ve vaší sadě záznamů k identifikaci záznamu v tabulce, který chcete aktualizovat. Bez všech potřebných sloupců může být v tabulce Aktualizováno více záznamů, případně poškozením referenční integrity tabulky. V tomto případě rozhraní vyvolá výjimky při volání `Update`.

##  <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>Přidání záznamu do sady záznamů

Můžete přidat nové záznamy do sady záznamů, pokud její členská funkce [CanAppend](../../mfc/reference/crecordset-class.md#canappend) vrací nenulovou hodnotu.

#### <a name="to-add-a-new-record-to-a-recordset"></a>Přidání nového záznamu do sady záznamů

1. Ujistěte se, že je sada záznamů připojena.

1. Zavolejte členskou funkci [AddNew](../../mfc/reference/crecordset-class.md#addnew) objektu sady záznamů.

   `AddNew` připraví sadu záznamů tak, aby fungovala jako vyrovnávací paměť úprav. Všechny datové členy pole jsou nastaveny na speciální hodnotu null a označeny jako beze změny, takže změněné (nezapsaná) hodnoty se zapisují do zdroje dat při volání metody [Update](../../mfc/reference/crecordset-class.md#update).

1. Nastavte hodnoty datových členů pole nového záznamu.

   Přiřaďte hodnoty k polím datových členů. Ty, které nepřiřazujete, nejsou zapsány do zdroje dat.

1. Zavolejte členskou funkci objektu sady záznamů `Update`.

   `Update` dokončí přidávání zápisem nového záznamu do zdroje dat. Informace o tom, co se stane, pokud selže volání `Update`, naleznete v tématu [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Informace o způsobu přidávání záznamů a o tom, jak jsou přidané záznamy viditelné v sadě záznamů, naleznete v tématu [Sada záznamů: jak funkce AddNew, Edit a DELETE Work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).

Následující příklad ukazuje, jak přidat nový záznam:

```cpp
if( !rsStudent.Open( ) )
    return FALSE;
if( !rsStudent.CanAppend( ) )
    return FALSE;                      // no field values were set
rsStudent.AddNew( );
rsStudent.m_strName = strName;
rsStudent.m_strCity = strCity;
rsStudent.m_strStreet = strStreet;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not added; no field values were set." );
    return FALSE;
}
```

> [!TIP]
>  Chcete-li zrušit volání `AddNew` nebo `Edit`, jednoduše proveďte jiné volání `AddNew` nebo `Edit` nebo zavolejte `Move` s parametrem *AFX_MOVE_REFRESH* . Datové členy se resetují na jejich předchozí hodnoty a pořád jste v režimu `Edit` nebo `Add`.

##  <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>Úprava záznamu v sadě záznamů

Můžete upravit existující záznamy, pokud funkce členské funkce [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) vaší sadou záznamů vrátí nenulovou hodnotu.

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Úprava existujícího záznamu v sadě záznamů

1. Ujistěte se, že je sada záznamů aktualizovatelná.

1. Posuňte se na záznam, který chcete aktualizovat.

1. Zavolejte členskou funkci [Edit](../../mfc/reference/crecordset-class.md#edit) objektu sady záznamů.

   `Edit` připraví sadu záznamů tak, aby fungovala jako vyrovnávací paměť úprav. Všechny datové členy pole jsou označeny, takže sada záznamů může později sdělit, zda byla změněna. Nové hodnoty pro změněné pole datových členů jsou při volání [aktualizace](../../mfc/reference/crecordset-class.md#update)zapsány do zdroje dat.

1. Nastavte hodnoty datových členů pole nového záznamu.

   Přiřaďte hodnoty k polím datových členů. Hodnoty, které nepřiřazujete, zůstávají beze změny.

1. Zavolejte členskou funkci objektu sady záznamů `Update`.

   `Update` dokončí úpravu zápisem změněného záznamu do zdroje dat. Informace o tom, co se stane, pokud selže volání `Update`, naleznete v tématu [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Po úpravě záznamu zůstane Upravovaný záznam aktuálním záznamem.

Následující příklad ukazuje operaci `Edit`. Předpokládá, že uživatel přesunul na záznam, který chce upravit.

```cpp
rsStudent.Edit( );
rsStudent.m_strStreet = strNewStreet;
rsStudent.m_strCity = strNewCity;
rsStudent.m_strState = strNewState;
rsStudent.m_strPostalCode = strNewPostalCode;
if( !rsStudent.Update( ) )
{
    AfxMessageBox( "Record not updated; no field values were set." );
    return FALSE;
}
```

> [!TIP]
> Chcete-li zrušit volání `AddNew` nebo `Edit`, jednoduše proveďte jiné volání `AddNew` nebo `Edit` nebo zavolejte `Move` s parametrem *AFX_MOVE_REFRESH* . Datové členy se resetují na jejich předchozí hodnoty a pořád jste v režimu `Edit` nebo `Add`.

##  <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>Odstranění záznamu ze sady záznamů

Záznamy lze odstranit, pokud členská funkce [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) vaší sady záznamů vrací nenulovou hodnotu.

#### <a name="to-delete-a-record"></a>Postup odstranění záznamu

1. Ujistěte se, že je sada záznamů aktualizovatelná.

1. Posuňte se na záznam, který chcete aktualizovat.

1. Zavolejte členskou funkci [Delete](../../mfc/reference/crecordset-class.md#delete) objektu sady záznamů.

   `Delete` okamžitě označí záznam jako odstraněný v sadě záznamů i ve zdroji dat.

   Na rozdíl od `AddNew` a `Edit`nemá `Delete` žádné odpovídající `Update` volání.

1. Posuňte se na jiný záznam.

   > [!NOTE]
   >  Při přesunu prostřednictvím sady záznamů nemusí být odstraněné záznamy vynechány. Další informace naleznete v tématu členská funkce [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) .

Následující příklad ukazuje operaci `Delete`. Předpokládá, že uživatel přesunul na záznam, který chce uživatel odstranit. Po volání `Delete` je důležité přejít na nový záznam.

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

Další informace o účincích `AddNew`, `Edit`a `Delete` členských funkcí naleznete v tématu [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
