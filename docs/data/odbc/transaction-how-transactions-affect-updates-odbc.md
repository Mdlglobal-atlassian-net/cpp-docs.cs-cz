---
title: "Transakce: Vliv transakcí na aktualizace (rozhraní ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59eb8aecbf2dd2138c8a0469d71364b55fd82774
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transakce: Vliv transakcí na aktualizace (rozhraní ODBC)
Aktualizace [zdroj dat](../../data/odbc/data-source-odbc.md) jsou spravovány během transakcí prostřednictvím vyrovnávací paměti (stejnou metodu použít mimo transakce). Pole datových členů sady záznamů slouží jako vyrovnávací paměť úprav obsahující aktuální záznam, který zálohuje sady záznamů dočasně během `AddNew` nebo **upravit**. Během **odstranit** operaci, aktuální záznam se nezálohuje společně v rámci transakce. Další informace o upravené vyrovnávací paměti a jak ukládat aktualizace na aktuální záznam najdete v tématu [sada záznamů: Jak sady záznamů aktualizace záznamů (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
> [!NOTE]
>  Pokud jste implementovali hromadné načítání řádků, nelze volat `AddNew`, **upravit**, nebo **odstranit**. Místo toho musíte napsat vlastní funkce pro provádění aktualizací ke zdroji dat. Další informace o hromadné načítání řádků najdete v tématu [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Během transakce `AddNew`, **upravit**, a **odstranit** operace může být potvrzena nebo vrácena zpět. Důsledky **CommitTrans** a **vrácení zpět** může způsobit, že aktuální záznam obnoven upravené vyrovnávací paměti. Abyste měli jistotu, že je správně obnoven aktuální záznam, je důležité pochopit, jak **CommitTrans** a **vrácení zpět** členské funkce `CDatabase` práce s funkcí aktualizace `CRecordset`.  
  
##  <a name="_core_how_committrans_affects_updates"></a>Jak ovlivňuje CommitTrans aktualizace  
 Následující tabulka popisuje účinky **CommitTrans** na transakce.  
  
### <a name="how-committrans-affects-updates"></a>Jak ovlivňuje CommitTrans aktualizace  
  
|Operace|Stav zdroje dat|  
|---------------|---------------------------|  
|`AddNew`a **aktualizace**a potom **CommitTrans**|Nový záznam se přidají do zdroje dat.|  
|`AddNew`(bez **aktualizace**) a potom **CommitTrans**|Nový záznam bude ztracena. Nebyla přidána do zdroje dat záznam.|  
|**Upravit** a **aktualizace**a potom **CommitTrans**|Úpravy potvrzené ke zdroji dat.|  
|**Upravit** (bez **aktualizace**) a potom **CommitTrans**|Úpravy záznamu, budou ztraceny. Záznam zůstává beze změny na datovém zdroji.|  
|**Odstranit** pak **CommitTrans**|Záznamy byly odstraněny ze zdroje dat.|  
  
##  <a name="_core_how_rollback_affects_updates"></a>Jak ovlivňuje vrácení transakce  
 Následující tabulka popisuje účinky **vrácení zpět** na transakce.  
  
### <a name="how-rollback-affects-transactions"></a>Jak ovlivňuje vrácení transakce  
  
|Operace|Stav aktuální záznam.|Musíte také|Stav zdroje dat|  
|---------------|------------------------------|-------------------|---------------------------|  
|`AddNew`a **aktualizace**, pak **vrácení zpět**|Obsah na aktuální záznam jsou ukládána dočasně, aby uvolnil prostor pro nový záznam. Nový záznam je zadán do vyrovnávací paměti pro úpravy. Po **aktualizace** nazývá aktuální záznam je obnovit do vyrovnávací paměti pro úpravy.||Přidání ke zdroji dat provedené **aktualizace** je obrácený.|  
|`AddNew`(bez **aktualizace**), pak **vrácení zpět**|Obsah na aktuální záznam jsou ukládána dočasně, aby uvolnil prostor pro nový záznam. Upravit vyrovnávací paměť obsahuje nový záznam.|Volání `AddNew` znovu k obnovení vyrovnávací paměť pro úpravu záznamu prázdné, nové. Nebo volání **přesunout**(0), chcete-li obnovit původní hodnoty upravené vyrovnávací paměti.|Protože **aktualizace** nebyla volána, nebyly provedeny žádné změny provedené v zdroji dat.|  
|**Upravit** a **aktualizace**, pak **vrácení zpět**|Neupravené verze na aktuální záznam jsou ukládána dočasně. Úpravy jsou provedeny obsah upravené vyrovnávací paměti. Po **aktualizace** je volána, neupravenou verzi záznamu je stále dočasně uložena.|*Dynamická sada*: přejděte mimo aktuální záznam pak zpět k obnovení neupravené verze záznamu upravené vyrovnávací paměti.<br /><br /> *Snímek*: volání **Requery –** aktualizuje sadu záznamů z datového zdroje.|Změny provedené zdroj dat **aktualizace** se vrátit zpět.|  
|**Upravit** (bez **aktualizace**), pak **vrácení zpět**|Neupravené verze na aktuální záznam jsou ukládána dočasně. Úpravy jsou provedeny obsah upravené vyrovnávací paměti.|Volání **upravit** znovu k obnovení neupravené verze záznamu upravené vyrovnávací paměti.|Protože **aktualizace** nebyla volána, nebyly provedeny žádné změny provedené v zdroji dat.|  
|**Odstranit** pak **vrácení zpět**|Obsah na aktuální záznam se odstraní.|Volání **Requery** obnovit ze zdroje dat obsah na aktuální záznam.|Odstranění dat ze zdroje dat je obrácený.|  
  
## <a name="see-also"></a>Viz také  
 [Transakce (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transakce (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transakce: Provádění transakcí v sadě záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [CDatabase – třída](../../mfc/reference/cdatabase-class.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)