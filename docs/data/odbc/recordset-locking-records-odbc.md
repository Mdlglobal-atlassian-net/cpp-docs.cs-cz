---
title: 'Sada záznamů: Zamykání záznamů (ODBC) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51c84014786b8c27def7a568b85da316079c2bc1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066328"
---
# <a name="recordset-locking-records-odbc"></a>Sada záznamů: Zamykání záznamů (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje:

- [Typy záznamu uzamčení k dispozici](#_core_record.2d.locking_modes).

- [Jak uzamknout záznamy ve vaší sadě záznamů při aktualizacích](#_core_locking_records_in_your_recordset).

Při aktualizaci záznamu ve zdroji dat pomocí sady záznamů, aplikace uzamknout záznam, aby žádný jiný uživatel upravovat záznam ve stejnou dobu. Stav záznamu aktualizovat ve stejnou dobu dva uživatele není definováno, pokud systém nemůže zaručit, že dva uživatele nejde aktualizovat záznam současně.

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené z `CRecordset` v který řádek hromadné načítání není implementovaná. Pokud jste implementovali hromadné načítání řádků, některé informace se nevztahují. Například nelze volat `Edit` a `Update` členské funkce. Další informace o hromadném načítání řádků naleznete v tématu [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="_core_record.2d.locking_modes"></a> Režimy zamykání záznamů

Databázové třídy poskytují dvě [režimy zamykání záznamů](../../mfc/reference/crecordset-class.md#setlockingmode):

- Optimistické zamykání (výchozí)

- Pesimistické zamykání

Aktualizace záznamu dojde ve třech krocích:

1. Operace zahájíte volání [upravit](../../mfc/reference/crecordset-class.md#edit) členskou funkci.

1. Při změně odpovídající pole z aktuální záznam.

1. Ukončení operace – a obvykle potvrďte aktualizaci – voláním [aktualizovat](../../mfc/reference/crecordset-class.md#update) členskou funkci.

Optimistické uzamykání záznamu ve zdroji dat pouze při uzamčení `Update` volání. Pokud používáte optimistické uzamykání, v prostředí, aplikace by měl zpracovat `Update` chybový stav. Pesimistické zamykání uzamkne záznam, jakmile zavoláte `Edit` a neuvolní ho dokud volání `Update` (chyby jsou označeny pomocí `CDBException` mechanismus, nikoli podle hodnoty false vrácený `Update`). Pesimistické zamykání má potenciální snížení výkonu pro ostatní uživatele, protože souběžný přístup do stejného záznamu muset počkat na dokončení vaší aplikace `Update` procesu.

##  <a name="_core_locking_records_in_your_recordset"></a> Uzamčení záznamů do sady záznamů

Pokud chcete změnit objekt sady záznamů [režim uzamčení](#_core_record.2d.locking_modes) z výchozí hodnoty, je nutné před voláním změnit režim `Edit`.

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Chcete-li změnit aktuální režim uzamčení pro sady záznamů

1. Volání [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) členskou funkci, zadat buď `CRecordset::pessimistic` nebo `CRecordset::optimistic`.

Nový režim uzamčení zůstává v platnosti, dokud nebude znovu změnit nebo sady záznamů je zavřený.

> [!NOTE]
>  Relativně málo ovladače rozhraní ODBC aktuálně podporují pesimistické zamykání.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Provedení spojení (rozhraní ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)