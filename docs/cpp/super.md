---
title: __super | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __super_cpp
dev_langs:
- C++
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4faf0130ab34b61dc19f5ac3bd615e2e6162b616
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467378"
---
# <a name="super"></a>__super
**Specifické pro Microsoft**  
  
 Umožňuje explicitně uvést, že je pro funkci, u které je prováděno přetížení, volána implementace základní funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__super::member_function();  
```  
  
## <a name="remarks"></a>Poznámky  
 Všechny dostupné metody základní třídy jsou ve fázi řešení přetížení zváženy a funkce, jež poskytne nejlepší výsledek, je ta, která je volána.  
  
 **__super** může být použit pouze v těle členské funkce.  
  
 **__super** nelze použít pomocí deklarace. Zobrazit [using – deklarace](../cpp/using-declaration.md) Další informace.  
  
 Se zavedením [atributy](../windows/cpp-attributes-reference.md) , které vkládají kód, může kód obsahovat jednu nebo více základních tříd, jejichž názvy nemusí být známy, ale které obsahují metody, které chcete volat.  
  
## <a name="example"></a>Příklad  
  
```cpp 
// deriv_super.cpp  
// compile with: /c  
struct B1 {  
   void mf(int) {}  
};  
  
struct B2 {  
   void mf(short) {}  
  
   void mf(char) {}  
};  
  
struct D : B1, B2 {  
   void mf(short) {  
      __super::mf(1);   // Calls B1::mf(int)  
      __super::mf('s');   // Calls B2::mf(char)  
   }  
};  
```  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [Klíčová slova](../cpp/keywords-cpp.md)