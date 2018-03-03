---
title: "Vložené funkce | Microsoft Docs"
ms.custom: 
ms.date: 10/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b5adadc990bed67abe739a4d73b2973b26ca207
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="inline-functions"></a>Vložené funkce

**Konkrétní Microsoft**

Klíčové slovo `__inline` přikazuje kompilátoru nahradit kód uvnitř definice funkce pro každou instanci jejího volání. K nahrazení však dochází pouze dle rozhodnutí kompilátoru. Kompilátor například nevloží funkci, je-li její adresa použita nebo je-li pro vložení příliš velká.

Aby byla funkce považována za vhodnou k vložení, musí pro svou definici používat nový styl.

Chcete-li zadat vloženou funkci, použijte tento tvar:

> **__inline** *typ*<sub>opt</sub> *definice funkce*

Použití vložených funkcí generuje rychlejší a někdy i menší kód, než jaký generuje ekvivalentní volání funkce, a to z následujících důvodů:

- Šetří čas potřebný k provedení volání funkcí.

- Malé vložené funkce o velikost přibližně tři a méně řádků vytvoří méně kódu než ekvivalentní volání funkce, protože kompilátor negeneruje kód pro zpracování argumentů a návratové hodnoty.

- Funkce generované jako vložené jsou předmětem optimalizací kódu, které nejsou běžným funkcím dostupné, protože kompilátor neprovádí meziprocedurální optimalizace.

Funkce používající klíčové slovo `__inline` by neměly být zaměněny s vloženým kódem assembleru. V tématu [vloženého assembleru](../c-language/inline-assembler-c.md) Další informace.

**Konkrétní Microsoft END**  

## <a name="see-also"></a>Viz také

[vložené, __inline, \__forceinline](../cpp/inline-functions-cpp.md)

