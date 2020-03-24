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
ms.openlocfilehash: 011191b99170b8a8338b5ca1a440a32404c4d793
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212820"
---
# <a name="recordset-odbc"></a>Sada záznamů (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Objekt [CRecordset](../../mfc/reference/crecordset-class.md) představuje sadu záznamů vybraných ze zdroje dat. Záznamy můžou být z těchto:

- Tabulka.

- Dotaz.

- Uložený postup, který přistupuje k jedné nebo více tabulkám.

Příkladem sady záznamů založených na tabulce jsou všichni zákazníci, kteří mají přístup k tabulce zákazníků. Příkladem dotazu jsou "všechny faktury pro Jana Smith". Příklad sady záznamů založené na uložené proceduře (někdy označované jako předdefinovaný dotaz) je "všechny účty problematické", což vyvolá uloženou proceduru v back-endové databázi. Sada záznamů může spojit dvě nebo více tabulek ze stejného zdroje dat, ale nikoli tabulky z různých zdrojů dat.

> [!NOTE]
>  Některé ovladače rozhraní ODBC podporují zobrazení databáze. Zobrazení v tomto smyslu je dotaz, který byl původně vytvořen příkazem SQL `CREATE VIEW`.

##  <a name="recordset-capabilities"></a><a name="_core_recordset_capabilities"></a>Možnosti sady záznamů

Všechny objekty sady záznamů sdílejí následující možnosti:

