---
title: Určení Podmíněná kompilace A.2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d54245a2df2f38bed2674a3bb3923f8212d35459
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="a2---specifying-conditional-compilation"></a>A.2   Nastavení podmíněné kompilace
Následující příklady ilustrují použití Podmíněná kompilace pomocí makro OpenMP `_OPENMP` ([části 2.2](../../parallel/openmp/2-2-conditional-compilation.md) na stránce 8). S kompilace OpenMP `_OPENMP` makro stane definováno.  
  
```  
# ifdef _OPENMP   
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```  
  
 Definované operátor preprocesoru umožňuje více než jeden makro má být testována v jediné směrnice.  
  
```  
# if defined(_OPENMP) && defined(VERBOSE)  
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```