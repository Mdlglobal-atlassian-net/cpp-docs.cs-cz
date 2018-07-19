---
title: Kontrolní výraz a uživatelem zadané zprávy (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 61531ad8471a7409a42fdd2d55b27a82d08ba340
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941025"
---
# <a name="assertion-and-user-supplied-messages-c"></a>Kontrolní výraz a uživatelem zadané zprávy (C++)
C++ jazyk podporuje tři mechanismy zpracování chyb, které vám pomůžou ladit vaše aplikace: [#error – direktiva](../preprocessor/hash-error-directive-c-cpp.md), [static_assert](../cpp/static-assert.md) – klíčové slovo a [vyhodnocení makra, _assert, _ wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) – makro. Všechny tři mechanismy vyvolávají chybové zprávy a dva z nich také testují kontrolní výrazy softwaru. Softwarové tvrzení Určuje podmínku, která očekáváte, že na hodnotu true v určitém místě v programu. Pokud kontrolní výraz doby kompilace selže, kompilátor vyvolá chybu kompilace a diagnostických zpráv. Selže-li kontrolní výraz modulu běhu, operační systém vyvolá diagnostickou zprávu a ukončí aplikaci.  
  
## <a name="remarks"></a>Poznámky  
 Životnost aplikace je tvořena předběžným zpracováním, kompilací a fází doby běhu. Každý mechanismus zpracování chyb přistupuje k informacím o ladění, které jsou k dispozici v průběhu jedné z těchto fází. Pro efektivní ladění je třeba zvolit mechanismus, který poskytuje příslušné informace o této fázi:  
  
-   [#Error – direktiva](../preprocessor/hash-error-directive-c-cpp.md) je v platnosti v době předběžného zpracování. Bezpodmínečně vysílá zprávy zadané uživatelem a způsobí selhání kompilace s chybou. Zpráva může obsahovat text, který je zpracováván direktivami preprocesoru, není však vyhodnocen žádný výsledný výraz.  
  
-   [Static_assert](../cpp/static-assert.md) deklarace je v platnosti v době kompilace. Testuje kontrolní výrazy softwaru, jež jsou reprezentovány pomocí integrálního výrazu zadaného uživatelem, který lze převést na hodnotu typu Boolean. Je-li výraz vyhodnocen jako nula (false), kompilátor vyvolá uživatelem definovanou zprávu a kompilace selže s chybou.  
  
     Deklarace `static_assert` je zvláště užitečná pro šablony ladění, protože argumenty šablony mohou být součástí výrazu definovaného uživatelem.  
  
-   [Vyhodnocení makra, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) – makro je v platnosti v době běhu. Vyhodnotí výraz definovaný uživatelem, a pokud je výsledek nula, systém vyvolá diagnostickou zprávu a ukončí aplikaci. Mnoho dalších maker, jako například[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) a tomuto makru _asserte –, ale vyvolává různé systémem nebo uživatelem definované diagnostické zprávy.  
  
## <a name="see-also"></a>Viz také  
 [#error – direktiva (C++)](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [_ASSERT, _asserte –, _ASSERT_EXPR makra](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [static_assert](../cpp/static-assert.md)   
 [_STATIC_ASSERT – makro](../c-runtime-library/reference/static-assert-macro.md)   
 [Šablony](../cpp/templates-cpp.md)