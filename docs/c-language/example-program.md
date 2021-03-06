---
title: Ukázkový program
ms.date: 11/04/2016
ms.assetid: fc22ef82-9caa-425f-b201-2891bc123d1f
ms.openlocfilehash: fc00ee391fd845039791b8cec727623074a7aeff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233932"
---
# <a name="example-program"></a>Ukázkový program

Následující zdrojová aplikace jazyka C se skládá ze dvou zdrojových souborů. Poskytuje přehled o různých deklaracích a definicích, které je možné v aplikaci jazyka C použít. Pozdější části této knihy popisují, jak napsat tyto deklarace, definice a inicializace a jak používat klíčová slova jazyka C, jako jsou **statické** a `extern`. Funkce `printf` je deklarována v souboru záhlaví STDIO.H jazyka C.

Funkce `main` a `max` jsou považovány za umístěné v samostatných souborech a provádění aplikace začíná funkcí `main`. Před funkcí `main` nejsou spuštěny žádné explicitní uživatelské funkce.

```
/*****************************************************************
                    FILE1.C - main function
*****************************************************************/

#define ONE     1
#define TWO     2
#define THREE   3
#include <stdio.h>

int a = 1;                       // Defining declarations
int b = 2;                       //  of external variables

extern int max( int a, int b );  // Function prototype

int main()                       // Function definition
{                                //  for main function
    int c;                       // Definitions for
    int d;                       //  two uninitialized
                                 //  local variables

    extern int u;                // Referencing declaration
                                 //  of external variable
                                 //  defined elsewhere
    static int v;                // Definition of variable
                                 //  with continuous lifetime

    int w = ONE, x = TWO, y = THREE;
    int z = 0;

    z = max( x, y );             // Executable statements
    w = max( z, w );
    printf_s( "%d %d\n", z, w );
    return 0;
}

/****************************************************************
            FILE2.C - definition of max function
****************************************************************/

int max( int a, int b )          // Note formal parameters are
                                 //  included in function header
{
    if( a > b )
        return( a );
    else
        return( b );
}
```

FILE1.C obsahuje prototyp funkce `max`. Tento druh deklarace se někdy nazývá „dopředná deklarace“, protože funkce je deklarována před jejím použitím. Definice funkce `main` zahrnuje volání funkce `max`.

Řádky začínající `#define` jsou direktivy preprocesoru. Tyto direktivy sdělují preprocesoru, že má nahradit identifikátory `ONE`, `TWO` a `THREE` v celém souboru FILE1.C čísly `1`, `2` a `3`. Direktivy se však nevztahují na soubor FILE2.C, který je kompilován samostatně a následně připojen k souboru FILE1.C. Řádek začínající příkazem `#include` sděluje kompilátoru, že je třeba zahrnout soubor STDIO.H, který obsahuje prototyp funkce `printf`. [Direktivy preprocesoru](../preprocessor/preprocessor-directives.md) jsou vysvětleny v *odkazu preprocesoru*.

FILE1.C používá pro inicializaci globálních proměnných `a` a `b` definující deklarace. Místní proměnné `c` a `d` jsou deklarovány, ale nejsou inicializovány. Úložiště je alokováno pro všechny tyto proměnné. Statické i externí proměnné `u` a `v` jsou automaticky inicializovány na hodnotu 0. Proto pouze `a`, `b`, `u` a `v` obsahují při deklaraci smysluplné hodnoty, protože jsou inicializovány explicitně nebo implicitně. FILE2.C obsahuje definici funkce `max`. Tato definice obsluhuje volání `max` v souboru FILE1.C.

Doba života a viditelnosti identifikátorů je popsána v tématu [životnost, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md). Další informace o funkcích naleznete v tématu [Functions](../c-language/functions-c.md).

## <a name="see-also"></a>Viz také

[Zdrojové soubory a zdrojové programy](../c-language/source-files-and-source-programs.md)
