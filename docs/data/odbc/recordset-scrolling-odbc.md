---
title: "Sada záznamů: Posouvání (ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 34dcfb9cb1d45710accba2ee6155e3c741b727be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-scrolling-odbc"></a>Sada záznamů: Posouvání (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Po otevření sady záznamů, budete potřebovat přístup k záznamům k zobrazení hodnot, provádět výpočty, generování sestav a tak dále. Posouvání vám umožňuje přechod mezi záznamy v rámci sady záznamů.  
  
 Toto téma vysvětluje:  
  
-   [Jak přejít z jednoho záznamu do druhého v sadě záznamů](#_core_scrolling_from_one_record_to_another).  
  
-   [Za jakých okolností posouvání je a nepodporuje](#_core_when_scrolling_is_supported).  
  
##  <a name="_core_scrolling_from_one_record_to_another"></a>Posouvání z jednoho záznamu  
 Třída `CRecordset` poskytuje **přesunout** členské funkce pro posouvání v rámci sady záznamů. Tyto funkce přesunout na aktuální záznam sady řádků. Pokud jste implementovali hromadné načítání řádků, **přesunout** operaci přemístí sadu záznamů velikostí sady řádků. Nemáte-li hromadné načítání, volání řádků **přesunout** funkce přemístí sadu záznamů podle jednoho záznamu pokaždé, když. Další informace o hromadné načítání řádků najdete v tématu [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Při procházení sadou, nemusí být přeskočeny odstraněné záznamy. Další informace najdete v tématu [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) – členská funkce.  
  
 Kromě **přesunout** funkce, `CRecordset` poskytuje členské funkce pro kontrolu, jestli jste přešli za konec nebo před začátek sady záznamů.  
  
 Chcete-li zjistit, zda je možné ve vaší sadě záznamů posouvání, zavolejte `CanScroll` – členská funkce.  
  
#### <a name="to-scroll"></a>Posun  
  
1.  Předávání jeden záznam nebo jedné sady řádků: volání [MoveNext](../../mfc/reference/crecordset-class.md#movenext) – členská funkce.  
  
2.  Zpětné jeden záznam nebo jedné sady řádků: volání [MovePrev](../../mfc/reference/crecordset-class.md#moveprev) – členská funkce.  
  
3.  Na první záznam v sadě záznamů: volání [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) – členská funkce.  
  
4.  Poslední záznam v sadě záznamů nebo poslední sadu řádků: volání [MoveLast](../../mfc/reference/crecordset-class.md#movelast) – členská funkce.  
  
5.  *N* záznamy vzhledem k aktuální pozici: volání [přesunout](../../mfc/reference/crecordset-class.md#move) – členská funkce.  
  
#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>K testování pro element end nebo na začátku sady záznamů  
  
1.  Přesunuli jste poslední záznam? Volání [IsEOF](../../mfc/reference/crecordset-class.md#iseof) – členská funkce.  
  
2.  Přesunuli před první záznamu (přesunutí zpět)? Volání [IsBOF](../../mfc/reference/crecordset-class.md#isbof) – členská funkce.  
  
 Následující příklad kódu používá `IsBOF` a `IsEOF` k rozpoznání mezí sady záznamů při posouvání v obou směrech.  
  
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
  
 `IsEOF`vrátí nenulovou hodnotu, pokud sada záznamů umístěna za poslední záznam. `IsBOF`vrátí nenulovou hodnotu, pokud sada záznamů umístěna před první záznam (před všechny záznamy). V obou případech je k provozu na aktuální záznam. Při volání `MovePrev` při `IsBOF` je již **TRUE** nebo volání `MoveNext` při `IsEOF` je již **TRUE**, vyvolá architektura `CDBException`. Můžete také použít `IsBOF` a `IsEOF` ke kontrole prázdnou sadu záznamů.  
  
 Další informace o navigaci v sadě záznamů najdete v tématu [sada záznamů: záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="_core_when_scrolling_is_supported"></a>Když je posouvání podporováno  
 Jako původně navržené SQL k dispozici pouze dál posouvání ale ODBC rozšiřuje možnosti posouvání. Dostupné úrovně podpory pro posouvání závisí na ovladače ODBC aplikace funguje se úroveň shody rozhraní API ODBC vaší ovladačů, a zda je knihovna kurzorů rozhraní ODBC načten do paměti. Další informace najdete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [ODBC: knihovny kurzorů ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!TIP]
>  Můžete řídit, jestli se používá knihovna kurzorů. Najdete v článku `bUseCursorLib` a `dwOptions` parametry, které [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open).  
  
> [!NOTE]
>  Na rozdíl od tříd MFC rozhraní DAO knihovny MFC rozhraní ODBC třídy neposkytují sadu **najít** funkce pro hledání záznamu další (nebo staršího) splňující zadaná kritéria.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)   
 [CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)   
 [Sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)