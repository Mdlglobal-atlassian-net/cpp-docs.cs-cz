---
title: Inicializace skalárních typů
ms.date: 11/04/2016
helpviewer_keywords:
- initializing scalar types
- register variables
- initialization, scalar types
- initializing variables, scalar types
- scalar types
- static variables, initializing
- automatic storage class, initializing scalar types
- automatic storage class
- types [C], initializing
ms.assetid: 73c516f5-c3ad-4d56-ab3b-f2a82b621104
ms.openlocfilehash: 3cf7eddcf43a65a787de60c391863d6471be7bcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232940"
---
# <a name="initializing-scalar-types"></a>Inicializace skalárních typů

Při inicializaci Skalární typy, hodnota *výrazu přiřazení* je přiřazená k proměnné. Pravidla převodu pro přiřazení použít. (Viz [převody typů](../c-language/type-conversions-c.md) o pravidla převodu.)

## <a name="syntax"></a>Syntaxe

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *init-declarator-list*<sub>optimalizované</sub> **;**

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specifikátory deklarace*<sub>optimalizované</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub>

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Init-declarator-list* **,** *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor* **=** *inicializátor*  / \* pro skalární inicializace \*/

*Inicializátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*

Můžete inicializovat proměnné libovolného typu, za předpokladu, že dodržují následující pravidla:

- Je možné inicializovat proměnné deklarované na úrovni rozsahu souboru. Pokud proměnnou na externí úrovni neinicializujete explicitně, je ve výchozím nastavení inicializována na hodnotu 0.

- Konstantní výraz lze použít k inicializaci všechny globální proměnná deklarovaná pomocí **statické** *storage-class-specifier*. Proměnné deklarované jako **statické** jsou inicializovány při zahájení provádění programu. Pokud neinicializujete explicitně globální **statické** proměnné, je inicializován na 0 ve výchozím nastavení, a každý člen, který má typ ukazatele se přiřadí ukazatel s hodnotou null.

- Proměnné deklarované s **automaticky** nebo **zaregistrovat** – specifikátor třídy úložiště se inicializuje pokaždé, když předává řízení provádění do bloku ve kterém jsou deklarovány. Při vynechání inicializátoru od deklarace **automaticky** nebo **zaregistrovat** proměnné, počáteční hodnota proměnné není definována. Pro automatické a hodnot registru, inicializátor není omezen na právě konstanty. To může být libovolný výraz zahrnující dříve definované hodnoty, dokonce i funkce volání.

- Počáteční hodnoty pro externí deklarace proměnných a pro všechny **statické** proměnné, externí nebo interní, musí být konstantní výrazy. (Další informace najdete v tématu [konstantní výrazy](../c-language/c-constant-expressions.md).) Adresa jakékoli externě deklarovaná nebo statická proměnná je konstantní, lze použít k inicializaci interně deklarované **statické** proměnné ukazatele. Ale adresu **automaticky** proměnnou nelze použít jako statický inicializátor, protože se může lišit pro každé spuštění bloku. Konstanty a proměnné hodnoty můžete použít k inicializaci **automaticky** a **zaregistrovat** proměnné.

- Pokud deklarace identifikátoru s rozsahem bloku, a má identifikátor vnější propojení, deklarace nemůže mít inicializace.

## <a name="examples"></a>Příklady

Následující příklady znázorňují inicializace:

```C
int x = 10;
```

Celočíselné proměnné `x` je inicializován na konstantní výraz `10`.

```C
register int *px = 0;
```

Ukazatel `px` je inicializován na hodnotu 0, vytváření ukazatel s "hodnotou null".

```C
const int c = (3 * 1024);
```

Tento příklad používá konstantní výraz `(3 * 1024)` inicializovat `c` na konstantní hodnotu, která nejde změnit z důvodu **const** – klíčové slovo.

```C
int *b = &x;
```

Tento příkaz inicializuje ukazatele `b` adresou jiné proměnné `x`.

```C
int *const a = &z;
```

Ukazatel `a` inicializovat pomocí adresy proměnné s názvem `z`. Ale od té doby je zadán jako **const**, proměnná `a` lze inicializovat pouze, nikdy nemění. Vždy odkazuje na stejném umístění.

```C
int GLOBAL ;

int function( void )
{
    int LOCAL ;
    static int *lp = &LOCAL;   /* Illegal initialization */
    static int *gp = &GLOBAL;  /* Legal initialization   */
    register int *rp = &LOCAL; /* Legal initialization   */
}
```

Globální proměnná `GLOBAL` je deklarované na vnější úrovni, má globální životnost. Lokální proměnná `LOCAL` má **automaticky** třídu úložiště a má jenom adresy během spuštění funkce, ve kterém je deklarována. Proto se pokus o inicializaci **statické** proměnné ukazatele `lp` adresou `LOCAL` není povolená. **Statické** proměnné ukazatele `gp` mohou být inicializovány na adresu `GLOBAL` vzhledem k tomu, že tato adresa je vždy stejný. Obdobně `*rp` lze inicializovat, protože `rp` místní proměnnou, která může mít nekonstantním inicializátor. Pokaždé, když je blok proveden, `LOCAL` má novou adresu, která je poté přiřazen `rp`.

## <a name="see-also"></a>Viz také:

[Inicializace](../c-language/initialization.md)
