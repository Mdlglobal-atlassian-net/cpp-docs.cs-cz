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
ms.openlocfilehash: 99e1d76f8d65def326b0514f3219cef43f695220
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512668"
---
# <a name="snapshot"></a>Snímek

Snímek je záznamů, který odráží statické zobrazení dat, který existoval v době vytvoření snímku. Při otevření snímku a přechod na všechny záznamy, obsahuje sadu záznamů a jejich hodnoty se nezmění, dokud je znovu sestavit snímku voláním `Requery`.

> [!NOTE]
>  Toto téma platí pro třídy knihovny MFC rozhraní ODBC. Pokud používáte tříd DAO knihovny MFC namísto třídy knihovny MFC rozhraní ODBC, přečtěte si téma [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open) popis sady záznamů typ snímku.

Aktualizovatelné nebo jen pro čtení snímky, můžete vytvořit s databázovými třídami. Na rozdíl od dynamických sad aktualizovatelné snímek neodráží změny pro záznam hodnot provedené ostatními uživateli, ale odrážejí, aktualizace a odstranění provedených váš program. Záznamy přidané do snímku nebudou viditelné ve snímku až do okamžiku volání `Requery`.

> [!TIP]
>  Snímek je v rozhraní ODBC statický kurzor. Statický kurzor nezobrazí ve skutečnosti řádek dat. dokud přejděte k tomuto záznamu. Pokud chcete mít jistotu, že jsou všechny záznamy načíst okamžitě, můžete posunout na konec objektu sady záznamů a poté přejděte k první záznam, který chcete zobrazit. Upozorňujeme, že na konec posouvání vyžaduje další režii a může snížit výkon.

Snímky jsou nejvíc hodí v situaci, pokud potřebujete data, která mají zachovat pevná během operací, jako při generování sestav, nebo provádět výpočty. I tak zdroj dat můžete značně odchýlit ze snímku, proto je vhodné k opětovnému sestavení čas od času.

Podpora snímků je založena na knihovna kurzorů rozhraní ODBC, který obsahuje statický kurzor a umístěné aktualizace (třeba aktualizovatelnosti) pro všechny ovladače úrovně 1. Knihovna kurzorů rozhraní DLL musí být načten v paměti pro tuto podporu. Při sestavování `CDatabase` objektu a volání jeho `OpenEx` členskou funkci, je nutné zadat `CDatabase::useCursorLib` možnost *dwOptions* parametru. Při volání `Open` ve výchozím nastavení je načtena členskou funkci, knihovna kurzorů rozhraní. Pokud používáte dynamické sady místo snímky, nechcete způsobit, že knihovna kurzorů, který se má načíst.

Snímky jsou k dispozici pouze v případě, že byla načtena knihovna kurzorů rozhraní ODBC, kdy `CDatabase` objekt byl vytvořen nebo ovladač ODBC používáte podporuje statický kurzor.

> [!NOTE]
>  U některých ovladačů rozhraní ODBC nemusí být aktualizovatelné snímky (statický kurzor). Zkontrolujte dokumentaci ovladače pro podporované typy kurzoru a souběžnosti typy, které podporují. Pokud chcete zajistit aktualizovatelné, ujistěte se, že načtení knihovna kurzorů rozhraní do paměti při vytváření `CDatabase` objektu. Další informace najdete v tématu [ODBC: Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!NOTE]
>  Pokud chcete použít snímky a dynamické sady, musíte je vytvořit na dva různé `CDatabase` objekty (dvě různá připojení).

Další informace o sdílené složce snímků vlastnosti s všechny sady záznamů najdete v tématu [sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md). Další informace o rozhraní ODBC a snímky, včetně knihovna kurzorů rozhraní ODBC, naleznete v tématu [ODBC](../../data/odbc/odbc-basics.md).

## <a name="see-also"></a>Viz také

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)