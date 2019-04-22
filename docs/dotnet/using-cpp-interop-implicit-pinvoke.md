---
title: Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)
ms.date: 11/04/2016
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
ms.openlocfilehash: aaa07373b7dd22807290ceefa9197b4013c61fe5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58778231"
---
# <a name="using-c-interop-implicit-pinvoke"></a>Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)

Na rozdíl od jiných jazyků .NET, Visual C++ podporuje interoperabilitu, která umožňuje spravovaným a nespravovaným kódem existovat ve stejné aplikaci a dokonce i ve stejném souboru (s [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy pragma). To umožňuje vývojářům Visual C++ integrovat funkce rozhraní .NET do stávajících aplikací Visual C++ bez narušení zbývajících částí aplikace.

Můžete také volat nespravované funkce pomocí spravované kompilantu [dllexport, dllimport](../cpp/dllexport-dllimport.md).

Implicitní služba PInvoke je užitečné, když není potřeba určit, jak budou zařazovat parametry funkce nebo některé podrobnosti, které lze zadat, pokud explicitně voláním DllImportAttribute.

Visual C++ poskytuje dva způsoby, jak spravovaných a nespravovaných funkcí pro spolupráci:

- [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

Explicitního volání PInvoke je podporována rozhraním .NET Framework a je k dispozici ve většině jazyků .NET. Ale jak již název napovídá, zprostředkovatele komunikace C++ je specifické pro Visual C++.

## <a name="c-interop"></a>interoperabilita C++

Interoperabilita C++ se doporučuje přes explicitního volání PInvoke, protože poskytuje lepší zabezpečení typů, je obvykle méně náročná na implementaci, je více forgiving nespravované rozhraní API se mění a umožňuje vylepšení výkonu, které nejsou možné s explicitní PInvoke. Zprostředkovatele komunikace C++ však není možné v případě nespravovaného kódu není k dispozici.

## <a name="c-com-interop"></a>interoperabilita C++ COM

Vzájemná funkční spolupráce funkcí podporovaných jazykem Visual C++ nabízí konkrétní výhody oproti jinými jazyky rozhraní .NET při rozhodování o vzájemné spolupráci se službou komponenty modelu COM. Namísto omezení rozhraní .NET Framework [Tlbimp.exe (Importér knihovny typů)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), jako je například omezenou podporu pro datové typy a povinné vystavení každého člena každé rozhraní modelu COM, zprostředkovatele komunikace C++ umožňuje modelu COM komponenty získat přístup na adrese, který se už nevyžadují samostatné sestavení vzájemné spolupráce. Na rozdíl od jazyka Visual Basic a C#, Visual C++ můžete použít přímo pomocí obvyklých mechanismů COM objekty COM (například **CoCreateInstance** a **QueryInterface**). To je možné z důvodu funkce zprostředkovatele komunikace C++, které způsobit, že kompilátor automatického vkládání kódu přechod k přesunutí ze spravovaných do nespravovaných funkcí a zpět.

Pomocí zprostředkovatele komunikace C++, komponenty modelu COM lze použít jako se obvykle používají nebo se dá zabalit uvnitř třídy jazyka C++. Tyto obálkové třídy se nazývají obálek volatelných za běhu vlastní nebo CRCWs a mají dvě výhody oproti použití přímo v kódu aplikace modelu COM:

- Výsledné třídy lze použít z jiných jazyků než Visual C++.

- Podrobnosti o rozhraní modelu COM lze skrýt z klienta spravovaného kódu. Datové typy .NET může být zastoupen nativní typy a podrobnosti o zařazování dat můžete uvnitř CRCW poskytováno transparentně.

Bez ohledu na to, zda COM se používají přímo nebo prostřednictvím CRCW musí zařazovat typy argumentů než jednoduché, přenositelné typy.

## <a name="blittable-types"></a>Přenositelné typy

Pro nespravovaná rozhraní API, používat jednoduché a vnitřní typy (viz [přenositelné a Non-přenositelné typy](/dotnet/framework/interop/blittable-and-non-blittable-types)), není vyžadováno žádné zvláštní kódování, protože tyto typy dat mají stejnou reprezentaci v paměti, ale vyžadují komplexnější datové typy explicitní zařazování dat. Příklad najdete v tématu [jak: Volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).

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

- [Postupy: Zařazování zpětných volání a delegátů pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

- [Postupy: Zařazování vložených ukazatelů pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)

- [Postupy: Přístup ke znakům v System::String](../dotnet/how-to-access-characters-in-a-system-string.md)

- [Postupy: Převod řetězce typu char * na pole System::Byte](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)

- [Postupy: Převod typu System::String na wchar_t * nebo char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [Postupy: Převod typu System::String na standardní řetězec](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [Postupy: Převod standardního řetězce na typ System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [Postupy: Získání ukazatele na bajtové pole](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [Postupy: Načtení nespravovaných prostředků do bajtového pole](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [Postupy: Změna referenční třídy v nativní funkci](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [Postupy: Určení, jestli je image nativní nebo CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [Postupy: Přidání nativní knihovny DLL do globální mezipaměti sestavení](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [Postupy: Uchování odkazu na typ hodnoty v nativním typu](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [Postupy: Uchování odkazu na objekt v nespravované paměti](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [Postupy: Zjišťování kompilace/CLR](../dotnet/how-to-detect-clr-compilation.md)

- [Postupy: Převody mezi hodnotami System::Guid a _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [Postupy: Určení výstupního parametru](../dotnet/how-to-specify-an-out-parameter.md)

- [Postupy: Použití nativního typu v kompilaci/CLR](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [Postupy: Deklarace obslužných rutin v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md)

- [Postupy: Zabalení nativních tříd pro použití v jazyce C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

Informace o použití delegátů ve scénáři spolupráce naleznete v tématu [delegate (rozšíření komponent C++)](../extensions/delegate-cpp-component-extensions.md).

## <a name="see-also"></a>Viz také:

- [Volání nativních funkcí ze spravovaného kódu](../dotnet/calling-native-functions-from-managed-code.md)
