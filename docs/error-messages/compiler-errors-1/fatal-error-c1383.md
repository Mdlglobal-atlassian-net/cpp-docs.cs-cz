---
title: "Závažná chyba C1383 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1383
dev_langs: C++
helpviewer_keywords: C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ff620211470e82cd53a893bdee94fb1ca5d405c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1383"></a>Závažná chyba C1383
– možnost kompilátoru /GL není kompatibilní s nainstalovanou verzí common language runtime  
  
 C1383 dojde, pokud používáte předchozí verzi modulu CLR s novější kompilátoru a když kompilujete s **/CLR** a **/GL.**  
  
 Pokud chcete vyřešit, buď nepoužívejte **/GL** s **/CLR** nebo nainstalujte verzi modulu CLR, který se dodává s vaší kompilátoru.  
  
 Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).