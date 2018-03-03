---
title: "C3161 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3161
dev_langs:
- C++
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0cdbbd9364435ebcfad114331b6ba7289cb8010
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3161"></a>C3161 chyby kompilátoru
"rozhraní": vnoření třídy, struktury, sjednocení nebo rozhraní v rozhraní je neplatný; vnoření rozhraní ve třídě, struktura nebo sjednocení je neplatný  
  
 [__Interface](../../cpp/interface.md) může vyskytovat pouze v globálním oboru nebo v oboru názvů. Třída, struktura nebo union nelze vložit do rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3161.  
  
```  
// C3161.cpp  
// compile with: /c  
__interface X {  
   __interface Y {};   // C3161 A nested interface  
};  
```