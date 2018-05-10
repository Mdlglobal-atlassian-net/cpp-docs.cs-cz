---
title: Operátory preprocesoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da6ff2a87007892cb5a76e7fc003e1d172056fb0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="preprocessor-operators"></a>Operátory preprocesoru
Čtyři operátory specifické pro preprocesor se používají v souvislosti s direktivou `#define` (shrnutí každého viz následující seznam). V následujících třech částech jsou popsány operátory převádějící na řetězec, převádějící na znak a vkládající token. Informace o **definované** operátor, najdete v části [#if, #elif, #else a #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).  
  
|Operátor|Akce|  
|--------------|------------|  
|[Nastavení velikosti řetězce (#) – operátor](../preprocessor/stringizing-operator-hash.md)|Způsobí, že odpovídající argument bude uzavřen v uvozovkách|  
|[Charakterizace operátoru (#@)](../preprocessor/charizing-operator-hash-at.md)|Způsobí, že odpovídající argument bude uzavřen v jednoduchých uvozovkách a bude považován za znak (specifické pro Microsoft)|  
|[Operátor vložení tokenu (#)](../preprocessor/token-pasting-operator-hash-hash.md)|Umožňuje, aby byly tokeny používané jako argumenty zřetězeny s dalšími tokeny, a tím vytvořily další tokeny|  
|[defined – operátor](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Zjednodušuje psaní složených výrazů v některých direktivách maker|  
  
## <a name="see-also"></a>Viz také  
 [Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)   
 [Předdefinovaná makra](../preprocessor/predefined-macros.md)   
 [C/C++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)