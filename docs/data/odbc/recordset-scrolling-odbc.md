---
title: 'Sada záznamů: Posouvání (ODBC) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: efe2df6f4ff2f157c81ea85e0adfc17934a3c44e
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337580"
---
# <a name="recordset-scrolling-odbc"></a>Sada záznamů: Posouvání (ODBC)
Toto téma platí pro třídy knihovny MFC rozhraní ODBC.  
  
 Po otevření sady záznamů, budete potřebovat přístup k záznamům k zobrazení hodnoty, provádět výpočty, generování sestav a tak dále. Posouvání umožňuje přesouvat mezi záznamy v rámci sady záznamů.  
  
 Toto téma vysvětluje:  
  
-   [Jak přejít z jednoho záznamu do druhého v sadě záznamů](#_core_scrolling_from_one_record_to_another).  
  
-   [Za jakých okolností posouvání je a nepodporuje](#_core_when_scrolling_is_supported).  
  
##  <a name="_core_scrolling_from_one_record_to_another"></a> Posunutí z jednoho záznamu  
 Třída `CRecordset` poskytuje `Move` členské funkce pro posouvání v rámci sady záznamů. Tyto funkce přesunout aktuální záznam sady řádků. Pokud jste implementovali hromadné načítání řádků, `Move` operace přemístí sadu záznamů na velikosti dané sadě řádků. Pokud jste neimplementovali hromadné načítání, volání řádků `Move` funkce přemístí záznamů podle jednoho záznamu pokaždé, když. Další informace o hromadném načítání řádků naleznete v tématu [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Při procházení záznamů, nemusí být přeskočeny odstraněné záznamy. Další informace najdete v tématu [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) členskou funkci.  
  
 Kromě `Move` funkce, `CRecordset` poskytuje členské funkce pro kontrolu, jestli jste přešli za koncem nebo náskok před začátkem sady záznamů.  
  
 Chcete-li zjistit, jestli je možné ve vaší sadě záznamů posouvání, zavolejte `CanScroll` členskou funkci.  
  
#### <a name="to-scroll"></a>Posun  
  
1.  Dál jeden záznam nebo jedné sady řádků: volání [MoveNext](../../mfc/reference/crecordset-class.md#movenext) členskou funkci.  
  
2.  Zpětně jeden záznam nebo jedné sady řádků: volání [MovePrev](../../mfc/reference/crecordset-class.md#moveprev) členskou funkci.  
  
3.  Na první záznam v sadě záznamů: volání [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) členskou funkci.  
  
4.  Poslední záznam v sadě záznamů nebo poslední sadu řádků: volání [MoveLast](../../mfc/reference/crecordset-class.md#movelast) členskou funkci.  
  
5.  *N* záznamy vzhledem k aktuální pozici: volání [přesunout](../../mfc/reference/crecordset-class.md#move) členskou funkci.  
  
#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>K otestování konec nebo začátek sady záznamů  
  
1.  Přesunuli za poslední záznam? Volání [IsEOF](../../mfc/reference/crecordset-class.md#iseof) členskou funkci.  
  
2.  Přesunuli náskok před první záznam (Přechod zpět)? Volání [IsBOF](../../mfc/reference/crecordset-class.md#isbof) členskou funkci.  
  
 Následující příklad kódu používá `IsBOF` a `IsEOF` k rozpoznání omezení sady záznamů při posouvání v obou směrech.  
  
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
  
 `IsEOF` vrací nenulovou hodnotu, pokud sada záznamů je umístěn za poslední záznam. `IsBOF` vrací nenulovou hodnotu, pokud sada záznamů je umístěn před první záznam (před všechny záznamy). V obou případech neexistuje aktuální záznam se má operace provést. Při volání `MovePrev` při `IsBOF` je již hodnotu TRUE nebo volání `MoveNext` při `IsEOF` už je hodnota TRUE, rozhraní vyvolá `CDBException`. Můžete také použít `IsBOF` a `IsEOF` ke kontrole prázdnou sadu záznamů.  
  
 Další informace o navigaci v sadě záznamů najdete v tématu [sada záznamů: záložky a absolutní pozice (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="_core_when_scrolling_is_supported"></a> Když se podporuje posouvání.  
 Jako původně navržený SQL k dispozici posouváním pouze vpřed, ale ODBC rozšiřuje možnosti posouvání. Dostupná úroveň podpory pro posouvání, závisí na ovladače rozhraní ODBC, vaše aplikace funguje s úroveň dodržování standardu váš ovladač rozhraní ODBC API, a zda je knihovna kurzorů rozhraní ODBC načten do paměti. Další informace najdete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [ODBC: Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!TIP]
>  Můžete řídit, jestli se používá knihovna kurzorů rozhraní. Zobrazit *bUseCursorLib* a *dwOptions* parametry [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open).  
  
> [!NOTE]
>  Na rozdíl od tříd DAO knihovny MFC, třídy knihovny MFC rozhraní ODBC se neposkytuje sadu `Find` funkce pro vyhledání záznam další (nebo staršího), splňující zadaná kritéria.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)   
 [CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)   
 [Sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)