---
title: Přehled zařazování v jazyku C++
ms.date: 06/28/2018
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
ms.openlocfilehash: 9e3b8f561ce6609eb2afedb527a16c4803f69c53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384735"
---
# <a name="overview-of-marshaling-in-c"></a>Přehled zařazování v jazyku C++

Ve smíšeném režimu někdy musíte zařazování dat mezi nativními a spravovanými typy. Visual Studio 2008 zavedené *zařazovací knihovna* umožňující zařazování a převádí data v jednoduché.  Zařazovací knihovna se skládá ze sady funkcí a `marshal_context` třídy, které provádějí zařazování pro běžné typy. Knihovny je definován v těchto záhlavích v **zahrnují/msclr –** adresář pro vaši verzi sady Visual Studio:

|Záhlaví|Popis|
|---------------|-----------------|
|marshal.h|`marshal_context` třídy a volného kontext zařazování funkce|
|marshal_atl.h| Funkce pro zařazování typů knihovny ATL|
|marshal_cppstd.h|Funkce pro zařazování typů standardní C++|
|marshal_windows.h|Funkce pro zařazování typů Windows|

Výchozí cesta pro **msclr –** složka je asi takhle nějak. v závislosti na tom, jakou verzi máte a číslo sestavení:

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

Můžete použít zařazovací knihovna, s nebo bez něj [marshal_context Class](../dotnet/marshal-context-class.md). Některé převody vyžadují kontextu. Ostatní převody, které je možné implementovat pomocí [marshal_as](../dotnet/marshal-as.md) funkce. V následující tabulce jsou uvedeny aktuální převodů podporovaných, zda vyžaduje kontext a jaké zařazování souboru je nutné zahrnout:

|Z typu|Na typ|Zařazování – metoda|Zahrnout soubor|
|---------------|-------------|--------------------|------------------|
|System::String ^|const char \*|marshal_context|marshal.h|
|const char \*|System::String ^|marshal_as|marshal.h|
|Char \*|System::String ^|marshal_as|marshal.h|
|System::String ^|Const wchar_t\*|marshal_context|marshal.h|
|const wchar_t \*|System::String ^|marshal_as|marshal.h|
|wchar_t \*|System::String ^|marshal_as|marshal.h|
|System::IntPtr|POPISOVAČ|marshal_as|marshal_windows.h|
|POPISOVAČ|System::IntPtr|marshal_as|marshal_windows.h|
|System::String ^|BSTR|marshal_context|marshal_windows.h|
|BSTR|System::String ^|marshal_as|marshal.h|
|System::String ^|bstr_t|marshal_as|marshal_windows.h|
|bstr_t|System::String ^|marshal_as|marshal_windows.h|
|System::String ^|std::string|marshal_as|marshal_cppstd.h|
|std::string|System::String ^|marshal_as|marshal_cppstd.h|
|System::String ^|std::wstring|marshal_as|marshal_cppstd.h|
|std::wstring|System::String ^|marshal_as|marshal_cppstd.h|
|System::String ^|CStringT\<char>|marshal_as|marshal_atl.h|
|CStringT\<char>|System::String ^|marshal_as|marshal_atl.h|
|System::String ^|CStringT<wchar_t>|marshal_as|marshal_atl.h|
|CStringT<wchar_t>|System::String ^|marshal_as|marshal_atl.h|
|System::String ^|CComBSTR|marshal_as|marshal_atl.h|
|CComBSTR|System::String ^|marshal_as|marshal_atl.h|

Zařazování vyžaduje kontext pouze při zařazení ze spravované do nativní datové typy a nativní typ, který převádíte na nemá destruktor pro automatické čištění. Zařazování kontextu zničí přidělené nativního datového typu ve svém destruktoru. Převody, které vyžadují kontext proto bude platit pouze do kontextu se odstraní. Chcete-li uložit všechny hodnoty zařazené, musíte zkopírovat hodnoty do vlastní proměnné.

> [!NOTE]
>  Pokud jste vložili `NULL`s do řetězce, výsledek zařazování řetězce není zaručena. Vložený `NULL`s může způsobit, že řetězec, který má být zkrácen nebo může být zachována.

Tento příklad ukazuje, jak zahrnout adresář msclr – deklarace zahrnout záhlaví:

`#include "msclr\marshal_cppstd.h"`

Knihovna zařazování je rozšiřitelný, kde můžete přidat vlastní zařazování typů. Další informace o rozšíření knihovny zařazování, naleznete v tématu [jak: Rozšíření knihovny zařazování](../dotnet/how-to-extend-the-marshaling-library.md).

V dřívějších verzích by mohla zařazování dat s využitím [vyvolání platformy](/dotnet/framework/interop/consuming-unmanaged-dll-functions). Další informace o `PInvoke`, naleznete v tématu [volání nativních funkcí ze spravovaného kódu](../dotnet/calling-native-functions-from-managed-code.md).

## <a name="see-also"></a>Viz také:

[Knihovna podpory C++](../dotnet/cpp-support-library.md)<br/>
[Postupy: Rozšíření knihovny zařazování](../dotnet/how-to-extend-the-marshaling-library.md)
