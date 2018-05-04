---
title: reinterpret_cast – operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- reinterpret_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd64960469c9c4ca069611f6ebeefeaac8b29ba0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="reinterpretcast-operator"></a>reinterpret_cast – operátor
Umožňuje převod všech ukazatelů na jiný typ ukazatele. Umožňuje také převést libovolný integrální typ na libovolný typ ukazatele a naopak.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
reinterpret_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>Poznámky  
 Zneužití operátoru `reinterpret_cast` může být snadno nebezpečné. Pokud není požadovaný převod ze své podstaty nižší úrovně, měly by být použity ostatní operátory přetypování.  
  
 Pro převody, jako jsou `reinterpret_cast` na `char*` nebo `int*` na `One_class*`, které jsou ze své podstaty nebezpečné, lze použít operátor `Unrelated_class*`.  
  
 Výsledek `reinterpret_cast` nelze bezpečně používat pro nic jiného než pro zpětné přetypování do původního stavu. Jiná použití jsou v nejlepším případě nepřenositelná.  
  
 `reinterpret_cast` Operátor nelze přetypovat rychle **const**, `volatile`, nebo **__unaligned** atributy. V tématu [const_cast – operátor](../cpp/const-cast-operator.md) informace o odebrání těchto atributů.  
  
 `reinterpret_cast` Operátor převede hodnotu ukazatele null. hodnota ukazatele null typu cílový.  
  
 Jedno praktické použití `reinterpret_cast` je ve funkci hash, která mapuje hodnotu na index tak, že dvě odlišné hodnoty zřídkakdy skončí se stejným indexem.  
  
```  
#include <iostream>  
using namespace std;  
  
// Returns a hash code based on an address  
unsigned short Hash( void *p ) {  
   unsigned int val = reinterpret_cast<unsigned int>( p );  
   return ( unsigned short )( val ^ (val >> 16));  
}  
  
using namespace std;  
int main() {  
   int a[20];  
   for ( int i = 0; i < 20; i++ )  
      cout << Hash( a + i ) << endl;  
}  
  
Output:   
64641  
64645  
64889  
64893  
64881  
64885  
64873  
64877  
64865  
64869  
64857  
64861  
64849  
64853  
64841  
64845  
64833  
64837  
64825  
64829  
```  
  
 `reinterpret_cast` umožňuje zacházet s ukazatelem jako s integrálním typem. Výsledek je následně bitově posunutý a je na něj použita logická funkce XOR, aby se vytvořil jedinečný index (jedinečný s vysokým stupněm pravděpodobnosti). Index je následně zkrácen standardem přetypování ve stylu jazyka C na návratový typ funkce.  
  
## <a name="see-also"></a>Viz také  
 [Operátory přetypování](../cpp/casting-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)