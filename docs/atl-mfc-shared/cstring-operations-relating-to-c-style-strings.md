---
title: CString – operace týkající se řetězců ve stylu jazyka C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, basic operations
- MFC [C++], string handling class
- string conversion [C++], C-style strings
- strings [C++], string operations
- standard run-time library string functions
- null values, Null-terminated string conversion
- string functions
- strings [C++], in C
- string arguments
- C-style strings
- strings [C++], class CString
- casting CString objects
ms.assetid: 5048de8a-5298-4891-b8a0-c554b5a3ac1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 765cb6ccf24415c174761c57268dc79e1fc6845b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062558"
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>CString – operace týkající se řetězců ve stylu C

A [CString](../atl-mfc-shared/using-cstring.md) objektu obsahuje znak řetězec data. `CString` dědí sadu [metody a operátory](../atl-mfc-shared/reference/cstringt-class.md) , která jsou definována v šabloně třídy [CStringT](../atl-mfc-shared/reference/cstringt-class.md) pro práci s řetězcovými daty. (`CString` je **typedef** , který se specializuje `CStringT` pracovat, jaká data znak, který `CString` podporuje.)

`CString` neukládá znaková data interně jako řetězec stylu C zakončený hodnotou null. Místo toho `CString` sleduje délku znaková data tak, aby lépe zabezpečený můžete sledovat data a prostor vyžaduje.

`CString` přijímají řetězce ve stylu jazyka C a nabízí způsobů, jak získat přístup k datům znak jako řetězec stylu C. Toto téma obsahuje následující oddíly, které vysvětlují, jak používat `CString` objekt, jako by byly řetězec stylu C zakončený hodnotou null.

- [Převádění řetězců ve stylu C zakončený hodnotou null](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)

