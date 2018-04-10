---
title: Proměnlivé datové členy (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- mutable_cpp
dev_langs:
- C++
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a93ae14e6f630d8974163ce8295626a524b49e3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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