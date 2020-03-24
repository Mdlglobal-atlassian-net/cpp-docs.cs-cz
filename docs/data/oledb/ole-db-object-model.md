---
title: OLE DB – model objektů
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: 192195d02b034546e50b1cb860b1f11c47dc2b65
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210116"
---
# <a name="ole-db-object-model"></a>OLE DB – model objektů

Model OLE DB objektů je tvořen následujícími objekty nebo komponentami. První čtyři uvedené objekty nebo komponenty (zdroje dat, relace, příkazy a sady řádků) vám umožní připojit se ke zdroji dat a zobrazit ho. Zbytek počínaje přistupujícími objekty se vztahuje na práci s daty, když se zobrazí.

## <a name="data-sources"></a>Zdroje dat

Objekty zdroje dat umožňují připojit se ke zdroji dat, například k souboru nebo systému DBMS. Objekt zdroje dat vytvoří a spravuje připojení a obsahuje informace o oprávněních a ověřováních (například přihlašovací jméno a heslo). Objekt zdroje dat může vytvořit jednu nebo více relací.

## <a name="sessions"></a>Relace

Relace spravuje konkrétní interakci se zdrojem dat pro dotazování a načítání dat. Každá relace je jediná transakce. Transakce je nedělitelná pracovní jednotka definovaná testem kyseliny. Definici kyseliny najdete v tématu [transakce](#vcconoledbcomponents_transactions).

Relace jsou důležité úlohy, jako je například otevření sad řádků a vrácení objektu zdroje dat, který jej vytvořil. Relace mohou také vracet metadata nebo informace o samotném zdroji dat (například informace o tabulce).

Relace může vytvořit jeden nebo více příkazů.

## <a name="commands"></a>Příkazy

Příkazy spouštějí textový příkaz, jako je například příkaz jazyka SQL. Pokud příkaz text určuje sadu řádků, například příkaz SQL **Select** , vytvoří příkaz sadu řádků.

Příkaz je jednoduše kontejner pro textový příkaz, což je řetězec (například příkaz jazyka SQL) předaný příjemcem do objektu zdroje dat, který může být spuštěný v podkladovém úložišti dat poskytovatele. Textový příkaz je typicky příkaz SQL **Select** (v takovém případě, protože příkaz SQL **Select** určuje sadu řádků, příkaz automaticky vytvoří sadu řádků).

## <a name="rowsets"></a>Sady řádků

Sady řádků zobrazují data ve formátu tabulky. Index je zvláštní případ sady řádků. Můžete vytvořit sady řádků z relace nebo příkazu.

### <a name="schema-rowsets"></a>Sady řádků schématu

Schémata mají metadata (strukturální informace) o databázi. Sady řádků schématu jsou sady řádků, které obsahují informace o schématu. Někteří poskytovatelé OLE DB pro DBMS podporují objekty sady řádků schématu. Další informace o sadách řádků schématu naleznete v tématu [Získávání metadat pomocí sad řádků schématu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) a [tříd sady řádků schématu a tříd typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Zobrazit objekty

Objekt zobrazení definuje podmnožinu řádků a sloupců ze sady řádků. Nemá žádná vlastní data. Zobrazení objektů nemůže kombinovat data z více sad řádků.

## <a name="accessors"></a>Přístupové objekty

Pouze OLE DB používá koncept přístupových objektů. Přístupový objekt popisuje, jak jsou data uložená v příjemci. Obsahuje sadu vazeb (nazývaných mapu sloupců) mezi poli sady řádků (sloupce) a datovými členy, které deklarujete v příjemci.

##  <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a>Převody

Transakční objekty jsou používány při potvrzení nebo přerušení vnořených transakcí na jiné, než na nejnižší úrovni. Transakce je nedělitelná pracovní jednotka definovaná testem kyseliny. KYSELost představuje:

- Nedělitelnost nemůže být rozdělená na menší pracovní jednotky.

- Souběžnosti, může dojít v jednom okamžiku k více transakcím.

- Izolace, jedna transakce má omezené znalosti o změnách provedených jiným

- Odolnost, transakce provádí trvalé změny

## <a name="enumerators"></a>Enumerátory

Enumerátory hledají dostupné zdroje dat a další enumerátory. Příjemci, kteří nejsou přizpůsobené pro konkrétní zdroj dat, používají enumerátory k vyhledání zdroje dat, který chcete použít.

Kořenový enumerátor, který je dodán v sadě Microsoft Data Access SDK, projde registrem, ve kterém hledají zdroje dat a další enumerátory. Jiné enumerátory přecházejí do registru nebo hledají způsobem specifickým pro konkrétního poskytovatele.

## <a name="errors"></a>Chyby

Jakékoli rozhraní u libovolného objektu OLE DB může generovat chyby. Chyby obsahují další informace o chybě, včetně volitelného vlastního objektu Error. Tyto informace jsou uloženy v HRESULT.

## <a name="notifications"></a>Oznámení

Oznámení používají skupiny spolupracujících příjemců, které sdílejí sadu řádků (kde sdílení znamená, že se zákazníci považují za fungující v rámci stejné transakce). Oznámení umožňují spolupráci uživatelů sdílejících sadu řádků, aby byli informováni o akcích sady řádků prováděných jejich partnery.

## <a name="see-also"></a>Viz také

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)
