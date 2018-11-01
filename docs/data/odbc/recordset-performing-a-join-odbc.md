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
ms.openlocfilehash: 135992e7eebd56c985c24228370695f10ac6da3a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523935"
---
# <a name="recordset-performing-a-join-odbc"></a>Sada záznamů: Provedení spojení (rozhraní ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

## <a name="what-a-join-is"></a>Co je spojení

Operace spojení, přístup k datům běžném, vám umožní pracovat s daty z více než jedné tabulky pomocí objektu jedné sady záznamů. Spojování dvou nebo více tabulek vrací záznamů, který může obsahovat sloupce z tabulek spolu, ale zobrazí se jako jedné tabulky do vaší aplikace. Někdy spojení používá všechny sloupce všech tabulek, ale někdy SQL **vyberte** klauzule ve spojení se používá jenom některé sloupce z každé tabulky. Databázové třídy podporují jen pro čtení spojení, ale není možné aktualizovat spojení.

Vyberte záznamy obsahující sloupce z tabulky připojené k doméně, potřebujete následující položky:

- Tabulkový seznam obsahující názvy všech tabulek, které jsou připojené.

- Sloupec seznamu obsahujícího názvy všech zúčastněných sloupců. Sloupce se stejným názvem, ale z různých tabulek jsou kvalifikovány podle názvu tabulky.

- Filtr (SQL **kde** klauzule), který určuje sloupce, na kterých se propojují tabulky. Tento filtr má podobu "Table1.KeyCol = Table2.KeyCol" a spojení.

Stejným způsobem můžete spojit více než dvě tabulky srovnáním více párů sloupců, každý pár připojí pomocí klíčového slova SQL **a**.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Deklarace třídy předdefinovaného dotazu (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)<br/>
[Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)