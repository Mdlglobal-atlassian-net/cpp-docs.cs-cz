---
title: Přehled posunutí souboru
ms.date: 11/04/2016
helpviewer_keywords:
- file translation [C++], about file translation
- translation [C++]
- translation phases
- files [C++], translation
- programs [C++], lexical conventions of
- preprocessing translation phase
ms.assetid: 5036c7b7-ccff-4e2c-b052-a9ea6c71af87
ms.openlocfilehash: cb8a8fea2411e4eb7de78545f70021f3617b0f52
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442858"
---
# <a name="overview-of-file-translation"></a>Přehled posunutí souboru

Programy jazyka C++ se stejně jako programy jazyka C skládají z jednoho nebo více souborů. Každý z těchto souborů je přeložen v následujícím konceptuálním pořadí (skutečné pořadí následuje pravidlo „jako kdyby“: překlad musí nastat, jako kdyby byly následovány tyto kroky):

1. Lexikální tokenizace. Mapování znaků a zpracování trigraph, spojování řádků a tokenizace jsou prováděny v této fázi překladu.

1. Předběžné zpracování. Tato fáze překladu přináší přidružené zdrojové soubory odkazované `#include` direktivy, zpracovává "převádějící na řetězec" a "charakterizace" direktivy a provádí tokenu vložení a rozšíření maker (viz [direktivy preprocesoru](../preprocessor/preprocessor-directives.md) v *odkazu preprocesoru* Další informace). Výsledkem fáze předběžného zpracování je sekvence tokenů, které společně definují „jednotku překladu“.

   Direktivy preprocesoru vždy začínají znakem čísla (**#**) znaků (to znamená, že první neprázdný znak na řádku musí být znak čísla). Na daném řádku se může objevit pouze jedna direktiva preprocesoru. Příklad:

    ```cpp
    #include <iostream>  // Include text of iostream in
                         //  translation unit.
    #define NDEBUG       // Define NDEBUG (NDEBUG contains empty
                         //  text string).
    ```

1. Generování kódu. Tato fáze překladu používá tokeny, které jsou vygenerovány ve fázi předběžného zpracování k vygenerování kódu objektu.

   V této fázi se provádí syntaktická a sémantická kontrola zdrojového kódu.

Zobrazit [fáze překladu](../preprocessor/phases-of-translation.md) v *odkazu preprocesoru* Další informace.

Preprocesor jazyka C++ je přísnou nadmnožinou preprocesoru standardu ANSI jazyka C, ale preprocesor jazyka C++ se v několika málo případech liší. Následující seznam popisuje několik rozdílů mezi preprocesory standardu ANSI jazyka C a jazyka C++:

- Jsou podporovány jednořádkové komentáře. Zobrazit [komentáře](../cpp/comments-cpp.md) Další informace.

- Jedno předdefinované makro `__cplusplus`, je určená jenom pro C++. Zobrazit [předdefinovaná makra](../preprocessor/predefined-macros.md) v *odkazu preprocesoru* Další informace.

- Preprocesor C nerozpozná operátorů jazyka C++: **.** <strong>\*</strong>, **->** <strong>\*</strong>, a **::**. Zobrazit [operátory](../cpp/cpp-built-in-operators-precedence-and-associativity.md) a [výrazy](../cpp/expressions-cpp.md), další informace o operátorech.

## <a name="see-also"></a>Viz také:

[Lexikální konvence](../cpp/lexical-conventions.md)
