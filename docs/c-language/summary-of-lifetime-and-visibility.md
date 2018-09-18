---
title: Souhrn doby platnosti a viditelnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ef73c7e9592f1365e946d32d2aecc5894899316
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061523"
---
# <a name="summary-of-lifetime-and-visibility"></a>Souhrn doby platnosti a viditelnosti

V následující tabulce je uveden seznam vlastností doby platnosti a viditelnosti pro většinu identifikátory. První tři sloupce zadejte atributy, které definují doby platnosti a viditelnosti. Doby platnosti a viditelnosti ve sloupci čtvrtý a pátý má identifikátor s atributy Dal první tři sloupce. V tabulce nepopisuje všechny možné případy. Odkazovat na [třídy úložiště](../c-language/c-storage-classes.md) Další informace.

### <a name="summary-of-lifetime-and-visibility"></a>Souhrn doby platnosti a viditelnosti

|Atributy:<br /><br /> úroveň|Položka|Třída úložiště<br /><br /> Specifikátor|Výsledek:<br /><br /> Doba platnosti|Viditelnost|
|---------------------------|----------|----------------------------------|--------------------------|----------------|
|Rozsah souboru|Definice proměnných|**static**|Globální|Zbývající část zdrojového souboru, ve kterém se vyskytuje|
||Deklarace proměnné|**extern**|Globální|Zbývající část zdrojového souboru, ve kterém se vyskytuje|
||Prototyp funkce nebo definice|**static**|Globální|Jeden zdrojový soubor|
||Prototyp funkce|**extern**|Globální|Zbývající část zdrojového souboru|
|Rozsah bloku|Deklarace proměnné|**extern**|Globální|Blok|
||Definice proměnných|**static**|Globální|Blok|
||Definice proměnných|**Automatické** nebo **zaregistrovat**|místní|Blok|

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje bloky, vnoření a viditelnost proměnné:

### <a name="code"></a>Kód

```
// Lifetime_and_Visibility.c

#include <stdio.h>

int i = 1;  // i defined at external level

int main()  // main function defined at external level
{
    printf_s( "%d\n", i ); // Prints 1 (value of external level i)
    {                                 // Begin first nested block
        int i = 2, j = 3;          // i and j defined at internal level
        printf_s( "%d %d\n", i, j );  // Prints 2, 3
        {                             // Begin second nested block
            int i = 0;                // i is redefined
            printf_s( "%d %d\n", i, j ); // Prints 0, 3
        }                             // End of second nested block
        printf_s( "%d\n", i );        // Prints 2 (outer definition
                                      //  restored)
    }                                 // End of first nested block
    printf_s( "%d\n", i );            // Prints 1 (external level
                                      // definition restored)
    return 0;
}
```

### <a name="comments"></a>Komentáře

V tomto příkladu jsou čtyři úrovně viditelnosti: na externí úrovni nebo na tři bloku. Na obrazovku, jak je uvedeno v komentářích následujících každého příkazu jsou vypsány hodnoty.

## <a name="see-also"></a>Viz také

[Doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md)