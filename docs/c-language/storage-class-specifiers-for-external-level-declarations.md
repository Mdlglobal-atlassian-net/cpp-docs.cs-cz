---
title: Specifikátory třídy úložiště pro deklarace na externí úrovni | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e4f2e80c22d7a341f5b44b77fc14ada8eb2f0098
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066608"
---
# <a name="storage-class-specifiers-for-external-level-declarations"></a>Specifikátory třídy úložiště pro deklarace na externí úrovni

Externí proměnné jsou proměnné v rozsahu souboru. Jsou definovány mimo jakoukoliv funkci a jsou potenciálně dostupné pro mnoho funkcí. Funkce lze definovat pouze na externí úrovni, a proto nemohou být vnořeny. Ve výchozím nastavení jsou všechny odkazy na vnější proměnné a funkce se stejným názvem odkazy na stejný objekt, což znamená, že mají „vnější propojení“. (Můžete použít **statické** – klíčové slovo chcete toto chování změnit. Zobrazit informace dále v této části Další podrobnosti o **statické**.)

Deklarace proměnných na externí úrovni jsou buď definice proměnných („definující deklarace“), nebo odkazy na proměnné definované jinde („odkazující deklarace“).

Externí deklarace proměnné, která také inicializuje proměnnou (implicitně nebo explicitně), je definující deklarací proměnné. Definici na externí úrovni lze provést několika způsoby:

- Proměnná deklarovaná pomocí **statické** specifikátor storage-class. Můžete explicitně inicializovat **statické** proměnné pomocí konstantního výrazu, jak je popsáno v [inicializace](../c-language/initialization.md). Při vynechání inicializátoru je ve výchozím nastavení proměnná inicializována na hodnotu 0. Například tyto dva příkazy jsou oba považovány za definice proměnné `k`.

    ```
    static int k = 16;
    static int k;
    ```

- Proměnná, která je explicitně inicializována na externí úrovni. Například `int j = 3;` je definicí proměnné `j`.

V deklaracích proměnných na externí úrovni (tedy mimo všechny funkce), můžete použít **statické** nebo `extern` – specifikátor třídy úložiště nebo specifikátor třídy úložiště zcela vynechat. Nelze použít **automaticky** a **zaregistrovat** *storage-class-specifier* terminály na vnější úrovni.

Jakmile je proměnná definována na externí úrovni, je viditelná ve zbytku jednotky překladu. Proměnná není viditelná před deklarací ve stejném zdrojovém souboru. Také se nezobrazuje v jiných zdrojových souborech programu, pokud není umožněno její zobrazení pomocí odkazující deklarace, jak je popsáno níže.

Pravidla týkající se **statické** patří:

- Proměnné deklarované mimo všechny bloky bez **statické** – klíčové slovo zachování hodnot v celém programu. Chcete-li omezit jejich přístup k určitým jednotkám překladu, je nutné použít **statické** – klíčové slovo. To jim umožňuje „vnitřní propojení“. Aby mohly být globálními v rámci celého programu, je třeba vynechat třídu explicitního úložiště a použít klíčové slovo `extern` (viz pravidla v dalším seznamu). To jim umožňuje „vnější propojení“. Vnitřní a vnější propojení jsou popsány také v [propojení](../c-language/linkage.md).

- V rámci programu lze definovat proměnné na externí úrovni pouze jednou. Můžete definovat další proměnnou se stejným názvem a **statické** specifikátor třídy úložiště v jiné jednotce překladu. Protože každý **statické** definice je viditelná pouze v rámci vlastní jednotky překladu, nedochází ke konfliktům. To poskytuje vhodný způsob, jak skrýt názvy identifikátorů, které musejí být sdíleny mezi funkcemi překladu jedné jednotky, ale nesmějí být viditelné pro ostatní jednotky překladu.

- **Statické** – specifikátor třídy úložiště můžete použít také na funkce. Pokud deklarujete funkci **statické**, je její název neviditelný mimo soubor, ve kterém je deklarována.

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

Nebyla-li proměnná `i` inicializována, měla by být automaticky nastavena na hodnotu 0. V tomto případě by byly vypsány hodnoty 1, 2 a 3. Zobrazit [inicializace](../c-language/initialization.md) informace o inicializaci proměnné.

## <a name="see-also"></a>Viz také

[Třídy úložiště jazyka C](../c-language/c-storage-classes.md)