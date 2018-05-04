---
title: 'Unicode: Široká Charakterová sada | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.international
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60fd19a46cff5607a768309585ab876f4a894db6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="unicode-the-wide-character-set"></a>Unicode: široká charakterová sada

Široká znaková je kód 2bajtová vícejazyčné znaků. Libovolný znak v použití moderní počítačů po celém světě, včetně technických symbolů a speciálních znaků pro publikování, může být reprezentován podle specifikace Unicode jako široký znak. Vyvíjí a udržuje velké Consortium, která zahrnuje Microsoft, standardu Unicode je nyní široce přijat.

Široká znaková je typu **wchar_t**. Řetězec široká charakterová je reprezentován jako **[wchar_t]** pole a ukazuje `wchar_t*` ukazatel. Může představovat libovolný znak ASCII jako široký znak přidáním prefixu písmena **L** znaku. L '\0' je například ukončení širokého (16 bitů) **NULL** znak. Podobně může představovat libovolný ASCII řetězcový literál jako široká charakterová řetězcový literál jednoduše tak, že prefixu písmena L k literál ASCII (L "Hello").

Obecně platí široké znaky trvat až další místo v paměti, než vícebajtové znaky, ale jsou rychlejší ke zpracování. Navíc jenom jeden národního prostředí může být reprezentován v daný okamžik v vícebajtové kódování, zatímco všechny znakové sady na světě jsou reprezentována současně reprezentace kódování Unicode.

## <a name="see-also"></a>Viz také

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
