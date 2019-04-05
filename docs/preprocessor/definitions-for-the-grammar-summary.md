---
title: Definice souhrnu gramatiky
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
ms.openlocfilehash: 6e8671ba0d68b13f68db0f2b08dab4fe98f917e7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024952"
---
# <a name="definitions-for-the-grammar-summary"></a>Definice souhrnu gramatiky

Terminály jsou koncové body v definici syntaxe. Žádné jiné řešení není možné. Terminály obsahují sadu vyhrazených slov a uživatelské identifikátory.

Neterminály jsou zástupné symboly v syntaxi. Většina je definována jinde v tomto souhrnu syntaxe. Definice mohou být rekurzivní. Následující neterminály jsou definovány v [lexikální konvence](../cpp/lexical-conventions.md) část *referenční dokumentace jazyka C++*:

`constant`, *konstantní výraz*, *identifikátor*, *– klíčové slovo*, `operator`, `punctuator`

Volitelná součást je označena pomocí indexovaný <sub>optimalizované</sub>. Následuje příklad označující volitelný výraz uzavřený do složených závorek:

**{** *výraz*<sub>optimalizované</sub> **}**

## <a name="see-also"></a>Viz také:

[Gramatický souhrn (C/C++)](../preprocessor/grammar-summary-c-cpp.md)