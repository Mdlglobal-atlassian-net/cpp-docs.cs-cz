---
title: "C4368 upozornění kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4368
dev_langs: C++
helpviewer_keywords: C4368
ms.assetid: cb85bcee-fd3d-4aa5-b626-2324f07a4f1b
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6fd66d8fb6d30a960c659345910242ec5a1a2e11
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4368"></a>C4368 upozornění kompilátoru
nelze definovat 'člen' jako člen spravovaného 'typu': smíšené typy nejsou podporovány  
  
 Nativní datový člen nelze vložit do typu CLR.  
  
 Je však možné deklarovat ukazatel na nativní typ a řídit jeho dobu platnosti v konstruktoru, destruktoru a finalizační metodě spravované třídy. Další informace najdete v části [destruktory a finalizační metody](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
 Toto upozornění je vždy vyvoláno jako chyba. Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma zakázat C4368.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4368.  
  
```  
// C4368.cpp  
// compile with: /clr /c  
struct N {};  
ref struct O {};  
ref struct R {  
    R() : m_p( new N ) {}  
    ~R() { delete m_p; }  
  
   property N prop;   // C4368  
   int i[10];   // C4368  
  
   property O ^ prop2;   // OK  
   N * m_p;   // OK  
};  
```