---
title: CString – operace týkající se řetězců ve stylu jazyka C
ms.date: 11/04/2016
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
ms.openlocfilehash: 406a934d3691c7787085cc319770074ac2ee5926
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317945"
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>CString – operace týkající se řetězců ve stylu jazyka C

[CString](../atl-mfc-shared/using-cstring.md) objekt obsahuje data řetězce znaků. `CString`dědí sadu [metod a operátorů,](../atl-mfc-shared/reference/cstringt-class.md) které jsou definovány v šabloně třídy [CStringT](../atl-mfc-shared/reference/cstringt-class.md) pro práci s řetězcovými daty. (`CString` je **typedef,** `CStringT` který se specializuje na práci `CString` s druhem znakových dat, která podporují.)

`CString`neukládá data znaků interně jako řetězec s nulovým ukončeným stylem C. Místo `CString` toho sleduje délku dat znaků tak, aby bylo možné bezpečněji sledovat data a místo, které vyžaduje.

`CString`přijímá řetězce stylu C a poskytuje způsoby přístupu k datům znaků jako řetězec stylu C. Toto téma obsahuje následující části, `CString` které vysvětlují, jak používat objekt, jako by se jednalo o řetězec s nulovým ukončeným stylem C.

- [Převod na řetězce ukončené nulou ve stylu C](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)

