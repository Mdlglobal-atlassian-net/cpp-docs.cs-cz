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
ms.openlocfilehash: 578b3b39d90b3beb80dbd201d4982fee30dc6bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212872"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Kromě možnosti výběru záznamů ze zdroje dat mohou sady záznamů (volitelně) aktualizovat nebo odstranit vybrané záznamy nebo přidat nové záznamy. Tři faktory určují možnost aktualizace sady záznamů: zda je připojený zdroj dat aktualizovatelný, možnosti, které zadáte při vytváření objektu sady záznamů, a SQL, který je vytvořen.

> [!NOTE]
>  SQL, na kterém je objekt `CRecordset` založený, může ovlivnit možnost aktualizace vaší sady záznamů. Například pokud váš SQL obsahuje klauzuli JOIN nebo **Group by** , sada MFC nastaví aktualizaci na false.

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Používáte-li hromadné načítání řádků, přečtěte si téma [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Toto téma vysvětluje:

- [Vaše role v sadě záznamů se aktualizuje](#_core_your_role_in_recordset_updating) a k čemu architektura používá.

- [Sada záznamů jako vyrovnávací paměť úprav](#_core_the_edit_buffer) a [rozdíly mezi podsadami a snímky](#_core_dynasets_and_snapshots).

[Sada záznamů: jak funkce AddNew, Edit a DELETE Work (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) popisuje akce těchto funkcí z místa zobrazení sady záznamů.

[Sada záznamů: Další informace o aktualizacích (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) dokončí příběh aktualizace sady záznamů tím, že vysvětlují, jak transakce ovlivňují aktualizace, jak zavírání sady záznamů nebo posouvání ovlivní probíhající aktualizace a jak vaše aktualizace komunikují s aktualizacemi jiných uživatelů.

##  <a name="your-role-in-recordset-updating"></a><a name="_core_your_role_in_recordset_updating"></a>Vaše role v sadě záznamů se aktualizuje

V následující tabulce je uvedena vaše role v používání sad záznamů k přidávání, úpravám nebo odstraňování záznamů a také toho, co rozhraní dělá.

### <a name="recordset-updating-you-and-the-framework"></a>Aktualizace sady záznamů: vaše a rozhraní

|Vy|Rozhraní .NET Framework|
|---------|-------------------|
|Určete, zda je zdroj dat aktualizovatelný (nebo jej nelze připojit).|Poskytuje členské funkce [CDatabase](../../mfc/reference/cdatabase-class.md) pro testování aktualizace nebo připojení zdroje dat.|
|Otevřete aktualizovatelnou sadu záznamů (libovolného typu).||
|Určete, zda sadu záznamů je možné aktualizovat voláním funkcí `CRecordset` Update, jako je například `CanUpdate` nebo `CanAppend`.||
|Volání členských funkcí sady záznamů pro přidání, úpravu a odstranění záznamů.|Spravuje mechanismy výměny dat mezi objektem sady záznamů a zdrojem dat.|
|Volitelně můžete použít transakce k řízení procesu aktualizace.|Poskytuje `CDatabase` členské funkce pro podporu transakcí.|

Další informace o transakcích naleznete v tématu [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="the-edit-buffer"></a><a name="_core_the_edit_buffer"></a>Úprava vyrovnávací paměti

V souhrnu pole datové členy sady záznamů slouží jako upravená vyrovnávací paměť, která obsahuje jeden záznam – aktuální záznam. Operace aktualizace používají tuto vyrovnávací paměť k tomu, aby fungovaly na aktuálním záznamu.

- Při přidání záznamu se k sestavení nového záznamu použije vyrovnávací paměť pro úpravy. Po dokončení přidávání záznamu se záznam, který byl dříve aktuální, začne znovu aktuální.

- Při aktualizaci (Edit) záznamu je použita vyrovnávací paměť pro úpravy k nastavení pole datových členů sady záznamů na nové hodnoty. Po dokončení aktualizace je aktualizovaný záznam stále aktuální.

Při volání metody [AddNew](../../mfc/reference/crecordset-class.md#addnew) nebo [Edit](../../mfc/reference/crecordset-class.md#edit)je uložen aktuální záznam, takže jej lze později obnovit podle potřeby. Když zavoláte [Delete](../../mfc/reference/crecordset-class.md#delete), aktuální záznam není uložený, ale je označený jako odstraněný a musíte se posouvat na jiný záznam.

> [!NOTE]
>  Vyrovnávací paměť pro úpravy nehraje žádnou roli při odstraňování záznamu. Když odstraníte aktuální záznam, bude záznam označený jako odstraněný a sada záznamů bude "ne na záznamu", dokud se nepřejdete na jiný záznam.

##  <a name="dynasets-and-snapshots"></a><a name="_core_dynasets_and_snapshots"></a>Dynamické sady a snímky

[Dynamické sady](../../data/odbc/dynaset.md) aktualizují obsah záznamu při posouvání na záznam. [Snímky](../../data/odbc/snapshot.md) jsou statické reprezentace záznamů, takže obsah záznamu se neaktualizuje, pokud nebudete volat [dotaz](../../mfc/reference/crecordset-class.md#requery)znovu. Chcete-li použít všechny funkce dynamických sad, je nutné pracovat s ovladačem ODBC, který odpovídá správné úrovni podpory rozhraní ODBC API. Další informace naleznete v tématu [rozhraní ODBC](../../data/odbc/odbc-basics.md) a [dynamická sada](../../data/odbc/dynaset.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Jak fungují operace AddNew, Edit a Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)
