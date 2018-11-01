---
title: once
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 3adb7ab30b445ab3223246d247be006d24475afa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534599"
---
# <a name="once"></a>once
Určuje, že soubor bude pomocí kompilátoru při kompilaci souboru zdrojového kódu obsažen (otevřen) pouze jednou.

## <a name="syntax"></a>Syntaxe

```
#pragma once
```

## <a name="remarks"></a>Poznámky

Použití `#pragma once` lze snížit dobu sestavení, protože kompilátor nesmí otevřít a číst soubor po první `#include` souboru v jednotce překladu. To se označuje jako *více obsahoval optimalizace, které*. Je podobný vliv `#include guard` idiom, který využívá Definice preprocesoru maker, která brání více zahrnutí obsah souboru. To také pomáhá zabránit porušení *jednu definici pravidla*– tento požadavek, že všechny šablony, typy, funkce a objekty mají více než jednu definici ve vašem kódu.

Příklad:

```
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

Doporučujeme, abyste `#pragma once` směrnice pro nový kód, protože není znečištění směrovány správu globální obor názvů s symbol preprocesoru. Vyžaduje méně psát, je méně rušivé a nemůže způsobit symbol kolizí – chyb vzniklých při různých hlavičkové soubory jako hodnotu guard používat stejné symbol preprocesoru. Není součástí standardu C++, ale je implementována přenositelnosti několik běžných kompilátory.

Neexistuje žádná výhoda použít i #include guard idiom a `#pragma once` ve stejném souboru. Kompilátor rozpozná #include guard idiom a implementuje násobek obsahoval optimalizace, stejně jako `#pragma once` směrnice, pokud žádný kód mimo komentář nebo direktivy preprocesoru pochází před nebo po standardní formuláře idiom:

```
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

Doporučujeme, abyste `#include guard` idiom, když kód musí být nepřenositelné na kompilátory, které neimplementují `#pragma once` směrnice, můžete zachovat konzistenci s existujícím kódem, nebo když zahrnují více optimalizace není možné. Tato situace může nastat ve složitých projektů při vytváření aliasů systému souborů nebo alias k zahrnutí cesty k zabránění kompilátoru v identifikaci identické soubory k zahrnutí canonical cestou.

Dejte pozor, abyste pomocí `#pragma once` nebo `#include guard` idiom v souborech hlaviček, které jsou určeny mají být zahrnuty více než jednou, pomocí symboly preprocesoru řídit jejich důsledky. Příklad tohoto návrhu, najdete v článku \<assert.h > soubor hlaviček. Také být opatrní při správě zahrnout cesty do Vyhněte se vytváření více cest k zahrnuté soubory, které, aby zhatila více obsahoval optimalizace, které pro obě `#include guard`s a `#pragma once`.

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)