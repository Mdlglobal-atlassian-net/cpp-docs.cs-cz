---
title: 'Sada záznamů: Provedení spojení (rozhraní ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- joins [C++], in recordsets
- data binding [C++], recordset columns
- recordsets [C++], binding data
- data binding [C++], columns in recordsets
- filters [C++], join conditions for recordsets
- ODBC recordsets [C++], joins
- recordsets [C++], joining tables
ms.assetid: ca720900-a156-4780-bf01-4293633bea64
ms.openlocfilehash: 7e8d42f2b96911cd57aca7c132b53ed7c10162be
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212794"
---
# <a name="recordset-performing-a-join-odbc"></a>Sada záznamů: Provedení spojení (rozhraní ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

## <a name="what-a-join-is"></a>Co je spojení

Operace join (běžný úkol pro přístup k datům) umožňuje pracovat s daty z více než jedné tabulky pomocí jediného objektu sady záznamů. Propojení dvou nebo více tabulek poskytne sadu záznamů, která může obsahovat sloupce z každé tabulky, ale zobrazí se jako jedna tabulka vaší aplikace. V některých případech se spojení používá všechny sloupce ze všech tabulek, někdy ale klauzule **Select** SQL v JOIN používá pouze některé sloupce z každé tabulky. Třídy databáze podporují spojení jen pro čtení, ale nelze aktualizovat spojení.

Chcete-li vybrat záznamy obsahující sloupce z připojených tabulek, potřebujete následující položky:

- Seznam tabulek obsahující názvy všech připojených tabulek.

- Seznam sloupců obsahující názvy všech zúčastněných sloupců Sloupce se stejným názvem, ale z různých tabulek, jsou kvalifikovány názvem tabulky.

- Filtr (klauzule **WHERE** jazyka SQL), který určuje sloupce, na které jsou tabulky připojeny. Tento filtr má podobu "Tabulka1. KeyCol = Tabulka2. KeyCol" a ve skutečnosti provádí spojení.

Stejný postup můžete spojit s více než dvěma tabulkami, a to tak, že porovnáte více párů sloupců, každý pár spojený pomocí klíčového slova SQL **a**.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Deklarace třídy předdefinovaného dotazu (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)
