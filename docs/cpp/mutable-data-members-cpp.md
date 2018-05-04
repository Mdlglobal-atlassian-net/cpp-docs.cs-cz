---
title: Proměnlivé datové členy (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- mutable_cpp
dev_langs:
- C++
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7dd639cbf1ef076dee6e447f317533bf12dae10
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="mutable-data-members-c"></a>Proměnlivé datové členy (C++)
Toto klíčové slovo lze použít pouze na nestatické a nekonstantní datové členy třídy. Pokud je deklarovaná datový člen `mutable`, pak je možné přiřadit hodnotu do tohoto člena dat z **const** – členská funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
mutable member-variable-declaration;  
```  
  
## <a name="remarks"></a>Poznámky  
 Například následující kód se zkompiluje bez chyb, protože `m_accessCount` byl deklarován jako `mutable`, a lze jej tedy upravit pomocí `GetFlag` i v případě, že `GetFlag` je konstantní členská funkce.  
  
```  
// mutable.cpp  
class X  
{  
public:  
   bool GetFlag() const  
   {  
      m_accessCount++;  
      return m_flag;  
   }  
private:  
   bool m_flag;  
   mutable int m_accessCount;  
};  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)