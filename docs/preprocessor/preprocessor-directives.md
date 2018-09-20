---
title: Direktivy preprocesoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3835d3c3d2900b97c16bc82963df2d08f35a879d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416289"
---
# <a name="preprocessor-directives"></a>Preprocesor – direktivy

Direktivy preprocesoru, jako například `#define` a `#ifdef`, se obvykle používají ke snadnému sestavení v různých pracovních prostředích a snadné změně zdrojových programů. Směrnice ve zdrojovém souboru říkají preprocesoru, že má provést konkrétní akce. Preprocesor může například nahradit tokeny v textu, vložit obsah z jiných souborů do zdrojového souboru nebo potlačit kompilaci části souboru odebráním úseků textu. Řádky preprocesoru jsou rozpoznány a provedeny před rozšířením makra. Proto pokud se makro rozšíří na něco, co vypadá jako příkaz preprocesoru, tento příkaz není rozpoznáván preprocesorem.

Příkazy preprocesoru používají stejnou znakovou sadu jako příkazy zdrojového souboru, s tím rozdílem, že Řídící sekvence nejsou podporovány. Znaková sada použitá v rámci příkazu preprocesoru je stejná jako znaková sada spuštění. Preprocesor rozpoznává také negativní hodnoty znaků.

Preprocesor rozpoznává následující direktivy:

|||||
|-|-|-|-|
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||

Znak čísla (**#**) musí být první nemezerový znak na řádku, který obsahuje směrnici; mezerové znaky mohou objevit mezi znakem čísla a prvním písmenem směrnice. Některé direktivy zahrnují argumenty nebo hodnoty. Jakýkoli text, který následuje direktivu (s výjimkou argumentu nebo hodnotu, která je součástí této direktivy) musí být předcházen oddělovač jednořádkový komentář (**//**) nebo uzavřen mezi oddělovače komentáře ( __/ \*\*/__). Řádky obsahující pokyny preprocesoru lze navázat tak, že bezprostředně před značku konec řádku zpětným lomítkem (**\\**).

Direktivy preprocesoru může vyskytovat kdekoli ve zdrojovém souboru, ale se vztahují pouze na zbývající část zdrojového souboru.

## <a name="see-also"></a>Viz také:

[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)<br/>
[Předdefinovaná makra](../preprocessor/predefined-macros.md)<br/>
[C/C++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)  
