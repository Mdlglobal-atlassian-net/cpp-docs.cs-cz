---
title: 'Transakce: Vliv transakcí na aktualizace (ODBC) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e540b68b820234ee6d30295b40c7e0f4cb7c806d
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338587"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transakce: Vliv transakcí na aktualizace (rozhraní ODBC)
Aktualizuje [zdroj dat](../../data/odbc/data-source-odbc.md) jsou spravovány během transakce prostřednictvím vyrovnávací paměti (stejnou metodu používá mimo transakce). Pole datových členů sady záznamů společně slouží jako vyrovnávací paměť úprav, který obsahuje aktuální záznam, který sada záznamů zálohuje dočasně během `AddNew` nebo `Edit`. Během `Delete` operaci, aktuální záznam nejsou zálohovány v rámci transakce. Další informace o vyrovnávací paměť pro úpravu a jak aktualizace uložit aktuální záznam najdete v tématu [sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat `AddNew`, `Edit`, nebo `Delete`. Místo toho musíte napsat vlastní funkce pro provádění aktualizací ke zdroji dat. Další informace o hromadném načítání řádků naleznete v tématu [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Během transakce `AddNew`, `Edit`, a `Delete` operace může být potvrzena nebo vrácena zpět. Účinky `CommitTrans` a `Rollback` může způsobit, že aktuální záznam obnoven do vyrovnávací paměti pro úpravy. Pokud chcete mít jistotu, že aktuální záznam správné obnovení, je důležité pochopit, jak `CommitTrans` a `Rollback` členské funkce `CDatabase` pracovat s funkcí aktualizace `CRecordset`.  
  
##  <a name="_core_how_committrans_affects_updates"></a> Jak ovlivňuje CommitTrans – aktualizace  
 Následující tabulka popisuje účinky `CommitTrans` transakcí.  
  
### <a name="how-committrans-affects-updates"></a>Jak ovlivňuje CommitTrans – aktualizace  
  
|Operace|Stav zdroje dat|  
|---------------|---------------------------|  
|`AddNew` a `Update`a pak `CommitTrans`|Ke zdroji dat jsou přidá nový záznam.|  
|`AddNew` (bez `Update`) a pak `CommitTrans`|Nový záznam se ztratí. Nebyla přidána do zdroje dat záznam.|  
|`Edit` a `Update`a pak `CommitTrans`|Úpravy potvrzeny ke zdroji dat.|  
|`Edit` (bez `Update`) a pak `CommitTrans`|Záznam se ztratí. Záznam ve zdroji dat. nemění.|  
|`Delete` Potom `CommitTrans`|Záznamy ze zdroje dat odstranit.|  
  
##  <a name="_core_how_rollback_affects_updates"></a> Jak ovlivňuje vrácení zpět transakcí  
 Následující tabulka popisuje účinky `Rollback` transakcí.  
  
### <a name="how-rollback-affects-transactions"></a>Jak ovlivňuje vrácení zpět transakcí  
  
|Operace|Stav aktuální záznam|Musíte také|Stav zdroje dat|  
|---------------|------------------------------|-------------------|---------------------------|  
|`AddNew` a `Update`, pak `Rollback`|Obsah aktuální záznam jsou ukládána dočasně, aby uvolnil prostor pro nový záznam. Nový záznam se zadá do vyrovnávací paměti pro úpravy. Po `Update` nazývá aktuální záznam, budou obnoveny do vyrovnávací paměti pro úpravy.||Přidání zdroje dat od `Update` je obrácený.|  
|`AddNew` (bez `Update`), pak `Rollback`|Obsah aktuální záznam jsou ukládána dočasně, aby uvolnil prostor pro nový záznam. Upravit vyrovnávací paměť obsahuje nový záznam.|Volání `AddNew` obnovíte vyrovnávací paměť pro úpravu prázdný nového záznamu. Nebo se telefonicky `Move`(0) k obnovení původních hodnot do vyrovnávací paměti pro úpravy.|Protože `Update` nebyla volána, nejsou žádné změny provedené na zdroj dat.|  
|`Edit` a `Update`, pak `Rollback`|Neupravenou verzi aktuální záznam jsou ukládána dočasně. Na obsah upravit vyrovnávací paměti jsou provedeny změny. Po `Update` je volána, označují bitem verze záznamu je stále dočasně ukládají.|*Dynamická sada*: přejděte mimo aktuální záznam pak se vrátit na obnovení neupravenou verzi záznamu vyrovnávací paměti pro úpravy.<br /><br /> *Snímek*: volání `Requery` k aktualizaci záznamů ze zdroje dat.|Změny do zdroje dat od `Update` se vrátit zpět.|  
|`Edit` (bez `Update`), pak `Rollback`|Neupravenou verzi aktuální záznam jsou ukládána dočasně. Na obsah upravit vyrovnávací paměti jsou provedeny změny.|Volání `Edit` znovu obnovíte neupravenou verzi záznamu vyrovnávací paměti pro úpravy.|Protože `Update` nebyla volána, nejsou žádné změny provedené na zdroj dat.|  
|`Delete` Potom `Rollback`|Obsah aktuální záznam je odstraněn.|Volání `Requery` obnovit obsah aktuální záznam ze zdroje dat.|Odstranění dat ze zdroje dat je obrácený.|  
  
## <a name="see-also"></a>Viz také  
 [Transakce (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transakce (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transakce: Provádění transakcí v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [CDatabase – třída](../../mfc/reference/cdatabase-class.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)