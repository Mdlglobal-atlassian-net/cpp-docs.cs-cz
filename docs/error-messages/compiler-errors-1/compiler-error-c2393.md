---
title: "C2393 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2393
dev_langs: C++
helpviewer_keywords: C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2c4f8d31fb6ddb6eaa9472dc7537edbcdc29054
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2393"></a>C2393 chyby kompilátoru
'symbol': symbol na appdomain nelze přidělit v segmentu, segmentu.  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 Použití [appdomain](../../cpp/appdomain.md) proměnné znamená, že jsou kompilujete s **/CLR: pure** nebo **/CLR: safe**, a bezpečné nebo čisté bitové kopie nemůže obsahovat segmenty data.  
  
 V tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2393.  
  
```  
// C2393.cpp  
// compile with: /clr:pure /c  
#pragma data_seg("myseg")  
int n = 0;   // C2393  
```