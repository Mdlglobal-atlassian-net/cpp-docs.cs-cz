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
ms.openlocfilehash: a13bffdc79f01c49c290b8b5d4388f06ce777105
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512369"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Seznam záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC).

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

> [!NOTE]
>  Nyní můžete přidat záznamy hromadné efektivněji. Další informace najdete v tématu [sada záznamů: přidávání hromadné záznamů (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené z `CRecordset` v který řádek hromadné načítání není implementovaná. Pokud používáte hromadné načítání řádků, přečtěte si téma [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Aktualizovatelné a dynamické sady umožňují přidat, upravit (Aktualizovat) a odstraňování záznamů. Toto téma vysvětluje:

- [Jak zjistit, zda sady záznamů aktualizovat](#_core_determining_whether_your_recordset_is_updatable).

- [Postup přidání nového záznamu](#_core_adding_a_record_to_a_recordset).

- [Úprava existující záznam](#_core_editing_a_record_in_a_recordset).

- [Odstranění záznamu](#_core_deleting_a_record_from_a_recordset).

Další informace o způsobu zpracování aktualizací se odhlásili a jak ostatním uživatelům se zobrazí vaše aktualizace, naleznete v tématu [sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Za normálních okolností při přidání, úpravy nebo odstranění záznamu sady záznamů se změní zdroj dat okamžitě. Místo toho můžete skupiny související aktualizace dávkovat do transakce. Pokud probíhá transakce, aktualizace se nestane konečné dokud potvrzení transakce. To umožňuje vzít zpět nebo vrátit zpět změny. Informace o transakcích najdete v tématu [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

Následující tabulka shrnuje možnosti dostupné pro sady záznamů s různými vlastnostmi aktualizace.

### <a name="recordset-readupdate-options"></a>Číst/aktualizovat možnosti sady záznamů

|Typ|Číst|Úprava záznamu|Odstranit záznam|Přidat nový (připojit)|
|----------|----------|-----------------|-------------------|------------------------|
|jen pro čtení|A|N|N|N|
|Jen pro připojení|A|N|N|A|
|Plně aktualizovat|A|A|A|A|

##  <a name="_core_determining_whether_your_recordset_is_updatable"></a> Určení, zda sady záznamů je aktualizovatelná

Objekt sady záznamů je aktualizovat, pokud je možné aktualizovat zdroj dat a otevřít sadu záznamů aktualizovat. Jeho aktualizovatelnosti závisí také na příkazu SQL můžete použít, možnosti ovladač rozhraní ODBC a zda je knihovna kurzorů rozhraní ODBC v paměti. Nelze aktualizovat jen pro čtení záznamů nebo datového zdroje.

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Určuje, jestli je aktualizovat sady záznamů

1. Volání objektu sady záznamů [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) členskou funkci.

   `CanUpdate` vrací nenulovou hodnotu, pokud je sada záznamů aktualizovatelná.

Ve výchozím nastavení sady záznamů jsou plně aktualizovatelné (může provádět `AddNew`, `Edit`, a `Delete` operace). Ale můžete použít také [pouze přidat](../../mfc/reference/crecordset-class.md#open) možnost otevření aktualizovatelné sady záznamů. Sada záznamů otevřít tímto způsobem umožňuje přidávání nových záznamů pomocí `AddNew`. Nelze upravit nebo odstranit existující záznamy. Můžete zkontrolovat, jestli je otevřená pouze pro přidávání voláním na sadu záznamů [CanAppend](../../mfc/reference/crecordset-class.md#canappend) členskou funkci. `CanAppend` vrací nenulovou hodnotu, pokud je sada záznamů aktualizovatelné nebo zcela otevřená pouze pro přidávání.

Následující kód ukazuje, jak můžete použít `CanUpdate` objekt sady záznamů volá `rsStudentSet`:

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
>  Při přípravě na sadu záznamů aktualizovat pomocí volání `Update`, Upozorňujeme, že vaše sada záznamů obsahuje všechny sloupce, které tvoří primární klíč tabulky (nebo všechny sloupce jakýkoli jedinečný index pro tabulku). V některých případech můžete použít rozhraní pouze vybrané sloupce ve vaší sadě záznamů pro identifikaci, který záznam v tabulce k aktualizaci. Bez všech potřebných sloupců může být aktualizován více záznamů v tabulce, případně poškození referenční integritu v tabulce. V tomto případě rozhraní vyvolá výjimky při volání `Update`.

##  <a name="_core_adding_a_record_to_a_recordset"></a> Přidání záznamu do sady záznamů

Sada záznamů můžete přidat nové záznamy, pokud jeho [CanAppend](../../mfc/reference/crecordset-class.md#canappend) členská funkce vrátí nenulovou hodnotu.

#### <a name="to-add-a-new-record-to-a-recordset"></a>Chcete-li přidat nový záznam do sady záznamů

1. Ujistěte se, že je připojitelná záznamů.

1. Volání objektu sady záznamů [AddNew](../../mfc/reference/crecordset-class.md#addnew) členskou funkci.

   `AddNew` připraví sadu záznamů tak, aby fungoval jako vyrovnávací paměť úprav. Všechny datové členy jsou nastavena na speciální hodnotu Null a označena jako beze změny, takže pouze změny (dirty) hodnoty jsou zapsány do zdroje dat při volání [aktualizace](../../mfc/reference/crecordset-class.md#update).

1. Nastavte hodnoty datové členy nového záznamu.

   Přiřadíte hodnoty pole datových členů. Ty, které nepřiřadíte nejsou zapsány do zdroje dat.

1. Volání objektu sady záznamů `Update` členskou funkci.

   `Update` zápisem nový záznam do zdroje dat se dokončí přidání. Pro informace o se stane, když převezmete služby volat `Update`, naleznete v tématu [sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Informace o jak přidat záznamy a kdy jsou viditelné ve vaší sadě záznamů přidání záznamů najdete v tématu [sada záznamů: jak funkce operací AddNew, Edit a odstranit pracovní (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).

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
>  Zrušení `AddNew` nebo `Edit` volání, jednoduše proveďte další volání `AddNew` nebo `Edit` nebo volání `Move` s *AFX_MOVE_REFRESH* parametru. Datové členy se resetují na předchozí hodnoty a jsou stále v `Edit` nebo `Add` režimu.

##  <a name="_core_editing_a_record_in_a_recordset"></a> Úprava záznamů v sadě záznamů

Pokud můžete upravit existující záznamy sady záznamů [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) členská funkce vrátí nenulovou hodnotu.

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Chcete-li upravit existující záznam v sadě záznamů

1. Ujistěte se, že je sada záznamů aktualizovatelná.

1. Přejděte na záznam, který chcete aktualizovat.

1. Volání objektu sady záznamů [upravit](../../mfc/reference/crecordset-class.md#edit) členskou funkci.

   `Edit` připraví sadu záznamů tak, aby fungoval jako vyrovnávací paměť úprav. Všechny datové členy jsou označeny tak, aby sada záznamů můžete říct později, zda byly změněny. Nové hodnoty pro pole datových členů jsou zapsány do zdroje dat při volání [aktualizace](../../mfc/reference/crecordset-class.md#update).

1. Nastavte hodnoty datové členy nového záznamu.

   Přiřadíte hodnoty pole datových členů. Plánované že nepřiřadíte hodnoty aktualizace mezipaměti zůstávají beze změny.

1. Volání objektu sady záznamů `Update` členskou funkci.

   `Update` napsáním změněného záznamu ke zdroji dat se dokončí úpravy. Pro informace o se stane, když převezmete služby volat `Update`, naleznete v tématu [sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

Po úpravě záznamu úpravě záznamu zůstane aktuální záznam.

Následující příklad ukazuje `Edit` operace. Předpokládá se, že se uživatel přesunul na záznam, který uživatel chce upravit.

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
> Zrušení `AddNew` nebo `Edit` volání, jednoduše proveďte další volání `AddNew` nebo `Edit` nebo volání `Move` s *AFX_MOVE_REFRESH* parametru. Datové členy se resetují na předchozí hodnoty a jsou stále v `Edit` nebo `Add` režimu.

##  <a name="_core_deleting_a_record_from_a_recordset"></a> Odstranění záznamu z sady záznamů

Záznamy můžete odstranit, pokud vaše sada záznamů [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) členská funkce vrátí nenulovou hodnotu.

#### <a name="to-delete-a-record"></a>Chcete-li odstranit záznam

1. Ujistěte se, že je sada záznamů aktualizovatelná.

1. Přejděte na záznam, který chcete aktualizovat.

1. Volání objektu sady záznamů [odstranit](../../mfc/reference/crecordset-class.md#delete) členskou funkci.

   `Delete` okamžitě označí záznamy jako odstraněné v sadě záznamů a ve zdroji dat.

   Na rozdíl od `AddNew` a `Edit`, `Delete` nemá odpovídající `Update` volání.

1. Přechod na jiný záznam.

   > [!NOTE]
   >  Při procházení záznamů, nemusí být přeskočeny odstraněné záznamy. Další informace najdete v tématu [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) členskou funkci.

Následující příklad ukazuje `Delete` operace. Předpokládá, uživatel přejde na záznam, který chce uživatel odstranit. Po `Delete` je volána, je důležité pro přesun do nového záznamu.

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

Další informace o důsledcích `AddNew`, `Edit`, a `Delete` členské funkce, najdete v článku [sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)