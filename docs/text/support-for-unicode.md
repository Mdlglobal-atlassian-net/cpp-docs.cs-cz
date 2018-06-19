---
title: Podpora pro Unicode | Microsoft Docs
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
ms.openlocfilehash: b9d5a435339e366d70749d64e5aae9264fe12b1f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858403"
---
# <a name="support-for-unicode"></a>Podpora pro Unicode

Unicode je specifikace pro podporu všech znakových sad, včetně těch, které nelze vyjádřit v právě jeden bajt (tj. Většina z nich). Pokud programujete pro mezinárodní trh, doporučujeme použít buď Unicode nebo [vícebajtové znakové sady](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS), nebo code vašeho programu, můžete ho vytvořit pro buď změnou přepínače.

Široká znaková je kód 2bajtová vícejazyčné znaků. Desítkami tisíc znaků, která obsahuje téměř všechny znaky používá moderní počítačů po celém světě, včetně technické symbolů a speciálních znaků pro publikování, může být reprezentován podle specifikace kódování Unicode jako jeden celou kódování znaků pomocí pomocí znakové sady UTF-16. Znaky, které nelze vyjádřit v právě jeden znak širokou představovat v páru Unicode pomocí funkce Unicode náhradní pár. Protože téměř každý znak běžně používaných je reprezentována v UTF-16 v jednom 16bitové široká znaková, pomocí široké znaky zjednodušuje programování s mezinárodními znakových sad. Široké znaky kódované pomocí znakové sady UTF-16LE (pro little endian) jsou formát nativní znak pro Windows.

Řetězec široká charakterová je reprezentován jako `wchar_t[]` pole a ukazuje `wchar_t*` ukazatel. Libovolný znak ASCII může být reprezentovaný jako široký znak prefixu písmena L znaku. L '\0' je například ukončení širokého (16 bitů) **NULL** znak. Podobně žádné ASCII řetězcový literál může být reprezentovaný jako široká charakterová řetězcový literál prefixu písmena L k literál ASCII (L "Hello").

Obecně platí široké znaky trvat další místo v paměti, než vícebajtové znaky, ale jsou rychlejší ke zpracování. Navíc jenom jeden národního prostředí může být reprezentován v daný okamžik v vícebajtové kódování, zatímco všechny znakové sady na světě jsou reprezentována současně reprezentace kódování Unicode.

Rozhraní MFC framework je kódování Unicode a MFC provede, povolení Unicode pomocí přenosných maker, jak je znázorněno v následující tabulce.

## <a name="portable-data-types-in-mfc"></a>Přenosné datové typy v prostředí MFC

|Bez přenositelností datový typ|Nahrazuje tento – makro|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`, `LPSTR` (Win32 datový typ) `LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (Win32 datový typ) `LPCWSTR`|`LPCTSTR`|

Třída `CString` používá `_TCHAR` jako jeho základní a poskytuje konstruktory a operátory pro snadné převody. Většina řetězcových operací pro kódování Unicode lze zapsat pomocí stejné logiky, která používá pro zpracování znakovou sadu ANSI systému Windows, s tím rozdílem, že základní jednotkou operace je znak 16bitové místo 8bitové bajtů. Na rozdíl od práce vícebajtových znakových sad, můžete nemusíte (a neměli) zacházet se znaky Unicode, jako by šlo dva rozdílné bajty. Máte, ale, jak nakládat s možností jednoho znaku reprezentována pár náhradní široké znaky. Obecně platí není napsat kód, který předpokládá, že délka řetězce je stejný jako počet znaků, ať už úzké nebo široké, aby obsahoval.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Vícebajtové znakové sady MBCS Podpora kódování Unicode MFC použití a](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Povolit kódování Unicode v mém programu](../text/international-enabling.md)

- [Povolit kódování Unicode a MBCS v mém programu](../text/internationalization-strategies.md)

- [Vytvoření mezinárodního programu pomocí kódování Unicode](../text/unicode-programming-summary.md)

- [Seznamte se s výhodami kódování Unicode](../text/benefits-of-character-set-portability.md)

- [Používat wmain, takže I široká charakterová argumenty předat programem](../text/support-for-using-wmain.md)

- [Zobrazit souhrn programování Unicode](../text/unicode-programming-summary.md)

- [Další informace o mapování obecného textu pro přenositelnost šířky bajtu](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Viz také

[Text a řetězce](../text/text-and-strings-in-visual-cpp.md)  
[Podpora použití funkce wmain](../text/support-for-using-wmain.md)  
