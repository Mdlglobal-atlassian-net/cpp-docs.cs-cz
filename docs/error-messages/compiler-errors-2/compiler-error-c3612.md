---
title: "C3612 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3612
dev_langs: C++
helpviewer_keywords: C3612
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b4cb0ecfbff311878137ea0c80f53388900ba7cf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3612"></a>C3612 chyby kompilátoru
'type': zapečetěné třídy nemohou být abstraktní.  
  
Typy, které jsou definované za použití `value` jsou zapečetěné ve výchozím nastavení, a pokud se implementuje všechny metody třídy base je abstraktní třídu. Zapečetěné abstraktní třída může být ani základní třídu ani může být vytvořena.  
  
Další informace najdete v tématu [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md).  
  
## <a name="example"></a>Příklad  
Následující ukázka generuje C3612:  
  
```  
// C3612.cpp  
// compile with: /clr /c  
value struct V: public System::ICloneable {};   // C3612  
  
// OK  
value struct V2: public System::ICloneable {  
   Object^ Clone();  
};  
```