---
title: reinterpret_cast – operátor | Dokumentace Microsoftu
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
ms.openlocfilehash: 18a7cdd80c1d7b6b17a988d8f3581c7757f69823
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947606"
---
# <a name="reinterpretcast-operator"></a>reinterpret_cast – operátor
Umožňuje převod všech ukazatelů na jiný typ ukazatele. Umožňuje také převést libovolný integrální typ na libovolný typ ukazatele a naopak.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
reinterpret_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>Poznámky  
 Zneužití **reinterpret_cast** operátor může být snadno nebezpečné. Pokud není požadovaný převod ze své podstaty nižší úrovně, měly by být použity ostatní operátory přetypování.  
  
 **Reinterpret_cast** lze použít operátor pro převody, jako `char*` k `int*`, nebo `One_class*` k `Unrelated_class*`, které jsou ze své podstaty nebezpečné.  
  
 Výsledek **reinterpret_cast** nelze bezpečně používat pro nic jiného než zpětné přetypování do původního stavu. Jiná použití jsou v nejlepším případě nepřenositelná.  
  
 **Reinterpret_cast** operátor nemůže přetypovat **const**, **volatile**, nebo **__unaligned** atributy. Zobrazit [operátor const_cast](../cpp/const-cast-operator.md) informace o odebírání těchto atributů.  
  
 **Reinterpret_cast** operátor převede hodnotu ukazatele null na hodnotu ukazatele null cílového typu.  
  
 Jedno praktické použití **reinterpret_cast** je ve funkci hash, která mapuje hodnotu na index takovým způsobem, že dvě odlišné hodnoty zřídkakdy skončí se stejným indexem.  
  
```cpp 
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
  
 **Reinterpret_cast** umožňuje zacházet jako s integrálním typem ukazatele. Výsledek je následně bitově posunutý a je na něj použita logická funkce XOR, aby se vytvořil jedinečný index (jedinečný s vysokým stupněm pravděpodobnosti). Index je následně zkrácen standardem přetypování ve stylu jazyka C na návratový typ funkce.  
  
## <a name="see-also"></a>Viz také  
 [Operátory přetypování](../cpp/casting-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)