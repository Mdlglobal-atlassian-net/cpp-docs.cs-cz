---
title: Použití funkce wmain namísto main
ms.date: 11/04/2016
f1_keywords:
- wmain
helpviewer_keywords:
- main function, vs. wmain
- wmain function
ms.assetid: 7abb1257-b85c-413a-b913-d45b1582a71d
ms.openlocfilehash: f47d7219a54b197ec59f109cf08879774b48e6f7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857213"
---
# <a name="using-wmain-instead-of-main"></a>Použití funkce wmain namísto main

**Specifické pro společnost Microsoft**

V programovacím modelu Unicode můžete definovat verzi `main` funkce s velkým znakem. Použijte **wmain** místo `main`, pokud chcete zapsat přenosný kód, který dodržuje specifikaci Unicode.

Dodeklarujete formální parametry k **wmain** pomocí podobného formátu pro `main`. Následně je možné do aplikace předat argumenty širokých znaků a volitelně ukazatel prostředí širokých znaků. Parametry *argv* a *envp* pro **wmain** jsou typu `wchar_t*`.

Pokud program používá funkci `main`, prostředí vícebajtového znaku se při spuštění programu vytvoří v operačním systému. Kopie prostředí s velkým počtem znaků je vytvořena pouze v případě potřeby (například voláním funkce [_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md) nebo [_wputenv](../c-runtime-library/reference/putenv-wputenv.md) ). Existuje-li již prostředí MBCS, je při prvním volání `_wputenv` nebo při prvním volání `_wgetenv` vytvořeno odpovídající prostředí řetězce širokého znaku, na které je následně odkázáno pomocí globální proměnné `_wenviron`, což je verze širokého znaku globální proměnné `_environ`. V tomto okamžiku vedle sebe existují dvě kopie prostředí (znaková sada MBCS a Unicode), které jsou udržovány v operačním systému po celou dobu trvání aplikace.

Podobně platí, že pokud váš program používá funkci **wmain** , vytvoří se při prvním volání funkce `_putenv` nebo `getenv`prostředí znakové sady MBCS (ASCII), na které odkazuje globální proměnná `_environ`.

Další informace o prostředí znakové sady MBCS naleznete v tématu [jednobajtové a vícebajtové znakové sady](../c-runtime-library/single-byte-and-multibyte-character-sets.md) v *Referenční příručce ke knihovně run-time.*

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[main: spuštění programu](../cpp/main-program-startup.md)