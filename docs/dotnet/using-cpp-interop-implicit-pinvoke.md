---
title: "Pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1f400ed3e93af8f7e0727d3fe378d0ac471bd18f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-c-interop-implicit-pinvoke"></a>Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)
Na rozdíl od jiných jazyků .NET, Visual C++ má interoperabilita podpory, který umožňuje spravovanými a nespravovanými kód existovat ve stejné aplikaci a to i ve stejném souboru (s [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy). To umožňuje vývojářům Visual C++ integrovat funkce .NET do stávajících aplikací Visual C++ bez narušení zbývající aplikace.  
  
 Nespravované funkce můžete také volat z spravované kompilace pomocí [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
 Implicitní PInvoke je užitečné, když není potřeba zadat jak zařazeno parametry funkce nebo některé podrobnosti, které je možné zadat při explicitním volání DllImportAttribute.  
  
 Visual C++ nabízí dva způsoby, kterými spravovaných a nespravovaných funkcí pro spolupráci:  
  
-   [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
 Explicitního volání PInvoke podporuje rozhraní .NET Framework a je dostupný ve většině jazyků .NET. Ale jak již název napovídá, zprostředkovatele komunikace C++ je specifické pro aplikaci Visual C++.  
  
## <a name="c-interop"></a>interoperabilita C++  
 Interoperabilita C++ se doporučuje namísto explicitního volání PInvoke, protože poskytuje lepší zabezpečení typů, je obvykle méně náročná na implementaci, je více forgiving, pokud nespravovaného rozhraní API se mění a umožňuje vylepšení výkonu, které nejsou možné pomocí explicitní PInvoke. Interoperabilita C++ však není možné, pokud není k dispozici nespravovaný zdrojový kód, nebo když kompilujete s **/CLR: safe**. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015. Informace najdete v tématu [prázdná a ověřitelný kód (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
## <a name="c-com-interop"></a>interoperabilita C++ COM  
 Funkce interoperability podporované Visual C++ nabízí konkrétní výhody oproti jinými jazyky rozhraní .NET, pokud jde o vzájemné spolupráci se službou COM – součásti. Namísto omezení rozhraní .NET Framework [Tlbimp.exe (Importér knihovny)](/dotnet/framework/tools/tlbimp-exe-type-library-importer), jako je například omezenou podporu pro datové typy a povinné vystavení každého člena každé rozhraní modelu COM, umožňuje Interoperabilita C++ COM součástí získat přístup na adrese bude a nevyžaduje samostatnou spolupráce – sestavení. Další informace najdete v tématu [pomocí modelu COM pomocí technologie .NET](http://msdn.microsoft.com/en-us/03976661-6278-4227-a6c1-3b3315502c15).  
  
## <a name="blittable-types"></a>Přenositelné typy  
 Pro nespravovaná rozhraní API, používat jednoduché, vlastní typy (viz [přenositelné a Non-přenositelné typy](http://msdn.microsoft.com/Library/d03b050e-2916-49a0-99ba-f19316e5c1b3)), není vyžadováno žádné speciální kódování, protože tyto typy dat mají stejnou reprezentaci v paměti, ale vyžadují komplexnější datové typy explicitní dat – zařazování. Příklad, naleznete v části [postupy: volání nativních knihoven DLL ze spravovaného kódu pomocí PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md).  
  
## <a name="example"></a>Příklad  
  
```  
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
  
-   [Postupy: Zařazování řetězců ANSI pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [Postupy: Zařazování řetězců kódování Unicode pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
-   [Postupy: Zařazování struktur pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-structures-using-cpp-interop.md)  
  
-   [Postupy: Zařazování polí pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-arrays-using-cpp-interop.md)  
  
-   [Postupy: zařazování zpětných volání a delegátů pomocí funkcí interoperability C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
-   [Postupy: zařazení vložených ukazatelů pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md)  
  
-   [Postupy: přístup ke znakům v datech třídy System::String](../dotnet/how-to-access-characters-in-a-system-string.md)  
  
-   [Postupy: převedení char * řetězce na pole System::Byte](../dotnet/how-to-convert-char-star-string-to-system-byte-array.md)  
  
-   [Postupy: převod typu System::String na wchar_t * nebo char\*](../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)  
  
-   [Postupy: převod typu System::String na standardní řetězec](../dotnet/how-to-convert-system-string-to-standard-string.md)  
  
-   [Postupy: převod standardního řetězce na typ System::String](../dotnet/how-to-convert-standard-string-to-system-string.md)  
  
-   [Postupy: získání ukazatele na pole bajtů](../dotnet/how-to-obtain-a-pointer-to-byte-array.md)  
  
-   [Postupy: načtení nespravovaných prostředků do bajtového pole](../dotnet/how-to-load-unmanaged-resources-into-a-byte-array.md)  
  
-   [Postupy: Změna referenční třídy v nativní funkci](../dotnet/how-to-modify-reference-class-in-a-native-function.md)  
  
-   [Postupy: určení, pokud bitová kopie je nativní nebo CLR](../dotnet/how-to-determine-if-an-image-is-native-or-clr.md)  
  
-   [Postupy: Přidání nativní knihovny DLL do globální mezipaměti sestavení](../dotnet/how-to-add-native-dll-to-global-assembly-cache.md)  
  
-   [Postupy: uložení odkazu na typ hodnoty v nativním typu](../dotnet/how-to-hold-reference-to-value-type-in-native-type.md)  
  
-   [Postupy: uchování odkazu na objekt v nespravované paměti](../dotnet/how-to-hold-object-reference-in-unmanaged-memory.md)  
  
-   [Postupy: zjištění kompilaci/CLR](../dotnet/how-to-detect-clr-compilation.md)  
  
-   [Postupy: převod mezi hodnotami System::Guid a _GUID](../dotnet/how-to-convert-between-system-guid-and-guid.md)  
  
-   [Postupy: určení výstupního parametru](../dotnet/how-to-specify-an-out-parameter.md)  
  
-   [Postupy: použití nativního typu v kompilaci/CLR](../dotnet/how-to-use-a-native-type-in-a-clr-compilation.md)  
  
-   [Postupy: deklarace obslužných rutin v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md)  
  
-   [Postupy: zabalení nativních tříd pro použití v jazyce C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
 Informace o použití delegátů ve scénáři interoperability najdete v tématu [delegáta (rozšíření komponent C++)](../windows/delegate-cpp-component-extensions.md).  
  
## <a name="see-also"></a>Viz také  
 [Volání nativních funkcí ze spravovaného kódu](../dotnet/calling-native-functions-from-managed-code.md)