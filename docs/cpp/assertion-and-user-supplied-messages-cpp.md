---
title: Kontrolní výraz a uživatelem zadané zprávy (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e93798dadee3e4270d82eac84a794c6133c05c07
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411702"
---
# <a name="assertion-and-user-supplied-messages-c"></a>Kontrolní výraz a uživatelem zadané zprávy (C++)
Ladění aplikace C++ jazyk podporuje tři zpracování chyb mechanismy, které vám pomůžou: [#error – direktiva](../preprocessor/hash-error-directive-c-cpp.md), [static_assert](../cpp/static-assert.md) – klíčové slovo a [assert – makro, _assert, _ wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) makro. Všechny tři mechanismy vyvolávají chybové zprávy a dva z nich také testují kontrolní výrazy softwaru. Kontrolní výraz softwaru Určuje podmínku, která byste měli být na určitém místě v programu na hodnotu true. Pokud kontrolní výraz doby kompilace selže, kompilátor vyvolá chybu kompilace a diagnostických zpráv. Selže-li kontrolní výraz modulu běhu, operační systém vyvolá diagnostickou zprávu a ukončí aplikaci.  
  
## <a name="remarks"></a>Poznámky  
 Životnost aplikace je tvořena předběžným zpracováním, kompilací a fází doby běhu. Každý mechanismus zpracování chyb přistupuje k informacím o ladění, které jsou k dispozici v průběhu jedné z těchto fází. Pro efektivní ladění je třeba zvolit mechanismus, který poskytuje příslušné informace o této fázi:  
  
-   [#Error – direktiva](../preprocessor/hash-error-directive-c-cpp.md) v předběžném zpracování čas je v platnosti. Bezpodmínečně vysílá zprávy zadané uživatelem a způsobí selhání kompilace s chybou. Zpráva může obsahovat text, který je zpracováván direktivami preprocesoru, není však vyhodnocen žádný výsledný výraz.  
  
-   [Static_assert](../cpp/static-assert.md) deklarace je v platnosti v čase kompilace. Testuje kontrolní výrazy softwaru, jež jsou reprezentovány pomocí integrálního výrazu zadaného uživatelem, který lze převést na hodnotu typu Boolean. Je-li výraz vyhodnocen jako nula (false), kompilátor vyvolá uživatelem definovanou zprávu a kompilace selže s chybou.  
  
     Deklarace `static_assert` je zvláště užitečná pro šablony ladění, protože argumenty šablony mohou být součástí výrazu definovaného uživatelem.  
  
-   [Assert – makro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) makro je v platnosti v době běhu. Vyhodnotí výraz definovaný uživatelem, a pokud je výsledek nula, systém vyvolá diagnostickou zprávu a ukončí aplikaci. Mnoho dalších maker, jako například[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) a `_ASSERTE`, vypadat podobně jako tento makro ale vydat jiné definované v systému nebo uživatelsky definovaných diagnostické zprávy.  
  
## <a name="see-also"></a>Viz také  
 [#error – direktiva (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [_ASSERT, _asserte –, _ASSERT_EXPR makra](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [static_assert](../cpp/static-assert.md)   
 [_Static_assert – makro](../c-runtime-library/reference/static-assert-macro.md)   
 [Šablony](../cpp/templates-cpp.md)