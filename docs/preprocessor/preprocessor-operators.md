---
title: "Operátory preprocesoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 551b2c3ba8a5055fc6b6dfd1b94c461c37e72209
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
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