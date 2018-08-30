---
title: Kódování Unicode a vícebajtových znaků (MBCS) podporu sady | Dokumentace Microsoftu
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
ms.openlocfilehash: 74f1f0f88828b5d6355c692aa8eaeecd5869bf57
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202931"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Kódování Unicode a vícebajtových znaků (MBCS) podporu sady

Některé jazyky, třeba japonštinu a čínštinu, mají velké znak sady. Pro podporu programování pro tyto trhy, umožňuje třídy knihovny MFC (Microsoft Foundation) dva různé přístupy k zpracování velkého znakových sad:

- [Kódování Unicode](#mfc-support-for-unicode-strings), `wchar_t` na základě široké znaky a řetězce s kódováním UTF-16.

- [Vícebajtové znakové sady (MBCS)](#mfc-support-for-mbcs-strings), **char** na základě jednoho nebo dvoubajtové znaky a řetězce zakódován do sady znaků specifických pro národní prostředí.

Microsoft se doporučuje knihovny MFC kódování Unicode pro veškeré nové vývojové a knihovny MBCS byla vyřazena jako zastaralá v sadě Visual Studio 2013 a Visual Studio 2015. To již neplatí. Upozornění na zastaralost znakové sady MBCS v sadě Visual Studio 2017 byly odebrány.

## <a name="mfc-support-for-unicode-strings"></a>Podpora MFC pro řetězce Unicode

Celou knihovnu třídy knihovny MFC podmíněně povoleny znaky znakové sady Unicode a řetězce jako UTF-16 uložené v širokých znaků. Zejména třídy [CString](../atl-mfc-shared/reference/cstringt-class.md) kódování Unicode.

Tyto knihovny ladicího programu a soubory DLL slouží k podpoře kódování Unicode v prostředí MFC:

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW. SOUBOR PDB|UAFXCWD.LIB|UAFXCWD. SOUBOR PDB|
|MFC*verze*U.LIB|MFC*verze*U.PDB|MFC*version*U.DLL|MFC*verze*UD. LIB|
|MFC*verze*UD. SOUBOR PDB|MFC*version*UD.DLL|MFCS*verze*U.LIB|MFCS*verze*U.PDB|
|MFCS*verze*UD. LIB|MFCS*verze*UD. SOUBOR PDB|MFCM*verze*U.LIB|MFCM*verze*U.PDB|
|MFCM*verze*U.DLL|MFCM*verze*UD. LIB|MFCM*verze*UD. SOUBOR PDB|MFCM*version*UD.DLL|

(*verze* představuje číslo verze souboru; například "140" znamená, že verze 14.0.)

`CString` je založen na datovém typu TCHAR. Pokud pro sestavení programu je definován symbol _UNICODE, TCHAR je definována jako typ `wchar_t`, 16bitový znak typ kódování. V opačném případě Tchar – je definován jako **char**, běžný znak 8bitové kódování. Proto v kódování Unicode `CString` se skládá ze znaků 16 bitů. Bez kódování Unicode, se skládá ze znaků typu **char**.

K dokončení programování Unicode vaší aplikace, musíte také:

- Použijte makro _T podmíněně kód literál řetězce přenositelnost na kódování Unicode.

- Při předávání řetězce věnujte pozornost, jestli argumenty funkce vyžadují délka ve znacích nebo délka v bajtech. Rozdíl je důležité, pokud používáte řetězců v kódu Unicode.

- Použijte přenosné verze funkcí jazyka C za běhu zpracování řetězců.

- Použijte následující datové typy znaků a ukazatelů na znaky:

   - Použít TCHAR, kde můžete využít **char**.

   - Použít LPTSTR, kde můžete využít **char**<strong>\*</strong>.

   - Použít LPCTSTR, kde můžete využít **const char**<strong>\*</strong>. `CString` poskytuje operátor LPCTSTR k převodu mezi `CString` a LPCTSTR.

`CString` poskytuje také s ohledem na Unicode konstruktory, operátory přiřazení a operátory porovnání.

[Run-Time Library Reference](../c-runtime-library/c-run-time-library-reference.md) definuje přenosná verze všechny jeho funkce pro zpracování řetězce. Další informace najdete v části kategorie [internacionalizace](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Podpora MFC pro řetězce znakové sady MBCS

Knihovna tříd je povolená i u vícebajtových znakových sad, ale nastavuje pouze pro dvoubajtové znakové (sady DBCS).

Vícebajtové znakové sady znak může být jeden nebo dva bajty široké. Pokud se jedná o dva bajty široké, jeho první bajt je speciální "vedoucí bajt" zvolená, který je z určitého rozsahu, v závislosti na tom, jaký kód stránky se používá. Dohromady, vedoucí a "poslední bajt" Zadejte jedinečné znaky kódování.

Pokud pro sestavení programu je definován symbol _MBCS, typu TCHAR, na kterém `CString` vychází, mapuje **char**. Je určit, které bajtů `CString` jsou vedoucí bajty a které jsou záznam bajtů. Knihovny run-time jazyka C poskytuje funkce, které vám pomohou určit to.

V části DBCS daný řetězec může obsahovat všechny jednobajtové znaky ANSI, všechny dvoubajtové znaky nebo kombinaci obou. Tyto možnosti vyžadují zvláštní pozornost při analýze řetězce. Jedná se o `CString` objekty.

> [!NOTE]
> Serializace řetězce Unicode v prostředí MFC může číst řetězce Unicode a MBCS bez ohledu na to, kterou verzi aplikace, kterou používáte. Datové soubory jsou přenosné mezi verzemi sady Unicode a MBCS programu.

`CString` Členské funkce použít speciální "obecný text" verze funkcí jazyka C za běhu, které volají nebo používají s ohledem na Unicode funkce. Proto například pokud `CString` by obvykle volání funkce `strcmp`, volá funkci odpovídající obecného textu `_tcscmp` místo. V závislosti na tom, jak jsou definované _UNICODE a _MBCS symboly `_tcscmp` mapuje následujícím způsobem:

|||
|-|-|
|_MBCS definováno|`_mbscmp`|
|_UNICODE definováno|`wcscmp`|
|Ani jedna symbol definovaný|`strcmp`|

> [!NOTE]
> _MBCS symboly a _UNICODE se vzájemně vylučují.

Mapování obecného textu funkcí pro všechny rutiny zpracování řetězce za běhu jsou popsány v [C Run-Time Library Reference](../c-runtime-library/c-run-time-library-reference.md). Seznam najdete v tématu [internacionalizace](../c-runtime-library/internationalization.md).

Obdobně `CString` metody jsou implementovány pomocí mapování obecného datového typu. Povolit znakovou sadu MBCS a Unicode, knihovna MFC používá TCHAR pro **char** nebo `wchar_t`, LPTSTR pro **char** <strong>\*</strong> nebo `wchar_t*`a LPCTSTR pro **const char** <strong>\*</strong> nebo `const wchar_t*`. Tyto zajistit správné mapování znakové sady MBCS a Unicode.

## <a name="see-also"></a>Viz také

[Řetězce (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[Zacházení s řetězci](../c-runtime-library/string-manipulation-crt.md)  
