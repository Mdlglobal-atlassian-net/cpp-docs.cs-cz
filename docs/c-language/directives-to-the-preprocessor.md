---
title: Direktivy pro preprocesor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 764bfd086612a10076e5c4800768b7b850ddbc7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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