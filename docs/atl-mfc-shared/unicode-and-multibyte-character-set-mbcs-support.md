---
title: Kódování Unicode a vícebajtových znaků (MBCS) podporu sady | Microsoft Docs
ms.custom: ''
ms.date: 1/09/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8492e4a6777e4d609e3b457cfc77d1b8a691eed3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>(MBCS) podporu kódování Unicode a vícebajtové znakové sady

Některé jazyky, například japonštiny a čínština, mají velký znakových sad. Pro podporu programování pro tyto trhy, Microsoft Foundation Class Library (MFC) umožňuje dva různé přístupy pro zpracování velkých znakových sad:

- [Unicode](#mfc-support-for-unicode-strings), `wchar_t` na základě široké znaky a řetězce kódovaná jako UTF-16.

- [Vícebajtové znakové sady (MBCS)](#mfc-support-for-mbcs-strings), `char` na základě jednoho nebo dvoubajtové znaky a řetězce v konkrétní národní prostředí znakovou sadu kódování.

Microsoft se doporučuje knihovny MFC Unicode pro všechny nové vývoj a knihovny MBCS byly zastaralé v sadě Visual Studio 2013 a Visual Studio 2015. To již neplatí. Znakové sady MBCS odstranění upozornění, že byla odebrána v Visual Studio 2017.

## <a name="mfc-support-for-unicode-strings"></a>Podpora MFC pro řetězců v kódu Unicode

Celý třídy knihovny MFC je povoleno podmíněně znaky kódování Unicode a řetězce uložené v široké znaky jako UTF-16. Na konkrétní třídy [CString](../atl-mfc-shared/reference/cstringt-class.md) kódování Unicode.

Tyto soubory knihoven DLL, knihovny a ladicí program slouží k podpoře kódování Unicode v prostředí MFC:

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW. PDB|UAFXCWD.LIB|UAFXCWD. PDB|
|MFC*verze*U.LIB|MFC*verze*U.PDB|MFC*version*U.DLL|MFC*verze*UD. LIB|
|MFC*verze*UD. PDB|MFC*version*UD.DLL|MFCS*verze*U.LIB|MFCS*verze*U.PDB|
|MFCS*verze*UD. LIB|MFCS*verze*UD. PDB|MFCM*verze*U.LIB|MFCM*verze*U.PDB|
|MFCM*verze*U.DLL|MFCM*verze*UD. LIB|MFCM*verze*UD. PDB|MFCM*version*UD.DLL|

(*verze* představuje číslo verze souboru; '140, například znamená verze 14.0.)

`CString` je založena na `TCHAR` datového typu. Pokud je symbol `_UNICODE` je definována pro sestavení vašeho programu `TCHAR` je definována jako typ `wchar_t`, typ kódování znaků 16 bitů. V opačném `TCHAR` je definován jako `char`, kódování normální 8bitové znaků. Proto v kódu Unicode `CString` se skládá z 16 rozšířené znaky. Bez kódování Unicode, se skládá z znaků typu `char`.

Do dokončení programování Unicode vaší aplikace, které je nutné také:

- Použití `_T` makro na podmíněně kód literálu řetězce přenosný na kódování Unicode.

- Pokud předáte řetězce, věnujte pozornost jestli argumenty funkce vyžadují délka ve znacích nebo délka v bajtech. Rozdíl je důležité, pokud používáte řetězců v kódu Unicode.

- Pomocí přenosného verzí funkcí jazyka C Runtime zpracování řetězce.

- Použijte následující typy dat pro znaky a znak ukazatele:

   - Použít `TCHAR` použít `char`.

   - Použít `LPTSTR` použít `char*`.

   - Použít `LPCTSTR` použít `const char*`. `CString` poskytuje operátor `LPCTSTR` pro převod mezi `CString` a `LPCTSTR`.

`CString` také poskytuje kódování Unicode konstruktory, přiřazení operátory a operátory porovnání.

[Referenční dokumentace běhové knihovny](../c-runtime-library/c-run-time-library-reference.md) definuje přenosné verzích všechny její funkce zpracování řetězců. Další informace najdete v tématu kategorii [internacionalizace](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Podpora MFC pro řetězce znakové sady MBCS

Knihovna tříd je povolená i u vícebajtových znakových sad, ale jenom pro dvoubajtové znakové nastaví (DBCS).

Znak v sadě vícebajtových znaků může být jedno nebo dvě bajtů široké. Pokud se dva bajty široké, jeho prvního bajtu je speciální "úvodní bajt" tedy vybrat z konkrétního rozsahu, v závislosti na tom, které kódu stránky se používá. Dohromady, realizace a "poslední bajt" Zadejte jedinečné znaky kódování.

Pokud je symbol `_MBCS` je definována pro sestavení vašeho programu typ `TCHAR`, na kterém `CString` je založen, se mapuje na `char`. Je určit, které bajtů `CString` jsou úvodní bajty a které jsou druhé bajty. Běhové knihovny jazyka C poskytuje funkce, můžete to zjistit.

V části DBCS daný řetězec může obsahovat všechny jednobajtové znaky ANSI, všechny dvoubajtové znaky nebo jejich kombinaci dva. Tyto možnosti vyžadují zvláštní pozornost při analýze řetězce. To zahrnuje `CString` objekty.

> [!NOTE]
> Serializace řetězec kódování Unicode v prostředí MFC může číst řetězce Unicode a MBCS bez ohledu na to, kterou verzi aplikace, kterou používáte. Datové soubory jsou přenosné mezi verzemi kódování Unicode a MBCS vašeho programu.

`CString` Členské funkce použít speciální "obecný text" verze C běhové funkce, které volají nebo používají funkce kódování Unicode. Tedy například pokud `CString` by obvykle volání funkce `strcmp`, volá funkci odpovídající obecného textu `_tcscmp` místo. V závislosti na tom, jak symboly `_MBCS` a `_UNICODE` jsou definovány `_tcscmp` mapuje následujícím způsobem:

|||
|-|-|
|`_MBCS` Definované|`_mbscmp`|
|`_UNICODE` Definované|`wcscmp`|
|Ani symbol definované|`strcmp`|

> [!NOTE]
> Symboly `_MBCS` a `_UNICODE` se vzájemně vylučují.

Mapování obecného textu funkcí pro všechny běhové rutiny zpracování řetězců, které jsou popsané v [referenční dokumentace knihoven C Run-Time](../c-runtime-library/c-run-time-library-reference.md). Seznam najdete v tématu [internacionalizace](../c-runtime-library/internationalization.md).

Podobně `CString` metody jsou implementovaná pomocí mapování obecných datových typů. Umožňuje MBCS a Unicode MFC používá `TCHAR` pro `char` nebo `wchar_t`, `LPTSTR` pro `char*` nebo `wchar_t*`, a `LPCTSTR` pro `const char*` nebo `const wchar_t*`. Tyto zajistit správné mapování pro MBCS nebo Unicode.

## <a name="see-also"></a>Viz také

[Řetězce (ATL a MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[Zacházení s řetězci](../c-runtime-library/string-manipulation-crt.md)  
