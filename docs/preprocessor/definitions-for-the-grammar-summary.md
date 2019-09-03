---
title: Definice shrnutí gramatiky
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
ms.openlocfilehash: 93cf6ffc5daf53a106c9f15a2289e2b52739d72f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222421"
---
# <a name="definitions-for-the-grammar-summary"></a>Definice shrnutí gramatiky

Terminály jsou koncové body v definici syntaxe. Žádné jiné řešení není možné. Terminály obsahují sadu vyhrazených slov a uživatelské identifikátory.

Neterminály jsou zástupné symboly v syntaxi. Většina je definována jinde v tomto souhrnu syntaxe. Definice mohou být rekurzivní. Následující neterminály jsou definovány v části [lexikální konvence](../cpp/lexical-conventions.md) v  *C++ referenční příručce jazyka*:

*konstanta*, *konstantní výraz*, *identifikátor*, *klíčové slovo*, *operátor*, *punctuator*

Volitelná součást je označena jako volitelná. <sub></sub> Následuje příklad označující volitelný výraz uzavřený do složených závorek:

**{** *Expression*<sub>opt</sub> **}**

## <a name="see-also"></a>Viz také:

[Souhrn gramatiky (CC++/)](../preprocessor/grammar-summary-c-cpp.md)
