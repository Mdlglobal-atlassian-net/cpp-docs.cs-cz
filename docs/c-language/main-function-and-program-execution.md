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
ms.openlocfilehash: e975f09b62ffbb536790c13eb8614453b1c1e8b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610428"
---
# <a name="main-function-and-program-execution"></a>main – spuštění funkce a programu

Každý program jazyka C má primární (hlavní) funkci, která musí mít název **hlavní**. Pokud váš kód používá programovací model Unicode, můžete použít verze širokého znaku **hlavní**, **wmain**. **Hlavní** funkci slouží jako výchozí bod pro spuštění programu. Obvykle řídí spuštění programu pomocí směrování volání dalších funkcí v programu. Program je obvykle ukončen na konci **hlavní**, i když můžete ukončit v jiných bodech programu z různých důvodů. V některých případech, například při zjištění určité chyby, lze vynutit ukončení programu. Chcete-li tak učinit, použijte **ukončit** funkce. Najdete v článku *Run-Time Library Reference* pro informace a příklad použití [ukončit](../c-runtime-library/reference/exit-exit-exit.md) funkce.

## <a name="syntax"></a>Syntaxe

```
main( int argc, char *argv[ ], char *envp[ ] )
```

## <a name="remarks"></a>Poznámky

Funkce v rámci zdrojového programu provádí jeden nebo více konkrétních úkolů. **Hlavní** funkce může volat tyto funkce k provedení svých úkolů. Když **hlavní** volá jinou funkci, předá řízení provádění této funkci, takže provádění začne prvním příkazem této funkce. Vrátí ovládací prvek **hlavní** při `return` je proveden příkaz nebo když je dosaženo konce funkce.

Je možné deklarovat všechny funkce, včetně **hlavní**s parametry. Pojem „parametr“ nebo „formální parametr“ odkazuje na identifikátor, který přijímá hodnotu předanou funkci. Zobrazit [parametry](../c-language/parameters.md) informace o předávání argumentů do parametrů. Když jedna funkce volá jinou, volaná funkce přijme hodnoty svých parametrů z volající funkce. Tyto hodnoty jsou označovány jako „argumenty“. Lze deklarovat formální parametry **hlavní** tak, aby může přijímat argumenty z příkazového řádku pomocí tohoto formátu:

Pokud chcete předat informace **hlavní** funkce, parametry jsou tradičně pojmenovány `argc` a `argv`, i když kompilátor jazyka C tyto názvy nevyžaduje. Typy parametrů `argc` a `argv` jsou definovány v jazyce C. Tradičně, pokud třetí parametr je předán do **hlavní**, tento parametr je pojmenován `envp`. Příklady dále v této části ukazují, jak používat tyto tři parametry pro přístup k argumentům příkazového řádku. Následující části popisují tyto parametry.

Zobrazit [použití funkce wmain](../c-language/using-wmain.md) popis širokoznaké verze **hlavní**.

## <a name="see-also"></a>Viz také

[main: spuštění programu](../cpp/main-program-startup.md)<br/>
[Analýza argumentů příkazového řádku jazyka C](../c-language/parsing-c-command-line-arguments.md)
