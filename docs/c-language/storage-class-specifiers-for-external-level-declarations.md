---
title: Specifikátory třídy úložiště pro deklarace na externí úrovni
ms.date: 11/04/2016
helpviewer_keywords:
- external definitions
- linkage [C++], external
- external linkage, variable declarations
- declaring variables, external variables
- declarations [C++], external
- declarations [C++], specifiers
- external declarations
- static variables, external declarations
- variables, visibility
- external linkage, storage-class specifiers
- referencing declarations
- visibility, variables
- static storage class specifiers
ms.assetid: b76b623a-80ec-4d5d-859b-6cef422657ee
ms.openlocfilehash: 941994f668fa035b569f9ccae2c301ebf42bcda6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157952"
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>Specifikátory třídy úložiště pro deklarace na externí úrovni

Externí proměnné jsou proměnné v rozsahu souboru. Jsou definovány mimo jakoukoliv funkci a jsou potenciálně dostupné pro mnoho funkcí. Funkce lze definovat pouze na externí úrovni, a proto nemohou být vnořeny. Ve výchozím nastavení jsou všechny odkazy na vnější proměnné a funkce se stejným názvem odkazy na stejný objekt, což znamená, že mají „vnější propojení“. (K přepsání můžete použít klíčové slovo **static** . Další informace o **statických**verzích najdete v části Další informace v této části.)

Deklarace proměnných na externí úrovni jsou buď definice proměnných („definující deklarace“), nebo odkazy na proměnné definované jinde („odkazující deklarace“).

Externí deklarace proměnné, která také inicializuje proměnnou (implicitně nebo explicitně), je definující deklarací proměnné. Definici na externí úrovni lze provést několika způsoby:

- Proměnná, kterou deklarujete se specifikátorem třídy úložiště **static** . **Statickou** proměnnou lze explicitně inicializovat pomocí konstantního výrazu, jak je popsáno v tématu [inicializace](../c-language/initialization.md). Při vynechání inicializátoru je ve výchozím nastavení proměnná inicializována na hodnotu 0. Například tyto dva příkazy jsou oba považovány za definice proměnné `k`.

    ```
    static int k = 16;
    static int k;
    ```

- Proměnná, která je explicitně inicializována na externí úrovni. Například `int j = 3;` je definicí proměnné `j`.

V deklaracích proměnných na externí úrovni (tj. mimo všechny funkce) můžete použít specifikátor třídy úložiště **static** nebo `extern` Storage nebo zcela vynechat specifikátor třídy úložiště. Na externí úrovni nemůžete použít terminály specifikátoru úložiště **auto** a **Register** *úložiště-Class* .

Jakmile je proměnná definována na externí úrovni, je viditelná ve zbytku jednotky překladu. Proměnná není viditelná před deklarací ve stejném zdrojovém souboru. Také se nezobrazuje v jiných zdrojových souborech programu, pokud není umožněno její zobrazení pomocí odkazující deklarace, jak je popsáno níže.

Pravidla týkající se **statického** zahrnutí:

- Proměnné deklarované mimo všechny bloky bez klíčového slova **static** vždy uchovávají jejich hodnoty v celém programu. Chcete-li omezit přístup k určité jednotce překladu, je nutné použít klíčové slovo **static** . To jim umožňuje „vnitřní propojení“. Aby mohly být globálními v rámci celého programu, je třeba vynechat třídu explicitního úložiště a použít klíčové slovo `extern` (viz pravidla v dalším seznamu). To jim umožňuje „vnější propojení“. Vnitřní a vnější propojení jsou také popsána v tématu [propojení](../c-language/linkage.md).

- V rámci programu lze definovat proměnné na externí úrovni pouze jednou. Můžete definovat další proměnnou se stejným názvem a **statickým** specifikátorem třídy úložiště v jiné jednotce překladu. Vzhledem k tomu, že každá **statická** definice je viditelná pouze v rámci vlastní jednotky překladu, nedochází k žádnému konfliktu. To poskytuje vhodný způsob, jak skrýt názvy identifikátorů, které musejí být sdíleny mezi funkcemi překladu jedné jednotky, ale nesmějí být viditelné pro ostatní jednotky překladu.

- Specifikátor třídy úložiště **static** se může vztahovat i na funkce. Pokud deklarujete funkci **statickou**, její název je neviditelný mimo soubor, ve kterém je deklarována.

Pravidla pro používání specifikátoru třídy úložiště `extern` jsou:

- Specifikátor třídy úložiště `extern` deklaruje odkaz na proměnnou definovanou jinde. Chcete-li zajistit, aby byla definice v jiném zdrojovém souboru viditelná nebo aby byla proměnná viditelná před svou definicí ve stejném zdrojovém souboru, můžete použít deklaraci `extern`. Jakmile je deklarován odkaz na proměnnou na externí úrovni, je proměnná viditelná napříč zbytkem jednotky překladu, ve které se nachází deklarovaný odkaz.

- Aby byl odkaz `extern` platný, proměnná, na kterou odkazuje, musí být na externí úrovni definována nanejvýš jednou. Tato definice (bez třídy úložiště `extern`) může být v libovolných jednotkách překladu, které tvoří program.

## <a name="example"></a>Příklad

Následující příklad znázorňuje externí deklarace:

```
/******************************************************************
                      SOURCE FILE ONE
*******************************************************************/
#include <stdio.h>

extern int i;                // Reference to i, defined below
void next( void );           // Function prototype

int main()
{
    i++;
    printf_s( "%d\n", i );   // i equals 4
    next();
}

int i = 3;                  // Definition of i

void next( void )
{
    i++;
    printf_s( "%d\n", i );  // i equals 5
    other();
}

/******************************************************************
                      SOURCE FILE TWO
*******************************************************************/
#include <stdio.h>

extern int i;              // Reference to i in
                           // first source file
void other( void )
{
    i++;
    printf_s( "%d\n", i ); // i equals 6
}
```

V tomto příkladu obsahují dva zdrojové soubory celkem tři externí deklarace `i`. Pouze jedna deklarace je „definující deklarací“. Tato deklarace

```
int i = 3;
```

definuje globální proměnnou `i` a inicializuje ji s počáteční hodnotou 3. „Odkazující“ deklarace `i` v horní části prvního zdrojového souboru umožňuje pomocí klíčového slova `extern` zviditelnit globální proměnnou před její definující deklarací v souboru. Odkazující deklarace `i` také způsobí ve druhém zdrojovém souboru zviditelnění proměnné v daném zdrojovém souboru. Není-li poskytnuta definující instance proměnné v jednotce překladu, předpokládá kompilátor přítomnost

```
extern int x;
```

odkazující deklarace a to, že se definující odkaz

```
int x = 0;
```

zobrazí v jiné jednotce překladu programu.

Všechny tři funkce, `main`, `next` a `other`, provádějí stejný úkol: zvyšují proměnnou `i` a vypíší ji. Jsou vypsány hodnoty 4, 5 a 6.

Nebyla-li proměnná `i` inicializována, měla by být automaticky nastavena na hodnotu 0. V tomto případě by byly vypsány hodnoty 1, 2 a 3. Viz [inicializace](../c-language/initialization.md) pro informace o inicializaci proměnné.

## <a name="see-also"></a>Viz také

[Třídy úložiště jazyka C](../c-language/c-storage-classes.md)
