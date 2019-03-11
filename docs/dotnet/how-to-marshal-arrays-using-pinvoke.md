---
title: 'Postupy: Zařazování polí pomocí služby PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
ms.openlocfilehash: 60b49135928e3dadffc2a3c7a422646d2f3a768d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57752308"
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>Postupy: Zařazování polí pomocí služby PInvoke

Toto téma vysvětluje, jak nativní funkce, které přijímají řetězce ve stylu jazyka C lze volat pomocí řetězce typu CLR <xref:System.String> s využitím podpory nástroje nespravovaného kódu rozhraní .NET Framework. Programátoři jazyka Visual C++ jsou ukončena. doporučujeme místo toho použijte funkce zprostředkovatele komunikace C++ (Pokud je to možné), protože deklarace P/Invoke obsahuje malý kompilace zpráv o chybách, není typově bezpečný a může být pracná k implementaci. Pokud není k dispozici zdrojový kód nespravované rozhraní API je zabalený jako knihovnu DLL, P/Invoke je jedinou možností (jinak, naleznete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)).

## <a name="example"></a>Příklad

Protože nativní a spravovaná pole jsou stanoveny odlišně v paměti, předávání úspěšně přes hranice spravovaného a nespravovaného vyžaduje převod nebo zařazování. Toto téma ukazuje, jak pole položek jednoduchých (blitable) může být předán nativních funkcí ze spravovaného kódu.

Jak platí obecně, zařazování dat spravovaného a nespravovaného <xref:System.Runtime.InteropServices.DllImportAttribute> atribut se používá k vytvoření spravovaný vstupní bod pro každou nativní funkci, která se použije. V případě funkcí, které přijímají polí jako argumentů <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut je potřeba použít také k určení pro kompilátor, jak budou data zařadit. V následujícím příkladu <xref:System.Runtime.InteropServices.UnmanagedType> výčtu se používá k označení, že se zařadit spravovaného pole jako pole stylu C.

Následující kód se skládá z nespravovaného a spravovaný modul. Nespravovaný modul je knihovnu DLL, která definuje funkci, která přijímá pole celých čísel. Druhý modul je spravované aplikace příkazového řádku, který importuje tuto funkci, ale definuje z hlediska spravovaného pole a používá <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut k určení, že pole mají být převedeny na nativní pole při volání.

Spravovaného modulu je kompilována s parametrem/CLR.

```cpp
// TraditionalDll4.cpp
// compile with: /LD /EHsc
#include <iostream>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);
}

void TakesAnArray(int len, int a[]) {
   printf_s("[unmanaged]\n");
   for (int i=0; i<len; i++)
      printf("%d = %d\n", i, a[i]);
}
```

```cpp
// MarshalBlitArray.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL {
   [DllImport("TraditionalDLL4.dll")]
   static public void TakesAnArray(
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);
};

int main() {
   array<int>^ b = gcnew array<int>(3);
   b[0] = 11;
   b[1] = 33;
   b[2] = 55;
   TraditionalDLL::TakesAnArray(3, b);

   Console::WriteLine("[managed]");
   for (int i=0; i<3; i++)
      Console::WriteLine("{0} = {1}", i, b[i]);
}
```

Všimněte si, že není žádná část knihovny DLL zpřístupněna spravovaného kódu pomocí tradiční #include. Ve skutečnosti, protože knihovna DLL je přístupná pouze za běhu, problémy s funkcemi, které se importují s <xref:System.Runtime.InteropServices.DllImportAttribute> nebudou zjištěna v době kompilace.

## <a name="see-also"></a>Viz také:

[Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
