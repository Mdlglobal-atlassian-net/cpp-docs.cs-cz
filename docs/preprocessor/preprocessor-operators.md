---
title: Operátory preprocesoru
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
ms.openlocfilehash: 5dd252fb495a05efe6eef45674f9ecd601a298a7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857941"
---
# <a name="preprocessor-operators"></a>Operátory preprocesoru

V kontextu direktivy `#define` se používají čtyři operátory specifické pro preprocesor. V následující tabulce najdete souhrn každé z nich. V následujících třech částech jsou popsány operátory převádějící na řetězec, převádějící na znak a vkládající token. Informace o operátoru `defined` naleznete v tématu [direktivy #if, #elif, #else a #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

|Operátor|Akce|
|--------------|------------|
|[Převodu – operátor (#)](../preprocessor/stringizing-operator-hash.md)|Způsobí, že odpovídající argument bude uzavřen v uvozovkách|
|[Charakterizace – operátor (# @)](../preprocessor/charizing-operator-hash-at.md)|Způsobí, že odpovídající argument bude uzavřen v jednoduchých uvozovkách a bude považován za znak (specifický pro společnost Microsoft).|
|[Operátor vložení tokenu (# #)](../preprocessor/token-pasting-operator-hash-hash.md)|Umožňuje, aby byly tokeny používané jako argumenty zřetězeny s dalšími tokeny, a tím vytvořily další tokeny|
|[definovaný operátor](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Zjednodušuje psaní složených výrazů v některých direktivách maker|

## <a name="see-also"></a>Viz také:

[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)\
[Předdefinovaná makra](../preprocessor/predefined-macros.md)\
[c/c++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)
