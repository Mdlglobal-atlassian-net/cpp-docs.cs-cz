---
title: "Postupy: Zařazování struktur pomocí služby PInvoke | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5bfca720a97ac8462afa970e54f13e0bd74a7808
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>Postupy: Zařazení struktur pomocí služby PInvoke
Tento dokument popisuje, jak nativních funkcí, které přijímají řetězce stylu jazyka C nelze volat ze spravovaných funkcí, které poskytují instanci <xref:System.String> pomocí P/Invoke. Přestože doporučujeme použít funkce interoperability C++ místo P/Invoke protože P/Invoke poskytuje malé kompilaci zpráv o chybách, není bezpečný a může být obtížné implementovat, pokud je jako knihovny DLL zabalené nespravovaného rozhraní API a zdrojový kód není k dispozici, P/Invoke je jedinou možností. Jinak najdete v následujících dokumentech:  
  
-   [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [Postupy: Zařazení struktur pomocí služby PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
 Ve výchozím nastavení nativní a spravovaná struktury jsou nastíněny jinak v paměti, takže úspěšně předání struktur přes spravované nebo nespravované hranice vyžaduje další kroky k zachování integrity dat.  
  
 Tento dokument popisuje kroky potřebné k definování spravované ekvivalenty nativní struktury, jak lze předat výsledné struktury k nespravovaným funkcím. Tento dokument předpokládá, že jednoduché struktury – ty, které neobsahují řetězce nebo ukazatele – se používají. Informace o interoperabilitě nepřenositelné najdete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md). P/Invoke nemůže mít nepřenositelné typy jako typ návratové hodnoty. Přenositelné typy mají stejnou reprezentaci v spravovanými a nespravovanými kódu. Další informace najdete v tématu [přenositelné a Non-přenositelné typy](http://msdn.microsoft.com/Library/d03b050e-2916-49a0-99ba-f19316e5c1b3).  
  
 Zařazování jednoduchých blittable struktur přes spravované nebo nespravované hranice nejprve vyžaduje definovat spravované verze každé nativní struktury. Tyto struktury může mít libovolný název právní; neexistuje žádný vztah mezi nativní a spravovaná verzi než jejich rozložení dat dvě struktury. Proto je důležité, aby spravovaná verze obsahuje pole, která jsou stejné, velikost a ve stejném pořadí jako nativní verze. (Neexistuje žádný mechanismus pro zajištění, že jsou spravovaná a nativní verze struktury ekvivalentní, takže nekompatibilita není zřejmá až při spuštění. Je pro programátory odpovědností zkontrolujte, zda dva struktury se stejné rozvržení data.)  
  
 Vzhledem k tomu, že členové spravovaných struktur někdy přeskupení z důvodů výkonu, je nutné použít <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut k označení, že strukturu jsou nastíněny postupně. Je také vhodné explicitně nastavit strukturu balení nastavení, aby byla stejná, který používá nativní struktuře. (Ve výchozím nastavení používá Visual C++ strukturu 8bajtový balení pro spravovaný kód.)  
  
1.  Pak pomocí <xref:System.Runtime.InteropServices.DllImportAttribute> deklarovat vstupních bodů, které odpovídají jakékoli nespravované funkci, které přijímají strukturu, ale používá spravovanou verzi struktury v podpisech funkce, která je bod moot, pokud používáte stejný název pro obě verze Struktura.  
  
2.  Spravovaný kód teď můžete předat spravovaná verze struktury k nespravovaným funkcím jakoby byly skutečně spravované funkce. Tyto struktury mohou být předány hodnotou nebo odkazem, jak je ukázáno v následujícím příkladu.  
  
## <a name="example"></a>Příklad  
 Následující kód se skládá z nespravovaného a spravovaný modul. Nespravovaný modul je knihovna DLL, která definuje strukturu s názvem umístění a funkci s názvem GetDistance, který přijímá dvě instance struktury umístění. Druhý modul je spravovaná aplikace příkazového řádku, která importuje funkci GetDistance, ale definuje z hlediska spravovaného ekvivalentu struktury Location, MLocation. V praxi by se stejným názvem pravděpodobně použít pro obě verze struktury; jiný název se ale používá zde prokázat, že prototyp DllImport jsou definovány na základě spravovaná verze.  
  
 Spravovaný modul je kompilovat s/CLR, ale/CLR: pure pracuje stejně dobře. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 Všimněte si, že žádná část knihovny DLL je vystaven spravovaného kódu pomocí tradiční #include – direktiva. Ve skutečnosti knihovnu DLL přístupná v době běhu, takže problémy s funkcemi, které jsou importovány s DllImport nejsou v době kompilace.  
  
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