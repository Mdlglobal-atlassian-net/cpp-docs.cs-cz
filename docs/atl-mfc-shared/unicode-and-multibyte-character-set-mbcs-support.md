---
title: Podpora znakových sad Unicode a MBCS
ms.date: 01/09/2017
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.openlocfilehash: e1b93a3540cba553afd8f133c18496bddbd561b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317440"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Podpora znakových sad Unicode a MBCS

Některé jazyky, například japonština a čínština, mají velké znakové sady. Pro podporu programování pro tyto trhy umožňuje knihovna microsoft foundation class library (MFC) dva různé přístupy k manipulaci s velkými znakovými sadami:

- [Unicode](#mfc-support-for-unicode-strings) `wchar_t` , založené na širokých znacích a řetězecích kódovaných jako UTF-16.

- [Vícebajtové znakové sady (MBCS),](#mfc-support-for-mbcs-strings)jednobajtové nebo dvoubajtové znaky založené na **znaku** a řetězce založené na znaku založené na znaku.

Společnost Microsoft doporučila knihovny Unicode knihovny MFC pro všechny nové vývoj a knihovny MBCS byly zastaralé v sadě Visual Studio 2013 a Visual Studio 2015. To již neplatí. Upozornění na vyřazení mbcs byly odebrány v sadě Visual Studio 2017.

## <a name="mfc-support-for-unicode-strings"></a>Podpora knihovny MFC pro řetězce Unicode

Celá knihovna tříd knihovny MFC je podmíněně povolena pro znaky Unicode a řetězce uložené v širokých znacích jako UTF-16. Zejména třída [CString](../atl-mfc-shared/reference/cstringt-class.md) je s podporou Unicode.

Tyto soubory knihovny, ladicího programu a knihovny DLL se používají pro podporu unicode v knihovně MFC:

|||||
|-|-|-|-|
|UAFXCW. Lib|UAFXCW. Pdb|UAFXCWD. Lib|UAFXCWD. Pdb|
|Verze*knihovny*MFC U.LIB|*MFC verze*U.PDB|Verze*knihovny*MFC U.DLL|MFC*verze*UD. Lib|
|MFC*verze*UD. Pdb|MFC*verze*UD. Knihovny dll|*Verze*knihovny MFCS U.LIB|*Verze*knihovny MFCS u.PDB|
|MFCS*verze*UD. Lib|MFCS*verze*UD. Pdb|MFCM*verze*U.LIB|*MFCM verze*U.PDB|
|MFCM*verze*U.DLL|MFCM*verze*UD. Lib|MFCM*verze*UD. Pdb|MFCM*verze*UD. Knihovny dll|

*(verze* představuje číslo verze souboru; například "140" znamená verze 14.0.)

`CString`je založen na datovém typu TCHAR. Pokud je symbol _UNICODE definován pro sestavení programu, tchar `wchar_t`je definován jako typ , 16bitový typ kódování znaků. Jinak tchar je definován jako **char**, normální 8bitové kódování znaků. Proto v rámci Unicode, a `CString` se skládá z 16bitových znaků. Bez Unicode se skládá ze znaků typu **char**.

Chcete-li dokončit programování aplikace Unicode, musíte také:

- Pomocí _T makra podmíněně kódovat literály, které mají být přenosné na Unicode.

- Při průchodu řetězce, věnujte pozornost tomu, zda argumenty funkce vyžadují délku ve znacích nebo délku v bajtů. Rozdíl je důležitý, pokud používáte řetězce Unicode.

- Používejte přenosné verze funkcí zpracování řetězců za běhu jazyka C.

- Pro znaky a ukazatele znaků použijte následující datové typy:

  - Použijte TCHAR, kde byste použít **char**.

  - Použijte LPTSTR, kde byste použít **char**<strong>\*</strong>.

  - Použijte LPCTSTR, kde byste použít **const char**<strong>\*</strong>. `CString`poskytuje operátor LPCTSTR převést mezi `CString` a LPCTSTR.

`CString`také dodává konstruktory podporující unicode, operátory přiřazení a operátory porovnání.

[Odkaz na knihovnu za běhu](../c-runtime-library/c-run-time-library-reference.md) definuje přenosné verze všech svých funkcí pro zpracování řetězců. Další informace naleznete v kategorii [Internacionalizace](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Podpora knihovny MFC pro řetězce mbcs

Knihovna tříd je také povolena pro vícebajtové znakové sady, ale pouze pro dvoubajtové znakové sady (DBCS).

Ve vícebajtové znakové sadě může být znak široký jeden nebo dva bajty. Pokud je dva bajty široké, jeho první bajt je speciální "olovo bajt", který je vybrán z určitého rozsahu, v závislosti na tom, která znaková stránka je používán. Dohromady hlavní a "koncové bajty" určují jedinečné kódování znaků.

Pokud je symbol _MBCS definován pro sestavení programu, zadejte `CString` TCHAR, na kterém je založen, mapuje na **znak**. Je na vás, abyste určili, `CString` které bajty v úvodních bajtů a které jsou koncové bajty. C run-time knihovna poskytuje funkce, které vám pomohou určit.

V části DBCS může daný řetězec obsahovat všechny jednobajtové znaky ANSI, všechny dvoubajtové znaky nebo jejich kombinaci. Tyto možnosti vyžadují zvláštní péči při analýzách řetězců. To `CString` zahrnuje objekty.

> [!NOTE]
> Serializace řetězce Unicode v knihovně MFC může číst řetězce Unicode i MBCS bez ohledu na to, kterou verzi aplikace, kterou používáte. Datové soubory jsou přenosné mezi verzemi programu Unicode a MBCS.

`CString`členské funkce používají speciální "obecný text" verze c run-time funkce, které volají, nebo používají funkce podporující Unicode. Proto například pokud `CString` funkce obvykle volat `strcmp`, volá odpovídající funkci `_tcscmp` obecného textu místo. V závislosti na tom, jak `_tcscmp` jsou definovány symboly _MBCS a _UNICODE, mapuje následující:

|||
|-|-|
|_MBCS definováno|`_mbscmp`|
|_UNICODE definováno|`wcscmp`|
|Ani jeden symbol definován|`strcmp`|

> [!NOTE]
> Symboly _MBCS a _UNICODE se vzájemně vylučují.

Mapování funkcí obecného textu pro všechny rutiny zpracování řetězce za běhu jsou popsány v [odkazu knihovny za běhu C](../c-runtime-library/c-run-time-library-reference.md). Seznam naleznete v tématu [Internacionalizace](../c-runtime-library/internationalization.md).

Podobně `CString` metody jsou implementovány pomocí mapování obecného datového typu. Chcete-li povolit mbcs a unicode, knihovna MFC používá `wchar_t*`TCHAR pro **char** nebo `wchar_t`, LPTSTR pro **char** <strong>\*</strong> nebo , a LPCTSTR pro **const char** <strong>\*</strong> nebo `const wchar_t*`. Ty zajišťují správné mapování pro mbcs nebo unicode.

## <a name="see-also"></a>Viz také

[Řetězce (KNIHOVNA ATL/Knihovna Knihovny AFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Zacházení s řetězci](../c-runtime-library/string-manipulation-crt.md)
