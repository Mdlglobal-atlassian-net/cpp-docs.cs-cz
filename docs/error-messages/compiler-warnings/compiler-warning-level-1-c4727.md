---
title: "Kompilátoru (úroveň 1) upozornění C4727 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4727
dev_langs:
- C++
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 813c2ab18cc81c4477ae094e6c2aa771e3135b7a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4727"></a>C4727 kompilátoru upozornění (úroveň 1)
"PCH s názvem pch_file se stejnou časové razítko v obj_file_1 a obj_file_2 nalezen.  Pomocí prvního PCH.  
  
 C4727 nastane při kompilaci více souborech určených ke kompilaci s **/Yc**, a kde bylo možné označit všechny soubory .obj s stejné časové razítko .pch kompilátoru.  
  
 Vyřešíte zkompilovat jeden zdrojový soubor s **/Yc /c** (vytvoří pch), a ostatní zkompilujte samostatně s **/Yu /c** (používá pch), propojte je společně.  
  
 Pokud tedy nebyla následující a generuje C4727:  
  
 **cl/CLR /GL a.cpp b.cpp c.cpp /Ycstdafx.h**  
  
 Je by provést následující místo:  
  
 **cl/CLR /GL a.cpp /Ycstdafx.h /c**  
  
 **cl/CLR /GL b.cpp c.cpp /Yustdafx.h/Link a.obj**  
  
 Další informace naleznete v tématu  
  
-   [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md)  
  
-   [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md)