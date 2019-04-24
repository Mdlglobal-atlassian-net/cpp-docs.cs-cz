---
title: Použití funkce wmain namísto main
ms.date: 11/04/2016
f1_keywords:
- wmain
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
ms.openlocfilehash: 8cdc986d1582d2b26f137e3147ce78bc83e9daca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257962"
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