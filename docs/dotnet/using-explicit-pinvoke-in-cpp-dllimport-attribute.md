---
title: Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
ms.openlocfilehash: ee9d77920f04f7eba5112c66a906b02b7fc4a658
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740534"
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)

Rozhraní .NET Framework poskytuje explicitní nespravovaného kódu (PInvoke) funkce s `Dllimport` atribut povolit spravovaným aplikacím volání nespravovaných funkcí zabalené uvnitř knihovny DLL. Vyžádáním explicitního volání PInvoke v situacích, kde nespravované rozhraní API jsou dodávány jako knihovny DLL a zdrojový kód není k dispozici. Volání Win32 funkcí, například vyžaduje PInvoke. Jinak použijte implicitní P {Invoke; viz [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md) Další informace.

PInvoke pracuje s použitím <xref:System.Runtime.InteropServices.DllImportAttribute>. Tento atribut, který přebírá název knihovny DLL jako svůj první argument, je umístěn před deklaraci funkce pro každý vstupní bod knihovny DLL, který se použije. Signatura funkce musí odpovídat názvu funkce exportovaných knihovnou DLL (ale některé převod typu mohou být provedeny implicitně definováním `DllImport` deklarace z hlediska spravovaných typů.)

Výsledkem je spravovaný vstupní bod pro každý nativní funkce knihovny DLL, který obsahuje nezbytné přechod code (nebo převodní rutina) a jednoduché datové převody. Spravované funkce potom může volat do knihovny DLL pomocí těchto vstupní body. Spravuje úplně kódu vložen do modulu jako výsledek volání PInvoke.

## <a name="in-this-section"></a>V tomto oddílu

- [Volání nativních funkcí ze spravovaného kódu](../dotnet/calling-native-functions-from-managed-code.md)

- [Postupy: Volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)

- [Postupy: Zařazování řetězců pomocí služby PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)

- [Postupy: Zařazování struktur pomocí služby PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)

- [Postupy: Zařazování polí pomocí služby PInvoke](../dotnet/how-to-marshal-arrays-using-pinvoke.md)

- [Postupy: Zařazování ukazatelů na funkce pomocí služby PInvoke](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)

- [Postupy: Zařazování vložených ukazatelů pomocí služby PInvoke](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)

## <a name="see-also"></a>Viz také:

[Volání nativních funkcí ze spravovaného kódu](../dotnet/calling-native-functions-from-managed-code.md)
