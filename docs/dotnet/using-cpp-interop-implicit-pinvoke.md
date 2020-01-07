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
ms.openlocfilehash: d26fbefd87b3ba6d6ca7e183be78608777f383b5
ms.sourcegitcommit: 27d9db019f6d84c94de9e6aff0170d918cee6738
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/06/2020
ms.locfileid: "75676927"
---
# <a name="using-c-interop-implicit-pinvoke"></a>Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)

Na rozdíl od jiných jazyků .NET má C++ vizuál podporu interoperability, která umožňuje, aby ve stejné aplikaci existoval spravovaný a nespravovaný kód, a dokonce i ve stejném souboru (se [spravovanými, nespravovanými](../preprocessor/managed-unmanaged.md) direktivami pragma). To umožňuje vizuálním C++ vývojářům integrovat funkce .NET do C++ stávajících vizuálních aplikací, aniž by narušili zbytek aplikace.

Nespravované funkce můžete volat také ze spravovaného kompilantu pomocí metody [dllexport, dllimport](../cpp/dllexport-dllimport.md).

Implicitní PInvoke je užitečné, pokud nepotřebujete určit, jakým způsobem budou zařazovat parametry funkce, nebo jakékoli jiné podrobnosti, které lze zadat při explicitním volání DllImportAttribute.

Vizuál C++ nabízí dva způsoby, kterými se spravované a nespravované funkce vzájemně spolupracují:

- [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

.NET Framework podporuje explicitní PInvoke a je k dispozici ve většině jazyků .NET. Ale jak jeho název implikuje C++ , interoperabilita je specifická C++pro vizuál.

## <a name="c-interop"></a>interoperabilita C++

C++Interoperabilita poskytuje lepší bezpečnost typů a obvykle je méně zdlouhavá pro implementaci. Nicméně C++ interoperabilita není možnost, pokud není nespravovaný zdrojový kód k dispozici nebo pro projekty pro různé platformy.

## <a name="c-com-interop"></a>interoperabilita C++ COM

Funkce interoperability, které nabízí C++ vizuál, nabízejí konkrétní výhody v jiných jazycích .NET, když jsou k dispozici pro spolupráci s komponentami com. Namísto omezení pro .NET Framework [Tlbimp. exe (importér knihovny typů)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), jako je například omezená podpora pro datové typy a povinná angažovanost každého člena každého rozhraní modelu COM, C++ umožňuje zprostředkovateli přístupu k komponentám com a nevyžaduje samostatná sestavení vzájemné spolupráce. Na rozdíl od Visual Basic C#a může C++ vizuál použít objekty COM přímo pomocí obvyklých mechanismů com (například **CoCreateInstance** a **QueryInterface**). To je možné v důsledku C++ funkcí spolupráce, které způsobí, že kompilátor automaticky vloží kód přechodu pro přesun ze spravovaných do nespravovaných funkcí a zpět.

Pomocí C++ zprostředkovatele komunikace lze komponenty modelu COM použít jako obvykle používané nebo mohou být zabaleny do C++ tříd. Tyto obálkové třídy se nazývají vlastní běhové obálky nebo CRCWs a mají dvě výhody při použití modelu COM přímo v kódu aplikace:

- Výslednou třídu lze použít z jiných jazyků než vizuálů C++.

- Podrobnosti o rozhraní modelu COM mohou být skryty ze spravovaného kódu klienta. Datové typy .NET lze použít místo nativních typů a podrobnosti o zařazování dat lze provádět transparentně v rámci CRCW.

Bez ohledu na to, zda je model COM použit přímo nebo prostřednictvím CRCW, musí být zařazeny typy argumentů jiné než jednoduché.

## <a name="blittable-types"></a>Typy přenosit

Pro nespravovaná rozhraní API, která používají jednoduché, vnitřní typy (viz přenositelné [a nepřenositelné typy](/dotnet/framework/interop/blittable-and-non-blittable-types)), není nutné žádné speciální kódování, protože tyto datové typy mají stejné reprezentace v paměti, ale složitější datové typy vyžadují explicitní zařazování dat. Příklad naleznete v tématu [Postupy: volání nativních knihoven DLL ze spravovaného kódu pomocí PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).

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

- [Postupy: převod typu System:: String na wchar_t * nebo char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)

- [Postupy: Převod typu System::String na standardní řetězec](../dotnet/how-to-convert-system-string-to-standard-string.md)

- [Postupy: Převod standardního řetězce na typ System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)

- [Postupy: Získání ukazatele na pole bajtů](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)

- [Postupy: Načtení nespravovaných prostředků do bajtového pole](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)

- [Postupy: Změna referenční třídy v nativní funkci](../dotnet/how-to-modify-reference-class-in-a-native-function.md)

- [Postupy: Určení, zda je bitová kopie nativní nebo CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)

- [Postupy: Přidání nativní knihovny DLL do globální mezipaměti sestavení](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)

- [Postupy: Uložení odkazu na typ hodnoty v nativním typu](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)

- [Postupy: Uchování odkazu na objekt v nespravované paměti](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)

- [Postupy: Rozpoznání kompilace/CLR](../dotnet/how-to-detect-clr-compilation.md)

- [Postupy: Převody mezi hodnotami System::Guid a _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)

- [Postupy: Určení výstupního parametru](../dotnet/how-to-specify-an-out-parameter.md)

- [Postupy: použití nativního typu v kompilaci/clr](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)

- [Postupy: Deklarace obslužných rutin v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md)

- [Postupy: Zabalení nativních tříd pro použití v jazyce C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

Informace o používání delegátů ve scénáři interoperability najdete v tématu [DelegateC++ (rozšíření komponent)](../extensions/delegate-cpp-component-extensions.md).

## <a name="see-also"></a>Viz také:

- [Volání nativních funkcí ze spravovaného kódu](../dotnet/calling-native-functions-from-managed-code.md)
