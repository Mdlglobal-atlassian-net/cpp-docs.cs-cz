---
title: Direktivy pro preprocesor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 711e28a569cefbb500a98ab33cd22c527a5fd7c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="directives-to-the-preprocessor"></a>Direktivy pro preprocesor
„Direktiva“ dává pokyn preprocesoru jazyka C k provedení konkrétní akce týkající se textu programu před kompilací. [Preprocesor – direktivy](../preprocessor/preprocessor-directives.md) jsou podrobně popsán v *preprocesor odkaz*. V tomto příkladu je použita direktiva preprocesoru `#define`:  
  
```  
#define MAX 100  
```  
  
 Tento příkaz sděluje kompilátoru, že před kompilací je třeba všechny výskyty `MAX` nahradit `100`. Mezi direktivy preprocesoru kompilátoru jazyka C patří:  
  
|#define – direktiva|#endif – direktiva|#ifdef|#line – direktiva|  
|--------------|-------------|-------------|------------|  
|`#elif`|`#error`|**#ifndef**|**#pragma**|  
|`#else`|`#if`|`#include`|`#undef`|  
  
## <a name="see-also"></a>Viz také  
 [Zdrojové soubory a zdrojové programy](../c-language/source-files-and-source-programs.md)