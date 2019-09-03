---
title: once – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 643ad83b672f7b632925383972751a966256eb41
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220539"
---
# <a name="once-pragma"></a>once – direktiva pragma

Určuje, že kompilátor zahrnuje hlavičkový soubor pouze jednou při kompilování souboru zdrojového kódu.

## <a name="syntax"></a>Syntaxe

> **#pragma jednou**

## <a name="remarks"></a>Poznámky

Použití `#pragma once` může snížit dobu sestavování, protože kompilátor se neotevře a znovu načte soubor po prvním `#include` souboru v jednotce překladu. Nazývá se *optimalizace vícenásobného zahrnutí*. Má podobný efekt jako příkaz *include Guard* idiom, který používá definice makra preprocesoru, aby nedocházelo k vícenásobnému zahrnutí obsahu souboru. Pomáhá také zabránit porušení *jednoho pravidla definice*, požadavek na to, že všechny šablony, typy, funkce a objekty nemají v kódu více než jednu definici.

Příklad:

```cpp
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

`#pragma once` Doporučujeme direktivu pro nový kód, protože se neznečišťující globální obor názvů se symbolem preprocesoru. Vyžaduje méně psaní, je méně rušivé a nemůže způsobit *kolize symbolů*, chyby způsobené v případě, že jiné soubory hlaviček používají stejný symbol preprocesoru jako hodnota Guard. Není součástí C++ standardu, ale je implementována přípravně několika běžnými kompilátory.

Neexistuje žádná výhoda použití obou funkcí include Guard idiom i `#pragma once` ve stejném souboru. Kompilátor rozpoznává idiomy Guard a implementuje optimalizaci s vícenásobným zahrnutím stejným způsobem jako `#pragma once` direktiva, pokud žádný kód nekomentáři ani direktiva preprocesoru nepatří do nebo po standardní formě idiom:

```cpp
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

Doporučujeme zahrnout idiom Guard, pokud kód musí být přenosný na kompilátory, které neimplementují `#pragma once` direktivu, pro zachování konzistence s existujícím kódem nebo v případě, že není možné optimalizovat vícenásobné zahrnutí. Může k tomu dojít v složitých projektech, když aliasy systému souborů nebo cesty include zabrání kompilátoru v identifikaci identických vložených souborů pomocí kanonické cesty.

Dejte pozor, abyste nepoužívali `#pragma once` nebo zahrnuli idiomy Guard do hlavičkových souborů, které jsou navržené tak, aby byly zahrnuty několikrát, které používají symboly preprocesoru k řízení jejich efektů. Příklad tohoto návrhu naleznete v \<> souboru hlaviček Assert. h. Také buďte opatrní při správě zahrnutých cest, abyste se vyhnuli vytváření více cest k zahrnutým souborům, což může mít za sebou možnost optimalizace vícenásobných zahrnutí pro zahrnuté i ochranné výrazy `#pragma once`.

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
