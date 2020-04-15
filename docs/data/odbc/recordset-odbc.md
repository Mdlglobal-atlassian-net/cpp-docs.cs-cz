---
title: Sada záznamů (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, snapshots
- recordsets, creating
- dynamic recordsets
- forward-only recordsets
- recordsets, dynasets
- ODBC recordsets, CRecordset objects
- ODBC recordsets
- recordsets, about recordsets
- snapshots, ODBC recordsets
- dynasets
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
ms.openlocfilehash: b7a55621f4875b24cc33a0fd49a5b8b4c88b34cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368639"
---
# <a name="recordset-odbc"></a>Sada záznamů (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Objekt [CRecordset](../../mfc/reference/crecordset-class.md) představuje sadu záznamů vybraných ze zdroje dat. Záznamy mohou podoby:

- Stůl.

- Dotaz.

- Uložená procedura, která přistupuje k jedné nebo více tabulkám.

Příkladem sady záznamů založených na tabulce je "všichni zákazníci", která přistupuje k tabulce Zákazník. Příkladem dotazu je "všechny faktury pro Joe Smith." Příkladem sady záznamů založených na uložené proceduře (někdy nazývané předdefinovaný dotaz) je "všechny delikventní účty", která vyvolá uloženou proceduru v databázi back-end. Sada záznamů může spojit dvě nebo více tabulek ze stejného zdroje dat, ale ne tabulky z různých zdrojů dat.

> [!NOTE]
> Některé ovladače ROZHRANÍ ODBC podporují zobrazení databáze. Zobrazení v tomto smyslu je dotaz původně `CREATE VIEW` vytvořený s příkazem SQL.

## <a name="recordset-capabilities"></a><a name="_core_recordset_capabilities"></a>Možnosti sady záznamů

Všechny objekty sady záznamů sdílejí následující možnosti:

- Pokud zdroj dat není jen pro čtení, můžete určit, aby byla sada záznamů [aktualizovatelná](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [připojitelná](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)nebo jen pro čtení. Pokud je sada záznamů aktualizovatelná, můžete zvolit pesimistické nebo optimistické metody [uzamčení](../../data/odbc/recordset-locking-records-odbc.md) za předpokladu, že ovladač poskytuje odpovídající podporu uzamčení. Pokud je zdroj dat jen pro čtení, bude sada záznamů jen pro čtení.

- Můžete volat členské funkce pro [procházení](../../data/odbc/recordset-scrolling-odbc.md) vybraných záznamů.

- Záznamy můžete [filtrovat](../../data/odbc/recordset-filtering-records-odbc.md) a omezit tak, které záznamy jsou vybrány z těch, které jsou k dispozici.

- Záznamy můžete [seřadit](../../data/odbc/recordset-sorting-records-odbc.md) vzestupně nebo sestupně na základě jednoho nebo více sloupců.

- Můžete [parametrizovat](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) sadu záznamů kvalifikovat výběr sady záznamů za běhu.

## <a name="snapshots-and-dynasets"></a><a name="_core_snapshots_and_dynasets"></a>Snímky a dynasady

Existují dva hlavní typy sad záznamů: [snímky](../../data/odbc/snapshot.md) a [dynasady](../../data/odbc/dynaset.md). Oba jsou podporovány třídou `CRecordset`. Každý sdílí společné charakteristiky všech sad záznamů, ale každý také rozšiřuje společné funkce svým vlastním specializovaným způsobem. Snímky poskytují statické zobrazení dat a jsou užitečné pro sestavy a další situace, ve kterých chcete zobrazit data tak, jak existovala v určitém čase. Sady dynasadí jsou užitečné, pokud chcete, aby aktualizace provedené jinými uživateli byly viditelné v sadě záznamů, aniž by bylo nutné znovu zařazovat nebo aktualizovat sadu záznamů. Snímky a dynamické sady mohou být aktualizovatelné nebo jen pro čtení. Chcete-li reflektovat záznamy přidané nebo odstraněné jinými uživateli, zavolejte [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery).

`CRecordset`Umožňuje také dva další typy sad záznamů: dynamické sady záznamů a sady záznamů pouze pro předávání. Dynamické sady záznamů jsou podobné dynamickým sadám; Dynamické sady záznamů však odrážejí všechny `CRecordset::Requery`záznamy přidané nebo odstraněné bez volání . Z tohoto důvodu dynamické sady záznamů jsou obecně nákladné s ohledem na dobu zpracování v systému DBMS a mnoho ovladačů ODBC je nepodporuje. Naproti tomu sady záznamů pouze pro předávání poskytují nejúčinnější metodu přístupu k datům pro sady záznamů, které nevyžadují aktualizace nebo zpětné posouvání. Můžete například použít sadu záznamů pouze pro předávání k migraci dat z jednoho zdroje dat do jiného, kde stačí pouze přesunout data ve směru dopředu. Chcete-li použít sadu záznamů pouze pro předávání, musíte provést obě následující akce:

- Předejte `CRecordset::forwardOnly` tuto možnost jako parametr *nOpenType* členské funkce [Otevřít.](../../mfc/reference/crecordset-class.md#open)

- Zadejte `CRecordset::readOnly` v parametru `Open` *dwOptions* aplikace .

    > [!NOTE]
    >  Informace o požadavcích ovladače ODBC na podporu dynaset naleznete v tématu [ODBC](../../data/odbc/odbc-basics.md). Seznam ovladačů ODBC zahrnutých v této verzi jazyka Visual C++ a informace o získání dalších ovladačů naleznete v [tématu Seznam ovladačů ODBC](../../data/odbc/odbc-driver-list.md).

## <a name="your-recordsets"></a><a name="_core_your_recordsets"></a>Vaše sady rekordů

Pro každou odlišnou tabulku, zobrazení nebo uloženou proceduru, ke které `CRecordset`chcete získat přístup, obvykle definujete třídu odvozenou z aplikace . (Výjimkou je spojení databáze, ve kterém jedna sada záznamů představuje sloupce ze dvou nebo více tabulek.) Při odvození třídy sady záznamů povolíte mechanismus výměny pole záznamu (RFX) nebo mechanismus hromadné výměny pole záznamu (Bulk RFX), které jsou podobné mechanismu výměny dat dialogu (DDX). RFX a Bulk RFX zjednodušují přenos dat ze zdroje dat do vaší sady záznamů; RFX navíc přenáší data ze sady záznamů do zdroje dat. Další informace naleznete v [tématech Výměna polí záznamů (RFX)](../../data/odbc/record-field-exchange-rfx.md) a [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Objekt sady záznamů umožňuje přístup ke všem vybraným záznamům. Procházení více vybraných záznamů `CRecordset` pomocí členských funkcí, například `MoveNext` a `MovePrev`. Současně objekt sady záznamů představuje pouze jeden z vybraných záznamů, aktuální záznam. Pole aktuálního záznamu můžete prozkoumat deklarováním proměnných členů sady záznamů, které odpovídají sloupcům tabulky nebo záznamů, které jsou výsledkem databázového dotazu. Informace o datových členech sady záznamů naleznete v [tématu Recordset: Architecture (ODBC).](../../data/odbc/recordset-architecture-odbc.md)

Následující témata vysvětlují podrobnosti použití objektů sady záznamů. Témata jsou uvedena ve funkčních kategoriích a přirozené pořadí procházení, které umožňuje sekvenční čtení.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Témata o mechanice otevírání, čtení a zavírání nahrávek

- [Sada záznamů: Architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [Sada záznamů: Vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [Sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [Sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [Sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [Sada záznamů: Řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Témata o mechanice úprav sad záznamů

- [Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>Témata o poněkud pokročilejších technikách

- [Sada záznamů: Provedení spojení (rozhraní ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [Sada záznamů: Deklarace třídy předdefinovaného dotazu (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [Sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [Sada záznamů: Hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [Sada záznamů: Práce s velkými datovými položkami (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>Témata o tom, jak sady záznamů fungují

- [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Viz také

[Připojení k otevřené databázi (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Spotřebovávat rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Transakce (ODBC)](../../data/odbc/transaction-odbc.md)
