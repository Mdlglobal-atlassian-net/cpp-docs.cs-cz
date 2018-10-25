---
title: OLE DB – Model objektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 65cb4ef7acad08d3065f8394d61a50441d5e597c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056565"
---
# <a name="ole-db-object-model"></a>OLE DB – model objektů

Objektový model OLE DB je vytvořen z následujících objektů nebo komponenty. První čtyři objekty nebo součásti (zdrojů dat, relace, příkazy a sady řádků) umožňují připojení ke zdroji dat a jeho zobrazení. Rest, počínaje přístupových objektů, se vztahují na práci s daty, jakmile se zobrazí.

## <a name="data-sources"></a>Zdroje dat

Objekty zdroje dat vám umožní připojit ke zdroji dat, jako je například soubor nebo DBMS. Objekt zdroje dat vytvoří a spravuje připojení a obsahuje informace o oprávnění a ověřování (například přihlašovací jméno a heslo). Objekt zdroje dat můžete vytvořit jednu nebo více relací.

## <a name="sessions"></a>Relace

Relace slouží ke správě konkrétní interakce se zdrojem dat pro dotazování a načíst data. Každá relace je jedna transakce. Transakce je nedělitelná jednotka práce definované ACID testem. Definici kyseliny naleznete v tématu [transakce](#vcconoledbcomponents_transactions).

Relace provádět důležité úkoly, jako je otevření sady řádků a vrátí objekt zdroje dat, který byl vytvořen. Relace můžete také vrátit metadata nebo informace o zdroji dat (například informace o tabulce).

Relaci můžete vytvořit jeden nebo více příkazů.

## <a name="commands"></a>Příkazy

Příkazy spustí text příkazu, jako je příkaz jazyka SQL. Pokud textový příkaz určuje sadu řádků, jako je například SQL **vyberte** příkaz, příkaz vytvoří v sadě řádků.

Příkaz je prostě kontejner pro textový příkaz, který je předán z příjemce na objekt zdroje dat pro spuštění podle poskytovatele základnímu úložišti dat. řetězec (například příkaz jazyka SQL). Text příkazu je obvykle SQL **vyberte** – příkaz (v takovém případě, protože SQL **vyberte** určuje sadu řádků, příkaz automaticky vytvoří sadu řádků).

## <a name="rowsets"></a>Sady řádků

Sady řádků zobrazení dat v tabelárním formátu. Index je zvláštní případ sady řádků. Sady řádků můžete vytvořit z relace nebo příkaz.

### <a name="schema-rowsets"></a>Sady řádků schématu

Schémata mají metadata (strukturální informace) o databázi. Sady řádků schématu jsou sady řádků, které mají informace o schématu. Někteří poskytovatelé OLE DB pro DBMS podporovat rozhraní objektu sady řádků schématu. Další informace o sad řádků schématu najdete v tématu [získávání metadat pomocí sad řádků schématu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) a [třídy sady řádků schématu a definiční třídy typů](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

### <a name="view-objects"></a>Zobrazit objekty

Objekt zobrazení definuje podmnožinu řádků a sloupců ze sady řádků. Nemá žádná data. Zobrazit objekty nelze kombinovat data z více sad řádků.

## <a name="accessors"></a>Přístupové objekty

Pouze technologie OLE DB používá koncept přistupující objekty. Přístupový objekt popisuje způsob uložení dat v příjemce. Obsahuje sadu vazby (označované jako mapování sloupců) mezi řádků polí (sloupců) a datové členy můžete deklarovat v příjemci.

##  <a name="vcconoledbcomponents_transactions"></a> Transakce

Objekty transakce se používají při potvrzení nebo přerušení vnořené transakce na jiné než nejnižší úroveň. Transakce je nedělitelná jednotka práce definované ACID testem. KYSELINY, zkratka pro:

- Atomicitu, nelze rozdělit do menších jednotek práce

- Souběžnost, více než jedna transakce může dojít v čase

- Izolace, jedna transakce má omezené znalosti o změny provedené jiným uživatelem

- Odolnost, provede transakce trvalé změny

## <a name="enumerators"></a>Enumerátory

Enumerátory vyhledat dostupné zdroje dat a další výčty. Příjemce, kteří nejsou přizpůsobená pro určitý zdroj dat pomocí enumerátory vyhledat zdroj dat používat.

Kořenový enumerátor dodáváno v sadě Microsoft Data Access SDK prochází registru, které hledáte, zdroje dat a další výčty. Další výčty procházení registru nebo vyhledávání v podobě specifickým pro zprostředkovatele.

## <a name="errors"></a>Chyby

Libovolné rozhraní libovolného objektu OLE DB mohou způsobit chyby. Chyby mají další informace o chybě, včetně objektu volitelné vlastních chyb. Tyto informace jsou uloženy v HRESULT.

## <a name="notifications"></a>Oznámení

Oznámení se používají skupiny spolupracující spotřebitelů sdílení sady řádků (kde sdílení znamená, že příjemci jsou předpokládá, že funguje v rámci jedné transakce). Oznámení povolení spolupracující příjemcům sdílení sadu řádků informován o akcích pro řádků přihlášením svoje konkurenty.

## <a name="see-also"></a>Viz také

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)