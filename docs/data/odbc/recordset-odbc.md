---
title: Sada záznamů (ODBC)
ms.date: 11/04/2016
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
ms.openlocfilehash: b201e152d83d3812253aa4803eebe715d726219d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034492"
---
# <a name="recordset-odbc"></a>Sada záznamů (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

A [CRecordset](../../mfc/reference/crecordset-class.md) objekt představuje sadu záznamů ze zdroje dat vybrané. Záznamy lze z:

- Tabulka.

- Dotaz.

- Uloženou proceduru, která přistupuje k jedné nebo více tabulek.

Příklad sady záznamů na základě tabulky je "všem zákazníkům,", který přistupuje k tabulky se zákazníky. Příklad dotazu je "všechny faktury Jan Novák." Příklad sady záznamů podle uložené procedury (říká se jim předdefinovaný dotaz) je "všechno nedobytné účtů" který volá uloženou proceduru v databázi back-end. Dva nebo více tabulek ze stejného zdroje dat, ale ne tabulek z různých zdrojů dat. můžete připojit na sadu záznamů.

> [!NOTE]
>  Informace o odvození třídy sady záznamů s průvodci, najdete v části [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) a [Podpora databáze, Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md).

> [!NOTE]
>  Některé ovladače rozhraní ODBC podporu zobrazení databáze. Zobrazení v tomto smyslu je dotaz původně vytvořené pomocí SQL `CREATE VIEW` příkazu. Průvodci aktuálně nepodporují zobrazení, ale je možné tato podpora kódu sami.

##  <a name="_core_recordset_capabilities"></a> Možnosti sady záznamů

Všechny objekty sady záznamů sdílet následující možnosti:

