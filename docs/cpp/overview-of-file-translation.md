---
title: "Přehled posunutí souboru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- file translation [C++], about file translation
- translation [C++]
- translation phases
- files [C++], translation
- programs [C++], lexical conventions of
- preprocessing translation phase
ms.assetid: 5036c7b7-ccff-4e2c-b052-a9ea6c71af87
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a088d2da30aa77f477f3f6e5064b6b98170e953b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-file-translation"></a>Přehled posunutí souboru
Programy jazyka C++ se stejně jako programy jazyka C skládají z jednoho nebo více souborů. Každý z těchto souborů je přeložen v následujícím konceptuálním pořadí (skutečné pořadí následuje pravidlo „jako kdyby“: překlad musí nastat, jako kdyby byly následovány tyto kroky):  
  
1.  Lexikální tokenizace. Mapování znaků a zpracování trigraph, spojování řádků a tokenizace jsou prováděny v této fázi překladu.  
  
2.  Předběžné zpracování. Tato fáze překladu přináší v pomocnou zdrojové soubory, které odkazuje `#include` direktivy, zpracovává "nastavení velikosti řetězce" a "charakterizace" direktivy a provádí vložení a makro rozšíření tokenu (najdete v části [direktivy pro preprocesor](../preprocessor/preprocessor-directives.md) v *preprocesor odkaz* informace). Výsledkem fáze předběžného zpracování je sekvence tokenů, které společně definují „jednotku překladu“.  
  
     Preprocesor – direktivy vždy začínají znakem čísla (**#**) znak (tedy první znak neprázdný na řádek musí být znaménko čísla). Na daném řádku se může objevit pouze jedna direktiva preprocesoru. Příklad:  
  
    ```  
    #include <iostream>  // Include text of iostream in   
                         //  translation unit.  
    #define NDEBUG       // Define NDEBUG (NDEBUG contains empty   
                         //  text string).  
    ```  
  
3.  Generování kódu. Tato fáze překladu používá tokeny, které jsou vygenerovány ve fázi předběžného zpracování k vygenerování kódu objektu.  
  
     V této fázi se provádí syntaktická a sémantická kontrola zdrojového kódu.  
  
 V tématu [fáze překladu](../preprocessor/phases-of-translation.md) v *preprocesor odkaz* Další informace.  
  
 Preprocesor jazyka C++ je přísnou nadmnožinou preprocesoru standardu ANSI jazyka C, ale preprocesor jazyka C++ se v několika málo případech liší. Následující seznam popisuje několik rozdílů mezi preprocesory standardu ANSI jazyka C a jazyka C++:  
  
-   Jsou podporovány jednořádkové komentáře. V tématu [komentáře](../cpp/comments-cpp.md) Další informace.  
  
-   Jedno předdefinované makro **__cplusplus**, je určená jenom pro C++. V tématu [předdefinovaná makra](../preprocessor/predefined-macros.md) v *preprocesor odkaz* Další informace.  
  
-   Preprocesor C nerozpoznává operátory jazyka C++: **.\*** ,  **-> \*** , a `::`. V tématu [operátory](../cpp/cpp-built-in-operators-precedence-and-associativity.md) a [výrazy](../cpp/expressions-cpp.md), další informace o operátory.  
  
## <a name="see-also"></a>Viz také  
 [Lexikální konvence](../cpp/lexical-conventions.md)