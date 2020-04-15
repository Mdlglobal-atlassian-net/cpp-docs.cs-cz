---
title: 'Sada záznamů: Posouvání (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets [C++], end of
- recordsets [C++], beginning of
- navigation [C++], recordsets
- recordsets [C++], moving to records
- ODBC recordsets, scrolling
- recordsets [C++], navigating
- scrolling [C++], recordsets
- Move method (recordsets)
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
ms.openlocfilehash: 931051296dff495939fcbd894102a1b00e48ee90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366930"
---
# <a name="recordset-scrolling-odbc"></a>Sada záznamů: Posouvání (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Po otevření sady záznamů je třeba získat přístup k záznamům, aby bylo nutné zobrazit hodnoty, provádět výpočty, generovat sestavy a tak dále. Posouvání umožňuje přechod ze záznamu na záznam v rámci sady záznamů.

Toto téma vysvětluje:

- [Jak se posouvat z jednoho záznamu do druhého v sadě záznamů](#_core_scrolling_from_one_record_to_another).

- [Za jakých okolností je a není podporováno posouvání](#_core_when_scrolling_is_supported).

## <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>Posouvání z jednoho záznamu na jiný

Třída `CRecordset` poskytuje `Move` členské funkce pro posouvání v rámci sady záznamů. Tyto funkce přesunout aktuální záznam podle sad řádků. Pokud jste implementovali hromadné načítání `Move` řádků, operace přemístí sadu záznamů podle velikosti sady řádků. Pokud jste neimplementovali hromadné načítání řádků, `Move` volání funkce pokaždé přemístí sadu záznamů o jeden záznam. Další informace o hromadném načítání řádků naleznete v tématu [Recordset: Fetching Records in Bulk (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

> [!NOTE]
> Při procházení sady záznamů nemusí být odstraněné záznamy přeskočeny. Další informace naleznete v členské funkci [IsDeleted.](../../mfc/reference/crecordset-class.md#isdeleted)

Kromě `Move` funkcí poskytuje `CRecordset` členské funkce pro kontrolu, zda jste se posunuli za konec nebo před začátkem sady záznamů.

Chcete-li zjistit, zda je v sadě `CanScroll` záznamů možné posouvání, zavolejte členní funkci.

#### <a name="to-scroll"></a>Posouvání

1. Přepošlete jeden záznam nebo jednu sadu řádků: volání členské funkce [MoveNext.](../../mfc/reference/crecordset-class.md#movenext)

1. Zpět jeden záznam nebo jedna sada řádků: volání členské funkce [MovePrev.](../../mfc/reference/crecordset-class.md#moveprev)

1. Chcete-li první záznam v sadě záznamů: volání [movefirst](../../mfc/reference/crecordset-class.md#movefirst) členské funkce.

1. K poslednímu záznamu v sadě záznamů nebo k poslední sadě řádků: volání členské funkce [MoveLast.](../../mfc/reference/crecordset-class.md#movelast)

1. *N* záznamů vzhledem k aktuální pozici: volání funkce [Move](../../mfc/reference/crecordset-class.md#move) člena.

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Testování konce nebo začátku sady záznamů

1. Prošli jste kolem posledního záznamu? Volání členské funkce [IsEOF.](../../mfc/reference/crecordset-class.md#iseof)

1. Posunuli jste se před první nahrávkou (posunuzpět)? Volání členské funkce [IsBOF.](../../mfc/reference/crecordset-class.md#isbof)

Následující příklad kódu `IsBOF` `IsEOF` používá a zjistit limity sady záznamů při posouvání v obou směrech.

```
// Open a recordset; first record is current
CCustSet rsCustSet( NULL );
rsCustSet.Open( );

if( rsCustSet.IsBOF( ) )
    return;
    // The recordset is empty

// Scroll to the end of the recordset, past
// the last record, so no record is current
while ( !rsCustSet.IsEOF( ) )
    rsCustSet.MoveNext( );

// Move to the last record
rsCustSet.MoveLast( );

// Scroll to beginning of the recordset, before
// the first record, so no record is current
while( !rsCustSet.IsBOF( ) )
    rsCustSet.MovePrev( );

// First record is current again
rsCustSet.MoveFirst( );
```

`IsEOF`vrátí nenulovou hodnotu, pokud je sada záznamů umístěna za posledním záznamem. `IsBOF`vrátí nenulovou hodnotu, pokud je sada záznamů umístěna před prvním záznamem (před všemi záznamy). V obou případech neexistuje žádný aktuální záznam, na kterém by bylo možné pracovat. Pokud `MovePrev` voláte, když `IsBOF` je `MoveNext` `IsEOF` již TRUE nebo volání, `CDBException`když je již TRUE, rozhraní vyvolá . Můžete také `IsBOF` použít `IsEOF` a zkontrolovat prázdnou sadu záznamů.

Další informace o navigaci sady záznamů naleznete v [tématu Recordset: Záložky a Absolutní pozice (ODBC).](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

## <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>Při posouvání je podporováno

Jak bylo původně navrženo, SQL za předpokladu, pouze dopředu posouvání, ale ODBC rozšiřuje možnosti posouvání. Dostupná úroveň podpory posouvání závisí na ovladačích ROZHRANÍ ODBC, se kterými aplikace pracuje, na úrovni shody rozhraní ODBC API ovladače a na tom, zda je knihovna kurzorů rozhraní ODBC načtena do paměti. Další informace naleznete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [ODBC: The ODBC Cursor Library](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
> Můžete určit, zda je použita knihovna kurzorů. Viz *parametry bUseCursorLib* a *dwOptions* do [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
> Na rozdíl od tříd Knihovny MFC DAO třídy `Find` Knihovny MFC ODBC neposkytují sadu funkcí pro vyhledání dalšího (nebo předchozího) záznamu, který splňuje zadaná kritéria.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
