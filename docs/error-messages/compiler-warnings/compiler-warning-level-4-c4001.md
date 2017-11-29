---
title: "Kompilátoru (úroveň 4) upozornění C4001 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4001
dev_langs: C++
helpviewer_keywords: C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 808b51724ce626371c011057295d3343cc02c984
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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