---
title: Chyba kompilátoru C2218 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2218
dev_langs:
- C++
helpviewer_keywords:
- C2218
ms.assetid: b0f55da4-8edb-4b45-b298-1a091981bd7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1efda7258616862efc464b493b51ada2c6bd7674
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172208"
---
# <a name="compiler-error-c2218"></a>Chyba kompilátoru C2218
'__vectorcall' nelze použít s ' / architektura: IA32.  
  
 `__vectorcall` Konvence volání je podporována pouze v nativním kódu na x86 a x64 procesorů, které obsahují Streaming SIMD Extensions 2 (SSE2) a vyšší. Další informace najdete v tématu [__vectorcall](../../cpp/vectorcall.md).  
  
 Chcete-li tuto chybu opravit, změnit možnosti kompilátoru cíl instrukcí SSE2, AVX nebo AVX2 nastaví. Další informace najdete v tématu [/arch (x86)](../../build/reference/arch-x86.md).