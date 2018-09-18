---
title: Použití funkce wmain namísto main | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- wmain
dev_langs:
- C++
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 274065ac3d753b744813a1fc88804ea26d44487d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104371"
---
# <a name="using-wmain-instead-of-main"></a>Použití funkce wmain namísto main

## <a name="microsoft-specific"></a>Specifické pro Microsoft

V programovacím modelu Unicode, můžete definovat širokoznaké verze `main` funkce. Použití **wmain** místo `main` Pokud chcete zapsat přenositelný kód, který splňuje specifikace Unicode.

Deklarovat formální parametry **wmain** pomocí formátu podobného `main`. Následně je možné do aplikace předat argumenty širokých znaků a volitelně ukazatel prostředí širokých znaků. *Argv* a *envp* parametry **wmain** jsou typu `wchar_t*`.

Pokud program používá `main` funkce, prostředí vícebajtových znaků se vytvoří v operačním systému při spuštění programu. Kopie širokého znaku prostředí je vytvořen pouze v případě potřeby (například voláním [_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md) nebo [_wputenv](../c-runtime-library/reference/putenv-wputenv.md) funkce). Existuje-li již prostředí MBCS, je při prvním volání `_wputenv` nebo při prvním volání `_wgetenv` vytvořeno odpovídající prostředí řetězce širokého znaku, na které je následně odkázáno pomocí globální proměnné `_wenviron`, což je verze širokého znaku globální proměnné `_environ`. V tomto okamžiku vedle sebe existují dvě kopie prostředí (znaková sada MBCS a Unicode), které jsou udržovány v operačním systému po celou dobu trvání aplikace.

Podobně pokud program používá **wmain** funkce, prostředí MBCS (ASCII) se vytvoří při prvním volání `_putenv` nebo `getenv`a ukazuje `_environ` globální proměnné.

Další informace o prostředí MBCS naleznete v tématu [jednobajtové a vícebajtové znakové sady](../c-runtime-library/single-byte-and-multibyte-character-sets.md) v *Run-Time Library Reference.*

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[main: spuštění programu](../cpp/main-program-startup.md)