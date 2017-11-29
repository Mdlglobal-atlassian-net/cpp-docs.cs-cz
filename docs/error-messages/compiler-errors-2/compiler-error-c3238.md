---
title: "C3238 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3238
dev_langs: C++
helpviewer_keywords: C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 51af2859cec319678f6b13caf7231a8f62a6177c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3238"></a>C3238 chyby kompilátoru
'type': typ s tímto názvem již byla předána do sestavení 'assembly.  
  
 Typ byl definován v aplikaci klienta, který je rovněž definovaný prostřednictvím typu předávání syntaxe v odkazované sestavení. Oba typy nemůže být definován v oboru aplikace.  
  
 V tématu [předávání typu (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří sestavení, které obsahuje typ, který byl předávány z jiného sestavení.  
  
```  
// C3238.cpp  
// compile with: /clr /LD  
public ref class R {};  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří sestavení, která obsahuje definici tohoto typu, ale ne jenom obsahuje typ předávání syntaxe.  
  
```  
// C3238_b.cpp  
// compile with: /clr /LD  
#using "C3238.dll"  
[ assembly:TypeForwardedTo(R::typeid) ];  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3238.  
  
```  
// C3238_c.cpp  
// compile with: /clr /c  
// C3238 expected  
// Delete the following line to resolve.  
#using "C3238_b.dll"  
public ref class R {};  
```