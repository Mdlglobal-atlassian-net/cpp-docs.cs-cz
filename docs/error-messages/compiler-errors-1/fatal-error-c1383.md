---
title: "Závažná chyba C1383 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1383
dev_langs:
- C++
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24e9d7652c96c84f94bafbf2c808f2e5430037b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1383"></a>Závažná chyba C1383
– možnost kompilátoru /GL není kompatibilní s nainstalovanou verzí common language runtime  
  
 C1383 dojde, pokud používáte předchozí verzi modulu CLR s novější kompilátoru a když kompilujete s **/CLR** a **/GL.**  
  
 Pokud chcete vyřešit, buď nepoužívejte **/GL** s **/CLR** nebo nainstalujte verzi modulu CLR, který se dodává s vaší kompilátoru.  
  
 Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).