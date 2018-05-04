---
title: __raise | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __raise
- __raise_cpp
dev_langs:
- C++
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93bd00c89df69d655f42c06509ef0360eff0c092
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="raise"></a>__raise
Zvýrazní stranu volání události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
__raise   
method-declarator  
;  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Ze spravovaného kódu lze událost vyvolat pouze ze třídy, ve které je definována. V tématu [událostí](../windows/event-cpp-component-extensions.md) Další informace.  
  
 Klíčové slovo `__raise` vygeneruje chybu, pokud zavoláte cokoli jiného než událost.  
  
> [!NOTE]
>  Třída šablony nebo struktura nemohou obsahovat události.  
  
## <a name="example"></a>Příklad  
  
```  
// EventHandlingRef_raise.cpp  
struct E {  
   __event void func1();  
   void func1(int) {}  
  
   void func2() {}  
  
   void b() {  
      __raise func1();  
      __raise func1(1);  // C3745: 'int Event::bar(int)':   
                         // only an event can be 'raised'  
      __raise func2();   // C3745  
   }  
};  
  
int main() {  
   E e;  
   __raise e.func1();  
   __raise e.func1(1);  // C3745  
   __raise e.func2();   // C3745  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [Zpracování událostí](../cpp/event-handling.md)   
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)