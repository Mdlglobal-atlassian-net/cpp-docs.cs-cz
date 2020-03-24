---
title: Komentáře (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
ms.openlocfilehash: 3326ad7d0b5118182a5d582061fd0c103986f232
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189751"
---
# <a name="comments-c"></a>Komentáře (C++)

Komentář je text, který kompilátor ignoruje, ale je užitečný pro programátory. Komentáře se obvykle používají pro popis kódu pro pozdější použití. Kompilátor je zpracovává jako prázdné znaky. Můžete použít komentáře v testování, aby byly některé řádky kódu neaktivní; Nicméně `#if`/`#endif` direktivy preprocesoru fungují lépe, protože můžete obklopit kód, který obsahuje komentáře, ale komentáře nelze vnořovat.

Komentář v jazyce C++ je zapsán některým z následujících způsobů:

- Znaky `/*` (lomítko, hvězdička) následované libovolnou posloupností znaků (včetně nových řádků) jsou následovány znaky `*/`. Tato syntaxe je stejná jako standard ANSI C.

- Znaky `//` (dvě lomítka) jsou následovány libovolnou posloupností znaků. Nový řádek, kterému bezprostředně nepředchází zpětné lomítko, ukončí tento typ komentáře. Proto se běžně nazývá „jednořádkový komentář“.

Znaky komentáře (`/*`, `*/` a `//`) nemají žádný zvláštní význam v rámci znakové konstanty, textového literálu ani komentáře. Komentáře zapsané pomocí první syntaxe proto nelze vnořovat.

## <a name="see-also"></a>Viz také

[Lexikální konvence](../cpp/lexical-conventions.md)
