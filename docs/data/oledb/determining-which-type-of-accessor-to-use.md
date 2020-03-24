---
title: Určení použitého typu přístupového objektu
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: 31efa36bcd61caa154cd3e4c147ad5ed8728b04c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210987"
---
# <a name="determining-which-type-of-accessor-to-use"></a>Určení použitého typu přístupového objektu

Můžete určit datové typy pro sadu řádků v době kompilace nebo v době běhu.

Pokud potřebujete určit datové typy v době kompilace, použijte statický přistupující objekt (například `CAccessor`).

Pokud potřebujete určit typy dat za běhu, použijte dynamický (`CDynamicAccessor` nebo jeho podřízené) nebo ručně přistupující objekt (`CManualAccessor`). V těchto případech můžete volat `GetColumnInfo` na sadě řádků pro vrácení informací o vazbě sloupce, ze kterých lze určit typy.

Následující tabulka uvádí typy přistupujících objektů, které jsou k dispozici v šablonách příjemců. Každý přistupující objekt má výhody a nevýhody. V závislosti na vaší situaci by měl jeden typ přístupového objektu vyhovovat vašim potřebám.

|Přistupující třída|Vazba|Parametr|Komentář|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|Vytvořte záznam uživatele pomocí COLUMN_ENTRY maker. Makra navážou datový člen v daném záznamu na přistupující objekt. Když je vytvořena sada řádků, sloupce nelze bez vazby.|Ano, pomocí PARAM_MAP položku makra. Po vytvoření vazby nelze parametry odvázat.|Nejrychlejší přistupující objekt z důvodu malého množství kódu.|
|`CDynamicAccessor`|Automatické.|Ne.|Užitečné, pokud neznáte typ dat v sadě řádků.|
|`CDynamicParameterAccessor`|Automatické, ale může být [přepsáno](../../data/oledb/overriding-a-dynamic-accessor.md).|Ano, pokud poskytovatel podporuje `ICommandWithParameters`. Parametry jsou automaticky svázány.|Pomalejší než `CDynamicAccessor`, ale užitečné pro volání obecných uložených procedur.|
|`CDynamicStringAccessor[A,W]`|Automatické.|Ne.|Načte data, ke kterým se získává data z úložiště dat, jako řetězcová data.|
|`CManualAccessor`|Ruční použití `AddBindEntry`.|Ručně pomocí `AddParameterEntry`.|Světl parametry a sloupce jsou vázány pouze jednou. Určíte typ dat, která se mají použít. (Příklad najdete v ukázce [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) Sample.) Vyžaduje více kódu než `CDynamicAccessor` nebo `CAccessor`. Je to více podobné volání OLE DB přímo.|
|`CXMLAccessor`|Automatické.|Ne.|Načte data, ke kterým se získává data z úložiště dat, jako data řetězců a naformátuje je jako data značek XML.|

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)
