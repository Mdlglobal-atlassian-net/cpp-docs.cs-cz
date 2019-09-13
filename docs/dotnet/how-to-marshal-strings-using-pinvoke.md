---
title: 'Postupy: Zařazování řetězců pomocí PInvoke'
ms.custom: get-started-article
ms.date: 09/09/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: d3b39a4ce40de2a26ffba4f52ab1e39c94767089
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907565"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Postupy: Zařazování řetězců pomocí PInvoke

Toto téma vysvětluje, jak nativní funkce, které přijímají řetězce ve stylu jazyka C, mohou být volány pomocí typu řetězce CLR System:: String, který využívá .NET Framework podporu vyvolání platformy. Vizuální C++ programátory jsou doporučováni používat C++ funkce spolupráce (Pokud je to možné), protože volání nespravovaného volání poskytuje malé zprávy o chybách při kompilaci, nejedná se o typově bezpečný a může být zdlouhavé pro implementaci. Pokud je nespravované rozhraní API zabaleno jako knihovna DLL a zdrojový kód není k dispozici, pak je P/Invoke jedinou možností, ale v opačném případě viz [použití C++ zprostředkovatele komunikace (implicitní PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Spravované a nespravované řetězce jsou v paměti rozloženy jinak, takže předávání řetězců ze spravovaných do nespravovaných funkcí vyžaduje, <xref:System.Runtime.InteropServices.MarshalAsAttribute> aby kompilátor pro vložení požadovaných mechanismů převodu pro zařazování řetězcových dat nahlásil. správně a bezpečně.

Stejně jako u funkcí, které používají pouze vnitřní datové <xref:System.Runtime.InteropServices.DllImportAttribute> typy, se používá k deklaraci spravovaných vstupních bodů do nativních funkcí, ale--pro předávání řetězců, namísto definování těchto vstupních bodů jako přebírání řetězců ve stylu jazyka C <xref:System.String> , popisovače typu místo toho je možné použít. To vyzve kompilátor k vložení kódu, který provede požadovaný převod. Pro každý argument funkce v nespravované funkci, která přebírá řetězec, <xref:System.Runtime.InteropServices.MarshalAsAttribute> by měl být použit atribut k označení toho, že by měl být objekt String zařazen do nativní funkce jako řetězec ve stylu jazyka C.

Zařazovací program zalomí volání nespravované funkce ve skryté obálce, která bude připravovat a kopírovat spravovaný řetězec do místně přiděleného řetězce v nespravovaném kontextu, který je poté předán nespravované funkci. Pokud se nespravované funkce vrátí, obálka buď odstraní prostředek, nebo pokud byl v zásobníku, je uvolněna, když se obálka dopadne mimo rozsah. Nespravovaná funkce není zodpovědná za tuto paměť. Nespravovaný kód vytvoří a odstraní jenom paměť v haldě nastavené podle vlastní CRT, takže nikdy nedochází k potížím s modulem pro zařazování pomocí jiné verze CRT.

Pokud vaše nespravované funkce vrátí řetězec buď jako návratovou hodnotu, nebo jako výstupní parametr, zařazovací modul ho zkopíruje do nového spravovaného řetězce a pak uvolní paměť. Další informace naleznete v tématu [výchozí chování zařazování](/dotnet/framework/interop/default-marshaling-behavior) a [zařazování dat pomocí vyvolání platformy](/dotnet/framework/interop/marshaling-data-with-platform-invoke).

## <a name="example"></a>Příklad

Následující kód se skládá z nespravovaného a spravovaného modulu. Nespravovaný modul je knihovna DLL, která definuje funkci nazvanou TakesAString, která přijímá řetězec ANSI ve stylu jazyka C ve formě znaku *. Spravovaný modul je aplikace příkazového řádku, která importuje funkci TakesAString, ale definuje ji jako přebírání spravovaného systému. řetězec místo znaku\*. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut slouží k určení, jak by měl být spravovaný řetězec zařazen při volání funkce TakesAString.

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

Tato technika způsobí, že kopie řetězce bude vytvořena na nespravované haldě, takže změny provedené v řetězci nativní funkcí nebudou promítnuty do spravované kopie řetězce.

Všimněte si, že žádná část knihovny DLL není k dispozici pro spravovaný kód prostřednictvím tradiční direktivy #include. Knihovna DLL je ve skutečnosti k dispozici pouze za běhu, takže problémy s funkcemi importovanými v nástroji `DllImport` nebudou zjištěny v době kompilace.

## <a name="see-also"></a>Viz také:

[Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