- Pokud zdroj dat není jen pro čtení, můžete určit, že sady záznamů být [aktualizovat](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [připojitelná](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), nebo jen pro čtení. Pokud sada záznamů je možné aktualizovat, můžete optimistického nebo pesimistického [uzamčení](../../data/odbc/recordset-locking-records-odbc.md) metody, k dispozici ovladač poskytuje vhodnou podporu uzamčení. Pokud zdroj dat je jen pro čtení, bude sada záznamů jen pro čtení.

- Můžete volat členské funkce pro [posuvníku](../../data/odbc/recordset-scrolling-odbc.md) si vybrané záznamy.

- Je možné [filtr](../../data/odbc/recordset-filtering-records-odbc.md) záznamy, abyste omezili záznamy, které jsou vybrány z jsou k dispozici.

- Je možné [řazení](../../data/odbc/recordset-sorting-records-odbc.md) záznamy ve vzestupném nebo sestupném pořadí podle jednoho nebo více sloupců.

- Je možné [parametrizovat](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) záznamů pro kvalifikaci záznamů výběr v době běhu.

##  <a name="_core_snapshots_and_dynasets"></a> Snímky a dynamické sady

Existují dva hlavní typy sad záznamů: [snímky](../../data/odbc/snapshot.md) a [dynamické sady](../../data/odbc/dynaset.md). Obě jsou podporovány třídou `CRecordset`. Každý sdílí běžné vlastnosti všech sad záznamů, ale také každý svým vlastním způsobem rozšiřuje běžné funkce. Snímky poskytovat statické zobrazení dat a jsou užitečné pro sestavy a jiné situace, ve kterých chcete zobrazit data jako existovala v určitou dobu. Dynamické sady jsou užitečné, pokud chcete, aby aktualizace provedené jinými uživateli mají být zobrazeny v sadě záznamů bez nutnosti requery nebo aktualizovat sadu záznamů. Snímky a dynamické sady může být možné aktualizovat nebo jen pro čtení. Přidání záznamů nebo volání odstraněné jinými uživateli [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery).

`CRecordset` také umožňuje dva typy sad záznamů: dynamické sady záznamů a pouze vpřed. Dynamické sady záznamů jsou podobné dynamické sady; ale dynamické promítne záznamy, které přidána nebo odstraněna bez volání `CRecordset::Requery`. Z tohoto důvodu dynamické sady záznamů jsou obecně nákladné s ohledem na doba zpracování na správce databáze a mnoho ovladačů ODBC je nepodporují. Naproti tomu poskytují dopředné sady záznamů nejefektivnější metoda přístupu k datům pro sady záznamů, které nevyžadují žádné aktualizace nebo zpětné posouvání. Můžete například použít záznamů s posouváním pouze vpřed pro migraci dat z jednoho zdroje dat do jiného, kde je potřeba jenom procházet data ve směru dopředu. Použití záznamů s posouváním pouze vpřed, proveďte oba následující kroky:

- Možnost předat `CRecordset::forwardOnly` jako *nOpenType* parametr [otevřít](../../mfc/reference/crecordset-class.md#open) členskou funkci.

- Zadejte `CRecordset::readOnly` v *dwOptions* parametr `Open`.

    > [!NOTE]
    >  Informace o požadavky ovladače ODBC pro dynamické sady podpory najdete v tématu [ODBC](../../data/odbc/odbc-basics.md). Seznam ovladačů ODBC zahrnuté v této verzi systému Visual C++ a informace o získání dalších ovladačů najdete v tématu [seznam ovladačů ODBC](../../data/odbc/odbc-driver-list.md).

##  <a name="_core_your_recordsets"></a> Vaše sady záznamů

Pro každou odlišné tabulky, zobrazení nebo uložené procedury, jež chcete získat přístup, obvykle definují třídy odvozené od `CRecordset`. (Výjimkou je připojení k databázi, ve které jedna sada záznamů představuje sloupci ze dvou nebo více tabulek). Při odvození třídy sady záznamů, povolíte mechanismus pole záznamu (RFX) systému exchange nebo hromadné mechanismem výměny (Bulk RFX) pole záznamu, které jsou podobné mechanismem výměny (DDX) dat dialogového okna. Přenos dat ze zdroje dat do sady záznamů; Zjednodušte RFX a Bulk RFX RFX navíc přenáší data ze sady záznamů ke zdroji dat. Další informace najdete v tématu [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md) a [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Objekt sady záznamů poskytuje přístup do všech vybraných záznamech. Při procházení několika vybraných záznamů pomocí `CRecordset` členské funkce, jako například `MoveNext` a `MovePrev`. Objekt sady záznamů ve stejnou dobu, představuje pouze jednu z vybraných záznamů aktuální záznam. Pole aktuální záznam můžete zkoumat deklarováním záznamů členské proměnné třídy, které odpovídají sloupcům tabulky nebo záznamy, které jsou výsledkem databázového dotazu. Informace o datových členů sady záznamů najdete v tématu [sada záznamů: Architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md).

Následující témata popisují podrobnosti o použití objektů sady záznamů. Témata jsou uvedeny v funkčních kategorií a přirozeném pořadí tak, aby povolovala sekvenční čtení.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Témata o mechanismu otevření, čtení a uzavírání sad záznamů

- [Recordset: Architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [Recordset: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [Recordset: Vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [Recordset: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [Recordset: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [Recordset: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [Recordset: Řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [Recordset: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Témata týkající se způsobu úpravy sad záznamů

- [Recordset: Přidání, aktualizace nebo odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [Recordset: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [Recordset: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>Témata o trochu více pokročilé techniky

- [Recordset: Provedení spojení (rozhraní ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [Recordset: Deklarování třídy pro předdefinovaný dotaz (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [Recordset: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [Recordset: (ODBC) hromadné načítání záznamů](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [Recordset: Práce s velkými datovými položkami (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [Recordset: Získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>Témata týkající se fungování sad záznamů

- [Recordset: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [Recordset: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Viz také:

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Transakce (ODBC)](../../data/odbc/transaction-odbc.md)