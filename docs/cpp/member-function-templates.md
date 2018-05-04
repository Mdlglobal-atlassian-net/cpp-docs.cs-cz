---
title: Šablony členských funkcí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function templates, member functions
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb7eeed732f8d9e69dd2571b69cf1c7247a38991
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="member-function-templates"></a>Šablony členských funkcí

Výraz šablona členu odkazuje na šablony členské funkce a šablony vnořené třídy. Šablony členské funkce jsou funkcemi šablony, které jsou členy třídy nebo šablony třídy.  
  
 Členské funkce mohou být šablonami funkce v několika kontextech. Všechny funkce šablon třídy jsou obecné, ale nejsou uvedeny jako šablony členu nebo šablony členské funkce. Pokud tyto členské funkce přijímají své vlastní argumenty šablon, jsou považovány za šablony členské funkce.  
  
## <a name="example"></a>Příklad

 Šablony členské funkce nešablonových nebo šablonových tříd jsou deklarovány jako šablony funkce s jejich parametry šablony.  
  
```cpp
// member_function_templates.cpp  
struct X  
{  
   template <class T> void mf(T* t) {}  
};  
  
int main()  
{  
   int i;  
   X* x = new X();  
   x->mf(&i);  
}  
```  
  
## <a name="example"></a>Příklad

 Následující příklad ukazuje šablonu členské funkce třídy šablony.  
  
```cpp
// member_function_templates2.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u)  
   {  
   }  
};  
  
int main()  
{  
}  
```  
  
## <a name="example"></a>Příklad
  
```cpp
// defining_member_templates_outside_class.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u);  
};  
  
template<typename T> template <typename U>  
void X<T>::mf(const U &u)  
{  
}  
  
int main()  
{  
}  
```  
  
## <a name="example"></a>Příklad

 Místní třídy nemohou mít členské šablony.  
  
 Šablony členské funkce nemohou být virtuálními funkcemi a nemohou přepsat virtuální funkce ze základní třídy, pokud jsou deklarovány pomocí stejného názvu jako virtuální funkce základní třídy.  
  
Následující příklad ukazuje šablonované uživatelem definovaný převod:  
  
```cpp
// templated_user_defined_conversions.cpp  
template <class T>  
struct S  
{  
   template <class U> operator S<U>()  
   {  
      return S<U>();  
   }  
};  
  
int main()  
{  
   S<int> s1;  
   S<long> s2 = s1;  // Convert s1 using UDC and copy constructs S<long>.  
}  
```  
  
## <a name="see-also"></a>Viz také

 [Šablony funkcí](../cpp/function-templates.md)
