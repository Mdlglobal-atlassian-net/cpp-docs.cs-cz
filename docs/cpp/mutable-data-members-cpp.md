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
ms.openlocfilehash: adc8f9c456d28089d57bc1f13b61ad8efa10b6b6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402917"
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
  
## <a name="see-also"></a>Viz také:  
 [Klíčová slova](../cpp/keywords-cpp.md)