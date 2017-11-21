---
title: "C3227 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3227
dev_langs: C++
helpviewer_keywords: C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2f65791d709b5790144cd919bf06b61fd94da973
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3227"></a>C3227 chyby kompilátoru
'parametr': '– klíčové slovo' nelze použít k přidělení obecného typu  
  
 Aby bylo možné vytvořit instanci typu, je vyžadován odpovídající konstruktor. Kompilátor však není možné zajistit, že je k dispozici odpovídající konstruktor.  
  
 Šablony můžete použít místo obecné typy Pokud chcete tuto chybu vyřešit, nebo můžete několika metod k vytvoření instance typu.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3227.  
  
```  
// C3227.cpp  
// compile with: /clr /c  
generic<class T> interface class ICreate {  
   static T Create();  
};  
  
generic <class T>  
where T : ICreate<T>  
ref class C {  
   void f() {  
      T t = new T;   // C3227  
  
      // OK  
      T t2 = ICreate<T>::Create();  
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );  
   }  
};  
```