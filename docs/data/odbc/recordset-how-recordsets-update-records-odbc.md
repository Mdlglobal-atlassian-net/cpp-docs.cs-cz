---
title: 'Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
ms.openlocfilehash: 03fb696c1fadd834962d37c8e75b5f8910af819e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366970"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Kromě možnosti výběru záznamů ze zdroje dat mohou sady záznamů (volitelně) vybrané záznamy aktualizovat nebo odstranit nebo přidat nové záznamy. Aktualizovatelnost sady záznamů určují tři faktory: zda lze aktualizovat připojený zdroj dat, možnosti, které zadáte při vytváření objektu sady záznamů, a sql, který je vytvořen.

> [!NOTE]
> Sql, na `CRecordset` kterém je objekt založen může ovlivnit aktualizovatelnost sady záznamů. Například pokud sql obsahuje spojení nebo **group by** klauzule, knihovna MFC nastaví aktualizovatelnost na NEPRAVDA.

> [!NOTE]
> Toto téma se vztahuje `CRecordset` na objekty odvozené od, ve kterém hromadné načítání řádků nebyla implementována. Pokud používáte hromadné načítání řádků, přečtěte si část [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Toto téma vysvětluje:

- [Vaše role v aktualizaci sady záznamů](#_core_your_role_in_recordset_updating) a co pro vás framework dělá.

- [Sada záznamů jako editační vyrovnávací paměť](#_core_the_edit_buffer) a [rozdíly mezi dynasadami a snímky](#_core_dynasets_and_snapshots).

[Sada záznamů: Jak přidatnovou, upravit a odstranit práci (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) popisuje akce těchto funkcí z hlediska sady záznamů.

[Sada záznamů: Další informace o aktualizacích (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) dokončí článek aktualizace sady záznamů tím, že vysvětlí, jak transakce ovlivňují aktualizace, jak zavření sady záznamů nebo posouvání ovlivňuje probíhající aktualizace a jak aktualizace interagují s aktualizacemi ostatních uživatelů.

## <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>Vaše role v aktualizaci sady záznamů

V následující tabulce je uvedena vaše role při přidávání, úpravách nebo odstraňování záznamů spolu s tím, co pro vás framework dělá.

### <a name="recordset-updating-you-and-the-framework"></a>Aktualizace sady záznamů: Vy a rozhraní

|Vy|Rámec|
|---------|-------------------|
|Určete, zda je zdroj dat aktualizovatelný (nebo připojitelný).|Poskytuje členské funkce [CDatabase](../../mfc/reference/cdatabase-class.md) pro testování aktualizovatelnosti nebo appendability zdroje dat.|
|Otevřete aktualizovatelnou sadu záznamů (libovolného typu).||
|Zjistěte, zda je sada záznamů `CRecordset` aktualizovatelná `CanUpdate` voláním funkcí aktualizace, jako je například nebo `CanAppend`.||
|Volání členských funkcí sady záznamů pro přidání, úpravu a odstranění záznamů.|Spravuje mechanismy výměny dat mezi objektem sady záznamů a zdrojem dat.|
|Volitelně můžete použít transakce k řízení procesu aktualizace.|Dodává `CDatabase` členské funkce pro podporu transakcí.|

Další informace o transakcích naleznete v [tématu Transakce (ODBC).](../../data/odbc/transaction-odbc.md)

## <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>Vyrovnávací paměť pro úpravy

Společně slouží datové členy pole sady záznamů jako vyrovnávací paměť pro úpravy, která obsahuje jeden záznam – aktuální záznam. Operace aktualizace používají tuto vyrovnávací paměť k provozu s aktuálním záznamem.

- Když přidáte záznam, vyrovnávací paměť pro úpravy se použije k vytvoření nového záznamu. Po přidání záznamu se záznam, který byl dříve aktuální, opět stane aktuálním.

- Při aktualizaci (úpravě) záznamu se vyrovnávací paměť pro úpravy používá k nastavení datových členů pole sady záznamů na nové hodnoty. Po dokončení aktualizace je aktualizovaný záznam stále aktuální.

Při volání [AddNew](../../mfc/reference/crecordset-class.md#addnew) nebo [Upravit](../../mfc/reference/crecordset-class.md#edit), aktuální záznam je uložen, takže jej lze později obnovit podle potřeby. Při volání [Odstranit](../../mfc/reference/crecordset-class.md#delete)není aktuální záznam uložen, ale je označen jako odstraněný a je nutné přejít na jiný záznam.

> [!NOTE]
> Vyrovnávací paměť pro úpravy nehraje při odstraňování záznamů žádnou roli. Když odstraníte aktuální záznam, záznam je označen jako odstraněný a sada záznamů je "není na záznamu", dokud se neposunete na jiný záznam.

## <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>Dynasady a snímky

[Sady dynasadcí](../../data/odbc/dynaset.md) aktualizují obsah záznamu při posouvání k záznamu. [Snímky](../../data/odbc/snapshot.md) jsou statické reprezentace záznamů, takže obsah záznamu se neaktualizuje, pokud nezavoláte [Requery](../../mfc/reference/crecordset-class.md#requery). Chcete-li používat všechny funkce dynasetu, musíte pracovat s ovladačem ODBC, který odpovídá správné úrovni podpory rozhraní API ROZHRANÍ ODBC. Další informace naleznete [v tématech ODBC](../../data/odbc/odbc-basics.md) a [Dynaset](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Jak fungují operace AddNew, Edit a Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
