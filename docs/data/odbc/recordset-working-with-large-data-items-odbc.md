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
ms.openlocfilehash: b84365461ce6d45fccdf1922974feff5af93f99f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212755"
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Sada záznamů: Práce s velkými datovými položkami (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC i třídy DAO knihovny MFC.

> [!NOTE]
>  Pokud používáte třídy knihovny MFC DAO, spravujte své velké datové položky pomocí třídy [CByteArray](../../mfc/reference/cbytearray-class.md) spíše než třídy [CLongBinary –](../../mfc/reference/clongbinary-class.md). Pokud používáte třídy knihovny MFC rozhraní ODBC s hromadnou načítající řádky, použijte `CLongBinary` místo `CByteArray`. Další informace o hromadném načítání řádků naleznete v tématu [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Předpokládejme, že vaše databáze může ukládat velké části dat, jako jsou rastrové obrázky (fotografie zaměstnanců, mapy, obrázky produktů, objekty OLE atd.). Tento druh dat se často označuje jako binární Large Object (nebo objekt BLOB), protože:

- Hodnota každého pole je velká.

- Na rozdíl od čísel a jiných jednoduchých datových typů nemá žádná předvídatelná velikost.

- Data se formless z perspektivy vašeho programu.

Toto téma vysvětluje, co podporují databázové třídy pro práci s takovými objekty.

##  <a name="managing-large-objects"></a><a name="_core_managing_large_objects"></a>Správa velkých objektů

Sady záznamů mají dva způsoby řešení speciálních potíží se správou binárních velkých objektů. Můžete použít třídu [CByteArray](../../mfc/reference/cbytearray-class.md) nebo můžete použít třídu [CLongBinary –](../../mfc/reference/clongbinary-class.md). Obecně je `CByteArray` upřednostňovaným způsobem správy velkých binárních dat.

`CByteArray` vyžaduje větší režii než `CLongBinary`, ale je více možností, jak je popsáno ve [třídě CByteArray](#_core_the_cbytearray_class). `CLongBinary` je stručně popsáno ve [třídě CLongBinary –](#_core_the_clongbinary_class).

Podrobné informace o použití `CByteArray` pro práci s velkými datovými položkami naleznete v části [Technická poznámka 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="cbytearray-class"></a><a name="_core_the_cbytearray_class"></a>CByteArray – třída

`CByteArray` je jedna z tříd kolekce knihovny MFC. Objekt `CByteArray` ukládá dynamické pole bajtů – pole může v případě potřeby růst. Třída poskytuje rychlý přístup podle indexu, stejně jako Vestavěná C++ pole. pro účely diagnostiky je možné serializovat a stanovit `CByteArray` objektů. Třída poskytuje členské funkce pro získání a nastavení zadaných bajtů, vkládání a přidávání bajtů a odebírání jednoho bajtu nebo všech bajtů. Tato zařízení usnadňují analýzu binárních dat. Například pokud binární objekt je objekt OLE, může být nutné pracovat s některými bajty hlaviček pro dosažení skutečného objektu.

##  <a name="using-cbytearray-in-recordsets"></a><a name="_core_using_cbytearray_in_recordsets"></a>Použití CByteArray v sadách záznamů

Poskytnutím datového člena pole vaší sady záznamů typ `CByteArray`, zadáte pevnou základ, ze kterého může [RFX](../../data/odbc/record-field-exchange-rfx.md) spravovat přenos takového objektu mezi vaší sadou záznamů a zdrojem dat a pomocí kterého lze manipulovat s daty uvnitř objektu. RFX potřebuje konkrétní lokalitu pro načtená data a potřebujete způsob, jak získat přístup k podkladovým datům.

Podrobné informace o použití `CByteArray` pro práci s velkými datovými položkami naleznete v části [Technická poznámka 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).

##  <a name="clongbinary-class"></a><a name="_core_the_clongbinary_class"></a>CLongBinary – – třída

Objekt [CLongBinary –](../../mfc/reference/clongbinary-class.md) je jednoduché prostředí kolem `HGLOBAL`ho popisovače do bloku úložiště přiděleného na haldě. Při vázání sloupce tabulky, který obsahuje binární rozsáhlý objekt, RFX přiděluje popisovač `HGLOBAL`, pokud potřebuje přenést data do sady záznamů a uložit popisovač do pole `CLongBinary` sady záznamů.

V takovém případě použijete `HGLOBAL` popisovač `m_hData`, abyste mohli pracovat s daty, která s nimi pracují, stejně jako při jakémkoli popisovači dat. Zde je místo, kde [CByteArray](../../mfc/reference/cbytearray-class.md) přidává funkce.

> [!CAUTION]
>  Objekty CLongBinary – nejde používat jako parametry volání funkcí. Kromě toho jejich implementace, která volá `::SQLGetData`, nutně zpomaluje posouvání výkonu u rolovacího snímku. To může mít také hodnotu true, pokud použijete `::SQLGetData` voláním pro načtení sloupců dynamického schématu.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Získávání součtů a jiných souhrnných výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)<br/>
[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)
