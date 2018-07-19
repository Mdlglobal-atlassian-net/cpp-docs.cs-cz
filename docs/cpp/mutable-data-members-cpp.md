---
title: Proměnlivé datové členy (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 65d2fc42021a01a1260b57f9516e53c439c8e604
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947704"
---
# <a name="mutable-data-members-c"></a>Proměnlivé datové členy (C++)
Toto klíčové slovo lze použít pouze na nestatické a nekonstantní datové členy třídy. Pokud je datový člen deklarován **proměnlivé**, je pro přiřazení k tomuto datovému členu z hodnoty **const** členskou funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
mutable member-variable-declaration;  
```  
  
## <a name="remarks"></a>Poznámky  
 Například následující kód se zkompiluje bez chyb protože `m_accessCount` byl deklarován jako **proměnlivé**a proto je možné upravovat prostřednictvím `GetFlag` i v případě, `GetFlag` je konstantní členskou funkci.  
  
```cpp 
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