---
title: TypeName | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- typename_cpp
dev_langs:
- C++
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6eebf038fbe3e5e18e3f2a1e8e7a2aa2554bf41
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="typename"></a>typename
V definicích šablony poskytuje nápovědu pro kompilátor, je neznámý identifikátor typu. Seznamy parametrů šablony se používá pro určení typu parametru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
typename identifier;  
```  
  
## <a name="remarks"></a>Poznámky  
 This – klíčové slovo musíte použít, pokud je název v definici šablony kvalifikovaný název, který závisí na šablonu argumentu; zadání je volitelné Pokud kvalifikovaný název není závislá. Další informace najdete v tématu [rozlišení šablon a názvů](../cpp/templates-and-name-resolution.md).  
  
 **TypeName** mohou být využívána libovolného typu kdekoli v šabloně deklarace a definice. Není povoleno v seznamu základních tříd, nejde-li o argument šablony základní třídy šablony.  
  
```  
template <class T>  
class C1 : typename T::InnerType // Error - typename not allowed.  
{};  
template <class T>  
class C2 : A<typename T::InnerType>  // typename OK.  
{};  
```  
  
 **Typename** – klíčové slovo lze také místě **třída** v parametru šablony zobrazí. Například následující příkazy jsou sémanticky ekvivalentní:  
  
```  
template<class T1, class T2>...  
template<typename T1, typename T2>...  
```  
  
## <a name="example"></a>Příklad  
  
```  
// typename.cpp  
template<class T> class X  
{  
   typename T::Y m_y;   // treat Y as a type  
};  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Šablony](../cpp/templates-cpp.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)