---
title: 'Unicode: Široká Charakterová sada'
ms.date: 11/04/2016
f1_keywords:
- c.international
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: dc9028be85870766af0274ede091d74a9b4d5130
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745435"
---
# <a name="unicode-the-wide-character-set"></a>Unicode: Široká Charakterová sada

Široký znak je znak vícejazyčné 2bajtových kód. Libovolný znak používaných moderní výpočetní po celém světě, včetně technických symbolů a speciálních znaků pro publikování, může být reprezentován podle specifikace Unicode jako širokého znaku. Vyvíjí a udržuje tak velké consortium, který zahrnuje Microsoft, Unicode standard je teď široce přijat.

Široký znak je typu **wchar_t**. Řetězec širokého znaku je vyjádřena jako **wchar_t []** pole a odkazuje `wchar_t*` ukazatel. Může představovat libovolný znak ASCII jako širokého znaku jsou písmeno **L** znak. Například L '\0' je ukončující znak null celou (16 bitů). Podobně může představovat libovolný řetězec ASCII literál širokého znaku řetězcový literál, jednoduše tak, že jsou písmeno L na literál ASCII (L "Hello").

Obecně platí široké znaky trvat i více místa v paměti vícebajtových znaků, ale jsou rychlejší ke zpracování. Kromě toho národní prostředí pouze jeden lze znázornit v daný okamžik v vícebajtové kódování, že všechny znakové sady v celém světě jsou reprezentovány současně reprezentace Unicode.

## <a name="see-also"></a>Viz také:

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
