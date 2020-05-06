---
title: Používání výrazu wmain
ms.date: 11/04/2016
helpviewer_keywords:
- wmain function
ms.assetid: d0300812-adc4-40c6-bba3-b2da25468c80
ms.openlocfilehash: d467d50a7188cd665f64de8b6f0ce6e6a37df752
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290817"
---
# <a name="using-wmain"></a>Používání výrazu wmain

**Specifické pro Microsoft**

V programovacím modelu Unicode můžete definovat verzi s velkým znakem **Hlavní** funkce. Použijte **wmain** namísto **Main** , pokud chcete zapsat přenosný kód, který odpovídá programovacímu modelu Unicode.

## <a name="syntax"></a>Syntaxe

```
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

## <a name="remarks"></a>Poznámky

Dodeklarujete formální parametry k **wmain** pomocí podobného formátu pro **Main**. Následně je možné do aplikace předat argumenty širokých znaků a volitelně ukazatel prostředí širokých znaků. Parametry `argv` a `envp` pro **wmain** jsou typu `wchar_t*`. Příklad:

Používá-li program funkci **Main** , je prostředí vícebajtového znaku vytvořeno při spuštění programu v běhové knihovně. Kopie prostředí s velkým počtem znaků je vytvořena pouze v případě potřeby (například voláním funkce `_wgetenv` nebo `_wputenv` ). Existuje-li již prostředí MBCS, je při prvním volání `_wputenv` nebo při prvním volání `_wgetenv` vytvořeno odpovídající prostředí řetězce širokého znaku, na které je následně odkázáno pomocí globální proměnné `_wenviron`, což je verze širokého znaku globální proměnné `_environ`. V tomto okamžiku vedle sebe existují dvě kopie prostředí (znaková sada MBCS a Unicode), které jsou udržovány v operačním systému po celou dobu trvání aplikace.

Podobně platí, že pokud váš program používá funkci **wmain** , prostředí s velkým znakem se vytvoří při spuštění programu a ukazuje na `_wenviron` globální proměnnou. Prostředí znakové sady MBCS (ASCII) je vytvořeno při prvním volání `_putenv` nebo `getenv`a ukazuje na `_environ` globální proměnnou.

Další informace o prostředí znakové sady MBCS naleznete v tématu [mezinárodní](../c-runtime-library/internationalization.md) použití v *Referenční příručce knihovny run-time.*

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)
