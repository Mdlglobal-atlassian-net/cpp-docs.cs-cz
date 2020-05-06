---
title: Výrazy hodnot L-Value a R-Value
ms.date: 11/04/2016
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
ms.openlocfilehash: bd5f702588a11b7841f77de539d113206833cde9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325517"
---
# <a name="l-value-and-r-value-expressions"></a>Výrazy hodnot L-Value a R-Value

Výrazy, které odkazují na umístění v paměti, se nazývají výrazy „l-hodnota“. L-hodnota představuje hodnotu "lokátoru" oblasti úložiště nebo "levou" hodnotu, což znamená, že se může objevit vlevo od znaménka rovná se (**=**). L-hodnoty jsou často identifikátory.

Výrazy odkazující na upravitelná umístění se nazývají „upravitelné l-hodnoty“. Upravitelná l-hodnota nemůže mít typ pole, nekompletní typ ani typ s atributem **const** . Aby bylo možné struktury a sjednocení upravovat l-hodnoty, nesmí mít žádné členy s atributem **const** . Název identifikátoru označuje umístění úložiště, zatímco hodnota proměnné je hodnota uložená v tomto umístění.

Identifikátor je upravitelná l-hodnota, odkazuje-li na umístění v paměti a je-li její typ aritmetický, struktura, sjednocení nebo ukazatel. Například pokud je `ptr` ukazatel na oblast úložiště, pak je `*ptr` upravitelná l-hodnota, jež určuje oblast úložiště, na které `ptr` ukazuje.

Jakýkoli z těchto výrazů jazyka C může být výrazem l-hodnoty:

- Identifikátor celočíselného typu, typu s plovoucí desetinnou čárkou, typu ukazatele, struktury nebo sjednocení

- Výraz dolního indexu (**[]**), který se nevyhodnocuje na pole.

- Výraz výběru členů (**->** nebo **.**)

- Výraz unárního-dereference (<strong>\*</strong>), který neodkazuje na pole

- Výraz l-hodnoty v závorkách

- Objekt **const** (neupravitelná l-hodnota)

Pojem „r-hodnota“ se někdy používá k popisu hodnoty výrazu a pro jeho odlišení od l-hodnoty. Všechny l-hodnoty jsou r-hodnotami, ale ne všechny r-hodnoty jsou l-hodnotami.

**Specifické pro Microsoft**

Jazyk Microsoft C zahrnuje rozšíření standardu ANSI C, které umožňuje přetypovat l-hodnoty pro použití jako l-hodnoty, pokud není velikost objektu zvětšena pomocí přetypování. (Další informace najdete v tématu [převody typu přetypování](../c-language/type-cast-conversions.md) .) Následující příklad znázorňuje tuto funkci:

```
char *p ;
short  i;
long l;

(long *) p = &l ;       /* Legal cast   */
(long) i = l ;          /* Illegal cast */
```

Výchozí hodnota pro Microsoft C znamená, že jsou rozšíření společnosti Microsoft povolena. Tato rozšíření zakažte pomocí možnosti kompilátoru/za.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Operandy a výrazy](../c-language/operands-and-expressions.md)
