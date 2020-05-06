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

Při inicializaci skalárních typů je hodnota *přiřazení výrazu* přiřazena proměnné. Pravidla převodu pro přiřazení platí. (Další informace o pravidlech převodu naleznete v tématu [převody typů](../c-language/type-conversions-c.md) .)

## <a name="syntax"></a>Syntaxe

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – specifikátory* *init-deklarátor-list*<sub>opt</sub> **;**

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru třídy úložiště* – *specifikátory*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru typu* *– Povolit specifikátory*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typ-specifikátor deklarace kvalifikátoru* *– specifikátory*<sub>opt</sub>

*init-deklarátor-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarátor-list* **,** *init-deklarátor*

*init-deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor* **=**  / *initializer* inicializátor\* pro skalární inicializaci\*/

*inicializátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*

Můžete inicializovat proměnné libovolného typu za předpokladu, že dodržujete následující pravidla:

- Proměnné deklarované na úrovni oboru souborů lze inicializovat. Pokud neinicializujete explicitně proměnnou na externí úrovni, je ve výchozím nastavení inicializována na hodnotu 0.

- Konstantní výraz lze použít k inicializaci jakékoli globální proměnné deklarované se *specifikátorem třídy úložiště* **static** . Proměnné deklarované jako **static** jsou inicializovány při zahájení provádění programu. Pokud explicitně neinicializujete globální **statickou** proměnnou, je ve výchozím nastavení inicializována na hodnotu 0 a každý člen, který má typ ukazatele, je přiřazen ukazatel s hodnotou null.

- Proměnné deklarované pomocí specifikátoru třídy úložiště **auto** nebo **Register** jsou inicializovány pokaždé, když ovládací prvek pro spuštění projde do bloku, ve kterém jsou deklarovány. Vynecháte-li inicializátor z deklarace proměnné **auto** nebo **Register** , není definována počáteční hodnota proměnné. Pro automatické a registrační hodnoty není inicializátor omezen na konstantu; může to být libovolný výraz, který zahrnuje dříve definované hodnoty, dokonce i volání funkcí.

- Počáteční hodnoty pro deklarace externích proměnných a pro všechny **statické** proměnné, ať už externí nebo interní, musí být konstantní výrazy. (Další informace naleznete v tématu [konstantní výrazy](../c-language/c-constant-expressions.md).) Vzhledem k tomu, že adresa všech externě deklarovaných nebo statických proměnných je konstantní, lze ji použít k inicializaci vnitřně deklarované **statické** proměnné ukazatele. Adresa proměnné **auto** však nemůže být použita jako statický inicializátor, protože může být pro každé spuštění bloku odlišná. Pro inicializaci proměnných **auto** a **Register** lze použít buď konstanty nebo hodnoty proměnných.

- Pokud deklarace identifikátoru má rozsah bloku a identifikátor má vnější propojení, deklarace nemůže mít inicializaci.

## <a name="examples"></a>Příklady

Následující příklady ilustrují inicializace:

```C
int x = 10;
```

Proměnná `x` celého čísla je inicializována do konstantního `10`výrazu.

```C
register int *px = 0;
```

Ukazatel `px` je inicializován na hodnotu 0 a vytváří ukazatel "null".

```C
const int c = (3 * 1024);
```

V tomto příkladu se používá konstantní `(3 * 1024)` výraz pro `c` inicializaci na konstantní hodnotu, kterou nelze upravovat z důvodu klíčového slova **const** .

```C
int *b = &x;
```

Tento příkaz inicializuje ukazatel `b` na adresu jiné proměnné,. `x`

```C
int *const a = &z;
```

Ukazatel `a` je inicializován s adresou proměnné s názvem `z`. Je-li však tento parametr uveden jako **const**, lze proměnnou `a` pouze inicializovat, nikdy Neupravovat. Vždy odkazuje na stejné umístění.

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

Globální proměnná `GLOBAL` je deklarována na externí úrovni, takže má globální životnost. Místní proměnná `LOCAL` má třídu **automatického** úložiště a má adresu pouze během provádění funkce, ve které je deklarována. Proto pokus o inicializaci proměnné `lp` `LOCAL` **statického** ukazatele s adresou není povolen. **Statickou** proměnnou `gp` ukazatele lze inicializovat na adresu, `GLOBAL` protože tato adresa je vždy stejná. Podobně lze `*rp` inicializovat, protože `rp` je místní proměnná a může mít nekonstantní inicializátor. Pokaždé, když je zapsán `LOCAL` blok, má novou adresu, která je pak přiřazena `rp`k.

## <a name="see-also"></a>Viz také

[Operace](../c-language/initialization.md)
