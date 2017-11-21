---
title: "C4394 upozornění kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4394
dev_langs: C++
helpviewer_keywords: C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5b201b95a2ec9d43c904de35ca581efbf31b7526
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4394"></a>C4394 upozornění kompilátoru
'function': symbol na appdomain by nemělo být označené jako __declspec(dllexport)  
  
 Označené jako funkci [appdomain](../../cpp/appdomain.md) `__declspec` modifikátor kompiluje MSIL (ne na nativní) a export tabulek ([exportovat](../../windows/export.md) `__declspec` modifikátor) nejsou podporovány pro spravované funkce.  
  
 Je možné deklarovat spravované funkce, která se mají veřejnou dostupnost. Další informace najdete v tématu [zadejte viditelnost](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) a [viditelnost členů](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).  
  
 C4394 je vždy vydané jako chyba.  Toto upozornění se můžete vypnout `#pragma warning` nebo **/wd**; najdete v části [upozornění](../../preprocessor/warning.md) nebo [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, nebo jsme /wo, /Wv, wdn (úroveň upozornění)](../../build/reference/compiler-option-warning-level.md)Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4394.  
  
```  
// C4394.cpp  
// compile with: /clr /c  
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394  
__declspec(dllexport) int g2 = 0;   // OK  
```