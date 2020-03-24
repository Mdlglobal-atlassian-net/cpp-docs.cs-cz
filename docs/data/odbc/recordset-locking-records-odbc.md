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
ms.openlocfilehash: d4e80816a131c997e9f5bfaa34f025394b05a358
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212859"
---
# <a name="recordset-locking-records-odbc"></a>Sada záznamů: Zamykání záznamů (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje:

- [Typy zamykání záznamů k dispozici](#_core_record.2d.locking_modes).

- [Jak uzamknout záznamy v sadě záznamů během aktualizací](#_core_locking_records_in_your_recordset).

Použijete-li sadu záznamů k aktualizaci záznamu ve zdroji dat, může aplikace uzamknout záznam, takže žádný jiný uživatel nebude moci současně aktualizovat záznam. Stav záznamu aktualizovaného dvěma uživateli ve stejnou dobu není definován, pokud systém nemůže zaručit, že dva uživatelé nemohou aktualizovat záznam současně.

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Pokud jste implementovali hromadné načítání řádků, některé informace se nevztahují. Například nemůžete volat `Edit` a `Update` členské funkce. Další informace o hromadném načítání řádků naleznete v tématu [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>Režimy zamykání záznamů

Třídy databáze poskytují dva [režimy zamykání záznamů](../../mfc/reference/crecordset-class.md#setlockingmode):

- Optimistické zamykání (výchozí nastavení)

- Pesimistické zamykání

Aktualizace záznamu probíhá ve třech krocích:

1. Operaci zahájíte voláním funkce [Upravit](../../mfc/reference/crecordset-class.md#edit) členskou funkci.

1. Změníte příslušná pole aktuálního záznamu.

1. Ukončíte operaci – a obvykle zadáte aktualizaci – voláním členské funkce [Update](../../mfc/reference/crecordset-class.md#update) .

Optimistické zamykání uzamkne záznam ve zdroji dat pouze během volání `Update`. Pokud používáte optimistické zamykání ve víceuživatelském prostředí, aplikace by měla zpracovat podmínku selhání `Update`. Pesimistické uzamykání uzamkne záznam hned po volání `Edit` a neuvolní ho, dokud nebudete volat `Update` (selhání jsou uvedena prostřednictvím mechanismu `CDBException`, nikoli hodnotou FALSE vrácenou `Update`). Pesimistické zamykání má potenciální snížení výkonu pro jiné uživatele, protože souběžný přístup ke stejnému záznamu může počkat až do dokončení procesu `Update` vaší aplikace.

##  <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>Zamykání záznamů v sadě záznamů

Chcete-li změnit [režim uzamykání](#_core_record.2d.locking_modes) objektu sady záznamů z výchozí hodnoty, je nutné před voláním `Edit`změnit režim.

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Změna aktuálního režimu uzamykání pro sadu záznamů

1. Zavolejte členskou funkci [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) a určete buď `CRecordset::pessimistic`, nebo `CRecordset::optimistic`.

Nový režim uzamykání zůstane v platnosti, dokud ho znovu nezměníte nebo dokud nebude sada záznamů zavřena.

> [!NOTE]
>  Relativně málo ovladačů ODBC aktuálně podporuje pesimistické zamykání.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Provedení spojení (rozhraní ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
