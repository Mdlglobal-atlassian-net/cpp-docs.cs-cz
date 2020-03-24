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
ms.openlocfilehash: 8a8305d2acacc79f5d7fe395087a0bd13dcbd196
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212768"
---
# <a name="recordset-scrolling-odbc"></a>Sada záznamů: Posouvání (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Po otevření sady záznamů budete potřebovat přístup k záznamům pro zobrazení hodnot, výpočtů, generování sestav atd. Posouvání umožňuje přesunout záznam ze záznamu na záznam v rámci vaší sady záznamů.

Toto téma vysvětluje:

- [Jak přejít z jednoho záznamu na jiný v sadě záznamů](#_core_scrolling_from_one_record_to_another).

- [Za jakých okolností je posouvání a není podporováno](#_core_when_scrolling_is_supported).

##  <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>Posouvání z jednoho záznamu na jiný

Třída `CRecordset` poskytuje `Move` členské funkce pro posouvání v rámci sady záznamů. Tyto funkce přesunou aktuální záznam pomocí sad řádků. Pokud jste implementovali hromadné načítání řádků, operace `Move` přemístí sadu záznamů o velikost sady řádků. Pokud jste neimplementovali hromadné načítání řádků, volání funkce `Move` přemístí sadu záznamů o jeden záznam pokaždé. Další informace o hromadném načítání řádků naleznete v tématu [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Při přesunu pomocí sady záznamů nemusí být odstraněné záznamy vynechány. Další informace naleznete v tématu členská funkce [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) .

Kromě funkcí `Move` poskytuje `CRecordset` členské funkce pro kontrolu, zda jste se přesunuli za konec nebo před začátek vaší sady záznamů.

Chcete-li určit, zda je možné ve vaší sadě záznamů použít posouvání, zavolejte členskou funkci `CanScroll`.

#### <a name="to-scroll"></a>Pro posouvání

1. Předejte jeden záznam nebo jednu sadu řádků: volejte členskou funkci [MoveNext](../../mfc/reference/crecordset-class.md#movenext) .

1. Zpět jeden záznam nebo jedna sada řádků: volejte členskou funkci [MovePrev](../../mfc/reference/crecordset-class.md#moveprev) .

1. Na první záznam v sadě záznamů: Zavolejte členskou funkci [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) .

1. Na poslední záznam v sadě záznamů nebo na poslední sadu řádků: volejte členskou funkci [MoveLast](../../mfc/reference/crecordset-class.md#movelast) .

1. *N* záznamů relativních k aktuální pozici: Zavolejte členskou funkci [Move](../../mfc/reference/crecordset-class.md#move) .

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Testování pro konec nebo začátek sady záznamů

1. Přesunuli jste se za poslední záznam? Zavolejte členskou funkci [IsEOF](../../mfc/reference/crecordset-class.md#iseof) .

1. Přesunuli jste se před první záznam (Přesun zpět)? Zavolejte členskou funkci [IsBOF](../../mfc/reference/crecordset-class.md#isbof) .

Následující příklad kódu používá `IsBOF` a `IsEOF` k detekci omezení sady záznamů při posouvání v obou směrech.

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

`IsEOF` vrátí nenulovou hodnotu, pokud je sada záznamů umístěna za poslední záznam. `IsBOF` vrátí nenulovou hodnotu, pokud je sada záznamů umístěna před první záznam (před všemi záznamy). V obou případech není k dispozici žádný aktuální záznam k provozu. Pokud zavoláte `MovePrev`, když je `IsBOF` již TRUE, nebo volání `MoveNext`, pokud `IsEOF` již má hodnotu TRUE, rozhraní vyvolá `CDBException`. K vyhledání prázdné sady záznamů můžete také použít `IsBOF` a `IsEOF`.

Další informace o navigaci v sadě záznamů naleznete v tématu [Sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>Když se podporuje posouvání

Jak jsme původně navrhli, SQL nabízí jenom přecházení, ale rozhraní ODBC rozšiřuje možnosti posouvání. Dostupná úroveň podpory pro posouvání závisí na ovladačích rozhraní ODBC, ve kterém vaše aplikace pracuje, na úrovni shody rozhraní ODBC API vašeho ovladače a na tom, zda je knihovna kurzorů rozhraní ODBC načtena do paměti. Další informace najdete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [ODBC: Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
>  Můžete určit, zda je použita knihovna kurzorů. Podívejte se na parametry *bUseCursorLib* a *dwOptions* pro [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
>  Na rozdíl od tříd MFC rozhraní DAO neposkytují třídy knihovny MFC rozhraní ODBC sadu funkcí `Find` pro vyhledání dalšího (nebo předchozího) záznamu, který splňuje zadaná kritéria.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset:: CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset:: CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
