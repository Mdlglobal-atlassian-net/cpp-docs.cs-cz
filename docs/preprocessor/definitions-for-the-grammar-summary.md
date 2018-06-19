---
title: Definice souhrnu gramatiky | Microsoft Docs
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
ms.openlocfilehash: 6d6c84354332b4d01ca07f672024fe9b488cd0a2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840064"
---
# <a name="definitions-for-the-grammar-summary"></a>Definice souhrnu gramatiky
Terminály jsou koncové body v definici syntaxe. Žádné jiné řešení není možné. Terminály obsahují sadu vyhrazených slov a uživatelské identifikátory.  
  
Neterminály jsou zástupné symboly v syntaxi. Většina je definována jinde v tomto souhrnu syntaxe. Definice mohou být rekurzivní. Následující terminálově nezávislých jsou definovány v [lexikální pravidla](../cpp/lexical-conventions.md) části *referenční příručka jazyka C++*:  
  
`constant`, *konstantní výraz*, *identifikátor*, *– klíčové slovo*, `operator`, `punctuator`  
  
Volitelná součást je označena zkratkou opt. Následuje příklad označující volitelný výraz uzavřený do složených závorek:  
  
**{** *výraz*opt **}**  
  
## <a name="see-also"></a>Viz také  
[Gramatický souhrn (C/C++)](../preprocessor/grammar-summary-c-cpp.md)