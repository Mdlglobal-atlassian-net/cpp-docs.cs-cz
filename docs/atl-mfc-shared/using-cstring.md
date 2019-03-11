---
title: CString – použití
ms.date: 06/18/2018
helpviewer_keywords:
- CString objects, C++ string manipulation
- CString objects, reference counting
- CString class (Visual C++)
ms.assetid: ed018aaf-8b10-46f9-828c-f9c092dc7609
ms.openlocfilehash: a84ae21b60d87971cb2f7b758dd369b4078607e6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740305"
---
# <a name="using-cstring"></a>CString – použití

Témata v této části popisují, jak programovat s `CString`. Referenční dokumentaci ke službě `CString` naleznete v dokumentaci k [CStringT](../atl-mfc-shared/reference/cstringt-class.md).

Použití `CString`, zahrnout `atlstr.h` záhlaví.

`CString`, `CStringA`, A `CStringW` třídy jsou specializace šablony třídy volá [CStringT](../atl-mfc-shared/reference/cstringt-class.md) na základě typu podporují znaková data.

A `CStringW` obsahuje objekt **wchar_t** zadejte a podporuje řetězců v kódu Unicode. A `CStringA` obsahuje objekt **char** typu a řetězce podporuje jednobajtové a vícebajtové (znakové sady MBCS). A `CString` objekt podporuje buď **char** typu nebo `wchar_t` typu, v závislosti na tom, zda je definován symbol znakové sady MBCS nebo kódování UNICODE v době kompilace.

A `CString` objekt znaková data uchová `CStringData` objektu. `CString` přijímá řetězec zakončený hodnotou NULL C-style. `CString` sleduje řetězec délky pro vyšší výkon, ale také zachová znak NULL v datech uložených znak pro podporu převodu na LPCWSTR. `CString` Exportuje řetězce ve stylu jazyka C zahrnuje ukončovacího znaku null. Můžete vložit s hodnotou NULL v jiných umístěních v `CString`, ale to může vést k neočekávaným výsledkům.

Následující sadu tříd řetězců je možné bez knihovny MFC, s nebo bez podpory CRT propojení: `CAtlString`, `CAtlStringA`, a `CAtlStringW`.

`CString` se používá v nativní projekty. Pro spravovaný kód (C + +/ CLI) projekty, používají `System::String`.

Chcete-li přidat více možností než `CString`, `CStringA`, nebo `CStringW` aktuálně nabídnout, měli byste vytvořit podtřídu `CStringT` , který obsahuje další funkce.

Následující kód ukazuje, jak vytvořit `CString` a tisku na standardní výstup:

```cpp
#include <atlstr.h>

int main() {
    CString aCString = CString(_T("A string"));
    _tprintf(_T("%s"), (LPCTSTR) aCString);
}
```

## <a name="in-this-section"></a>V tomto oddílu

[CString – základní operace](../atl-mfc-shared/basic-cstring-operations.md)<br/>
Popisuje základní `CString` operace, včetně vytváření objektů z řetězcové literály jazyka C, přístup k jednotlivé znaky `CString`zřetězení dvou objektů a porovnání `CString` objekty.

[Správa řetězcových dat](../atl-mfc-shared/string-data-management.md)<br/>
Popisuje použití kódování Unicode a MBCS s `CString`.

[CString – sémantika](../atl-mfc-shared/cstring-semantics.md)<br/>
Vysvětluje, jak `CString` objekty se používají.

[CString – operace týkající se řetězců ve stylu jazyka C](../atl-mfc-shared/cstring-operations-relating-to-c-style-strings.md)<br/>
Popisuje práce s obsahem `CString` objekt jako řetězec stylu C zakončený hodnotou null.

[Přidělování a uvolňování pro BSTR](../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md)<br/>
Tento článek popisuje použití paměti pro BSTR a modelu COM objekty.

[CString – čištění výjimek](../atl-mfc-shared/cstring-exception-cleanup.md)<br/>
Vysvětluje, že explicitní vyčištění v MFC 3.0 a novější už nejsou potřebná.

[CString – předávání argumentů](../atl-mfc-shared/cstring-argument-passing.md)<br/>
Vysvětluje, jak předat CString – objekty funkce a jak vrátit `CString` objekty z funkce.

[Podpora znakových sad Unicode a MBCS](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)<br/>
Popisuje, jak MFC je povolená pro kódování Unicode a MBCS podporovat.

## <a name="reference"></a>Odkaz

[CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Poskytuje referenční informace o `CStringT` třídy.

[CSimpleStringT – třída](../atl-mfc-shared/reference/csimplestringt-class.md)<br/>
Poskytuje referenční informace o `CSimpleStringT` třídy.

## <a name="related-sections"></a>Související oddíly

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
Obsahuje odkazy na témata, která popisují několik způsobů, jak spravovat data řetězce.

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
