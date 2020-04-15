---
title: OLE DB – model objektů
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: b37205eb91317c602010a4b568057845b2345ef0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369801"
---
# <a name="ole-db-object-model"></a>OLE DB – model objektů

Objektový model TECHNOLOGIE OLE DB je tvořen následujícími objekty nebo součástmi. První čtyři uvedené objekty nebo součásti (zdroje dat, relace, příkazy a sady řádků) umožňují připojit se ke zdroji dat a zobrazit jej. Zbytek, počínaje přístupovými mikinami, se vztahuje k práci s daty, když se zobrazí.

## <a name="data-sources"></a>Zdroje dat

Objekty zdroje dat umožňují připojení ke zdroji dat, například k souboru nebo systému DBMS. Objekt zdroje dat vytvoří a spravuje připojení a obsahuje oprávnění a informace o ověřování (například přihlašovací jméno a heslo). Objekt zdroje dat může vytvořit jednu nebo více relací.

## <a name="sessions"></a>Relace

Relace spravuje konkrétní interakci se zdrojem dat pro dotazování a načítání dat. Každá relace je jedna transakce. Transakce je nedělitelná pracovní jednotka definovaná acid testem. Definici ACID naleznete v tématu [Transactions](#vcconoledbcomponents_transactions).

Relace provést důležité úkoly, jako je například otevření sad řádků a vrácení objektu zdroje dat, který jej vytvořil. Relace mohou také vrátit metadata nebo informace o samotném zdroji dat (například informace o tabulce).

Relace může vytvořit jeden nebo více příkazů.

## <a name="commands"></a>Příkazy

Příkazy spouštějí textový příkaz, například příkaz SQL. Pokud textový příkaz určuje sadu řádků, například příkaz SQL **SELECT,** příkaz vytvoří sadu řádků.

Příkaz je jednoduše kontejner pro textový příkaz, což je řetězec (například příkaz SQL) předaný z příjemce do objektu zdroje dat pro spuštění základním úložištěm dat zprostředkovatele. Textový příkaz je obvykle příkaz SQL **SELECT** (v takovém případě, protože SQL **SELECT** určuje sadu řádků, příkaz automaticky vytvoří sadu řádků).

## <a name="rowsets"></a>Řádků

Sady řádků zobrazují data v tabulkovém formátu. Index je zvláštní případ sady řádků. Sady řádků můžete vytvořit z relace nebo příkazu.

### <a name="schema-rowsets"></a>Sady řádků schématu

Schémata mají metadata (strukturální informace) o databázi. Sady řádků schématu jsou sady řádků, které mají informace o schématu. Někteří zprostředkovatelé TECHNOLOGIE OLE DB pro objekty sady řádků systému DBMS podporují objekty sady řádků schématu. Další informace o sadách řádků schématu naleznete v [tématu Získání metadat pomocí sad řádků schématu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) a [tříd sady řádků schématu a tříd Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Zobrazit objekty

Objekt zobrazení definuje podmnožinu řádků a sloupců ze sady řádků. Nemá vlastní data. Objekty zobrazení nemohou kombinovat data z více sad řádků.

## <a name="accessors"></a>Přístupové objekty

Pouze TECHNOLOGIE OLE DB používá koncept přistupujících dat. Přistupující objekt popisuje, jak jsou data uložena v spotřebiteli. Má sadu vazeb (nazývané mapování sloupců) mezi poli sady řádků (sloupci) a datovými členy, které deklarujete v spotřebiteli.

## <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a>Transakce

Transakční objekty se používají při potvrzení nebo přerušení vnořených transakcí na jiné než nejnižší úrovni. Transakce je nedělitelná pracovní jednotka definovaná acid testem. ACID znamená:

- Nedělitost, nelze rozdělit na menší pracovní jednotky

- Souběžnost, může dojít k více transakcím najednou

- Izolace, jedna transakce má omezené znalosti o změnách provedených jiným

- Trvanlivost, transakce provádí trvalé změny

## <a name="enumerators"></a>Enumerátory

Čítače výčtu vyhledávají dostupné zdroje dat a další čítače výčtů. Spotřebitelé, kteří nejsou přizpůsobeni pro konkrétní zdroj dat, používají čítače výčtů k vyhledání zdroje dat, který chcete použít.

Kořenový čítač výčtu dodaný v sadě Microsoft Data Access SDK prochází registrem a hledá zdroje dat a další čítače výčtů. Ostatní čítače výčtu procházet registru nebo hledání způsobem specifické pro zprostředkovatele.

## <a name="errors"></a>chyby

Jakékoli rozhraní na libovolném objektu TECHNOLOGIE OLE DB může generovat chyby. Chyby mají další informace o chybě, včetně volitelného vlastního objektu chyby. Tyto informace jsou uloženy v HRESULT.

## <a name="notifications"></a>Oznámení

Oznámení používají skupiny spolupracujících spotřebitelů sdílejících sadu řádků (kde sdílení znamená, že se předpokládá, že spotřebitelé pracují v rámci stejné transakce). Oznámení umožňují spolupracujícím spotřebitelům sdílejícím sadu řádků, aby byli informováni o akcích v sadě řádků prováděných jejich partnery.

## <a name="see-also"></a>Viz také

[OLE DB – programování](../../data/oledb/ole-db-programming.md)<br/>
[Přehled programování technologie OLE DB](../../data/oledb/ole-db-programming-overview.md)
