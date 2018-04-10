---
title: __super | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- __super_cpp
dev_langs:
- C++
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93585337ae34e7c95d1c11b0a970afc8b36987bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="super"></a>__super
**Konkrétní Microsoft**  
  
 Umožňuje explicitně uvést, že je pro funkci, u které je prováděno přetížení, volána implementace základní funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
__super::  
member_function  
();  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Všechny dostupné metody základní třídy jsou ve fázi řešení přetížení zváženy a funkce, jež poskytne nejlepší výsledek, je ta, která je volána.  
  
 `__super` může být použit pouze v rámci těla členské funkce.  
  
 `__super` nelze použít s deklarací using. V tématu [pomocí deklarace](../cpp/using-declaration.md) Další informace.  
  
 Se zavedením [atributy](../windows/cpp-attributes-reference.md) který vložení kódu, kód může obsahovat jeden nebo více základní třídy, jejichž názvy nemusí vědět, ale které obsahují metody, které chcete volat.  
  
## <a name="example"></a>Příklad  
  
```  
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
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)