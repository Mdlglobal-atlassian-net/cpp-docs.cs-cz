---
title: "C3084 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3084
dev_langs: C++
helpviewer_keywords: C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a160c807bbc8a44c8073cc66ddacad7c8a398d53
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3084"></a>C3084 chyby kompilátoru
'function': finalizační metodu/destruktor nemůže být '– klíčové slovo'  
  
 Finalizační metodu nebo destruktor byla deklarována nesprávně.  
  
 Například by nemělo destruktor označeny jako zapečetěné.  Destruktoru bude dostupná pro odvozené typy.  Další informace najdete v tématu [explicitní přepsání](../../windows/explicit-overrides-cpp-component-extensions.md) a [destruktory a finalizační metody v postupy: definování a používání tříd a struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3084.  
  
```  
// C3084.cpp  
// compile with: /clr /c  
ref struct R {  
protected:  
   !R() sealed;   // C3084  
   !R() abstract;   // C3084  
   !R();  
};  
```