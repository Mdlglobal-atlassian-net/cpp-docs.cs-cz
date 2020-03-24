---
title: reinterpret_cast – operátor
ms.date: 11/04/2016
f1_keywords:
- reinterpret_cast_cpp
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
ms.openlocfilehash: 34c2fcb0e1f7f4df4e207d1737afc9c42e011feb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188282"
---
# <a name="reinterpret_cast-operator"></a>reinterpret_cast – operátor

Umožňuje převod všech ukazatelů na jiný typ ukazatele. Umožňuje také převést libovolný integrální typ na libovolný typ ukazatele a naopak.

## <a name="syntax"></a>Syntaxe

```
reinterpret_cast < type-id > ( expression )
```

## <a name="remarks"></a>Poznámky

Zneužití operátoru **reinterpret_cast** může být snadno nebezpečné. Pokud není požadovaný převod ze své podstaty nižší úrovně, měly by být použity ostatní operátory přetypování.

Operátor **reinterpret_cast** lze použít pro převody jako `char*` na `int*`nebo `One_class*` na `Unrelated_class*`, které jsou v podstatě nebezpečné.

Výsledek **reinterpret_cast** nelze bezpečně použít pro cokoli jiného než při přetypování zpět na původní typ. Jiná použití jsou v nejlepším případě nepřenositelná.

Operátor **reinterpret_cast** nemůže přetypovat na atributy **const**, **volatile**nebo **__unaligned** . Informace o odebírání těchto atributů najdete v tématu [operátor const_cast](../cpp/const-cast-operator.md) .

Operátor **reinterpret_cast** převede hodnotu ukazatele null na hodnotu ukazatele null cílového typu.

Jedním z praktických způsobů použití **reinterpret_cast** je funkce hash, která mapuje hodnotu na index takovým způsobem, že dvě odlišné hodnoty jsou zřídka zakončené stejným indexem.

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

**Reinterpret_cast** umožňuje, aby byl ukazatel považován za integrální typ. Výsledek je následně bitově posunutý a je na něj použita logická funkce XOR, aby se vytvořil jedinečný index (jedinečný s vysokým stupněm pravděpodobnosti). Index je následně zkrácen standardem přetypování ve stylu jazyka C na návratový typ funkce.

## <a name="see-also"></a>Viz také

[Operátory přetypování](../cpp/casting-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
