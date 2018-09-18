---
title: Diagnostika vytištěná podle funkce assert | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac5473a2dd592bbd9af2f65044d3d7d97515dc37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103383"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostika vytištěná podle funkce assert

**ANSI 4.2** diagnostické zprávy vytištěné funkcí a její chování **vyhodnocení** – funkce

**Vyhodnocení** funkce vytiskne diagnostickou zprávu a zavolá **přerušit** rutině, pokud je výraz nepravdivý (0). Diagnostická zpráva má tvar

> **Chyba kontrolního výrazu**: <em>výraz</em>**, soubor** <em>filename</em>**, řádek** *číslo řádku*

kde *filename* je název zdrojového souboru a *linenumber* je číslo řádku výrazu, který se ve zdrojovém souboru se nezdařilo. Pokud nebyla provedena žádná akce *výraz* hodnotu true (nenulovou).

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)