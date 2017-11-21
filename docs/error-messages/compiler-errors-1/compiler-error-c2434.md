---
title: "C2434 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2434
dev_langs: C++
helpviewer_keywords: C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 954ef1f8db47c5cd9c420e8099cc3060ebb8a32b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2434"></a>C2434 chyby kompilátoru
'symbol': symbol deklarovat s __declspec(process) nelze inicializovat dynamicky v/CLR: pure režimu  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 Není možné dynamicky inicializovat proměnnou na proces pod **/CLR: pure**. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [proces](../../cpp/process.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2434.  
  
```  
// C2434.cpp  
// compile with: /clr:pure /c  
int f() { return 0; }  
__declspec(process) int i = f();   // C2434  
__declspec(process) int i2 = 0;   // OK  
```