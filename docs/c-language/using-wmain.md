---
title: Používání výrazu wmain
ms.date: 11/04/2016
helpviewer_keywords:
- wmain function
ms.assetid: d0300812-adc4-40c6-bba3-b2da25468c80
ms.openlocfilehash: 65efacb76e80dedee13d8e1af017686075c1168e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460590"
---
# <a name="using-wmain"></a>Používání výrazu wmain

**Specifické pro Microsoft**

V programovacím modelu Unicode, můžete definovat širokoznaké verze **hlavní** funkce. Použití **wmain** místo **hlavní** Pokud chcete zapsat přenositelný kód, který splňuje Unicode programovacího modelu.

## <a name="syntax"></a>Syntaxe

```
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

## <a name="remarks"></a>Poznámky

Deklarovat formální parametry **wmain** pomocí formátu podobného **hlavní**. Následně je možné do aplikace předat argumenty širokých znaků a volitelně ukazatel prostředí širokých znaků. `argv` a `envp` parametry **wmain** jsou typu `wchar_t*`. Příklad:

Pokud program používá **hlavní** funkce, vytvoří prostředí vícebajtových znaků knihovny run-time při spuštění programu. Kopie širokého znaku prostředí je vytvořen pouze v případě potřeby (například voláním `_wgetenv` nebo `_wputenv` funkce). Existuje-li již prostředí MBCS, je při prvním volání `_wputenv` nebo při prvním volání `_wgetenv` vytvořeno odpovídající prostředí řetězce širokého znaku, na které je následně odkázáno pomocí globální proměnné `_wenviron`, což je verze širokého znaku globální proměnné `_environ`. V tomto okamžiku vedle sebe existují dvě kopie prostředí (znaková sada MBCS a Unicode), které jsou udržovány v operačním systému po celou dobu trvání aplikace.

Podobně pokud program používá **wmain** funkce, širokého znaku prostředí je vytvořen při spuštění programu a odkazuje `_wenviron` globální proměnné. Prostředí MBCS (ASCII) se vytvoří při prvním volání `_putenv` nebo `getenv`a ukazuje `_environ` globální proměnné.

Další informace o prostředí MBCS naleznete v tématu [internacionalizace](../c-runtime-library/internationalization.md) v *Run-Time Library Reference.*

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)