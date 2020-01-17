---
title: main – spuštění funkce a programu
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
ms.openlocfilehash: 28b0d826dc02376f952d3522f2f037eacd298b8e
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123939"
---
# <a name="main-function-and-program-execution"></a>main – spuštění funkce a programu

Každý program v jazyce C má primární (hlavní) funkci, která musí být pojmenována jako **Main**. Pokud váš kód dodržuje programovací model Unicode, můžete použít verzi s velkým znakem, která je **Hlavní**, **wmain**. **Hlavní** funkce slouží jako výchozí bod pro spuštění programu. Obvykle řídí spuštění programu pomocí směrování volání dalších funkcí v programu. Program obvykle zastaví provádění na konci **Main**, i když může z různých důvodů skončit v jiných místech programu. V některých případech, například při zjištění určité chyby, lze vynutit ukončení programu. Uděláte to tak, že použijete funkci **Exit** . Informace o a příklad použití funkce [Exit](../c-runtime-library/reference/exit-exit-exit.md) najdete v referenčních informacích ke *knihovně run-time* .

## <a name="syntax"></a>Syntaxe

```
main( int argc, char *argv[ ], char *envp[ ] )
```

## <a name="remarks"></a>Poznámky

Funkce v rámci zdrojového programu provádí jeden nebo více konkrétních úkolů. Funkce **Main** může volat tyto funkce a provádět jejich příslušné úkoly. Když funkce **Main** volá jinou funkci, předá řízení spuštění funkci, takže provádění začíná prvním příkazem ve funkci. Funkce vrátí řízení na **Main** , pokud je proveden příkaz `return` nebo když je dosaženo konce funkce.

Všechny funkce, včetně **Main**, můžete deklarovat jako parametry. Pojem „parametr“ nebo „formální parametr“ odkazuje na identifikátor, který přijímá hodnotu předanou funkci. Informace o předávání argumentů parametrům naleznete v tématu [Parameters](../c-language/parameters.md) . Když jedna funkce volá jinou, volaná funkce přijme hodnoty svých parametrů z volající funkce. Tyto hodnoty jsou označovány jako „argumenty“. Můžete deklarovat formální parametry do **Main** , aby mohla přijímat argumenty z příkazového řádku pomocí tohoto formátu:

Pokud chcete předat informace **Hlavní** funkci, jsou tyto parametry tradičně pojmenovány `argc` a `argv`, i když kompilátor jazyka C tyto názvy nevyžaduje. Typy parametrů `argc` a `argv` jsou definovány v jazyce C. Tradičně platí, že pokud je třetí parametr předán do **Main**, je tento parametr pojmenován `envp`. Příklady dále v této části ukazují, jak používat tyto tři parametry pro přístup k argumentům příkazového řádku. Následující části popisují tyto parametry.

Popis verze geografického znaku **Main**najdete v tématu [použití wmain](../c-language/using-wmain.md) .

## <a name="see-also"></a>Viz také:

[hlavní funkce a argumenty příkazového řádku (C++)](../cpp/main-function-command-line-args.md)\
[Analýza argumentů příkazového řádku jazyka C](../c-language/parsing-c-command-line-arguments.md)
