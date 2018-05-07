---
title: Závažná chyba C1383 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1383
dev_langs:
- C++
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae5e16959597e16f25320778be4d4b45ca5950e0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1383"></a>Závažná chyba C1383
– možnost kompilátoru /GL není kompatibilní s nainstalovanou verzí common language runtime  
  
 C1383 dojde, pokud používáte předchozí verzi modulu CLR s novější kompilátoru a když kompilujete s **/CLR** a **/GL.**  
  
 Pokud chcete vyřešit, buď nepoužívejte **/GL** s **/CLR** nebo nainstalujte verzi modulu CLR, který se dodává s vaší kompilátoru.  
  
 Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).