---
title: Kvalifikátory typu
ms.date: 11/04/2016
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
ms.openlocfilehash: a5cb7ab3de8938b77dc95be3ee442f71d3b18b42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344795"
---
# <a name="type-qualifiers"></a>Kvalifikátory typu

Kvalifikátory typu poskytují jednu ze dvou vlastností identifikátoru. Kvalifikátor typu **const** deklaruje objekt, který nemůže být upravitelný. Kvalifikátor `volatile` typu deklaruje položku, jejíž hodnotu lze legitimně změnit o něco mimo ovládací prvek programu, ve kterém se zobrazí, jako je například souběžné provádění vlákna.

Dva kvalifikátory typu, **const** a `volatile`, mohou být v deklaraci uvedeny pouze jednou. Kvalifikátory typu se můžou objevit u libovolného specifikátoru typu; nemohou však být zobrazeny za první čárkou v deklaraci více položek. Například následující deklarace jsou platné:

```
typedef volatile int VI;
const int ci;
```

Tyto deklarace nejsou platné:

```
typedef int *i, volatile *vi;
float f, const cf;
```

Kvalifikátory typu jsou relevantní pouze při přístupu k identifikátorům jako l-hodnoty ve výrazech. Informace o l-hodnotách a výrazech naleznete v tématu [výrazy l-value a R-Value](../c-language/l-value-and-r-value-expressions.md) .

## <a name="syntax"></a>Syntaxe

*kvalifikátor typu*: **constvolatile**

Níže jsou platné **const** a `volatile` deklarace:

```
int const *p_ci;       /* Pointer to constant int */
int const (*p_ci);     /* Pointer to constant int */
int *const cp_i;       /* Constant pointer to int */
int (*const cp_i);     /* Constant pointer to int */
int volatile vint;     /* Volatile integer        */
```

Pokud specifikace typu pole obsahuje kvalifikátory typu, je element kvalifikován, nikoli typu pole. Pokud specifikace typu funkce zahrnuje kvalifikátory, chování není definováno. `volatile` Ani **konstanta** nemá vliv na rozsah hodnot nebo aritmetických vlastností objektu.

Tento seznam popisuje, jak použít **const** a `volatile`.

- Klíčové slovo **const** lze použít pro úpravu jakéhokoli základního nebo agregačního typu nebo ukazatele na objekt libovolného typu nebo `typedef`. Pokud je položka deklarována pouze s kvalifikátorem **const** Type, jeho typ je **const int**. **Konstantní** proměnnou lze inicializovat nebo lze umístit do oblasti úložiště jen pro čtení. Klíčové slovo **const** je užitečné pro deklaraci ukazatelů na **const** , protože to vyžaduje, aby funkce neměnila ukazatel jakýmkoli způsobem.

- Kompilátor předpokládá, že v jakémkoli okamžiku v programu je k `volatile` proměnné možné přistupovat neznámým procesem, který používá nebo upravuje jeho hodnotu. Bez ohledu na optimalizace, které jsou zadány na příkazovém řádku, musí být kód pro každé přiřazení nebo odkaz na `volatile` proměnnou generován i v případě, že se zdá být neúčinným.

   Pokud `volatile` se používá samostatně, `int` předpokládá se. Specifikátor `volatile` typu lze použít k zajištění spolehlivého přístupu ke speciálním umístěním v paměti. Používejte `volatile` s datovými objekty, které mohou být k dispozici nebo změněny obslužnými rutinami signálu, souběžným spouštěním programů nebo speciálním hardwarem, jako jsou například vstupně-výstupní Registry mapované paměti. Proměnnou můžete deklarovat jako `volatile` pro její dobu života, nebo můžete přetypovat jeden odkaz. `volatile`

- Položka může být současně **const** a `volatile`, v takovém případě by položka nemohla být oprávněně upravena vlastním programem, ale mohla by být upravena pomocí nějakého asynchronního procesu.

## <a name="see-also"></a>Viz také

[Deklarace a typy](../c-language/declarations-and-types.md)
