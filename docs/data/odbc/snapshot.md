---
title: Snímek
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC cursor library [ODBC], snapshots
- cursors [ODBC], static
- recordsets, snapshots
- snapshots, support in ODBC
- static cursors
- ODBC recordsets, snapshots
- cursor library [ODBC], snapshots
- snapshots
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
ms.openlocfilehash: e487b5abcc5eee4e3f4b1941100980eac4a040c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366911"
---
# <a name="snapshot"></a>Snímek

Snímek je sada záznamů, která odráží statické zobrazení dat tak, jak existovala v době, kdy byl snímek vytvořen. Když otevřete snímek a přesunout na všechny záznamy, sada záznamů, které obsahuje a `Requery`jejich hodnoty se nezmění, dokud znovu snímek voláním .

> [!NOTE]
> Toto téma se vztahuje na třídy Knihovny MFC ODBC. Pokud používáte třídy MFC DAO místo tříd knihovny MFC ODBC, naleznete v tématu [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open) pro popis sad záznamů typu snímek.

Můžete vytvořit aktualizovatelné snímky nebo snímky jen pro čtení s třídami databáze. Na rozdíl od dynamické sady aktualizovatelný snímek neodráží změny hodnot záznamů provedených jinými uživateli, ale odráží aktualizace a odstranění provedené programem. Záznamy přidané do snímku se nestanou viditelnými `Requery`pro snímek, dokud nezavoláte .

> [!TIP]
> Snímek je statický kurzor ODBC. Statické kurzory ve skutečnosti nezískají řádek dat, dokud se k tomuto záznamu neposunete. Chcete-li zajistit okamžité načtení všech záznamů, můžete přejít na konec sady záznamů a potom přejít na první záznam, který chcete zobrazit. Všimněte si však, že posouvání na konec znamená další režii a může snížit výkon.

Snímky jsou nejcennější, když potřebujete, aby data zůstala pevná během operací, jako když generujete sestavu nebo provádíte výpočty. I tak se zdroj dat může značně lišit od snímku, takže jej budete chtít čas od času znovu sestavit.

Podpora snímků je založena na knihovně kurzorů ODBC, která poskytuje statické kurzory a umístěné aktualizace (potřebné pro aktualizovatelnost) pro libovolný ovladač úrovně 1. Knihovna DLL knihovny kurzorů musí být načtena do paměti pro tuto podporu. Při vytváření `CDatabase` objektu a `OpenEx` volání jeho členské `CDatabase::useCursorLib` funkce je nutné zadat možnost parametru *dwOptions.* Pokud zavoláte `Open` členovou funkci, knihovna kurzorů se načte ve výchozím nastavení. Pokud používáte sady dynasety namísto snímků, nechcete způsobit načtení knihovny kurzoru.

Snímky jsou k dispozici pouze v případě, `CDatabase` že knihovna kurzorů ROZHRANÍ ODBC byla načtena při vytvoření objektu nebo ovladač ODBC, který používáte, podporuje statické kurzory.

> [!NOTE]
> U některých ovladačů ROZHRANÍ ODBC nemusí být možné aktualizovat snímky (statické kurzory). Zkontrolujte, zda dokumentace ovladače pro podporované typy kurzorů a typy souběžnosti, které podporují. Chcete-li zaručit aktualizovatelné snímky, ujistěte se, že `CDatabase` při vytváření objektu načtete knihovnu kurzorů do paměti. Další informace naleznete [v tématu ODBC: The ODBC Cursor Library](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
> Pokud chcete použít snímky i dynasady, musíte je založit na dvou různých `CDatabase` objektech (dvě různá připojení).

Další informace o vlastnostech, které snímky sdílejí se všemi sadami záznamů, naleznete v [tématu Recordset (ODBC).](../../data/odbc/recordset-odbc.md) Další informace o rozhraní ODBC a snímcích, včetně knihovny kurzorů ODBC, naleznete v [tématu ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Viz také

[Připojení k otevřené databázi (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
