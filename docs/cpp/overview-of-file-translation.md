---
title: Přehled posunutí souboru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- file translation [C++], about file translation
- translation [C++]
- translation phases
- files [C++], translation
- programs [C++], lexical conventions of
- preprocessing translation phase
ms.assetid: 5036c7b7-ccff-4e2c-b052-a9ea6c71af87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d0aa647f6f94d31f1a06bb09b143554dba51b68
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861743"
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
