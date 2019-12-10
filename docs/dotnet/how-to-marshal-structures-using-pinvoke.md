---
title: 'Postupy: Zařazení struktur pomocí služby PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
ms.openlocfilehash: fe5d2cf4804baea286827e9d5e270c10cd587b30
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988449"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>Postupy: Zařazení struktur pomocí služby PInvoke

Tento dokument vysvětluje, jak mohou být nativní funkce, které přijímají struktury ve stylu jazyka C, volány ze spravovaných funkcí pomocí volání nespravovaného kódu. I když doporučujeme použít funkce C++ spolupráce namísto volání nespravovaného kódu, protože volání nespravovaného kódu poskytuje malou dobu kompilace, není typově bezpečná a může být zdlouhavá k implementaci, pokud je NESPRAVOVANÉ rozhraní API zabaleno jako knihovna DLL a zdrojový kód není k dispozici, je P/Invoke jediná možnost. V opačném případě se podívejte na následující dokumenty:

- [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Postupy: Zařazení řetězců pomocí služby PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

Ve výchozím nastavení jsou nativní a spravované struktury v paměti rozloženy jinak, takže úspěšné předávání struktur napříč spravovaným nebo nespravovaným ohraničením vyžaduje dodatečné kroky pro zachování integrity dat.

Tento dokument vysvětluje kroky nutné k definování spravovaných ekvivalentů nativních struktur a způsobu, jakým mohou být výsledné struktury předány nespravovaným funkcím. Tento dokument předpokládá, že se používají jednoduché struktury – ty, které neobsahují řetězce nebo ukazatele –. Informace o nepřímých interakcích najdete v [tématu C++ použití zprostředkovatele komunikace (implicitní PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md). Volání nespravovaného volání nemůže mít jako návratovou hodnotu typy bez jakýchkoli přenositelné. Přenositelné typy mají stejné vyjádření ve spravovaném i nespravovaném kódu. Další informace najdete v tématu přenositelné [a nepřenositelné typy](/dotnet/framework/interop/blittable-and-non-blittable-types).

Zařazování jednoduchých, přípravných struktur v rámci spravovaného a nespravovaného ohraničení nejprve vyžaduje, aby byly definovány spravované verze každé nativní struktury. Tyto struktury můžou mít jakýkoliv právní název. neexistuje žádný vztah mezi nativní a spravovanou verzí dvou struktur kromě jejich rozvržení dat. Proto je důležité, aby spravovaná verze obsahovala pole, která mají stejnou velikost a ve stejném pořadí jako nativní verze. (Neexistuje žádný mechanismus pro zajištění, že spravované a nativní verze struktury jsou ekvivalentní, takže nekompatibility nebudou zjevné až do doby běhu. Je zodpovědností programátora, aby bylo zajištěno, že obě struktury mají stejné rozložení dat.)

Vzhledem k tomu, že členové spravovaných struktur jsou někdy znovu uspořádány pro účely výkonu, je nutné použít atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> k označení toho, že struktura je rozložena postupně. Je také vhodné explicitně nastavit nastavení balení struktury tak, aby bylo stejné jako pro použití v nativní struktuře. (I když ve výchozím nastavení C++ vizuál používá pro spravovaný kód 8 bajtů struktury.)

1. Dále použijte <xref:System.Runtime.InteropServices.DllImportAttribute> k deklaraci vstupních bodů, které odpovídají jakýmkoli nespravovaným funkcím, které přijímají strukturu, ale používají spravovanou verzi struktury v podpisech funkce, což je moot bod, pokud použijete stejný název pro obě verze struktury.

1. Spravovaný kód nyní může předat spravovanou verzi struktury nespravovaným funkcím, jako by se jednalo o skutečně spravované funkce. Tyto struktury mohou být předány buď podle hodnoty, nebo podle odkazu, jak je znázorněno v následujícím příkladu.

## <a name="example"></a>Příklad

Následující kód se skládá z nespravovaného a spravovaného modulu. Nespravovaný modul je knihovna DLL, která definuje strukturu nazvanou umístění a funkci s názvem GetDistance, která přijímá dvě instance struktury umístění. Druhým modulem je spravovaná aplikace příkazového řádku, která importuje funkci GetDistance, ale definuje ji na základě spravovaného ekvivalentu struktury umístění MLocation. V praxi se stejný název pravděpodobně používá pro obě verze struktury. Zde se však používá jiný název, který ukazuje, že prototyp DllImport je definován ve smyslu spravované verze.

Všimněte si, že žádná část knihovny DLL není k dispozici pro spravovaný kód pomocí tradiční direktivy #include. Knihovna DLL je ve skutečnosti k dispozici pouze za běhu, takže problémy s funkcemi importovanými pomocí DllImport nebudou v době kompilace zjištěny.

```cpp
// TraditionalDll3.cpp
// compile with: /LD /EHsc
#include <iostream>
#include <stdio.h>
#include <math.h>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
   #define TRADITIONALDLL_API __declspec(dllexport)
#else
   #define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct Location {
   int x;
   int y;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API double GetDistance(Location, Location);
   TRADITIONALDLL_API void InitLocation(Location*);
}

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
```

## <a name="example"></a>Příklad

```cpp
// MarshalStruct_pi.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MLocation {
   int x;
   int y;
};

value struct TraditionalDLL {
   [DllImport("TraditionalDLL3.dll")]
   static public double GetDistance(MLocation, MLocation);
   [DllImport("TraditionalDLL3.dll")]
   static public double InitLocation(MLocation*);
};

int main() {
   MLocation loc1;
   loc1.x = 0;
   loc1.y = 0;

   MLocation loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = TraditionalDLL::GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   MLocation loc3;
   TraditionalDLL::InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

```Output
[unmanaged] loc1(0,0) loc2(100,100)
[managed] distance = 141.42135623731
[unmanaged] Initializing location...
[managed] x=50 y=50
```

## <a name="see-also"></a>Viz také:

[Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
