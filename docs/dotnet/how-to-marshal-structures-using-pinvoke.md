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
ms.openlocfilehash: e79eb343f81cf2d66e394be7561d2c9727c4c9ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429107"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>Postupy: Zařazení struktur pomocí služby PInvoke

Tento dokument popisuje, jak nativní funkce, které přijímají struktury stylu jazyka C lze volat z spravovaných funkcí pomocí pomocí deklarace P/Invoke. Přestože doporučujeme používat funkce zprostředkovatele komunikace C++ místo P/Invoke vzhledem k tomu, že P/Invoke obsahuje malý kompilace zpráv o chybách, není typově bezpečný a může být pracná implementovat, pokud nespravovaná rozhraní API je zabalený jako knihovnu DLL a zdrojový kód není k dispozici, P/Invoke je jedinou možností. V opačném případě najdete v následujících dokumentech:

- [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Postupy: Zařazení řetězců pomocí služby PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

Ve výchozím nastavení nativní a spravovaná struktury jsou stanoveny odlišně v paměti, úspěšném předání struktury přes hranice spravovaného a nespravovaného vyžaduje další kroky k zachování integrity dat.

Tento dokument popisuje kroky potřebné k definování spravované ekvivalenty nativních struktur a jak výsledné struktury mohou být předány nespravované funkci. Tento dokument předpokládá, že jednoduchá struktury – ty, které neobsahují řetězce nebo ukazatelů, se používají. Informace o interoperabilitě nepřenositelné najdete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md). P/Invoke nemůže mít nepřenositelné typy jako návratovou hodnotu. Přenositelné typy zabírají stejné množství spravovaného a nespravovaného kódu. Další informace najdete v tématu [přenositelné a Non-přenositelné typy](/dotnet/framework/interop/blittable-and-non-blittable-types).

Zařazování jednoduchý, blittable struktury přes hranice spravovaného a nespravovaného nejprve vyžaduje definovat spravovaná verze nativní struktury. Tyto struktury mohou mít libovolný platný název. není žádný vztah mezi nativní a spravovaná verze dvě struktury než jejich data rozložení. Proto je důležité, že spravovaná verze obsahuje pole, která budou mít stejné velikosti a ve stejném pořadí jako původní verze. (Neexistuje žádný mechanismus pro zajištění, že spravovaný a nativní verze struktury jsou ekvivalentní, takže nekompatibilita není zřejmé, až do spuštění. Zodpovídá programátor Ujistěte se, že dvě struktury se stejné rozvržení data.)

Protože jsou členové struktur spravované někdy přeskupení pro účely výkonu, je nutné použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut označuje, že struktury jsou rozloženy postupně. Je také vhodné obalování nastavení stejný jako, který používá strukturou nativní struktury explicitně nastavit. (I když se ve výchozím nastavení, Visual C++ používá strukturu 8bajtový balení pro spravovaný kód.)

1. Pak pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> deklarovat vstupních bodů, které odpovídají jakékoli nespravované funkce, které přijímají struktuře, ale používat spravované verzi struktury v podpisech funkcí, což je bod moot, pokud použijete stejný název pro obě verze Struktura.

1. Spravovaný kód teď můžete předat spravovaná verze struktury k nespravovaným funkcím jakoby byly skutečně spravované funkce. Tyto struktury může být předán podle hodnoty nebo podle odkazu, jak je ukázáno v následujícím příkladu.

## <a name="example"></a>Příklad

Následující kód se skládá z nespravovaného a spravovaný modul. Nespravovaný modul je knihovnu DLL, která definuje strukturu s názvem umístění a funkci s názvem GetDistance, která přijímá dva výskyty struktura umístění. Druhý modul je spravované aplikace příkazového řádku, který importuje GetDistance funkce, ale definuje jde o ekvivalent spravované umístění struktury MLocation. V praxi se stejným názvem se pravděpodobně použije pro obě verze struktury; jiný název se ale používá tady předvést, co se týče spravovaná verze je definován DllImport prototypu.

Všimněte si, že není žádná část knihovny DLL zpřístupněna spravovaného kódu pomocí tradiční #include. Knihovny DLL ve skutečnosti přistupuje za běhu pouze, takže problémy s funkcí, které jsou importovány pomocí DllImport nebude v době kompilace.

```
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

```
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

## <a name="see-also"></a>Viz také

[Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