- [Práce se standardními funkcemi řetězce knihovny za běhu](#_core_working_with_standard_run.2d.time_library_string_functions)

- [Úprava obsahu CString přímo](#_core_modifying_cstring_contents_directly)

- [Použití objektů CString s funkcemi proměnnéargumentu](#_core_using_cstring_objects_with_variable_argument_functions)

- [Určení formálních parametrů CString](#_core_specifying_cstring_formal_parameters)

## <a name="using-cstring-as-a-c-style-null-terminated-string"></a><a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a>Použití řetězce CString jako řetězce s nulovým ukončeným stylem C

Chcete-li `CString` použít objekt jako řetězec ve stylu C, přetypování objektu LPCTSTR. V následujícím příkladu `CString` vrátí ukazatel pro čtení jen pro čtení c-styl null ukončenřetězec. Funkce `strcpy` vloží kopii řetězce stylu C do `myString`proměnné .

```cpp
CString aCString = "A string";
char myString[256];
strcpy(myString, (LPCTSTR)aCString);
```

Metody můžete `CString` použít například `SetAt`k úpravě jednotlivých znaků v řetězcovém objektu. Ukazatel LPCTSTR je však dočasné a stane se `CString`neplatným při jakékoli změně . Může `CString` také přejít mimo rozsah a být automaticky odstraněny. Doporučujeme získat nový Ukazatel LPCTSTR `CString` objektu pokaždé, když jej použijete.

Někdy můžete potřebovat kopii `CString` dat přímo upravit. Pomocí zabezpečenější `strcpy_s` funkce (nebo `_tcscpy_s`unicode/mbcs-portable) `CString` zkopírujte objekt do samostatné vyrovnávací paměti. Toto je místo, kde lze znaky bezpečně upravit, jak ukazuje následující příklad.

[!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]

> [!NOTE]
> Třetí argument `strcpy_s` (nebo Unicode/MBCS `_tcscpy_s`přenosný) je `const wchar_t*` buď (Unicode) `const char*` nebo (ANSI). Výše uvedený příklad `CString` předá pro tento argument. Kompilátor Jazyka C++ automaticky použije funkci `CString` převodu definovanou pro třídu, která převádí a `CString` na `LPCTSTR`. Schopnost definovat operace přetypování z jednoho typu do druhého je jednou z nejužitečnějších funkcí jazyka C++.

## <a name="working-with-standard-run-time-library-string-functions"></a><a name="_core_working_with_standard_run.2d.time_library_string_functions"></a>Práce se standardními funkcemi řetězce knihovny run-time

Měli byste být schopni `CString` najít metodu k provedení jakékoli operace řetězce, pro které můžete `strcmp` zvážit použití standardní c run-time `_tcscmp`knihovny řetězce funkce, jako je například (nebo Unicode/MBCS-portable ).

Pokud je nutné použít funkce řetězce c run-time, můžete použít techniky popsané v _core_using_cstring_as_a_c.2d.style_null.2d.terminated_string. Objekt můžete `CString` zkopírovat do ekvivalentní vyrovnávací paměti řetězce ve stylu C, provést operace ve vyrovnávací paměti `CString` a pak přiřadit výsledný řetězec stylu C zpět k objektu.

## <a name="modifying-cstring-contents-directly"></a><a name="_core_modifying_cstring_contents_directly"></a>Změna obsahu řetězce CString přímo

Ve většině situací byste `CString` měli použít členské funkce `CString` k úpravě `CString` obsahu objektu nebo k převodu na znakový řetězec ve stylu C.

Existují některé situace, kdy má smysl `CString` přímo upravit obsah, například při práci s funkcemi operačního systému, které vyžadují vyrovnávací paměť znaků.

Metody `GetBuffer` `ReleaseBuffer` a nabízejí přístup k vyrovnávací `CString` paměti vnitřníznak objektu a umožňují jej přímo upravovat. Následující kroky ukazují, jak tyto funkce k tomuto účelu používat.

### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>Použití objektů GetBuffer a ReleaseBuffer pro přístup k vnitřní vyrovnávací paměti znaků objektu CString

1. Volání `GetBuffer` objektu `CString` a určete délku vyrovnávací paměti, kterou požadujete.

1. Pomocí ukazatele vrácené ho `GetBuffer` zapisovat znaky přímo do objektu. `CString`

1. Volání `ReleaseBuffer` objektu `CString` aktualizovat všechny `CString` informace o vnitřním stavu, například délka řetězce. Po úpravě obsahu `CString` objektu přímo, `ReleaseBuffer` musíte volat před `CString` voláním jakékoli jiné členské funkce.

## <a name="using-cstring-objects-with-variable-argument-functions"></a><a name="_core_using_cstring_objects_with_variable_argument_functions"></a>Použití objektů CString s funkcemi proměnné argumenty

Některé funkce Jazyka C mají proměnný počet argumentů. Pozoruhodným příkladem `printf_s`je . Z důvodu způsobu, jakým je tento druh funkce deklarována, kompilátor nemůže být jisti typem argumentů a nemůže určit, kterou operaci převodu provést u každého argumentu. Proto je nezbytné použít explicitní typ přetypování `CString` při předávání objektu do funkce, která má proměnný počet argumentů.

Chcete-li `CString` použít objekt ve funkci proměnné `CString` argument, explicitně přetypování na řetězec LPCTSTR, jak je znázorněno v následujícím příkladu.

[!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]

## <a name="specifying-cstring-formal-parameters"></a><a name="_core_specifying_cstring_formal_parameters"></a>Určení formálních parametrů řetězce CString

Pro většinu funkcí, které potřebují argument řetězce, je nejlepší zadat formální `const` parametr v`LPCTSTR`prototypu funkce `CString`jako ukazatel na znak ( ) namísto . Pokud je formální parametr `const` zadán jako ukazatel na znak, můžete předat buď ukazatel na pole`"hi there"`TCHAR, literálový řetězec [ ], nebo `CString` objekt. Objekt `CString` bude automaticky převeden na LPCTSTR. Jakékoliv místo, kde můžete použít LPCTSTR, `CString` můžete také použít objekt.

Můžete také zadat formální parametr jako odkaz na `const CString&`konstantní řetězec (to znamená), pokud argument nebude změněn. Přetažení **const** modifikátor, pokud řetězec bude změněn funkcí. Pokud je požadována výchozí hodnota null, inicializujte ji na nulový řetězec [`""`], jak je znázorněno níže:

[!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]

U většiny výsledků funkce můžete `CString` jednoduše vrátit objekt podle hodnoty.

## <a name="see-also"></a>Viz také

[Řetězce (KNIHOVNA ATL/Knihovna Knihovny AFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CString – předávání argumentů](../atl-mfc-shared/cstring-argument-passing.md)
