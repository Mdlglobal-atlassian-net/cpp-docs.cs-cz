---
title: 'Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b16faf4c5ef0208c946cff123ecbe62b513e65ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Kromě schopnosti vyberte záznamy ze zdroje dat sady záznamů můžete (volitelně) aktualizovat nebo odstranit vybrané záznamy nebo přidat nové záznamy. Sady záznamů aktualizovatelnosti určit třech faktorech: jestli je možné aktualizovat připojeného zdroje dat, možnosti určíte, že při vytváření objektu sady záznamů a SQL, který je vytvořen.  
  
> [!NOTE]
>  SQL, na kterém vaše `CRecordset` objekt založen může ovlivnit aktualizovatelnosti sady záznamů. Například pokud vaše SQL obsahuje spojení nebo **GROUP BY** klauzuli MFC nastaví aktualizovatelnosti na **FALSE**.  
  
> [!NOTE]
>  Toto téma se vztahuje na objekty, které jsou odvozené z `CRecordset` v který řádek hromadné načítání se neimplementovala. Pokud používáte hromadné načítání řádků, přečtěte si téma [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Toto téma vysvětluje:  
  
-   [Vaše role při aktualizaci sady záznamů](#_core_your_role_in_recordset_updating) a co rozhraní framework za vás.  
  
-   [Sada záznamů jako vyrovnávací paměť úprav](#_core_the_edit_buffer) a [rozdíly mezi dynamické sady a snímky](#_core_dynasets_and_snapshots).  
  
 [Sada záznamů: Jak AddNew, Edit a odstranit pracovní (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) popisuje akce, které z těchto funkcí z hlediska sady záznamů.  
  
 [Sada záznamů: Další o aktualizace (rozhraní ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) vysvětlením vliv transakcí na aktualizace, jak zavřít sadu záznamů, posouvání ovlivňuje aktualizace v průběhu a jak se vaše aktualizace komunikovat s aktualizace jiné dokončí scénáře aktualizace sady záznamů uživatelé.  
  
##  <a name="_core_your_role_in_recordset_updating"></a> Vaše Role při aktualizaci sady záznamů  
 Následující tabulka ukazuje vaše role při použití sady záznamů Pokud chcete přidat, upravit nebo odstranit záznamy, společně s rozhraní provede za vás.  
  
### <a name="recordset-updating-you-and-the-framework"></a>Aktualizace sady záznamů: Vy a architektura  
  
|Vy|Rozhraní framework|  
|---------|-------------------|  
|Určí, zda je zdroj dat lze aktualizovat (nebo připojitelná).|Zdroje [CDatabase](../../mfc/reference/cdatabase-class.md) členské funkce pro testování aktualizovatelnosti zdroj dat nebo připojitelnosti.|  
|Otevřete aktualizovat sadu záznamů (libovolný typ).||  
|Určit, zda je sada záznamů aktualizovat voláním `CRecordset` aktualizační funkce `CanUpdate` nebo `CanAppend`.||  
|Volání členských funkcí přidat, upravit a odstranit záznamy sada záznamů.|Mechanismus výměny dat mezi objektu sady záznamů a zdroji dat spravuje.|  
|Volitelně můžete používejte transakce pro řízení procesu aktualizace.|Zdroje `CDatabase` členské funkce pro podporu transakcí.|  
  
 Další informace o transakcích najdete v tématu [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_the_edit_buffer"></a> Vyrovnávací paměti pro úpravy  
 Souhrnně vzato pole datových členů sady záznamů slouží jako upravená vyrovnávací paměť, která obsahuje jeden záznam – záznam na aktuální záznam. Operace aktualizace pomocí této vyrovnávací paměti k provozu na aktuální záznam.  
  
-   Když přidáte záznam, vyrovnávací paměť pro úpravu slouží k vytvoření nového záznamu. Po dokončení přidávání záznamu, stane záznam, který byl dříve aktuální aktuální znovu.  
  
-   Při aktualizaci vyrovnávací paměti (Upravit) záznam úpravy slouží k nastavení pole datových členů sady záznamů nové hodnoty. Po dokončení aktualizace, aktualizované záznamu je stále aktuální.  
  
 Při volání [AddNew](../../mfc/reference/crecordset-class.md#addnew) nebo [upravit](../../mfc/reference/crecordset-class.md#edit), je uložen na aktuální záznam, tak může být obnovena novější podle potřeby. Při volání [odstranit](../../mfc/reference/crecordset-class.md#delete), není uložen na aktuální záznam, ale je označen jako odstraněný, a musí přejít k jinému záznamu.  
  
> [!NOTE]
>  Vyrovnávací paměť pro úpravu hraje žádné roli při odstraňování záznamu. Pokud odstraníte záznam na aktuální záznam, záznamu je označen jako odstraněný a sada záznamů je "ne na záznam" dokud přejděte na jiný záznam.  
  
##  <a name="_core_dynasets_and_snapshots"></a> Dynamické sady a snímky  
 [Dynamické sady](../../data/odbc/dynaset.md) aktualizovat obsah záznamů při posunutí záznamu. [Snímky](../../data/odbc/snapshot.md) představují statické záznamy, takže obsah záznamů není aktualizován, dokud zavoláte [Requery –](../../mfc/reference/crecordset-class.md#requery). Pokud chcete používat všechny funkce dynamické sady, musí být práce s ovladač ODBC, který vyhovuje správné úrovně podpory rozhraní API ODBC. Další informace najdete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [dynamická sada](../../data/odbc/dynaset.md).  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Jak fungují operace AddNew, Edit a Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)