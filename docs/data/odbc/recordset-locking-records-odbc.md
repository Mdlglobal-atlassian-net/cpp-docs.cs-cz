---
title: 'Sada záznamů: Zamykání záznamů (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 76d7ab2df01e485ffff70120609227b9fbae6ac5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-locking-records-odbc"></a>Sada záznamů: Zamykání záznamů (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma vysvětluje:  
  
-   [Druhy zamykání záznamů k dispozici](#_core_record.2d.locking_modes).  
  
-   [Jak uzamknout záznamy ve vaší sadě záznamů během aktualizací](#_core_locking_records_in_your_recordset).  
  
 Při aktualizaci záznamu ve zdroji dat pomocí sady záznamů, vaše aplikace uzamknout záznam, aby žádný jiný uživatel můžete aktualizovat záznam ve stejnou dobu. Pokud systém nemůže zaručit, že dva uživatelé současně nelze aktualizovat záznam, není definován stav záznam aktualizovat dva uživatelé ve stejnou dobu.  
  
> [!NOTE]
>  Toto téma se vztahuje na objekty, které jsou odvozené z `CRecordset` v který řádek hromadné načítání se neimplementovala. Pokud jste implementovali hromadné načítání řádků, tak se nevztahuje na některé z informací. Například nelze volat **upravit** a **aktualizace** členské funkce. Další informace o hromadné načítání řádků najdete v tématu [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_record.2d.locking_modes"></a>Režimy uzamčení záznamu  
 Databázové třídy poskytují dva [režimy uzamčení záznamu](../../mfc/reference/crecordset-class.md#setlockingmode):  
  
-   Optimistické zamykání (výchozí)  
  
-   Pesimistické zamykání  
  
 Aktualizace záznamu se skládá ze tří kroků:  
  
1.  Operaci zahájíte volání [upravit](../../mfc/reference/crecordset-class.md#edit) – členská funkce.  
  
2.  Můžete změnit na odpovídající pole na aktuální záznam.  
  
3.  Ukončení operace – a obvykle zapíšete aktualizaci – voláním [aktualizace](../../mfc/reference/crecordset-class.md#update) – členská funkce.  
  
 Optimistické zamykání uzamkne záznam ve zdroji dat pouze během **aktualizace** volání. Pokud používáte optimistické zamykání v prostředí s více uživateli, by měla řídit tyto aplikace **aktualizace** podmínce chyby. Pesimistické zamykání uzamkne záznam, jakmile zavoláte **upravit** a neuvolní jej dokud volání **aktualizace** (chyby jsou označeny pomocí `CDBException` mechanismus, nikoli podle hodnoty **FALSE** vrácený **aktualizace**). Pesimistické zamykání má potenciální snížení výkonu pro ostatní uživatele, protože souběžný přístup na stejné záznam pravděpodobně muset počkat na dokončení vaší aplikace **aktualizace** procesu.  
  
##  <a name="_core_locking_records_in_your_recordset"></a>Uzamčení záznamů v sady záznamů  
 Pokud chcete změnit objekt sady záznamů [režim uzamčení](#_core_record.2d.locking_modes) z výchozí, musíte změnit režim před voláním **upravit**.  
  
#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Chcete-li změnit aktuální režim uzamčení pro sady záznamů  
  
1.  Volání [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) funkce člena, zadání buď **CRecordset::pessimistic** nebo **CRecordset::optimistic**.  
  
 Nový režim uzamčení zůstává v platnosti, dokud nebude znovu změnit nebo sadu záznamů je uzavřený.  
  
> [!NOTE]
>  Pesimistické zamykání aktuálně podporují poměrně málo ovladačů ODBC.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Provedení spojení (rozhraní ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)   
 [Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)