---
title: 'Postupy: Zařazení řetězců pomocí služby PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: 86ce065da5c214c0da803ad53d19eaec3de5efb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598117"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Postupy: Zařazení řetězců pomocí služby PInvoke

Toto téma vysvětluje, jak nativní funkce, které přijímají řetězce ve stylu jazyka C lze volat pomocí řetězce CLR zadejte System::String s využitím podpory nástroje nespravovaného kódu rozhraní .NET Framework. Programátoři jazyka Visual C++ jsou ukončena. doporučujeme místo toho použijte funkce zprostředkovatele komunikace C++ (Pokud je to možné), protože deklarace P/Invoke obsahuje malý kompilace zpráv o chybách, není typově bezpečný a může být pracná k implementaci. Pokud nespravované rozhraní API je zabalený jako knihovnu DLL a zdrojový kód není k dispozici, pak P/Invoke je jedinou možností, ale jinak naleznete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Spravované a nespravované řetězce jsou stanoveny odlišně v paměti, takže předávání řetězce ze spravované na nespravované funkce vyžaduje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut pokyn kompilátoru k vložení vyžaduje převod mechanismy pro zařazování dat řetězce správné a bezpečné.

Stejně jako u funkce, které používají jenom typy vnitřních datových <xref:System.Runtime.InteropServices.DllImportAttribute> se používá k deklaraci spravovaný vstupní body do nativních funkcí, ale--při předávání řetězce – místo definování těchto vstupních bodů, aby přijímaly řetězců ve stylu C, popisovač <xref:System.String> typu je možné místo toho. Tento parametr vyzve kompilátoru k vložení kódu, který provede požadované převod. Pro každý argument funkce v nespravované funkci, která přebírá řetězec <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut má použít k označení, že na objekt řetězce by měl být zařazen do nativní funkce jako řetězec stylu C.

## <a name="example"></a>Příklad

Následující kód se skládá z nespravovaného a spravovaný modul. Nespravovaný modul je knihovnu DLL, která definuje funkci nazvanou TakesAString, který přijímá řetězec ANSI C-style ve formě char *. Spravovaný modul je aplikace příkazového řádku, který importuje TakesAString funkce, ale definuje, aby přijímaly spravované System.String místo typu char\*. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut slouží k určení, jak by měly být zařazeny spravované řetězce při volání TakesAString.

```
// TraditionalDll2.cpp
// compile with: /LD /EHsc
#include <windows.h>
#include <stdio.h>
#include <iostream>

using namespace std;

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAString(char*);
}

void TakesAString(char* p) {
   printf_s("[unmanaged] %s\n", p);
}
```

```
// MarshalString.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL
{
   [DllImport("TraditionalDLL2.dll")]
      static public void
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);
};

int main() {
   String^ s = gcnew String("sample string");
    Console::WriteLine("[managed] passing managed string to unmanaged function...");
   TraditionalDLL::TakesAString(s);
   Console::WriteLine("[managed] {0}", s);
}
```

Tento postup způsobí, že kopie řetězec, který má být postavená na nespravované haldě, takže změny provedené na řetězec pomocí nativní funkce se neprojeví v spravovaného kopie řetězce.

Všimněte si, že žádná část knihovny DLL je přístupný pro spravovaný kód prostřednictvím tradiční #include. Ve skutečnosti knihovny DLL přistupuje pouze za běhu, takže problémy s funkcí importovány pomocí `DllImport` nebudou zjištěna v době kompilace.

## <a name="see-also"></a>Viz také

[Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)