---
title: 2.6.4 atomic – konstrukce
ms.date: 11/04/2016
ms.assetid: e4232ef1-4058-42ce-9de0-0ca788312aba
ms.openlocfilehash: 1f477a59ef475fda9bd0daeeb4edac18a3eeedb9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677653"
---
# <a name="264-atomic-construct"></a>2.6.4 atomic – konstrukce

`atomic` Směrnice zajišťuje atomicky, aktualizaci umístění konkrétní paměťové místo vystavení možnost více souběžných vláken pro zápis. Syntaxe `atomic` direktivy je následující:

```
#pragma omp atomic new-lineexpression-stmt
```

Příkaz výrazu musí mít jednu z následujících forem:

*x binop*= *výraz*

x ++

++ x

x--

--x

V předchozích výrazů:

- *x* je výraz l-hodnota s skalárního typu.

- *výraz* je výraz s skalárního typu a neodkazuje objektu určeném *x*.

- `binop` není přetíženého operátoru a je jedním z +, \*, -, / &, ^, &#124;, <\<, nebo >>.

I když je definováno implementací Určuje, zda implementace nahradí všechny `atomic` direktivy s **kritické** direktivy, které mají stejný jedinečný *název*, `atomic` – direktiva povolení lepší optimalizace. Často hardwarové pokyny jsou k dispozici, které můžete provádět atomické aktualizace s minimálními nároky.

Zatížení a úložiště objektu určeném *x* jsou atomické, vyhodnocení *expr* není atomické. Aby nedošlo ke konfliktům časování, by měly být chráněné všechny aktualizace umístění paralelně s `atomic` direktiv, kromě těch, které jsou známé jako zdarma ke konfliktům časování.

Omezení `atomic` směrnice jsou následující:

- Musí mít kompatibilní typ atomic všude, kde x umístění úložiště v celém programu.

## <a name="examples"></a>Příklady:

```
extern float a[], *p = a, b;
/* Protect against races among multiple updates. */
#pragma omp atomic
a[index[i]] += b;
/* Protect against races with updates through a. */
#pragma omp atomic
p[i] -= 1.0f;

extern union {int n; float x;} u;
/* ERROR - References through incompatible types. */
#pragma omp atomic
u.n++;
#pragma omp atomic
u.x -= 1.0f;
```