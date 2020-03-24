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
ms.openlocfilehash: 62b5952f3052a3248175ce7892b1cf4615f1dd17
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212690"
---
# <a name="snapshot"></a>Snímek

Snímek je sada záznamů, která odráží statické zobrazení dat v době vytvoření snímku. Když otevřete snímek a přesunete se do všech záznamů, sada záznamů, které obsahuje, a jejich hodnoty se nezmění, dokud znovu sestavíte snímek voláním `Requery`.

> [!NOTE]
>  Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC. Pokud používáte třídy knihovny MFC rozhraní DAO namísto tříd knihovny MFC rozhraní ODBC, viz [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open) pro popis záznamů typu Snapshot.

Pomocí databázových tříd můžete vytvořit snímky s aktualizovatelným nebo jen pro čtení. Na rozdíl od dynamického snímku neodráží aktualizovatelné snímky změny v záznamu hodnot provedených ostatními uživateli, ale odráží aktualizace a odstranění provedené vaším programem. Záznamy přidané do snímku se neprojeví ve snímku, dokud nebudete volat `Requery`.

> [!TIP]
>  Snímek je statický kurzor rozhraní ODBC. Statické kurzory ve skutečnosti neobsahují řádek dat, dokud se neposouváte k záznamu. Aby bylo zajištěno, že všechny záznamy budou ihned načteny, můžete přejít na konec vaší sady záznamů a pak přejít na první záznam, který chcete zobrazit. Všimněte si ale, že posun na konec zahrnuje dodatečnou režii a může snížit výkon.

Snímky jsou nejužitečnější, pokud potřebujete, aby data zůstala pevná během svých operací, jako když generujete sestavu nebo provádíte výpočty. I tak se může stát, že se zdroj dat významně neliší od snímku, takže ho můžete chtít znovu sestavit v čase.

Podpora snímků je založena na knihovně rozhraní ODBC, která poskytuje statické kurzory a umístěné aktualizace (nutné pro aktualizovatelnost) pro všechny ovladače úrovně 1. Knihovna kurzorů musí být načtena do paměti pro tuto podporu. Při vytváření objektu `CDatabase` a volání jeho členské funkce `OpenEx` je nutné zadat možnost `CDatabase::useCursorLib` parametru *dwOptions* . Pokud zavoláte členskou funkci `Open`, knihovna kurzorů se nahraje ve výchozím nastavení. Pokud používáte dynamické sady místo snímků, nechcete způsobit načtení knihovny kurzorů.

Snímky jsou k dispozici pouze v případě, že byla načtena knihovna kurzorů rozhraní ODBC, když byl vytvořen objekt `CDatabase` nebo ovladač ODBC, který používáte, podporuje statické kurzory.

> [!NOTE]
>  U některých ovladačů rozhraní ODBC nemusí být snímky (statické kurzory) možné aktualizovatelné. V dokumentaci k ovladači najdete podporované typy kurzorů a typy souběžnosti, které podporují. Chcete-li zaručit aktualizovatelné snímky, nezapomeňte při vytváření objektu `CDatabase` načíst knihovnu kurzorů do paměti. Další informace najdete v tématu [ODBC: Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
>  Pokud chcete použít snímky i dynamické sady, je nutné je založit na dvou různých `CDatabase` objektů (dvě různá připojení).

Další informace o sdílení snímků vlastností se všemi sadami záznamů naleznete v tématu [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md). Další informace o rozhraní ODBC a snímcích, včetně knihovny kurzorů rozhraní ODBC, najdete v tématu [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)
