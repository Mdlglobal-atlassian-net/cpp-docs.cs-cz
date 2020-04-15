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
ms.openlocfilehash: 628ffb2feee385a4114b0dbea074f81678c529d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367111"
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Seznam záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC).

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

> [!NOTE]
> Nyní můžete hromadně přidávat záznamy efektivněji. Další informace naleznete [v tématu Recordset: Adding Records in Bulk (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).

> [!NOTE]
> Toto téma se vztahuje `CRecordset` na objekty odvozené od, ve kterém hromadné načítání řádků nebyla implementována. Pokud používáte hromadné načítání řádků, přečtěte si část [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Aktualizovatelné snímky a dynamické sady umožňují přidávat, upravovat (aktualizovat) a odstraňovat záznamy. Toto téma vysvětluje:

- [Jak zjistit, zda je sada záznamů aktualizovatelná](#_core_determining_whether_your_recordset_is_updatable).

- [Jak přidat nový záznam](#_core_adding_a_record_to_a_recordset).

- [Jak upravit existující záznam](#_core_editing_a_record_in_a_recordset).

- [Jak odstranit záznam](#_core_deleting_a_record_from_a_recordset).

Další informace o tom, jak jsou aktualizace prováděny a jak se aktualizace zobrazují ostatním uživatelům, naleznete v [tématu Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Za normálních okolností při přidávání, úpravě nebo odstranění záznamu sada záznamů okamžitě změní zdroj dat. Místo toho můžete dávkové skupiny souvisejících aktualizací do transakcí. Pokud probíhá transakce, aktualizace se nestane konečnou, dokud transakci nepotvrdíte. To vám umožní vzít zpět nebo vrátit zpět změny. Informace o transakcích naleznete v tématu [Transakce (ODBC).](../../data/odbc/transaction-odbc.md)

Následující tabulka shrnuje možnosti, které jsou k dispozici pro sady záznamů s různými charakteristikami aktualizace.

### <a name="recordset-readupdate-options"></a>Možnosti čtení a aktualizace sady záznamů

|Typ|Čtení|Úprava záznamu|Odstranění záznamu|Přidat nový (připojit)|
|----------|----------|-----------------|-------------------|------------------------|
|Jen pro čtení|Ano|Ne|Ne|Ne|
|Pouze pro připojení|Ano|Ne|Ne|Ano|
|Plně aktualizovatelné|Ano|Ano|Ano|Ano|

## <a name="determining-whether-your-recordset-is-updateable"></a><a name="_core_determining_whether_your_recordset_is_updatable"></a>Určení, zda je sada záznamů aktualizovatelná

Objekt sady záznamů je aktualizovatelný, pokud je zdroj dat aktualizovatelný a vy jste ji otevřeli jako aktualizovatelnou. Jeho aktualizovatelnost závisí také na příkazu SQL, který používáte, na možnostech ovladače ODBC a na tom, zda je knihovna kurzorů ROZHRANÍ ODBC v paměti. Nelze aktualizovat sadu záznamů jen pro čtení nebo zdroj dat.

#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Zjištění, zda je sada záznamů aktualizovatelná

1. Volání členské funkce objektu [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) objektu sady záznamů.

   `CanUpdate`vrátí nenulovou hodnotu, pokud je sada záznamů aktualizovatelná.

Ve výchozím nastavení lze sady záznamů plně `AddNew` `Edit`aktualizovat `Delete` (můžete provádět , a operace). Ale můžete také použít [možnost appendOnly](../../mfc/reference/crecordset-class.md#open) k otevření aktualizovatelných sad záznamů. Sada záznamů otevřená tímto způsobem umožňuje `AddNew`pouze přidávání nových záznamů s . Existující záznamy nelze upravovat ani odstraňovat. Můžete otestovat, zda je sada záznamů otevřena pouze pro připojení voláním členské funkce [CanAppend.](../../mfc/reference/crecordset-class.md#canappend) `CanAppend`vrátí nenulovou hodnotu, pokud je sada záznamů plně aktualizovatelná nebo otevřená pouze pro připojení.

Následující kód ukazuje, jak `CanUpdate` můžete použít pro `rsStudentSet`objekt sady záznamů s názvem :

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
> Při přípravě na aktualizaci `Update`sady záznamů voláním , dbát na to, aby sada záznamů obsahuje všechny sloupce tvoří primární klíč tabulky (nebo všechny sloupce libovolného jedinečného indexu v tabulce). V některých případech může rozhraní framework použít pouze sloupce vybrané v sadě záznamů k identifikaci záznamu v tabulce k aktualizaci. Bez všech potřebných sloupců může být v tabulce aktualizováno více záznamů, což může poškodit referenční integritu tabulky. V tomto případě rozhraní framework vyvolá výjimky při volání `Update`.

## <a name="adding-a-record-to-a-recordset"></a><a name="_core_adding_a_record_to_a_recordset"></a>Přidání záznamu do sady záznamů

Nové záznamy můžete přidat do sady záznamů, pokud jeho členská funkce [CanAppend](../../mfc/reference/crecordset-class.md#canappend) vrátí nenulovou hodnotu.

#### <a name="to-add-a-new-record-to-a-recordset"></a>Přidání nového záznamu do sady záznamů

1. Ujistěte se, že sadu záznamů lze připojit.

1. Volání členské funkce [addnew](../../mfc/reference/crecordset-class.md#addnew) objektu sady záznamů.

   `AddNew`připraví sadu záznamů tak, aby působila jako vyrovnávací paměť pro úpravy. Všechny datové členy pole jsou nastaveny na speciální hodnotu Null a označeny jako nezměněné, takže pouze změněné (dirty) hodnoty jsou zapsány do zdroje dat při volání [Update](../../mfc/reference/crecordset-class.md#update).

1. Nastavte hodnoty datových členů pole nového záznamu.

   Přiřaďte datové členy pole hodnoty. Ty, které nepřiřadíte, nejsou zapsány do zdroje dat.

1. Volání `Update` členské funkce objektu sady záznamů.

   `Update`dokončí přidání zápisem nového záznamu do zdroje dat. Informace o tom, že `Update`se vám nepodaří zavolat , naleznete v [tématu Recordset: How Recordsets Update Records (ODBC).](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

Informace o tom, jak funguje přidávání záznamů a o tom, kdy jsou přidané záznamy viditelné v sadě záznamů, naleznete v [tématu Sada záznamů: Jak přidatnovou, upravit a odstranit práci (ODBC).](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)

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
> Chcete-li `AddNew` `Edit` zrušit hovor nebo hovor, `Edit` jednoduše `Move` proveďte další hovor nebo `AddNew` hovor s *parametrem AFX_MOVE_REFRESH.* Členové dat jsou obnoveny na své `Edit` předchozí `Add` hodnoty a jste stále v režimu nebo režimu.

## <a name="editing-a-record-in-a-recordset"></a><a name="_core_editing_a_record_in_a_recordset"></a>Úprava záznamu v sadě záznamů

Existující záznamy můžete upravit, pokud členská funkce [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) sady záznamů vrátí nenulovou hodnotu.

#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Úprava existujícího záznamu v sadě záznamů

1. Ujistěte se, že sadu záznamů lze aktualizovat.

1. Přejděte k záznamu, který chcete aktualizovat.

1. Volání členské funkce [Edit](../../mfc/reference/crecordset-class.md#edit) objektu sady záznamů.

   `Edit`připraví sadu záznamů tak, aby působila jako vyrovnávací paměť pro úpravy. Všechny datové členy pole jsou označeny tak, aby sada záznamů později zjistit, zda byly změněny. Nové hodnoty pro změněné datové členy pole jsou zapsány do zdroje dat při volání [Update](../../mfc/reference/crecordset-class.md#update).

1. Nastavte hodnoty datových členů pole nového záznamu.

   Přiřaďte datové členy pole hodnoty. Ty, které nepřiřadíte hodnoty, zůstanou nezměněny.

1. Volání `Update` členské funkce objektu sady záznamů.

   `Update`dokončí úpravu zápisem změněného záznamu do zdroje dat. Informace o tom, že `Update`se vám nepodaří zavolat , naleznete v [tématu Recordset: How Recordsets Update Records (ODBC).](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

Po úpravě záznamu zůstane upravený záznam aktuálním záznamem.

Následující příklad ukazuje `Edit` operaci. Předpokládá, že uživatel byl přesunut do záznamu, který chce upravit.

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
> Chcete-li `AddNew` `Edit` zrušit hovor nebo hovor, `Edit` jednoduše `Move` proveďte další hovor nebo `AddNew` hovor s *parametrem AFX_MOVE_REFRESH.* Členové dat jsou obnoveny na své `Edit` předchozí `Add` hodnoty a jste stále v režimu nebo režimu.

## <a name="deleting-a-record-from-a-recordset"></a><a name="_core_deleting_a_record_from_a_recordset"></a>Odstranění záznamu ze sady záznamů

Pokud členská funkce [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) sady záznamů vrátí nenulovou hodnotu, můžete záznamy odstranit.

#### <a name="to-delete-a-record"></a>Odstranění záznamu

1. Ujistěte se, že sadu záznamů lze aktualizovat.

1. Přejděte k záznamu, který chcete aktualizovat.

1. Volání [členské](../../mfc/reference/crecordset-class.md#delete) funkce delete objektu sady záznamů.

   `Delete`okamžitě označí záznam jako odstraněný, a to jak v sadě záznamů, tak ve zdroji dat.

   Na `AddNew` `Edit`rozdíl `Delete` od `Update` a , nemá žádné odpovídající volání.

1. Přejděte na jiný záznam.

   > [!NOTE]
   >  Při procházení sady záznamů nemusí být odstraněné záznamy přeskočeny. Další informace naleznete v členské funkci [IsDeleted.](../../mfc/reference/crecordset-class.md#isdeleted)

Následující příklad ukazuje `Delete` operaci. Předpokládá, že uživatel byl přesunut do záznamu, který chce odstranit. Poté, co `Delete` je volána, je důležité přejít na nový záznam.

```
rsStudent.Delete( );
rsStudent.MoveNext( );
```

Další informace o účincích `Edit`funkcí `Delete` , a členské položky naleznete v `AddNew`tématu [Recordset: How Recordsets Update Records (ODBC).](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
