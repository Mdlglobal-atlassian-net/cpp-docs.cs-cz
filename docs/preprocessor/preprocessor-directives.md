---
title: Direktivy preprocesoru
ms.date: 08/29/2019
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
ms.openlocfilehash: 86432ebf210523dd958f3258075d9e9c6d3bb4e6
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222275"
---
# <a name="preprocessor-directives"></a>Direktivy preprocesoru

Direktivy preprocesoru, jako `#define` jsou a `#ifdef`, se obvykle používají k usnadnění změny zdrojových programů a jejich kompilaci v různých prostředích pro spuštění. Direktivy ve zdrojovém souboru oznamují, aby preprocesor přijal konkrétní akce. Například preprocesor může nahradit tokeny v textu, vložit obsah dalších souborů do zdrojového souboru nebo potlačit kompilaci části souboru odebráním oddílů textu. Řádky preprocesoru jsou rozpoznány a provedeny před rozšířením makra. Proto pokud se makro rozšíří na něco, co vypadá jako příkaz preprocesoru, není rozpoznán preprocesorem.

Příkazy preprocesoru používají stejnou sadu znaků jako příkazy zdrojového souboru, s výjimkou, že řídicí sekvence nejsou podporovány. Znaková sada použitá v příkazech preprocesoru je stejná jako znaková sada spuštění. Preprocesor také rozpoznává záporné hodnoty znaků.

Preprocesor rozpoznává následující direktivy:

|||||
|-|-|-|-|
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||

Znak čísla (`#`) musí být prvním neprázdným znakem na řádku, který obsahuje direktivu. Mezi znakem čísla a prvním písmenem direktivy se mohou vyskytovat prázdné znaky. Některé direktivy obsahují argumenty nebo hodnoty. Jakýkoli text, který následuje za direktivou (s výjimkou argumentu nebo hodnoty, který je součástí direktivy), musí předcházet oddělovač komentářů () s jedním`//`řádkem () nebo uzavřený v oddělovačích komentářů (`/* */`). Řádky obsahující direktivy preprocesoru lze pokračovat přímo před značkou konce řádku pomocí zpětného lomítka (`\`).

Direktivy preprocesoru se mohou objevit kdekoli ve zdrojovém souboru, ale po zobrazení se vztahují pouze na zbytek zdrojového souboru.

## <a name="see-also"></a>Viz také:

[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)\
[Předdefinovaná makra](../preprocessor/predefined-macros.md)\
[c/c++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)
