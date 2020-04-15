---
title: Přehled zařazování v jazyku C++
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
ms.openlocfilehash: 0c7bf18fa823c6301a79c3f989efa73c9e8f628a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372000"
---
# <a name="overview-of-marshaling-in-ccli"></a>Přehled zařazování v jazyce C++/CLI

Ve smíšeném režimu někdy musí být data mezi nativními a spravovanými typy. *Zařazovací knihovna* vám pomůže zařadit a převést data jednoduchým způsobem.  Zařazování knihovny se skládá `marshal_context` ze sady funkcí a třídy, které provádějí zařazování pro běžné typy. Knihovna je definována v těchto záhlavích v adresáři **include/msclr** pro edici Visual Studio:

|Hlavička|Popis|
|---------------|-----------------|
|maršál.h|`marshal_context`třídní a bezkontextové zařazovací funkce|
|marshal_atl.h| Funkce pro zařazování typů ATL|
|marshal_cppstd.h|Funkce pro zařazování standardních typů jazyka C++|
|marshal_windows.h|Funkce pro zařazování typů systému Windows|

Výchozí cesta pro složku **MSCLR** je něco takového v závislosti na tom, kterou edici máte, a číslo sestavení:

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

Knihovnu zařazování můžete použít s [marshal_context třídou](../dotnet/marshal-context-class.md)nebo bez ní . Některé převody vyžadují kontext. Další převody lze implementovat pomocí [funkce marshal_as.](../dotnet/marshal-as.md) V následující tabulce jsou uvedeny aktuální podporované převody, zda vyžadují kontext a jaký soubor marshalu musíte zahrnout:

|Od typu|Chcete-li zadat|Metoda marshal|Zahrnout soubor|
|---------------|-------------|--------------------|------------------|
|Systém::Řetězec^|const char\*|marshal_context|maršál.h|
|const char\*|Systém::Řetězec^|marshal_as|maršál.h|
|Char\*|Systém::Řetězec^|marshal_as|maršál.h|
|Systém::Řetězec^|wchar_t\*|marshal_context|maršál.h|
|wchar_t\*|Systém::Řetězec^|marshal_as|maršál.h|
|Wchar_t\*|Systém::Řetězec^|marshal_as|maršál.h|
|Systém::IntPtr|Zpracování|marshal_as|marshal_windows.h|
|Zpracování|Systém::IntPtr|marshal_as|marshal_windows.h|
|Systém::Řetězec^|Bstr|marshal_context|marshal_windows.h|
|Bstr|Systém::Řetězec^|marshal_as|maršál.h|
|Systém::Řetězec^|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|Systém::Řetězec^|marshal_as|marshal_windows.h|
|Systém::Řetězec^|std::řetězec|marshal_as|marshal_cppstd.h|
|std::řetězec|Systém::Řetězec^|marshal_as|marshal_cppstd.h|
|Systém::Řetězec^|std::wstring|marshal_as|marshal_cppstd.h|
|std::wstring|Systém::Řetězec^|marshal_as|marshal_cppstd.h|
|Systém::Řetězec^|CStringT\<char>|marshal_as|marshal_atl.h|
|CStringT\<char>|Systém::Řetězec^|marshal_as|marshal_atl.h|
|Systém::Řetězec^|wchar_t> wchar_t CString<T|marshal_as|marshal_atl.h|
|wchar_t> wchar_t CString<T|Systém::Řetězec^|marshal_as|marshal_atl.h|
|Systém::Řetězec^|CComBSTR|marshal_as|marshal_atl.h|
|CComBSTR|Systém::Řetězec^|marshal_as|marshal_atl.h|

Zařazování vyžaduje kontext pouze v případě, že zařazujete ze spravovaných na nativních datových typů a nativní typ, na který převádíte, nemá destruktor pro automatické vyčištění. Kontext zařazování zničí přidělený nativní datový typ v jeho destruktoru. Proto převody, které vyžadují kontext bude platný pouze do odstranění kontextu. Chcete-li uložit všechny zařazované hodnoty, je nutné zkopírovat hodnoty do vlastních proměnných.

> [!NOTE]
> Pokud jste vložili `NULL`s v řetězci, výsledek zařazování řetězce není zaručena. Vložené `NULL`s může způsobit, že řetězec zkrácen nebo mohou být zachovány.

Tento příklad ukazuje, jak zahrnout adresář msclr do deklarace hlavičky include:

`#include "msclr\marshal_cppstd.h"`

Zařazovací knihovna je rozšiřitelná, takže můžete přidat vlastní typy zařazování. Další informace o rozšíření zařazovací knihovny naleznete v [tématu How to: Extend the Marshaling Library](../dotnet/how-to-extend-the-marshaling-library.md).

## <a name="see-also"></a>Viz také

[Knihovna podpory C++](../dotnet/cpp-support-library.md)<br/>
[Postupy: Rozšíření knihovny zařazování](../dotnet/how-to-extend-the-marshaling-library.md)
