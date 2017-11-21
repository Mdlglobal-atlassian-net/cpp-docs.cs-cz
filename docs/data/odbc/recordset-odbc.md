---
title: "Sada záznamů (ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 668cd4b2f27c2cde18528c0eb2d4d661160c4e4e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-odbc"></a>Sada záznamů (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 A [CRecordset](../../mfc/reference/crecordset-class.md) objekt představuje sadu záznamy ze zdroje dat vybraná. Záznamy lze z:  
  
-   Tabulka.  
  
-   Dotaz.  
  
-   Uložené procedury, která přistupuje k jedné nebo více tabulek.  
  
 Příklad sady záznamů na základě v tabulce je "všem zákazníkům,", který přistupuje k tabulce zákazníka. Příklad dotazu je "všechny faktury Jan Smith." Příkladem záznamů založené na uložené procedury (někdy nazývané předdefinovaný dotaz) je "všechny nesplacené účty," který vyvolá uloženou proceduru v databázi back-end. Sady záznamů se můžete zapojit do dvou nebo více tabulek z jednoho zdroje dat, ale není tabulky z různých zdrojů.  
  
> [!NOTE]
>  Informace o odvození třídy sady záznamů s průvodců najdete v tématu [přidání příjemce rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) a [Podpora databáze, Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md).  
  
> [!NOTE]
>  Některé ovladače ODBC podporují zobrazení databáze. Zobrazení v tomto smyslu je dotaz původně vytvořen pomocí SQL `CREATE VIEW` příkaz. Průvodci aktuálně nepodporují zobrazení, ale je možné code tato podpora sami.  
  
##  <a name="_core_recordset_capabilities"></a>Funkce sady záznamů  
 Všechny objekty sady záznamů sdílet následující možnosti:  
  
-   Pokud zdroj dat není jen pro čtení, můžete určit, aby sady záznamů [aktualizovat](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [připojitelná](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), nebo jen pro čtení. Pokud je sada záznamů aktualizovatelná, můžete vybrat pesimistické nebo optimistické [uzamčení](../../data/odbc/recordset-locking-records-odbc.md) způsoby, které poskytuje ovladač poskytuje vhodnou podporu uzamčení. Pokud je zdroj dat jen pro čtení, bude sada záznamů jen pro čtení.  
  
-   Můžete volat členské funkce [scroll](../../data/odbc/recordset-scrolling-odbc.md) prostřednictvím vybrané záznamy.  
  
-   Můžete [filtru](../../data/odbc/recordset-filtering-records-odbc.md) záznamy, abyste omezili záznamy, které jsou vybrány z jsou k dispozici.  
  
-   Můžete [řazení](../../data/odbc/recordset-sorting-records-odbc.md) záznamy ve vzestupném nebo sestupném pořadí podle jednoho nebo více sloupců.  
  
-   Můžete [Parametrizace](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) sadu záznamů pro získání výběru sady záznamů v době běhu.  
  
##  <a name="_core_snapshots_and_dynasets"></a>Snímky a dynamické sady  
 Existují dva hlavní typy sad záznamů: [snímky](../../data/odbc/snapshot.md) a [dynamické sady](../../data/odbc/dynaset.md). Obě jsou podporovány třídou `CRecordset`. Každý sdílí stejné charakteristiky všech sad záznamů, ale každý taky ji rozšiřuje na běžné funkce v svým vlastním způsobem. Snímky poskytují statické zobrazení dat a jsou užitečné pro sestavy a jiné situace, ve kterých chcete zobrazit data tak, jak byly v určitou dobu. Dynamické sady jsou užitečné, pokud chcete aktualizace provedené jinými uživateli mají být zobrazeny v sadě záznamů bez nutnosti znovu spustit dotaz nebo aktualizovat sadu záznamů. Snímky a dynamické sady může být v aktualizovatelné nebo jen pro čtení. Odrážel záznamy přidání nebo odstranění jiných uživatelů, zavolejte [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery).  
  
 `CRecordset`také umožňuje dva typy sad záznamů: dynamické sady záznamů a dopředné sady záznamů. Dynamické sady záznamů jsou podobné dynamické sady; ale dynamické sady záznamů odrážel všechny záznamy při přidání nebo odstranění bez volání `CRecordset::Requery`. Z tohoto důvodu dynamické sady záznamů jsou obvykle levnější s ohledem na doba zpracování na databázového systému a mnoho ovladačů ODBC je nepodporují. Naproti tomu dopředné sady záznamů poskytují nejúčinnější metodu přístupu k datům pro sady záznamů, které nevyžadují aktualizace nebo zpětné posouvání. Můžete například použít dopředná sada záznamů pro migraci dat z jednoho zdroje dat na jiný, kde je potřeba jenom procházet data směrem vpřed. Chcete-li použít dopředné záznamů, musíte udělat obě z následujících akcí:  
  
-   Předat možnosti **CRecordset::forwardOnly** jako `nOpenType` parametr [otevřete](../../mfc/reference/crecordset-class.md#open) – členská funkce.  
  
-   Zadejte **CRecordset::readOnly** v `dwOptions` parametr **otevřete**.  
  
    > [!NOTE]
    >  Informace o požadavky ovladače ODBC pro dynamické sady podpory najdete v tématu [ODBC](../../data/odbc/odbc-basics.md). Seznam ovladačů ODBC zahrnuté v této verzi systému Visual C++ a informace o získání dalších ovladačů najdete v části [seznam ovladačů ODBC](../../data/odbc/odbc-driver-list.md).  
  
##  <a name="_core_your_recordsets"></a>Vaše sady záznamů  
 Pro každý odlišné tabulka, zobrazení nebo uložené procedury, jež chcete získat přístup, je obvykle definovat třídy odvozené od `CRecordset`. (Výjimkou jsou připojení k databázi, ve které jedna sada záznamů představuje sloupce ze dvou nebo více tabulek.) Pokud odvodíte třídu sady záznamů, povolíte mechanismus pole záznamu (exchange – RFX) nebo mechanismus pole záznamu (Bulk RFX) systému exchange, podobné mechanismus dialogové okno dat systému exchange (DDX). RFX a Bulk RFX zjednodušují přenos dat ze zdroje dat do sady záznamů; RFX navíc ke zdroji dat přenáší data ze sady záznamů. Další informace najdete v tématu [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md) a [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Objekt sady záznamů umožňuje přístup do všech vybraných záznamech. Můžete procházet více vybraných záznamů pomocí `CRecordset` členské funkce, jako například `MoveNext` a `MovePrev`. Objekt sady záznamů ve stejnou dobu, představuje pouze jeden z vybraných záznamů na aktuální záznam. Deklarováním sada záznamů třída členské proměnné, které odpovídají na sloupce tabulky nebo záznamy, které jsou výsledkem dotazu databáze můžete zkontrolovat pole na aktuální záznam. Informace o datových členů sady záznamů najdete v tématu [sada záznamů: architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md).  
  
 Následující témata vysvětlují, podrobnosti o používání objektů sady záznamů. Témata jsou uvedeny v funkčních kategorií a v přirozeném pořadí tak, aby povolovala sekvenční čtení.  
  
### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Témata o způsobech otevření, čtení a uzavírání sad záznamů  
  
-   [Sada záznamů: Architektura (ODBC)](../../data/odbc/recordset-architecture-odbc.md)  
  
-   [Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)  
  
-   [Sada záznamů: Vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)  
  
-   [Sada záznamů: Posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)  
  
-   [Sada záznamů: Záložky a absolutní umístění (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)  
  
-   [Sada záznamů: Filtrování záznamů (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)  
  
-   [Sada záznamů: Řazení záznamů (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)  
  
-   [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)  
  
### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Témata o způsobu úpravy sady záznamů  
  
-   [Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)  
  
-   [Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)  
  
-   [Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)  
  
### <a name="topics-about-somewhat-more-advanced-techniques"></a>Témata o trochu pokročilejší techniky  
  
-   [Sada záznamů: Provedení spojení (rozhraní ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)  
  
-   [Sada záznamů: Deklarování třídy pro předdefinovaný dotaz (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)  
  
-   [Sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)  
  
-   [Sada záznamů: Hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)  
  
-   [Sada záznamů: Práce s velkými datovými položkami (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)  
  
-   [Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)  
  
### <a name="topics-about-how-recordsets-work"></a>Témata o fungování sady záznamů  
  
-   [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)  
  
-   [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Transakce (ODBC)](../../data/odbc/transaction-odbc.md)