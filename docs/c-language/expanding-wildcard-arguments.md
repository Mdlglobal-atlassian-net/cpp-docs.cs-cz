---
title: Rozbalení argumentů zástupných znaků
ms.date: 11/04/2016
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
ms.openlocfilehash: 2224d01eeb3ec54a9c0ff895dfa45574135f7c0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443417"
---
# <a name="expanding-wildcard-arguments"></a>Rozbalení argumentů zástupných znaků

**Specifické pro Microsoft**

Při spuštění programu v jazyce C, můžete použít buď dva zástupné znaky – otazník (?) a hvězdičku (*) – chcete zadat cestu a název souboru argument v příkazovém řádku.

Zástupné znaky nejsou ve výchozím nastavení, rozbalení argumentů příkazového řádku. Můžete nahradit vektoru normální argument `argv` načítání rutinu s verzí, díky propojení s setargv.obj nebo wsetargv.obj soubor rozšiřovat zástupné znaky. Pokud program používá `main` funkce, propojení s knihovnou setargv.obj. Pokud program používá `wmain` funkce, propojení s knihovnou wsetargv.obj. Obě tyto mají ekvivalentní chování.

Chcete-li propojit s setargv.obj nebo wsetargv.obj, použijte **/link** možnost. Příklad:

**cl example.c/Link setargv.obj**

Zástupné znaky jsou rozbaleny stejným způsobem jako příkazy operačního systému. (Viz příručka uživatele operačního systému, pokud nejste obeznámeni se zástupnými znaky.)

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Možnosti odkazů](../c-runtime-library/link-options.md)<br/>
[main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)