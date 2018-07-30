---
title: 'Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC) | Dokumentace Microsoftu'
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
ms.openlocfilehash: 2697952b500c7643bf0723c99395e56ebc48ad84
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340700"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)
Toto téma platí pro třídy knihovny MFC rozhraní ODBC.  
  
 Kromě schopnosti vyberte záznamy ze zdroje dat sady záznamů můžete (volitelně) aktualizovat nebo odstranit vybrané záznamy nebo přidat nové záznamy. Tři faktory aktualizovatelnosti sada záznamů: Určuje, zda je možné aktualizovat připojených zdrojů dat, možnosti zadáte při vytváření objektu sady záznamů a SQL, který je vytvořen.  
  
> [!NOTE]
>  SQL, na kterém vaše `CRecordset` podle objektu může ovlivnit aktualizovatelnosti sady záznamů. Například pokud vaše SQL obsahuje spojení nebo **Group** klauzule MFC nastaví aktualizovatelnosti na hodnotu FALSE.  
  
> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené z `CRecordset` v který řádek hromadné načítání není implementovaná. Pokud používáte hromadné načítání řádků, přečtěte si téma [sada záznamů: načítání hromadné záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Toto téma vysvětluje:  
  
-   [Vaše role při aktualizaci sady záznamů](#_core_your_role_in_recordset_updating) a rozhraní udělá za vás.  
  
-   [Sada záznamů jako vyrovnávací paměť úprav](#_core_the_edit_buffer) a [rozdíly v dynamických sadách a snímky](#_core_dynasets_and_snapshots).  
  
 [Sada záznamů: Jak funkce operací AddNew, Edit a Delete práce (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) popisuje akce, které z těchto funkcí z hlediska sady záznamů.  
  
 [Sada záznamů: Další informace o aktualizace (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) poslední částí scénáře aktualizace sady záznamů a s vysvětlením vliv transakcí na aktualizace, jak uzavírání sady záznamů nebo posouvání ovlivňuje Probíhá aktualizace a jak aktualizace využívat aktualizace jiných uživatelé.  
  
##  <a name="_core_your_role_in_recordset_updating"></a> Vaše Role při aktualizaci sady záznamů  
 Následující tabulka uvádí vaši roli v použití sad záznamů přidat, upravit nebo odstranit záznamy, spolu s rozhraní udělá za vás.  
  
### <a name="recordset-updating-you-and-the-framework"></a>Aktualizace sady záznamů: Jste a rozhraní  
  
|Vy|Rozhraní framework|  
|---------|-------------------|  
|Zjistit, zda zdroj dat je možné aktualizovat (nebo připojitelná).|Poskytuje [CDatabase](../../mfc/reference/cdatabase-class.md) členské funkce pro testování aktualizovatelnosti zdroj dat nebo připojitelnosti.|  
|Otevřete aktualizovatelnou sadu záznamů (libovolného typu).||  
|Zjistit, jestli je sada záznamů aktualizovat pomocí volání `CRecordset` aktualizace funkcí, jako `CanUpdate` nebo `CanAppend`.||  
|Sada záznamů volejte členské funkce pro přidání, úpravy a odstraňování záznamů.|Spravuje mechanismu výměna dat mezi objektu sady záznamů a zdrojem dat.|  
|Volitelně můžete používání transakcí k řízení procesu aktualizace.|Poskytuje `CDatabase` členské funkce pro podporu transakcí.|  
  
 Další informace o transakcích najdete v tématu [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_the_edit_buffer"></a> Vyrovnávací paměť pro úpravu  
 Přijata společně, datové členy polí sady záznamů sloužit jako vyrovnávací paměť úprav, který obsahuje jeden záznam – aktuální záznam. Operace aktualizace pomocí této vyrovnávací paměti pro provoz na aktuální záznam.  
  
-   Po přidání záznamu vyrovnávací paměť pro úpravu slouží k vytvoření nového záznamu. Po dokončení přidávání záznam záznam, který byl dříve aktuální opět aktuální.  
  
-   Při aktualizaci vyrovnávací paměti (Upravit) záznam, úpravy slouží k nastavení datové členy polí sady záznamů s novými hodnotami. Po dokončení aktualizace, je stále aktuální aktualizovaný záznam.  
  
 Při volání [AddNew](../../mfc/reference/crecordset-class.md#addnew) nebo [upravit](../../mfc/reference/crecordset-class.md#edit), aktuální záznam je uložen, takže ji můžete obnovit později podle potřeby. Při volání [odstranit](../../mfc/reference/crecordset-class.md#delete)a musí přejít k jinému záznamu aktuální záznam se neuloží, ale je označen jako odstraněný.  
  
> [!NOTE]
>  Vyrovnávací paměť pro úpravu hraje žádná role při odstraňování záznamu. Když odstraníte aktuální záznam, záznam je označen jako odstraněný a sady záznamů je "ne na záznam" dokud přejděte na jiný záznam.  
  
##  <a name="_core_dynasets_and_snapshots"></a> Dynamické sady a snímky  
 [Dynamické sady](../../data/odbc/dynaset.md) aktualizace záznamu obsah při posunutí se záznam. [Snímky](../../data/odbc/snapshot.md) jsou statické reprezentace záznamy, takže obsah záznamů se neobnovily Pokud zavoláte [Requery](../../mfc/reference/crecordset-class.md#requery). Pokud chcete používat všechny funkce dynamické sady, musí pracovat prostřednictvím ovladače ODBC, který odpovídá správnou úroveň podpory rozhraní API ODBC. Další informace najdete v tématu [ODBC](../../data/odbc/odbc-basics.md) a [dynamická sada](../../data/odbc/dynaset.md).  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Jak fungují operace AddNew, Edit a Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)