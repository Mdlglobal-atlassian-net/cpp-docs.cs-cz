---
title: Podpora pro Unicode
ms.date: 01/09/2018
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.openlocfilehash: c30cb1fbfb1930b5e4b026e58c478f0099e8ecdf
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929922"
---
# <a name="support-for-unicode"></a>Podpora pro Unicode

Kódování Unicode je specifikace pro podporu všech znakových sad, včetně těch, které nemohou být reprezentovány v jednom bajtu.  Pokud programujete pro mezinárodní trh, doporučujeme použít buď sadu Unicode, nebo [vícebajtovou znakovou sadu](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS). Nebo můžete kód programovat, abyste ho mohli sestavit buď změnou přepínače.

Velký znak je 2 bajt kódu vícejazyčného znaku. Desítky tisíc znaků, včetně téměř všech znaků používaných v moderních computingech po celém světě, včetně technických symbolů a speciálních publikačních znaků, se dají reprezentovat podle specifikace Unicode jako jediného celého znaku zakódovaného použití UTF-16. Znaky, které nemohou být reprezentovány pouze s jedním velkým znakem, mohou být reprezentovány v páru Unicode pomocí funkce náhradního páru Unicode. Vzhledem k tomu, že téměř každý znak v běžném použití je reprezentován v kódování UTF-16 v jednom 16bitovém samostatném znaku, je použití velkých znaků zjednodušeno programování s mezinárodními znakovými sadami. V systému Windows jsou pro systém Windows naformátované znaky pomocí UTF-16LE (pro Little Endian).

Řetězec s velkým znakem je reprezentován jako `wchar_t[]` pole a ukazuje na `wchar_t*` ukazatel. Libovolný znak ASCII může být reprezentován jako libovolným znakem, a to pomocí předpony písmene L až k znaku. Například L ' \ 0 ' je ukončující (16bitový) znak NULL. Podobně libovolný řetězcový literál ASCII může být reprezentován jako řetězcový literál s libovolným znakem, a to tak, že se písmeno L přikládá na literál ASCII (L "Hello").

Obecně platí, že většina znaků vybere více místa v paměti než vícebajtové znaky, ale je rychlejší pro zpracování. Kromě toho lze reprezentovat pouze jedno národní prostředí v vícebajtovém kódování, zatímco všechny znakové sady na světě jsou zastoupeny současně reprezentacemi Unicode.

Rozhraní MFC podporuje v celém systému kódování Unicode a MFC provádí povolení kódování Unicode pomocí přenosných maker, jak je znázorněno v následující tabulce.

## <a name="portable-data-types-in-mfc"></a>Přenosné datové typy v MFC

|Nepřenosný datový typ|Nahrazeno tímto makrem|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`, `LPSTR` (Datový typ Win32),`LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (Datový typ Win32),`LPCWSTR`|`LPCTSTR`|

Třída `CString` používá`_TCHAR` jako základní a poskytuje konstruktory a operátory pro snadné převody. Většinu operací s řetězci pro sadu Unicode lze zapsat pomocí stejné logiky používané pro zpracování znakové sady Windows ANSI s tím rozdílem, že základní Jednotková operace je 16bitový znak namísto 8bitové bajtu. Na rozdíl od použití vícebajtových znakových sad není nutné (a neměli) považovat znak Unicode, jako by šlo o dva odlišné bajty. Je však nutné se vypořádat s možností jednoho znaku reprezentovaného náhradní dvojicí velkých znaků. Obecně nepište kód, který předpokládá délku řetězce, je stejný jako počet znaků, který obsahuje zúžené nebo široké.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Použití podpory MFC Unicode a vícebajtové znakové sady (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Povolit kódování Unicode v programu](../text/international-enabling.md)

- [V programu Povolit kódování Unicode i znakovou sadu MBCS](../text/internationalization-strategies.md)

- [Použití Unicode k vytvoření mezinárodního programu](../text/unicode-programming-summary.md)

- [Seznamte se s výhodami kódování Unicode](../text/benefits-of-character-set-portability.md)

- [Použití wmain, takže můžu do programu předat argumenty pro velké znaky](../text/support-for-using-wmain.md)

- [Zobrazit souhrn programování v kódování Unicode](../text/unicode-programming-summary.md)

- [Seznamte se s mapováním obecného textu pro přenositelnost šířky bajtu](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Viz také:

[Text a řetězce](../text/text-and-strings-in-visual-cpp.md)<br/>
[Podpora použití funkce wmain](../text/support-for-using-wmain.md)