---
title: 'Sada záznamů: Práce s velkými datovými položkami (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
ms.openlocfilehash: 872fa7229738314b86b6ae6c0d5dc5a5562b27f1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360603"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Sada záznamů: Práce s velkými datovými položkami (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC i třídy Knihovny MFC DAO.

> [!NOTE]
> Pokud používáte třídy Knihovny MFC DAO, spravujte velké datové položky s třídou [CByteArray](../../mfc/reference/cbytearray-class.md) spíše než třídou [CLongBinary](../../mfc/reference/clongbinary-class.md). Pokud používáte třídy Knihovny MFC ODBC `CLongBinary` s `CByteArray`hromadným načítáním řádků, použijte místo . Další informace o hromadném načítání řádků naleznete v tématu [Recordset: Fetching Records in Bulk (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Předpokládejme, že databáze může ukládat velké části dat, například rastrové obrázky (fotografie zaměstnanců, mapy, obrázky produktů, objekty OLE a tak dále). Tento druh dat se často označuje jako binární velký objekt (nebo objekt BLOB), protože:

- Každá hodnota pole je velká.

- Na rozdíl od čísel a jiných jednoduchých datových typů nemá žádnou předvídatelnou velikost.

- Data jsou z pohledu vašeho programu beztvará.

Toto téma vysvětluje, jakou podporu poskytují databázové třídy pro práci s těmito objekty.

## <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>Správa velkých objektů

Sady záznamů mají dva způsoby, jak vyřešit zvláštní potíže správy binárních velkých objektů. Můžete použít třídu [CByteArray](../../mfc/reference/cbytearray-class.md) nebo můžete použít třídu [CLongBinary](../../mfc/reference/clongbinary-class.md). Obecně platí, `CByteArray` že je upřednostňovaný způsob správy velkých binárních dat.

`CByteArray`vyžaduje větší `CLongBinary` režii než ale je schopnější, jak je popsáno v [CByteArray Class](#_core_the_cbytearray_class). `CLongBinary`je stručně popsán v [CLongBinary Class](#_core_the_clongbinary_class).

Podrobné informace o `CByteArray` použití pro práci s velkými datovými položkami naleznete [v technické poznámce 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>Třída CByteArray

`CByteArray`je jednou z tříd kolekce knihovny MFC. Objekt `CByteArray` ukládá dynamické pole bajtů – pole může v případě potřeby růst. Třída poskytuje rychlý přístup podle indexu, stejně jako u vestavěných polí C++. `CByteArray`objekty mohou být serializovány a vyřazovány pro diagnostické účely. Třída poskytuje členské funkce pro získání a nastavení určených bajtů, vkládání a připojování bajtů a odebrání jednoho bajtu nebo všech bajtů. Tato zařízení usnadňují analýzu binárních dat. Například pokud binární objekt je objekt OLE, bude pravděpodobně muset pracovat přes některé bajty záhlaví k dosažení skutečného objektu.

## <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>Použití pole CByteArray v sadách záznamů

Poskytnutím datového člena pole vašeho `CByteArray`souboru záznamů typu poskytujete pevnou základnu, ze které může [RFX](../../data/odbc/record-field-exchange-rfx.md) spravovat přenos takového objektu mezi sadou záznamů a zdrojem dat a jehož prostřednictvím můžete manipulovat s daty uvnitř objektu. RFX potřebuje konkrétní web pro načtená data a potřebujete způsob, jak získat přístup k podkladovým datům.

Podrobné informace o `CByteArray` použití pro práci s velkými datovými položkami naleznete [v technické poznámce 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

## <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>Třída CLongBinary

[CLongBinary](../../mfc/reference/clongbinary-class.md) objekt je jednoduché prostředí `HGLOBAL` kolem popisovače na blok úložiště přidělené na haldě. Při váže sloupec tabulky obsahující binární velký objekt, RFX `HGLOBAL` přiděluje popisovač, když potřebuje k přenosu `CLongBinary` dat do sady záznamů a ukládá popisovač v poli sady záznamů.

Na druhé straně `HGLOBAL` pomocí `m_hData`popisovače , pracovat s daty sám, pracovat na něm stejně jako u všech dat popisovače. Toto je místo, kde [CByteArray](../../mfc/reference/cbytearray-class.md) přidává schopnosti.

> [!CAUTION]
> CLongBinary objekty nelze použít jako parametry v volání funkce. Kromě toho jejich implementace, `::SQLGetData`která volá , nutně zpomaluje posouvání výkon pro posuvný snímek. To může také platit, `::SQLGetData` když pomocí volání sami načíst sloupce dynamického schématu.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)
