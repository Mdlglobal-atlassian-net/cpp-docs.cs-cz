---
title: Manipulátory výstupního datového proudu s jedním argumentem (int nebo long)
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: e093512af2741329c58db0b613453f3388bacdf2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530986"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipulátory výstupního datového proudu s jedním argumentem (int nebo long)

Iostream – knihovna tříd poskytuje sadu makra pro vytváření parametrizovaných manipulátory. Manipulátory s jedním **int** nebo **dlouhé** argument představují zvláštní případ. K vytvoření manipulátor datového proudu výstupu, která přijímá jeden **int** nebo **dlouhé** argument (jako je `setw`), je nutné použít _Smanip makra, která je definována v \<iomanip >. Tento příklad definuje `fillblank` manipulátor, který se vkládá zadaný počet prázdných hodnot do datového proudu:

## <a name="example"></a>Příklad

```cpp
// output_stream_manip.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

void fb( ios_base& os, int l )
{
   ostream *pos = dynamic_cast<ostream*>(&os);
   if (pos)
   {
      for( int i=0; i < l; i++ )
      (*pos) << ' ';
   };
}

_Smanip<int>
   __cdecl fillblank(int no)
   {
   return (_Smanip<int>(&fb, no));
   }

int main( )
{
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";
}
```

## <a name="see-also"></a>Viz také:

[Vlastní manipulátory s argumenty](../standard-library/custom-manipulators-with-arguments.md)<br/>
