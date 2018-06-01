---
title: Pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- blittable types [C++]
- platform invoke [C++], implicit
- interop [C++], features
- data marshaling [C++], C++ Interop features
- porting [C++], C++ native to .NET
- COM interfaces [C++]
- implicit platform invoke
- examples [C++], interoperability
- types [C++], blittable
- marshaling [C++], C++ Interop features
- platform invoke [C++], examples
- interoperability [C++]
- C++ Interop
- interoperability [C++], Implicit PInvoke
- C++, interop
- C++ COM Interop
- .NET [C++], porting C++ native to
ms.assetid: 5f710bf1-88ae-4c4e-8326-b3f0b7c4c68a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a095f252c4e46e212e42a7ab4cf3cb8d5ef6f53d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704289"
---
# <a name="using-c-interop-implicit-pinvoke"></a>Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)

Na rozdíl od jiných jazyků .NET, Visual C++ má interoperabilita podpory, který umožňuje spravovanými a nespravovanými kód existovat ve stejné aplikaci a to i ve stejném souboru (s [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy). To umožňuje vývojářům Visual C++ integrovat funkce .NET do stávajících aplikací Visual C++ bez narušení zbývající aplikace.

Nespravované funkce můžete také volat z spravované kompilace pomocí [dllexport, dllimport](../cpp/dllexport-dllimport.md).

Implicitní PInvoke je užitečné, když není potřeba zadat jak zařazeno parametry funkce nebo některé podrobnosti, které je možné zadat při explicitním volání DllImportAttribute.

Visual C++ nabízí dva způsoby, kterými spravovaných a nespravovaných funkcí pro spolupráci:

- [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

Explicitního volání PInvoke podporuje rozhraní .NET Framework a je dostupný ve většině jazyků .NET. Ale jak již název napovídá, zprostředkovatele komunikace C++ je specifické pro aplikaci Visual C++.

## <a name="c-interop"></a>interoperabilita C++

Interoperabilita C++ se doporučuje namísto explicitního volání PInvoke, protože poskytuje lepší zabezpečení typů, je obvykle méně náročná na implementaci, je více forgiving, pokud nespravovaného rozhraní API se mění a umožňuje vylepšení výkonu, které nejsou možné pomocí explicitní PInvoke. Interoperabilita C++ však není možné, pokud není k dispozici nespravovaný zdrojový kód.

## <a name="c-com-interop"></a>interoperabilita C++ COM

Funkce interoperability podporované Visual C++ nabízí konkrétní výhody oproti jinými jazyky rozhraní .NET, pokud jde o vzájemné spolupráci se službou COM – součásti. Namísto omezení rozhraní .NET Framework [Tlbimp.exe (Importér knihovny)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), jako je například omezenou podporu pro datové typy a povinné vystavení každého člena každé rozhraní modelu COM, umožňuje Interoperabilita C++ COM součástí získat přístup na adrese bude a nevyžaduje samostatnou spolupráce – sestavení. Na rozdíl od jazyka Visual Basic a C#, Visual C++, můžete použít objekty COM přímo pomocí obvyklé mechanismy COM (například **CoCreateInstance** a **QueryInterface**). To je možné z důvodu funkce interoperability C++, které způsobí kompilátoru automatického vkládání kódu přechod k přesunutí ze spravovaných do nespravovaných funkcí a zpět.

Pomocí zprostředkovatele komunikace C++, COM – součásti lze použít jako běžně se používá nebo může být uzavřen do třídy jazyka C++. Tyto třídy obálky se označují jako vlastní běhové obálky s možností nebo CRCWs a mají dva výhod oproti použití COM přímo v kódu aplikace:

- Výsledný třídu můžete použít z jiných jazyků než Visual C++.

- Podrobnosti o rozhraní modelu COM, může být skryté z klienta spravovaného kódu. Jde použít místo nativní typy .NET datové typy a podrobnosti o zařazování dat lze provést transparentně uvnitř CRCW.

Bez ohledu na to, jestli je COM používat přímo nebo prostřednictvím CRCW musí být zařazené typy argumentů než jednoduché, přenositelné typy.

## <a name="blittable-types"></a>Přenositelné typy

Pro nespravovaná rozhraní API, používat jednoduché, vlastní typy (viz [přenositelné a Non-přenositelné typy](/dotnet/framework/interop/blittable-and-non-blittable-types)), není vyžadováno žádné speciální kódování, protože tyto typy dat mají stejnou reprezentaci v paměti, ale vyžadují komplexnější datové typy explicitní dat – zařazování. Příklad, naleznete v části [postupy: volání nativních knihoven DLL ze spravovaného kódu pomocí PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).

## <a name="example"></a>Příklad

```cpp
// vcmcppv2_impl_dllimp.cpp
// compile with: /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

// Implicit DLLImport specifying calling convention
extern "C" int __stdcall MessageBeep(int);

// explicit DLLImport needed here to use P/Invoke marshalling because
// System::String ^ is not the type of the first parameter to printf
[DllImport("msvcrt.dll", EntryPoint = "printf", CallingConvention = CallingConvention::Cdecl,  CharSet = CharSet::Ansi)]
// or just
// [DllImport("msvcrt.dll")]
int printf(System::String ^, ...);

int main() {
   // (string literals are System::String by default)
   printf("Begin beep\n");
   MessageBeep(100000);
   printf("Done\n");
}
```

```Output
Begin beep
Done
```

## <a name="in-this-section"></a>V tomto oddílu

- [Postupy: Zařazování řetězců v kódu ANSI pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

- [Postupy: Zařazování struktur pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-structures-using-cpp-interop.md)

- [Postupy: Zařazování polí pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)

- [Postupy: Zařazování zpětných volání a delegátů pomocí funkcí interoperability C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

- [Postupy: Zařazení vložených ukazatelů pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

- [Postupy: Přístup ke znakům v datech třídy System::String](../dotnet/how-to-access-characters-in-a-system-string.md)

- [Postupy: Převod řetězce typu char * na pole System::Byte](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)

- [Postupy: převod typu System::String na wchar_t * nebo char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [Postupy: Převod typu System::String na standardní řetězec](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [Postupy: Převod standardního řetězce na typ System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [Postupy: Získání ukazatele na pole bajtů](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [Postupy: Načtení nespravovaných prostředků do bajtového pole](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [Postupy: Změna referenční třídy v nativní funkci](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [Postupy: Určení, zda je bitová kopie nativní nebo CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [Postupy: Přidání nativní knihovny DLL do globální mezipaměti sestavení](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [Postupy: Uložení odkazu na typ hodnoty v nativním typu](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [Postupy: Uchování odkazu na objekt v nespravované paměti](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [Postupy: zjištění kompilaci/CLR](../dotnet/how-to-detect-clr-compilation.md)

- [Postupy: Převody mezi hodnotami System::Guid a _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [Postupy: Určení výstupního parametru](../dotnet/how-to-specify-an-out-parameter.md)

- [Postupy: použití nativního typu v kompilaci/CLR](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [Postupy: Deklarace obslužných rutin v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md)

- [Postupy: Zabalení nativních tříd pro použití v jazyce C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

Informace o použití delegátů ve scénáři interoperability najdete v tématu [delegáta (rozšíření komponent C++)](../windows/delegate-cpp-component-extensions.md).

## <a name="see-also"></a>Viz také:

- [Volání nativních funkcí ze spravovaného kódu](../dotnet/calling-native-functions-from-managed-code.md)
