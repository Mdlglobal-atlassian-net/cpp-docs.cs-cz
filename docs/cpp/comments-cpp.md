---
title: Komentáře (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- code comments, C++
- comments, documenting code
- comments, C++ code
- white space, C++ comments
ms.assetid: 6fcb906c-c264-4083-84bc-373800b2e514
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 919c40dce53dd5d1c8847287099c61c3e1b229cf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="comments-c"></a>Komentáře (C++)
Komentář je text, který kompilátor ignoruje, ale je užitečný pro programátory. Komentáře se obvykle používají pro popis kódu pro pozdější použití. Kompilátor je zpracovává jako prázdné znaky. Komentáře v testování můžete nastavit určité řádků kódu neaktivní; ale `#if` / `#endif` preprocesor – direktivy fungují lépe pro tento protože můžete obklopit kód, který obsahuje komentáře, ale nelze je vnořovat komentáře.  
  
 Komentář v jazyce C++ je zapsán některým z následujících způsobů:  
  
-   Znaky `/*` (lomítko, hvězdička) následované libovolnou posloupností znaků (včetně nových řádků) jsou následovány znaky `*/`. Tato syntaxe je stejná jako standard ANSI C.  
  
-   Znaky `//` (dvě lomítka) jsou následovány libovolnou posloupností znaků. Nový řádek, kterému bezprostředně nepředchází zpětné lomítko, ukončí tento typ komentáře. Proto se běžně nazývá „jednořádkový komentář“.  
  
 Znaky komentáře (`/*`, `*/` a `//`) nemají žádný zvláštní význam v rámci znakové konstanty, textového literálu ani komentáře. Komentáře zapsané pomocí první syntaxe proto nelze vnořovat.  
  
## <a name="see-also"></a>Viz také  
 [Lexikální konvence](../cpp/lexical-conventions.md)