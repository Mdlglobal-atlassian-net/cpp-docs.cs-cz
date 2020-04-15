---
title: 'Sada záznamů: Zamykání záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
ms.openlocfilehash: abd5f817ad321241df2d8565bd6bf346c0792088
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366965"
---
# <a name="recordset-locking-records-odbc"></a>Sada záznamů: Zamykání záznamů (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Toto téma vysvětluje:

- [Druhy zamykání záznamů k dispozici](#_core_record.2d.locking_modes).

- [Jak uzamknout záznamy v sadě záznamů během aktualizací](#_core_locking_records_in_your_recordset).

Při použití sady záznamů k aktualizaci záznamu ve zdroji dat může aplikace záznam uzamknout, aby žádný jiný uživatel mohl záznam aktualizovat současně. Stav záznamu aktualizovaného dvěma uživateli současně není definován, pokud systém nemůže zaručit, že dva uživatelé nemohou aktualizovat záznam současně.

> [!NOTE]
> Toto téma se vztahuje `CRecordset` na objekty odvozené od, ve kterém hromadné načítání řádků nebyla implementována. Pokud jste implementovali hromadné načítání řádků, některé informace se nevztahují. Například nelze volat `Edit` a `Update` členské funkce. Další informace o hromadném načítání řádků naleznete v tématu [Recordset: Fetching Records in Bulk (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>Režimy zamykání záznamů

Třídy databáze poskytují dva [režimy zamykání záznamů](../../mfc/reference/crecordset-class.md#setlockingmode):

- Optimistické zamykání (výchozí nastavení)

- Pesimistické zamykání

Aktualizace záznamu probíhá ve třech krocích:

1. Operaci zahájíte voláním funkce [Upravit](../../mfc/reference/crecordset-class.md#edit) člen.

1. Změníte příslušná pole aktuálního záznamu.

1. Operaci ukončíte a obvykle potvrdíte aktualizaci voláním členské funkce [Aktualizace.](../../mfc/reference/crecordset-class.md#update)

Optimistické uzamčení uzamkne záznam `Update` ve zdroji dat pouze během volání. Pokud používáte optimistické zamykání v prostředí `Update` s více uživateli, aplikace by měla zpracovat podmínku selhání. Pesimistické zamykání uzamkne záznam, `Edit` jakmile `Update` zavoláte, a neuvolní `CDBException` jej, dokud nezavoláte `Update`(chyby jsou indikovány prostřednictvím mechanismu, nikoli hodnotou FALSE vrácenou ). Pesimistické zamykání má potenciální snížení výkonu pro ostatní uživatele, protože souběžný přístup `Update` ke stejnému záznamu může čekat až do dokončení procesu aplikace.

## <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>Zamykání záznamů v sadě záznamů

Chcete-li změnit [režim uzamčení](#_core_record.2d.locking_modes) objektu sady záznamů z výchozího režimu, je nutné změnit režim před voláním `Edit`.

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Změna aktuálního režimu uzamčení sady záznamů

1. Volání množiny [SetLockingMode,](../../mfc/reference/crecordset-class.md#setlockingmode) `CRecordset::pessimistic` určující `CRecordset::optimistic`buď nebo .

Nový režim uzamčení zůstane v platnosti, dokud jej znovu nezměníte nebo dokud není sada záznamů uzavřena.

> [!NOTE]
> Relativně málo ovladačů ODBC v současné době podporuje pesimistické zamykání.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Provedení spojení (rozhraní ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
