---
title: Kompilátoru (úroveň 1) upozornění C4727 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4727
dev_langs:
- C++
helpviewer_keywords:
- C4727
ms.assetid: 991b0087-3a50-40f5-9cdb-cdc367cd472c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c92e42fe275f821e333a0f04a116034a5bb849a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282779"
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
  
-   [/Yc (vytvoření souboru předkompilované hlavičky)](../../build/reference/yc-create-precompiled-header-file.md)  
  
-   [/Yu (použití souboru předkompilované hlavičky)](../../build/reference/yu-use-precompiled-header-file.md)