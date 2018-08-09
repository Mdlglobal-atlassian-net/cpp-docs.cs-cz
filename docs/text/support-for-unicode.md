---
title: Podpora pro Unicode | Dokumentace Microsoftu
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53c71e1efad109daea689725ebbbb7dd9b100d30
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020167"
---
# <a name="support-for-unicode"></a>Podpora pro Unicode

Kódování Unicode je specifikace pro podporu všech znakových sad, včetně těch, které nelze vyjádřit v právě jeden bajt (tj. Většina z nich). Pokud programujete pro mezinárodní trh, doporučujeme použít buď ve formátu Unicode nebo [vícebajtové znakové sady](../text/support-for-multibyte-character-sets-mbcss.md) znakové sady (MBCS), nebo abyste mohli sestavit pro buď tak, že změníte přepínač kódu programu.

Široký znak je znak vícejazyčné 2bajtových kód. Desítky tisíc znaků tvořících téměř všechny znaky moderní výpočet po celém světě, včetně technické symboly a speciálních znaků pro publikování, může být reprezentován podle specifikace Unicode jako jeden širokého znaku kódovaný pomocí pomocí kódování UTF-16. Znaky, které nelze reprezentovat v jediné širokého znaku lze znázornit v páru Unicode pomocí funkci Unicode náhradní pár. Protože téměř všechny znaky v běžné použití je reprezentován v kódování UTF-16 v jedné 16 bitů široký znak, zjednodušuje použití širokých znaků programování mezinárodních znakových sad. Široké znaky kódovaný pomocí kódování UTF-16LE (pro little endian) jsou formátu nativní znaků pro Windows.

Řetězec širokého znaku je vyjádřena jako `wchar_t[]` pole a odkazuje `wchar_t*` ukazatel. Libovolný znak ASCII můžou být vyjádřeny jako širokého znaku jsou písmeno L znak. Například L '\0' je ukončující znak NULL celou (16 bitů). Podobně všechny ASCII řetězcový literál může být reprezentována jako řetězcový literál širokého znaku jsou písmeno L na literál ASCII (L "Hello").

Obecně platí široké znaky nezabírají více místa v paměti než vícebajtových znaků, ale jsou rychlejší ke zpracování. Kromě toho národní prostředí pouze jeden lze znázornit v daný okamžik v vícebajtové kódování, že všechny znakové sady v celém světě jsou reprezentovány současně reprezentace Unicode.

Rozhraní MFC je kódování Unicode a knihovna MFC provede povolení Unicode pomocí přenosné makra, jak je znázorněno v následující tabulce.

## <a name="portable-data-types-in-mfc"></a>Přenosné datové typy v knihovně MFC

|Non-portable datový typ|Nahrazuje tento – makro|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`, `LPSTR` (Win32 datový typ) `LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (Win32 datový typ) `LPCWSTR`|`LPCTSTR`|

Třída `CString` používá `_TCHAR` jako její základ a poskytuje konstruktory a operátory pro snadné převody. Většinu operací s řetězci Unicode lze zapsat pomocí stejné logiky použité pro zpracování znakovou sadu Windows ANSI, s tím rozdílem, že je základní jednotka operace 16bitový znak namísto bajtů 8 bitů. Na rozdíl od práce s vícebajtových znakových sad, je není nutné (a by neměla) zacházet se znaky Unicode, jako by šlo o dva bajty odlišné. Máte však řešení s možností jeden znak reprezentován náhradní pár širokých znaků. Obecně platí ne napsat kód, který předpokládá, že délka řetězce je stejný jako počet znaků, zda úzké nebo široké, aby obsahoval.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Použití knihovny MFC kódování Unicode a podporu vícebajtovou znakovou sadu (MBCS)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Povolit kódování Unicode v mé aplikaci](../text/international-enabling.md)

- [Povolit kódování Unicode a MBCS v mé aplikaci](../text/internationalization-strategies.md)

- [Použití kódování Unicode k vytvoření mezinárodní programu](../text/unicode-programming-summary.md)

- [Přečtěte si o výhodách kódování Unicode](../text/benefits-of-character-set-portability.md)

- [Používat wmain, takže program spouštím můžu můžete předat argumenty širokých znaků](../text/support-for-using-wmain.md)

- [Prohlédnout souhrnné informace o programování v kódování Unicode](../text/unicode-programming-summary.md)

- [Další informace o mapování obecného textu pro přenositelnost šířky bajtu](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Viz také:
 [Text a řetězce](../text/text-and-strings-in-visual-cpp.md)  
 [Podpora použití funkce wmain](../text/support-for-using-wmain.md)  