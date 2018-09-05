---
title: Definice souhrnu gramatiky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c11f2f839ef806d74eae65c9fc8fe3a71cd2e9c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760809"
---
# <a name="definitions-for-the-grammar-summary"></a>Definice souhrnu gramatiky

Terminály jsou koncové body v definici syntaxe. Žádné jiné řešení není možné. Terminály obsahují sadu vyhrazených slov a uživatelské identifikátory.

Neterminály jsou zástupné symboly v syntaxi. Většina je definována jinde v tomto souhrnu syntaxe. Definice mohou být rekurzivní. Následující neterminály jsou definovány v [lexikální konvence](../cpp/lexical-conventions.md) část *referenční dokumentace jazyka C++*:

`constant`, *konstantní výraz*, *identifikátor*, *– klíčové slovo*, `operator`, `punctuator`

Volitelná součást je označena pomocí indexovaný <sub>optimalizované</sub>. Následuje příklad označující volitelný výraz uzavřený do složených závorek:

**{** *výraz*<sub>optimalizované</sub> **}**

## <a name="see-also"></a>Viz také

[Gramatický souhrn (C/C++)](../preprocessor/grammar-summary-c-cpp.md)