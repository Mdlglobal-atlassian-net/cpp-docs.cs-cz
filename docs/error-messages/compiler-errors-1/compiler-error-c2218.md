---
title: "Chyba kompilátoru C2218 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2218
dev_langs:
- C++
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cce36d9e8d4e8f2ac82ddec9a967ac7e045b4a03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2218"></a>Chyba kompilátoru C2218
'__vectorcall' nelze použít s ' / architektura: IA32.  
  
 `__vectorcall` Konvence volání je podporována pouze v nativním kódu na x86 a x64 procesorů, které obsahují Streaming SIMD Extensions 2 (SSE2) a vyšší. Další informace najdete v tématu [__vectorcall](../../cpp/vectorcall.md).  
  
 Chcete-li tuto chybu opravit, změnit možnosti kompilátoru cíl instrukcí SSE2, AVX nebo AVX2 nastaví. Další informace najdete v tématu [/arch (x86)](../../build/reference/arch-x86.md).