- Pokud zdroj dat není jen pro čtení, můžete určit, že vaše sada záznamů bude [aktualizovatelná](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [připojitelná](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)nebo jen pro čtení. Pokud je sada záznamů aktualizovatelná, můžete zvolit pesimistické nebo optimistické metody [zamykání](../../data/odbc/recordset-locking-records-odbc.md) . za předpokladu, že ovladač dodává příslušnou podporu uzamykání. Pokud je zdroj dat jen pro čtení, sada záznamů bude jen pro čtení.

- Můžete volat členské funkce pro [procházení](../../data/odbc/recordset-scrolling-odbc.md) vybraných záznamů.

- Záznamy můžete [filtrovat](../../data/odbc/recordset-filtering-records-odbc.md) , chcete-li omezit, které záznamy jsou vybrány z těch, které jsou k dispozici.

- Záznamy můžete [Seřadit](../../data/odbc/recordset-sorting-records-odbc.md) ve vzestupném nebo sestupném pořadí podle jednoho nebo více sloupců.

- Můžete [parametrizovat](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) sadu záznamů pro kvalifikaci výběru sady záznamů v době běhu.

##  <a name="snapshots-and-dynasets"></a><a name="_core_snapshots_and_dynasets"></a>Snímky a dynamické sady

Existují dva hlavní typy sad záznamů: [snímky](../../data/odbc/snapshot.md) a [dynamické sady](../../data/odbc/dynaset.md). Obě jsou podporovány třídou `CRecordset`. Každá sdílí společné charakteristiky všech sad záznamů, ale každá z nich také rozšiřuje společné funkce vlastním specializovaném způsobem. Snímky poskytují statické zobrazení dat a jsou užitečné v sestavách a dalších situacích, ve kterých chcete zobrazit data v určitou dobu. Dynamické sady jsou užitečné, pokud chcete, aby se aktualizace provedené ostatními uživateli zobrazovaly v sadě záznamů bez nutnosti opakovaného dotazování nebo aktualizace sady záznamů. Snímky a dynamické sady mohou být aktualizovatelné nebo jen pro čtení. Chcete-li odrážet záznamy přidané nebo odstraněné jinými uživateli, zavolejte metodu [CRecordset:: Requery](../../mfc/reference/crecordset-class.md#requery).

`CRecordset` také umožňuje dva další typy sad záznamů: dynamické sady záznamů a sady záznamů s přesměrováním. Dynamické sady záznamů jsou podobně jako dynamické sady; Nicméně dynamická sada záznamů odráží všechny záznamy přidané nebo odstraněné bez volání `CRecordset::Requery`. Z tohoto důvodu jsou dynamické sady záznamů všeobecně nákladné v souvislosti s časem zpracování v systému DBMS a řada ovladačů rozhraní ODBC je nepodporuje. Naproti tomu jenom sady záznamů s dopřednou sadou poskytují nejúčinnější metodu přístupu k datům pro sady záznamů, které nevyžadují aktualizace nebo zpětné posouvání. Například můžete použít pouze dopředné sady záznamů k migraci dat z jednoho zdroje dat do jiného, kde stačí procházet data směrem vpřed. Chcete-li použít pouze dopředné sady záznamů, je nutné provést následující akce:

- Předat možnost `CRecordset::forwardOnly` jako parametr *NOpenType* [otevřené](../../mfc/reference/crecordset-class.md#open) členské funkce.

- Zadejte `CRecordset::readOnly` v parametru *dwoptionss* `Open`.

    > [!NOTE]
    >  Informace o požadavcích na ovladač ODBC pro podporu dynamické sady najdete v tématu [ODBC](../../data/odbc/odbc-basics.md). Seznam ovladačů rozhraní ODBC, které jsou součástí této verze sady Visual C++ , a informace o získání dalších ovladačů naleznete v tématu [seznam ovladačů rozhraní ODBC](../../data/odbc/odbc-driver-list.md).

##  <a name="your-recordsets"></a><a name="_core_your_recordsets"></a>Vaše sady záznamů

Pro každou jednotlivou tabulku, zobrazení nebo uloženou proceduru, ke kterým chcete získat přístup, obvykle definujete třídu odvozenou z `CRecordset`. (Výjimkou je připojení k databázi, ve kterém jedna sada záznamů představuje sloupce ze dvou nebo více tabulek.) Při odvozování třídy sady záznamů povolíte mechanismus výměny pole záznamu (RFX) nebo hromadného mechanismu výměny pole záznamu (Bulk RFX), které jsou podobné mechanismu pro výměnu dat dialogových oken (DDX). RFX a hromadné RFX zjednodušují přenos dat ze zdroje dat do vaší sady záznamů. RFX navíc přenáší data ze sady záznamů do zdroje dat. Další informace naleznete v tématu [Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md) a [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Objekt sady záznamů vám umožní přístup ke všem vybraným záznamům. Procházejte několika vybranými záznamy pomocí `CRecordset` členských funkcí, jako je například `MoveNext` a `MovePrev`. Ve stejnou dobu objekt sady záznamů představuje pouze jeden z vybraných záznamů, aktuální záznam. Můžete kontrolovat pole aktuálního záznamu deklarováním členských proměnných třídy sady záznamů, které odpovídají sloupcům tabulky nebo záznamům, které jsou výsledkem databázového dotazu. Informace o datových členech sady záznamů naleznete v tématu [Sada záznamů: architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md).

V následujících tématech najdete vysvětlení podrobností o použití objektů sady záznamů. Témata jsou uvedená v tématu funkční kategorie a přirozené pořadí procházení umožňující sekvenční čtení.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Témata týkající se mechanismu otevírání, čtení a zavírání sad záznamů

- [Sada záznamů: Architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [Sada záznamů: Vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [Sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [Sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [Sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [Sada záznamů: Řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Témata týkající se úprav sady záznamů

- [Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>Témata o trochu pokročilejších technikách

- [Sada záznamů: Provedení spojení (rozhraní ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [Sada záznamů: Deklarace třídy předdefinovaného dotazu (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [Sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [Sada záznamů: Hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [Sada záznamů: Práce s velkými datovými položkami (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [Sada záznamů: Získávání součtů a jiných souhrnných výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>Témata týkající se fungování sady záznamů

- [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Využití MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Transakce (ODBC)](../../data/odbc/transaction-odbc.md)
