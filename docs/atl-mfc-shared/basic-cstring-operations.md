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
ms.openlocfilehash: 08c496038efc9e24e1c1610da07b6824c3a50b64
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746211"
---
# <a name="basic-cstring-operations"></a>CString – základní operace

Toto téma vysvětluje následující základní [CString](../atl-mfc-shared/reference/cstringt-class.md) operace:

- [Vytváření objektů CString ze standardní řetězcové literály jazyka C](#_core_creating_cstring_objects_from_standard_c_literal_strings)

- [Přístup ke jednotlivým znakům v CString](#_core_accessing_individual_characters_in_a_cstring)

- [Zřetězení dvou CString – objekty](#_core_concatenating_two_cstring_objects)

- [Porovnání CString – objekty](#_core_comparing_cstring_objects)

- [Převod CString – objekty](#_core_converting_cstring_objects)

`Class CString` je založen na šabloně třídy [cstringt – třída](../atl-mfc-shared/reference/cstringt-class.md). `CString` je **typedef** z `CStringT`. Více přesně `CString` je **typedef** z *explicitní specializace* z `CStringT`, což je běžný způsob, jak definovat třídu pomocí šablony třídy. Podobně definovaných tříd jsou `CStringA` a `CStringW`.

`CString`, `CStringA`, a `CStringW` jsou definovány v atlstr.h. `CStringT` je definováno v cstringt.h.

`CString`, `CStringA`, a `CStringW` každý získat sadu metod a operátory definované ve `CStringT` pro použití s řetězcovými datovými podporují. Některé metody duplicitní a v některých případech toto služby řetězec běhových knihoven C.

Poznámka: `CString` je nativních tříd. Pro třídu řetězec, který je určen pro použití v jazyce C + +/ CLI spravovaných projektů, použití `System.String`.

##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a> Vytváření objektů CString z řetězcových literálů Standard jazyka C

Můžete přiřadit literálu řetězce ve stylu jazyka C k `CString` stejně jako můžete přiřadit jednu `CString` objektu na jiný.

- Přiřadí hodnotu řetězcový literál na C `CString` objektu.

   [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]

- Přiřadí hodnotu jednoho `CString` do jiného `CString` objektu.

   [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]

   Obsah `CString` objektu jsou zkopírovány v případě, že jedna `CString` je přiřazen objekt do jiné. Proto dva řetězce nesmí ho sdílet odkaz na skutečné znaky, které společně tvoří řetězec. Další informace o tom, jak používat `CString` objekty jako hodnoty, najdete v článku [CString – sémantika](../atl-mfc-shared/cstring-semantics.md).

   > [!NOTE]
   > Při psaní vaší aplikace tak, že mohou být zkompilovány pro kódování Unicode nebo standardu ANSI, řetězcových literálů v kódu s použitím _T – makro. Další informace najdete v tématu [vícebajtové znakové sady (MBCS) Podpora kódování Unicode a](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).

##  <a name="_core_accessing_individual_characters_in_a_cstring"></a> Přístup ke jednotlivým znakům v CString

Dostanete jednotlivé znaky `CString` s použitím `GetAt` a `SetAt` metody. Pole elementu nebo dolní index, operátor ([]) můžete také použít místo `GetAt` zobrazíte jednotlivých znaků. (To se podobá přístup k prvkům pole pomocí indexu jako standardní řetězce C-style.) Index hodnoty `CString` znaky jsou počítány od nuly.

##  <a name="_core_concatenating_two_cstring_objects"></a> Zřetězení dvou CString – objekty

Ke zřetězení dvou `CString` objekty, použít operátory řetězení (+ nebo +=), následujícím způsobem.

[!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]

Alespoň jeden argument pro operátory zřetězení (+ nebo +=) musí být `CString` objektu, ale můžete použít textový konstantním znakem (třeba `"big"`) nebo **char** (například "x") pro tento argument.

##  <a name="_core_comparing_cstring_objects"></a> Porovnání CString – objekty

`Compare` Metoda a == – operátor pro `CString` jsou ekvivalentní. `Compare`, **operátor ==**, a `CompareNoCase` vědomi znakové sady MBCS a Unicode; `CompareNoCase` je velká a malá písmena. `Collate` Metoda `CString` je citlivé na národní prostředí a často je pomalejší než `Compare`. Použití `Collate` pouze pokud musíte dodržet při řazení pravidla jako zadané pomocí aktuálního národního prostředí.

V následující tabulce jsou uvedeny dostupné [CString](../atl-mfc-shared/reference/cstringt-class.md) porovnání funkcí a jejich ekvivalentní kódování Unicode a MBCS-portable funkce v knihovně C Runtime.

|CString – funkce|MBCS – funkce|Unicode – funkce|
|----------------------|-------------------|----------------------|
|`Compare`|`_mbscmp`|`wcscmp`|
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|
|`Collate`|`_mbscoll`|`wcscoll`|

`CStringT` Třída šablony definuje relační operátory (<, \<=, > =, >, ==, a! =), které jsou k dispozici pro použití `CString`. Můžete porovnat dva `CStrings` pomocí těchto operátorů, jak je znázorněno v následujícím příkladu.

[!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]

##  <a name="_core_converting_cstring_objects"></a> Převod CString – objekty

Informace o převádění objektů CString na jiné typy řetězce, naleznete v tématu [jak: Převést mezi různými typy řetězců](../text/how-to-convert-between-various-string-types.md).

## <a name="using-cstring-with-wcout"></a>CString – použití s wcout

Použití CString s `wcout` musí explicitně přetypovat objekt, který má `const wchar_t*` jak je znázorněno v následujícím příkladu:

```cpp
CString cs("meow");

wcout << (const wchar_t*) cs << endl;
```

Bez přetypování `cs` je považován za `void*` a `wcout` vypíše adresu objektu. Toto chování je způsobené drobné interakce mezi šablony argument odvození přetížení rozlišení a které jsou v samotných správné a splňovala podmínky shody se standardem jazyka C++.

## <a name="see-also"></a>Viz také:

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT – třída](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Specializace šablon](../cpp/template-specialization-cpp.md)<br/>
[Postupy: Převody různých typů řetězců](../text/how-to-convert-between-various-string-types.md)
