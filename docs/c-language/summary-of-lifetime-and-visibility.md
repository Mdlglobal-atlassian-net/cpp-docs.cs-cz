---
title: Souhrn doby platnosti a viditelnosti
ms.date: 11/04/2016
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
ms.openlocfilehash: f364c3c0b558c00e3d411ab5b697ed01ec395cbd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299075"
---
# <a name="summary-of-lifetime-and-visibility"></a>Souhrn doby platnosti a viditelnosti

Následující tabulka představuje souhrn vlastností životnosti a viditelnosti pro většinu identifikátorů. První tři sloupce poskytují atributy, které definují životnost a viditelnost. Identifikátor s atributy, které jsou zadány v prvních třech sloupcích, má životnost a viditelnost zobrazených ve čtvrtém a pátém sloupci. Tabulka ale nepokrývá všechny možné případy. Další informace najdete v tématu [třídy úložiště](../c-language/c-storage-classes.md) .

### <a name="summary-of-lifetime-and-visibility"></a>Souhrn doby platnosti a viditelnosti

|Atributy:<br /><br /> Úroveň|Položka|Třída úložiště<br /><br /> Specifikátor|Result:<br /><br /> Doba platnosti|Viditelnost|
|---------------------------|----------|----------------------------------|--------------------------|----------------|
|Rozsah souboru|Definice proměnné|**static**|Globální|Zbytek zdrojového souboru, ve kterém se vyskytuje|
||Deklarace proměnné|**extern**|Globální|Zbytek zdrojového souboru, ve kterém se vyskytuje|
||Prototyp nebo definice funkce|**static**|Globální|Jeden zdrojový soubor|
||Prototyp funkce|**extern**|Globální|Zbytek zdrojového souboru|
|Rozsah bloku|Deklarace proměnné|**extern**|Globální|Blok|
||Definice proměnné|**static**|Globální|Blok|
||Definice proměnné|**Automatické** nebo **registrace**|Local|Blok|

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad znázorňuje bloky, vnořování a viditelnost proměnných:

### <a name="code"></a>kód

```c
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

V tomto příkladu jsou čtyři úrovně viditelnosti: externí úroveň a tři úrovně bloku. Hodnoty se vytisknou na obrazovku, jak je uvedeno v komentářích po jednotlivých příkazech.

## <a name="see-also"></a>Viz také

[Doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md)
