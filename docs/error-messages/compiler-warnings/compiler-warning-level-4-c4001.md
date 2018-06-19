---
title: Kompilátoru (úroveň 4) upozornění C4001 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4001
dev_langs:
- C++
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc728fa5c66fb4b42c8fe4a785f36048ffbaed4e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292656"
---
# <a name="compiler-warning-level-4-c4001"></a>C4001 kompilátoru upozornění (úroveň 4)
byl použit nestandardní rozšíření 'komentář jeden řádek.  

> [!NOTE] 
> Toto upozornění se v aplikaci Visual Studio 2017 verze 15,5 odebrat, protože jeden řádek komentáře jsou standardní ve C99.
  
 Jeden řádek komentáře jsou standard v jazyce C++ a standardní ve C počínaje C99. V části striktní kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), C soubory, které obsahují jeden řádek komentáře generovat C4001 z důvodu nestandardní rozšíření. Vzhledem k tomu, že jeden řádek komentáře jsou standardní v jazyce C++, C soubory obsahující jeden řádek komentáře nevedou C4001 při kompilaci s rozšíření Microsoft (/Ze).  
  
## <a name="example"></a>Příklad  
 Chcete-li zakázat upozornění, zrušte komentář u [#pragma warning(disable:4001)](../../preprocessor/warning.md).  
  
```  
// C4001.cpp  
// compile with: /W4 /Za /TC  
// #pragma warning(disable:4001)  
int main()  
{  
   // single-line comment in main  
   // C4001  
}  
```