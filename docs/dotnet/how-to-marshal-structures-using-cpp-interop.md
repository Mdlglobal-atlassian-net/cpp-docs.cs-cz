---
title: 'Postupy: Zařazování struktur pomocí interoperability C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Interop, structures
- structures [C++], marshaling
- data marshaling [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
ms.openlocfilehash: 93aeabc3fe984bee8a9281281320d61dccd182bf
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739394"
---
# <a name="how-to-marshal-structures-using-c-interop"></a>Postupy: Zařazování struktur pomocí interoperability C++

Toto téma popisuje jeden aspekt vzájemná funkční spolupráce jazyka Visual C++. Další informace najdete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy #pragma implementace spravovaných a nespravovaných funkcí ve stejném souboru, ale tyto funkce spolupracují stejným způsobem, pokud jsou definovány v samostatných souborech. Soubory, které obsahují pouze nespravované funkce nemusí být kompilována s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje předávání struktury ze spravované na nespravované funkci, podle hodnoty a podle reference. Vzhledem k tomu, že struktura v tomto příkladu obsahuje pouze jednoduché, vnitřní datové typy (viz [přenositelné a Non-přenositelné typy](/dotnet/framework/interop/blittable-and-non-blittable-types)), není požadováno žádné speciální zařazování. Chcete-li zařadit nepřenositelné struktury, jako jsou ty, které obsahují ukazatele, přečtěte si téma [jak: Zařazení vložených ukazatelů pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

```
// PassStruct1.cpp
// compile with: /clr

#include <stdio.h>
#include <math.h>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

struct Location {
   int x;
   int y;
};

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}

#pragma managed

int main() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   Location loc3;
   InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje podle hodnoty a podle reference předávání struktury z nespravované na spravované funkce. Vzhledem k tomu, že struktura v tomto příkladu obsahuje pouze jednoduché, vnitřní datové typy (naleznete v tématu [přenositelné a Non-přenositelné typy](/dotnet/framework/interop/blittable-and-non-blittable-types)), žádná speciální zařazování je povinný. Chcete-li zařadit nepřenositelné struktury, jako jsou ty, které obsahují ukazatele, přečtěte si téma [jak: Zařazení vložených ukazatelů pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

```
// PassStruct2.cpp
// compile with: /clr
#include <stdio.h>
#include <math.h>
using namespace System;

// native structure definition
struct Location {
   int x;
   int y;
};

#pragma managed

double GetDistance(Location loc1, Location loc2) {
   Console::Write("[managed] got loc1({0},{1})", loc1.x, loc1.y);
   Console::WriteLine(" loc2({0},{1})", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   Console::WriteLine("[managed] Initializing location...");
   lp->x = 50;
   lp->y = 50;
}

#pragma unmanaged

int UnmanagedFunc() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   printf_s("(unmanaged) loc1=(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2=(%d,%d)\n", loc2.x, loc2.y);

   double dist = GetDistance(loc1, loc2);
   printf_s("[unmanaged] distance = %f\n", dist);

   Location loc3;
   InitLocation(&loc3);
   printf_s("[unmanaged] got x=%d y=%d\n", loc3.x, loc3.y);

    return 0;
}

#pragma managed

int main() {
   UnmanagedFunc();
}
```

## <a name="see-also"></a>Viz také:

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
