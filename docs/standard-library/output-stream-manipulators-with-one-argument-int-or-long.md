---
title: Manipulátory výstupního datového proudu s jedním argumentem (int nebo long)
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: 93e4de25323514eb4105814b565dc3ddc3fbb737
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453000"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipulátory výstupního datového proudu s jedním argumentem (int nebo long)

Knihovna tříd iostream – poskytuje sadu maker pro vytváření parametrizovaných manipulací. Manipulace s jedním **int** nebo dlouhým  argumentem jsou zvláštní případ. Chcete-li vytvořit výstupní datový proud manipulátor, který přijímá jeden **int** nebo **dlouhý** argument `setw`(jako), je nutné použít makro _Smanip, které je definováno \<v iomanip >. Tento příklad definuje `fillblank` manipulátor, který do datového proudu Vloží zadaný počet prázdných hodnot:

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

[Vlastní manipulátory s argumenty](../standard-library/custom-manipulators-with-arguments.md)
