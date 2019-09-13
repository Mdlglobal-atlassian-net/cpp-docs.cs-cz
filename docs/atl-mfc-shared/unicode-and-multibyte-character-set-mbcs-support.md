---
title: Podpora Unicode a vícebajtové znakové sady (MBCS)
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
ms.openlocfilehash: 983b3d9bc72d99ab3c665f86cffd205dccf873e8
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927892"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Podpora Unicode a vícebajtové znakové sady (MBCS)

Některé jazyky, například japonské a čínské, mají velké znakové sady. Pro podporu programování pro tyto trhy umožňuje knihovna Microsoft Foundation Class (MFC) dva různé přístupy ke zpracování velkých znakových sad:

- [Kódování Unicode](#mfc-support-for-unicode-strings), `wchar_t` založené na znacích a řetězce kódované jako UTF-16.

- [Vícebajtové znakové sady (MBCS)](#mfc-support-for-mbcs-strings) **, znaky** jednoduchého nebo dvoubajtového znaku a řetězce kódované v sadě znaků specifické pro národní prostředí.

Společnost Microsoft doporučuje knihovny MFC Unicode pro všechny nové vývojové prostředí a knihovny znakové sady MBCS byly zastaralé v Visual Studio 2013 a sadě Visual Studio 2015. To již neplatí. Upozornění na zastaralost znakové sady MBCS byla v aplikaci Visual Studio 2017 odebrána.

## <a name="mfc-support-for-unicode-strings"></a>Podpora MFC pro řetězce Unicode

Celá knihovna tříd knihovny MFC je podmíněně povolena pro znaky Unicode a řetězce uložené v rámci velkých znaků jako UTF-16. Konkrétně třída [CString](../atl-mfc-shared/reference/cstringt-class.md) má povolenou znakovou sadu Unicode.

Tyto knihovny, ladicí program a soubory DLL se používají k podpoře kódování Unicode v MFC:

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW.PDB|UAFXCWD.LIB|UAFXCWD.PDB|
|MFC*verze*U. lib|MFC*version*U.PDB|MFC*version*U.DLL|UD*verze*knihovny MFC. Knihovna|
|MFC*version*UD.PDB|MFC*version*UD.DLL|MFCS*verze*U. lib|MFCS*version*U.PDB|
|MFCS*verze*ud. Knihovna|MFCS*version*UD.PDB|MFCM*verze*U. lib|MFCM*version*U.PDB|
|MFCM*version*U.DLL|MFCM*verze*ud. Knihovna|MFCM*verze*ud. PDB|MFCM*version*UD.DLL|

(*verze* představuje číslo verze souboru, například ' 140 ' znamená verzi 14,0.)

`CString`je založena na datovém typu TCHAR. Pokud je symbol _UNICODE definován pro sestavení vašeho programu, TCHAR je definován jako typ `wchar_t`, 16bitový typ kódování znaků. V opačném případě jsou TCHARy definovány jako **char**, což je normální 8bitové kódování znaků. Proto `CString` se v části Unicode skládá ze 16 bitových znaků. Bez kódování Unicode se skládá z znaků typu **char**.

Chcete-li dokončit programování v kódování Unicode vaší aplikace, je nutné také:

- Použijte makro _T pro podmíněné kódování řetězců literálů pro přenos do kódování Unicode.

- Při předávání řetězců věnujte pozornost tomu, zda argumenty funkce vyžadují délku ve znacích nebo délku v bajtech. Rozdíl je důležitý, pokud používáte řetězce Unicode.

- Používejte přenositelné verze funkcí pro zpracování řetězců jazyka C za běhu.

- Pro znaky a ukazatele znaků použijte následující typy dat:

   - Použijte TCHAR, kde byste použili **char**.

   - Použijte LPTSTR, kde byste použili **char**<strong>\*</strong>.

   - Použijte LPCTSTR, kde byste použili **const char**<strong>\*</strong>. `CString`poskytuje operátor LPCTSTR k převodu mezi `CString` a LPCTSTR.

`CString`poskytuje také konstruktory podporující kódování Unicode, operátory přiřazení a operátory porovnání.

Referenční dokumentace ke [knihovně modulu runtime](../c-runtime-library/c-run-time-library-reference.md) definuje přenositelné verze všech svých funkcí pro zpracování řetězců. Další informace najdete v tématu [mezinárodní](../c-runtime-library/internationalization.md)přidaná kategorie.

## <a name="mfc-support-for-mbcs-strings"></a>Podpora MFC pro řetězce znakové sady MBCS

Knihovna tříd je také povolena pro vícebajtové znakové sady, ale pouze pro dvoubajtové znakové sady (DBCS).

V vícebajtové znakové sadě může být znak jeden nebo dva bajty na šířku. Pokud jsou dva bajty široké, první bajt je speciální "vedoucí bajt", který se vybere z konkrétního rozsahu v závislosti na používané znakové stránce. Společně a "koncové bajty" určují jedinečné kódování znaků.

Pokud je symbol _MBCS definován pro sestavení programu, zadejte TCHAR, na kterém `CString` je založena, se mapuje na **char**. Je až na to, abyste zjistili, které bajty v `CString` jsou vedoucí bajty a které jsou koncové bajty. Knihovna run-time jazyka C poskytuje funkce, které vám pomůžou je určit.

V rámci sady DBCS může daný řetězec obsahovat všechny jednobajtové znaky ANSI, všechny dvoubajtové znaky nebo kombinaci obou. Tyto možnosti vyžadují zvláštní péči při analýze řetězců. To zahrnuje `CString` objekty.

> [!NOTE]
> Serializace řetězců Unicode v knihovně MFC může číst řetězce Unicode a MBCS bez ohledu na to, kterou verzi aplikace používáte. Datové soubory jsou přenosné mezi verzemi programu Unicode a MBCS.

`CString`Členské funkce používají speciální verze "obecného textu" běhových funkcí jazyka C, které volají, nebo používají funkce podporující kódování Unicode. Proto, pokud `CString` by například funkce obvykle volala `strcmp`, volá místo toho odpovídající funkci `_tcscmp` obecného textu. V závislosti na tom, jak jsou definovány symboly _MBCS a _UNICODE `_tcscmp` , se provede mapování následujícím způsobem:

|||
|-|-|
|_MBCS definováno|`_mbscmp`|
|_UNICODE definováno|`wcscmp`|
|Není definován žádný symbol.|`strcmp`|

> [!NOTE]
> Symboly _MBCS a _UNICODE se vzájemně vylučují.

Mapování funkcí obecného textu pro všechny rutiny zpracování řetězců běhu jsou popsány v tématu Referenční dokumentace běhové [knihovny jazyka C](../c-runtime-library/c-run-time-library-reference.md). Seznam najdete v tématu [mezinárodní](../c-runtime-library/internationalization.md).

`CString` Podobně metody jsou implementovány pomocí mapování obecných datových typů. Chcete-li povolit znakovou sadu MBCS i Unicode, knihovna MFC používá `wchar_t`TCHAR pro char nebo, `wchar_t*`LPTSTR pro **char** <strong>\*</strong> nebo a LPCTSTR pro `const wchar_t*` **const char** <strong>\*</strong> nebo. To zajistí správné mapování buď znakové sady MBCS nebo Unicode.

## <a name="see-also"></a>Viz také:

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Manipulace s řetězci](../c-runtime-library/string-manipulation-crt.md)
