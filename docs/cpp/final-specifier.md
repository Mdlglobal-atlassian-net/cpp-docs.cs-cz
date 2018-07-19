---
title: final – specifikátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- final_CPP
dev_langs:
- C++
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 594bc432cb12b63c76172b06ee078d5b0f72de55
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947493"
---
# <a name="final-specifier"></a>final – specifikátor
Můžete použít **konečné** – klíčové slovo pro označení virtuálních funkcí, které nelze přepsat v odvozené třídě. Lze jej také použít k označení tříd, ze kterých nelze dědit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
function-declaration final;  
class class-name final base-classes  
```  
  
## <a name="remarks"></a>Poznámky  
 **poslední** je kontextový a má zvláštní význam, jen když se používá po deklaraci funkce nebo názvu třídy, jinak, to není rezervované klíčové slovo.  
  
 Když **konečné** se používá v deklaracích třídy `base-classes` volitelnou částí deklarace.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu **konečné** – klíčové slovo k určení toho, že virtuální funkci nelze přepsat.  
  
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
  
 Informace o tom, jak určit, že můžete členské funkce přepsat, naleznete v tématu [specifikátor override](../cpp/override-specifier.md).  
  
 Následující příklad používá **konečné** – klíčové slovo k určení, zda třídu nelze zdědit.  
  
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
 [klíčová slova](../cpp/keywords-cpp.md)   
 [override – specifikátor](../cpp/override-specifier.md)