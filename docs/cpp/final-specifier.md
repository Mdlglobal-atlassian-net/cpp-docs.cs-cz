---
title: "final – specifikátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: final_CPP
dev_langs: C++
helpviewer_keywords: final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a3f7c5afd4010983ea943193b7abfb99f22eda38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="final-specifier"></a>final – specifikátor
Klíčové slovo `final` lze použít pro označení virtuálních funkcí, které nelze v odvozené třídě přepsat. Lze jej také použít k označení tříd, ze kterých nelze dědit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
function-declaration final;  
```  
  
```  
  
class class-name final base-classes  
```  
  
## <a name="remarks"></a>Poznámky  
 `final` je kontextové klíčové slovo a má zvláštní význam pouze v případě, že se používá po deklaraci funkce nebo názvu třídy, v ostatních případech to není rezervované klíčové slovo.  
  
 Když je klíčové slovo `final` použito v deklaracích třídy, je `base-classes` volitelnou částí deklarace.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je klíčové slovo `final` použito pro určení toho, že virtuální funkci nelze přepsat.  
  
```cpp  
class BaseClass  
{  
    virtual void func() final;  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void func(); // compiler error: attempting to   
                         // override a final function  
};  
```  
  
 Informace o tom, jak určit, že je možné přepsat členské funkce najdete v tématu [override – specifikátor](../cpp/override-specifier.md).  
  
 Následující příklad používá klíčové slovo `final` k určení toho, že ze třídy nelze dědit.  
  
```cpp  
class BaseClass final   
{  
};  
  
class DerivedClass: public BaseClass // compiler error: BaseClass is   
                                     // marked as non-inheritable  
{  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [override – specifikátor](../cpp/override-specifier.md)