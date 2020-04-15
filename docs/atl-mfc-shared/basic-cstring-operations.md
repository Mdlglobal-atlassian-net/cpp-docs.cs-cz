---
title: CString – základní operace
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects, basic operations
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
ms.openlocfilehash: 68947dc37e5398ac7caa4754e9af40223cec7bf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317951"
---
# <a name="basic-cstring-operations"></a>CString – základní operace

Toto téma vysvětluje následující základní operace [CString:](../atl-mfc-shared/reference/cstringt-class.md)

- [Vytváření objektů CString ze standardních řetězců literálu C](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [Přístup k jednotlivým znakům v řetězci CString](#_core_accessing_individual_characters_in_a_cstring)

- [Zřetězení dvou objektů CString](#_core_concatenating_two_cstring_objects)

- [Porovnání objektů CString](#_core_comparing_cstring_objects)

- [Převod objektů CString](#_core_converting_cstring_objects)

`Class CString`je založen na třídě [CStringT třídy .](../atl-mfc-shared/reference/cstringt-class.md) `CString`je **typedef** `CStringT`. Přesněji, `CString` je **typedef** *explicitní specializace* `CStringT`, což je běžný způsob, jak použít šablonu třídy k definování třídy. Podobně definované třídy jsou `CStringA` a `CStringW`.

`CString`, `CStringA`a `CStringW` jsou definovány v atlstr.h. `CStringT`je definována v cstringt.h.

`CString`, `CStringA`a `CStringW` každý získat sadu metod a `CStringT` operátorů definovaných pro použití s řetězcová data, která podporují. Některé metody duplikovat a v některých případech překonat řetězec služby c run-time knihoven.

Poznámka: `CString` je nativní třída. Pro třídu řetězce, která je pro použití v projektu `System.String`spravovaném c++/CLI, použijte .

## <a name="creating-cstring-objects-from-standard-c-literal-strings"></a><a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>Vytváření objektů CString ze standardních řetězců literálu C

Řetězce literálu ve stylu C `CString` můžete přiřadit stejně `CString` jako jeden objekt druhému.

- Přiřaďte `CString` objektu hodnotu řetězce literálu C.

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- Přiřaďte `CString` hodnotu `CString` jednoho k jinému objektu.

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   Obsah objektu `CString` se zkopíruje, `CString` když je jeden objekt přiřazen jinému objektu. Proto dva řetězce nesdílejí odkaz na skutečné znaky, které tvoří řetězec. Další informace o použití `CString` objektů jako hodnot naleznete v tématu [CString Sémantiku](../atl-mfc-shared/cstring-semantics.md).

   > [!NOTE]
   > Chcete-li napsat aplikaci tak, aby mohla být kompilována pro Kódování Unicode nebo pro ANSI, kódové řetězce literálu pomocí _T makra. Další informace naleznete [v tématu Podpora znakové sady Unicode a vícebajtové znakové sady (MBCS).](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

## <a name="accessing-individual-characters-in-a-cstring"></a><a name="_core_accessing_individual_characters_in_a_cstring"></a>Přístup k jednotlivým znakům v řetězci CString

K jednotlivým znakům `CString` v objektu `GetAt` `SetAt` můžete přistupovat pomocí metod a. Můžete také použít element pole nebo dolní index operátoru `GetAt` ( [ ] ) namísto získání jednotlivých znaků. (To se podobá přístup u prvků pole podle indexu, jako ve standardních řetězcích stylu C.) Hodnoty indexu `CString` pro znaky jsou od nuly.

## <a name="concatenating-two-cstring-objects"></a><a name="_core_concatenating_two_cstring_objects"></a>Zřetězení dvou objektů CString

Chcete-li zřetězit dva `CString` objekty, použijte operátory zřetězení (+ nebo +=), následujícím způsobem.

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

Alespoň jeden argument operátorů zřetězení (+ nebo `CString` +=) musí být objekt, ale můžete `"big"`použít řetězec konstantní znak (například) nebo **znak** (například 'x') pro jiný argument.

## <a name="comparing-cstring-objects"></a><a name="_core_comparing_cstring_objects"></a>Porovnání objektů CString

Metoda `Compare` a operátor == `CString` pro jsou ekvivalentní. `Compare`, **operator==** `CompareNoCase` , a jsou mbcs a unicode vědomi; `CompareNoCase` také malá a velká písmena. Metoda `Collate` `CString` je národní prostředí citlivé a je `Compare`často pomalejší než . Používejte `Collate` pouze v případě, že je nutné dodržovat pravidla řazení určená aktuálním národním prostředím.

V následující tabulce jsou uvedeny dostupné funkce porovnání [CString](../atl-mfc-shared/reference/cstringt-class.md) a jejich ekvivalentní funkce Přenosné Unicode/MBCS v knihovně c run-time.

|CString|MBCS|Unicode|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

Šablona `CStringT` třídy definuje relační \<operátory (<, =, >=, >, ==a !=), které jsou k dispozici pro použití . `CString` Můžete porovnat `CStrings` dva pomocí těchto operátorů, jak je znázorněno v následujícím příkladu.

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

## <a name="converting-cstring-objects"></a><a name="_core_converting_cstring_objects"></a>Převod objektů CString

Informace o převodu objektů CString na jiné typy řetězců naleznete v tématu [How to: Convert Between Various String Types](../text/how-to-convert-between-various-string-types.md).

## <a name="using-cstring-with-wcout"></a>Použití CString s wcout

Chcete-li použít `wcout` CString s musíte explicitně přetypovat objekt, `const wchar_t*` jak je znázorněno v následujícím příkladu:

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

Bez přetypádky `cs` je `void*` `wcout` považován za a a vytiskne adresu objektu. Toto chování je způsobeno jemné interakce mezi odpočet argument šablony a rozlišení přetížení, které jsou samy o sobě správné a v souladu se standardem C++.

## <a name="see-also"></a>Viz také

[Řetězce (KNIHOVNA ATL/Knihovna Knihovny AFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT – třída](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Specializace šablon](../cpp/template-specialization-cpp.md)<br/>
[Postupy: Převody mezi různými typy řetězců](../text/how-to-convert-between-various-string-types.md)
