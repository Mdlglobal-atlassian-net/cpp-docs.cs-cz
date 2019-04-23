---
title: 'Recordset: Práce s velkými datovými položkami (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 3ba8d4af5b0781c425dd3b1223e2208b279f055e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033041"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Recordset: Práce s velkými datovými položkami (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC a tříd DAO knihovny MFC.

> [!NOTE]
>  Pokud používáte tříd DAO knihovny MFC, spravovat vaše velkými datovými položkami s třídou [CByteArray](../../mfc/reference/cbytearray-class.md) namísto třídy [CLongBinary](../../mfc/reference/clongbinary-class.md). Pokud používáte třídy knihovny MFC rozhraní ODBC s hromadné načítání řádků, použijte `CLongBinary` spíše než `CByteArray`. Další informace o hromadném načítání řádků naleznete v tématu [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Předpokládejme, že databáze můžete ukládat velké časti dat, jako je například rastrové obrázky (zaměstnance fotografie, map, obrázků produktů, objekty OLE a tak dále). Tento typ dat je často označovány jako binárních rozsáhlých objektů (nebo objektů BLOB), protože:

- Každá hodnota pole je velká.

- Na rozdíl od jiných jednoduché datové typy a čísla nemá žádné předvídatelné velikost.

- Data jsou formless z pohledu aplikace.

Toto téma vysvětluje, jaké podporu poskytují databázových tříd pro práci s tyto objekty.

##  <a name="_core_managing_large_objects"></a> Správa velkých objektů

Sady záznamů mají dva způsoby, jak vyřešit speciální ztížit správu binární rozsáhlé objekty. Můžete použít třídu [CByteArray](../../mfc/reference/cbytearray-class.md) nebo můžete použít třídu [CLongBinary](../../mfc/reference/clongbinary-class.md). Obecně platí `CByteArray` je upřednostňovaný způsob, jak spravovat velké binární data.

`CByteArray` vyžaduje další režii než `CLongBinary` , ale je více možností, jak je popsáno v [CByteArray – třída](#_core_the_cbytearray_class). `CLongBinary` je popsán v krátce [CLongBinary – třída](#_core_the_clongbinary_class).

Podrobné informace o používání `CByteArray` práci s velkými datovými položkami, naleznete v tématu [Technická poznámka 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="_core_the_cbytearray_class"></a> CByteArray – třída

`CByteArray` je jedním z třídy kolekcí MFC. A `CByteArray` ukládá dynamická pole bajtů – pole můžou růst podle potřeby. Třída poskytující rychlý přístup podle indexu, stejně jako u předdefinované pole jazyka C++. `CByteArray` objekty lze serializovat a zálohované k diagnostickým účelům. Třída poskytuje členské funkce pro získání a nastavení zadaných bajtů, vkládání a přidávání bajtů a odebrání jednoho bajtu nebo všechny bajty. Tato zařízení provést, analýze binárních dat, jednodušší. Pokud binární objekt je objekt OLE, budete muset projít některé hlavičky bajtů na objekt, který vede.

##  <a name="_core_using_cbytearray_in_recordsets"></a> Použití CByteArray v sadách záznamů

Tím, že pole datový člen třídy sady záznamů typu `CByteArray`, zadejte pevnou základ, ze kterého [RFX](../../data/odbc/record-field-exchange-rfx.md) můžete spravovat přenos takového objektu mezi sady záznamů a zdrojem dat a přes který můžete upravit data v objektu. RFX potřebuje určité lokalitě pro načtená data a potřebujete způsob, jak přistupovat k podkladová data.

Podrobné informace o používání `CByteArray` práci s velkými datovými položkami, naleznete v tématu [Technická poznámka 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="_core_the_clongbinary_class"></a> CLongBinary – třída

A [CLongBinary](../../mfc/reference/clongbinary-class.md) objekt je jednoduchá prostředí kolem `HGLOBAL` popisovače blok úložiště přidělený k haldě. Když se váže na sloupec tabulky obsahující binární rozsáhlý objekt, přidělí RFX `HGLOBAL` řešit při přenosu dat do sady záznamů je potřeba a uloží popisovač v `CLongBinary` pole sady záznamů.

Pak použijete `HGLOBAL` zpracování, `m_hData`, pracovat s daty, provozující, stejně jako na žádném data. Tady [CByteArray](../../mfc/reference/cbytearray-class.md) přidává funkce.

> [!CAUTION]
>  CLongBinary – objekty nelze použít jako parametry volání funkce. Kromě toho, jejich implementaci, která volá `::SQLGetData`, nemusí být zpomaluje výkonu posunování posuvný snímku. To může také být pravdivá, když použijete `::SQLGetData` volání sami načíst dynamické schéma sloupce.

## <a name="see-also"></a>Viz také:

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)