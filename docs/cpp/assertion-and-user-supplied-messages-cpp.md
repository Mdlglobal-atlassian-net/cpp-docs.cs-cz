---
title: Kontrolní výraz a uživatelem zadané zprávy (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
ms.openlocfilehash: d76f0c2f7dc5a4202bff3f93e097a1c186f4601a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190557"
---
# <a name="assertion-and-user-supplied-messages-c"></a>Kontrolní výraz a uživatelem zadané zprávy (C++)

Jazyk podporuje tři mechanismy zpracování chyb, které vám pomůžou s laděním aplikace: [direktiva #error](../preprocessor/hash-error-directive-c-cpp.md), klíčové slovo Static_assert a [makro ASSERT _ASSERT _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) makro. [static_assert](../cpp/static-assert.md) C++ Všechny tři mechanismy vyvolávají chybové zprávy a dva z nich také testují kontrolní výrazy softwaru. Softwarový kontrolní výraz určuje podmínku, kterou očekáváte, že bude platit v určitém místě v programu. Pokud kontrolní výraz doby kompilace selže, kompilátor vyvolá chybu kompilace a diagnostických zpráv. Selže-li kontrolní výraz modulu běhu, operační systém vyvolá diagnostickou zprávu a ukončí aplikaci.

## <a name="remarks"></a>Poznámky

Životnost aplikace je tvořena předběžným zpracováním, kompilací a fází doby běhu. Každý mechanismus zpracování chyb přistupuje k informacím o ladění, které jsou k dispozici v průběhu jedné z těchto fází. Pro efektivní ladění je třeba zvolit mechanismus, který poskytuje příslušné informace o této fázi:

- [Direktiva #error](../preprocessor/hash-error-directive-c-cpp.md) je v platnosti v době předběžného zpracování. Bezpodmínečně vysílá zprávy zadané uživatelem a způsobí selhání kompilace s chybou. Zpráva může obsahovat text, který je zpracováván direktivami preprocesoru, není však vyhodnocen žádný výsledný výraz.

- Deklarace [static_assert](../cpp/static-assert.md) se projeví v době kompilace. Testuje kontrolní výrazy softwaru, jež jsou reprezentovány pomocí integrálního výrazu zadaného uživatelem, který lze převést na hodnotu typu Boolean. Je-li výraz vyhodnocen jako nula (false), kompilátor vyvolá uživatelem definovanou zprávu a kompilace selže s chybou.

   Deklarace `static_assert` je zvláště užitečná pro šablony ladění, protože argumenty šablony mohou být součástí výrazu definovaného uživatelem.

- [Makro assert _ASSERT, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) makro je v platnosti v době běhu. Vyhodnotí výraz definovaný uživatelem, a pokud je výsledek nula, systém vyvolá diagnostickou zprávu a ukončí aplikaci. Mnoho dalších maker, například[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) a _ASSERTE, připomíná toto makro, ale vydává různé diagnostické zprávy definované systémem nebo uživatelem.

## <a name="see-also"></a>Viz také

[#error – direktiva (C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)<br/>
[static_assert](../cpp/static-assert.md)<br/>
[_STATIC_ASSERT – makro](../c-runtime-library/reference/static-assert-macro.md)<br/>
[Šablony](../cpp/templates-cpp.md)
