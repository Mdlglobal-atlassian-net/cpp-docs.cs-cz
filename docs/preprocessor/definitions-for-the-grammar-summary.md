---
title: Definice souhrnu gramatiky | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- preprocessor, definitions
- preprocessor
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 36ce8a4f1bf6e4c5e9c79298899c871c74c1707b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="definitions-for-the-grammar-summary"></a>Definice souhrnu gramatiky
Terminály jsou koncové body v definici syntaxe. Žádné jiné řešení není možné. Terminály obsahují sadu vyhrazených slov a uživatelské identifikátory.  
  
Neterminály jsou zástupné symboly v syntaxi. Většina je definována jinde v tomto souhrnu syntaxe. Definice mohou být rekurzivní. Následující terminálově nezávislých jsou definovány v [lexikální pravidla](../cpp/lexical-conventions.md) části *referenční příručka jazyka C++*:  
  
`constant`, *konstantní výraz*, *identifikátor*, *– klíčové slovo*, `operator`,`punctuator`  
  
Volitelná součást je označena zkratkou opt. Následuje příklad označující volitelný výraz uzavřený do složených závorek:  
  
**{** *výraz*opt **}**  
  
## <a name="see-also"></a>Viz také  
[Gramatický souhrn (C/C++)](../preprocessor/grammar-summary-c-cpp.md)