- [Práce s řetězci funkce standardní knihovny run-time](#_core_working_with_standard_run.2d.time_library_string_functions)

- [Úprava CString obsah přímo](#_core_modifying_cstring_contents_directly)

- [CString – objekty pomocí funkce argumentů proměnných](#_core_using_cstring_objects_with_variable_argument_functions)

- [Určení CString formální parametry.](#_core_specifying_cstring_formal_parameters)

##  <a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a> CString – použití jako řetězec stylu C zakončený hodnotou Null

Použití `CString` objektu jako řetězec stylu C, objekt přetypujte na LPCTSTR. V následujícím příkladu `CString` vrací ukazatel jen pro čtení ve stylu jazyka C řetězec zakončený hodnotou null. `strcpy` Funkce vloží kopii řetězce ve stylu jazyka C v proměnné `myString`.

```cpp
CString aCString = "A string";
char myString[256];
strcpy(myString, (LPCTSTR)aCString);
```

Můžete použít `CString` metody, například `SetAt`můžete upravit jednotlivé znaky na objekt řetězce. Ale LPCTSTR ukazatel je dočasný a níže uvedených situací při jakékoli změně `CString`. `CString` Můžete také přejít mimo rozsah a automaticky se neodstraní. Doporučujeme, abyste měli čerstvé LPCTSTR ukazatel `CString` objektu pokaždé, když použijete jednu.

Někdy můžete potřebovat kopii `CString` data upravovat přímo. Použijte funkci bezpečnější `strcpy_s` (nebo Unicode a MBCS-přenosné `_tcscpy_s`) ke kopírování `CString` objektu do samostatných vyrovnávací paměti. To je, kde je možné bezpečně upravit znaků, jak je znázorněno v následujícím příkladu.

[!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]

> [!NOTE]
> Třetí argument `strcpy_s` (nebo Unicode a MBCS-přenosné `_tcscpy_s`) je buď `const wchar_t*` (Unicode) nebo `const char*` (ANSI). V příkladu výše průchody `CString` pro tento argument. Kompilátor C++ automaticky použije funkce pro převod definovaný pro `CString` třídu, která převede `CString` do `LPCTSTR`. Schopnost definovat operace přetypování z jednoho typu na jiný je mezi nejužitečnější funkce jazyka C++.

##  <a name="_core_working_with_standard_run.2d.time_library_string_functions"></a> Práce s řetězci funkce standardní knihovny Run-Time

Byste měli najít `CString` metoda provádět jakékoli operace řetězců, pro které můžete zvážit použití funkce řetězec standardní knihovny run-time jazyka C, jako `strcmp` (nebo Unicode a MBCS-přenosné `_tcscmp`).

Pokud je nutné použít funkce jazyka C za běhu řetězce, můžete použít techniky popsané v _core_using_cstring_as_a_c.2d.style_null.2d.terminated_string. Můžete zkopírovat `CString` objektu do vyrovnávací paměti ekvivalentní řetězce ve stylu jazyka C, provádění operací na vyrovnávací paměť a potom přiřadit výsledný řetězec C-style zpět do `CString` objektu.

##  <a name="_core_modifying_cstring_contents_directly"></a> Úprava CString obsah přímo

Ve většině případů byste měli použít `CString` členské funkce, chcete-li změnit obsah `CString` objektu nebo k převodu `CString` na řetězec znaků C-style.

To bude dávat smysl přímo upravit v některých situacích `CString` obsah, například při práci s funkcemi operačního systému, které vyžadují vyrovnávací paměti pro znaky.

`GetBuffer` a `ReleaseBuffer` metody poskytují přístup k interní znak vyrovnávací paměť `CString` objektu a umožňují upravovat přímo. Následující kroky ukazují, jak používat tyto funkce pro tento účel.

### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>Použití getbuffer – a ReleaseBuffer pro přístup k vyrovnávací paměti pro interní znaky CString objektu

1. Volání `GetBuffer` pro `CString` a určení délku vyrovnávací paměti, budete potřebovat.

1. Použít ukazatele vrácené `GetBuffer` pro zápis znaků do přímo `CString` objektu.

1. Volání `ReleaseBuffer` pro `CString` objektu k aktualizaci všech interní `CString` informace, například délku řetězce stavu. Když upravíte obsah `CString` objektu přímo, je nutné volat `ReleaseBuffer` před voláním jakékoli jiné `CString` členské funkce.

##  <a name="_core_using_cstring_objects_with_variable_argument_functions"></a> CString – objekty pomocí funkce argumentů proměnných

Některé funkce C přijímají proměnný počet argumentů. Je důležité příklad `printf_s`. Kvůli způsobu, jakým tento druh funkce je deklarovaná kompilátor nemůže být jisti typ argumentů a nemůže určit, kterou převod operaci má provést pro každý argument. Proto je důležité použít explicitní typ přetypování při předávání `CString` objekt funkce, která přijímá proměnný počet argumentů.

Použití `CString` objektu ve funkci argumentů s proměnnou délkou explicitně přetypován `CString` LPCTSTR řetězec, jak je znázorněno v následujícím příkladu.

[!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]

##  <a name="_core_specifying_cstring_formal_parameters"></a> Určení CString formální parametry

Pro většinu funkcí, které vyžadují jako argument řetězec je nejvhodnější k určení formálních parametrů v prototypu funkce jako `const` ukazatel na znak (`LPCTSTR`) místo `CString`. Pokud je formální parametr zadán jako `const` ukazatel na znak, můžete předat buď ukazatele na pole TCHAR, řetězcový literál [`"hi there"`], nebo `CString` objektu. `CString` Objektu se automaticky převedou na LPCTSTR. Můžete použít LPCTSTR jakéhokoli místa, můžete použít také `CString` objektu.

Formální parametr můžete také určit jako odkaz na konstanty typu řetězec (to znamená `const CString&`) Pokud tento argument se nezmění. Přetáhněte **const** modifikátor Pokud řetězec se upravit funkci. V případě potřeby je výchozí hodnota null, inicializovat jej na řetězec s hodnotou null [`""`], jak je znázorněno níže:

[!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]

Pro většinu funkcí výsledky, můžete jednoduše vrátit `CString` objektu podle hodnoty.

## <a name="see-also"></a>Viz také

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CString – předávání argumentů](../atl-mfc-shared/cstring-argument-passing.md)
