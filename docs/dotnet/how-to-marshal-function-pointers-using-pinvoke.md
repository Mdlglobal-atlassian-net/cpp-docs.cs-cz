---
title: 'Postupy: Zařazení ukazatelů na funkce pomocí služby PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
ms.openlocfilehash: 2f12c86b7e32955622a4a2c598d01057e303a329
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435604"
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>Postupy: Zařazení ukazatelů na funkce pomocí služby PInvoke

Toto téma vysvětluje, jak spravované delegáti se dá použít namísto ukazatelů na funkce při interoperabilitě se službou nespravovaných funkcí pomocí funkce rozhraní .NET Framework P/Invoke. Programátory v jazyce Visual C++ jsou však doporučujeme místo toho použít funkce zprostředkovatele komunikace C++ (Pokud je to možné), protože deklarace P/Invoke obsahuje malý kompilace zpráv o chybách, není typově bezpečný a může být pracná k implementaci. Pokud není k dispozici zdrojový kód nespravované rozhraní API je zabalený jako knihovnu DLL, P/Invoke je jedinou možností. V opačném případě naleznete v následujících tématech:

- [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Postupy: Zařazování zpětných volání a delegátů pomocí funkcí interoperability C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

Nespravovaná rozhraní API, které přebírají ukazatele funkce jako argumenty lze volat ze spravovaného kódu pomocí spravované delegáta místo ukazatel nativní funkce. Kompilátor automaticky zařadí delegátů k nespravovaným funkcím jako ukazatel na funkci a vloží nezbytné přechod spravovaného a nespravovaného kódu.

## <a name="example"></a>Příklad

Následující kód se skládá z nespravovaného a spravovaný modul. Nespravovaný modul je knihovnu DLL, která definuje funkci nazvanou TakesCallback, která přijímá ukazatel na funkci. Tato adresa se používá ke spuštění funkce.

Definuje delegáta, který je zařazen do nativního kódu jako ukazatel na funkci a používá spravovaný modul <xref:System.Runtime.InteropServices.DllImportAttribute> atribut vystavit nativní funkce TakesCallback pro spravovaný kód. Ve funkci main instance delegáta se a předaný funkci TakesCallback. Výstup programu ukazuje, že tato funkce se provede pomocí nativní TakesCallback funkce.

Spravované funkce potlačuje uvolňování paměti pro spravované delegáta k zabránění uvolňování paměti rozhraní .NET Framework z přemístění delegáta, zatímco nativní funkce.

```cpp
// TraditionalDll5.cpp
// compile with: /LD /EHsc
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   /* Declare an unmanaged function type that takes two int arguments
      Note the use of __stdcall for compatibility with managed code */
   typedef int (__stdcall *CALLBACK)(int);
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);
}

int TakesCallback(CALLBACK fp, int n) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n);
}
```

```cpp
// MarshalDelegate.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

public delegate int GetTheAnswerDelegate(int);
public value struct TraditionalDLL {
   [DllImport("TraditionalDLL5.dll")]
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);
};

int GetNumber(int n) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;
   return x + n;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TraditionalDLL::TakesCallback(fp, 42);
}
```

Všimněte si, že není žádná část knihovny DLL zpřístupněna spravovaného kódu pomocí tradiční #include. Ve skutečnosti se knihovny DLL přistupuje za běhu pouze, takže problémy s funkcí importovány s <xref:System.Runtime.InteropServices.DllImportAttribute> nebudou zjištěna v době kompilace.

## <a name="see-also"></a>Viz také

[Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)