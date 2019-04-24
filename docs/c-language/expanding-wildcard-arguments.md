---
title: Rozbalení argumentů zástupných znaků
ms.date: 11/04/2016
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
ms.openlocfilehash: f1fb964fe98223fb7187b83c7101027ed1f9cbea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233804"
---
# <a name="expanding-wildcard-arguments"></a>Rozbalení argumentů zástupných znaků

**Microsoft Specific**

Při spuštění programu v jazyce C, můžete použít buď dva zástupné znaky – otazník (?) a hvězdičku (*) – chcete zadat cestu a název souboru argument v příkazovém řádku.

Zástupné znaky nejsou ve výchozím nastavení, rozbalení argumentů příkazového řádku. Můžete nahradit vektoru normální argument `argv` načítání rutinu s verzí, díky propojení s setargv.obj nebo wsetargv.obj soubor rozšiřovat zástupné znaky. Pokud program používá `main` funkce, propojení s knihovnou setargv.obj. Pokud program používá `wmain` funkce, propojení s knihovnou wsetargv.obj. Obě tyto mají ekvivalentní chování.

Chcete-li propojit s setargv.obj nebo wsetargv.obj, použijte **/link** možnost. Příklad:

**cl example.c/Link setargv.obj**

Zástupné znaky jsou rozbaleny stejným způsobem jako příkazy operačního systému. (Viz příručka uživatele operačního systému, pokud nejste obeznámeni se zástupnými znaky.)

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Možnosti odkazů](../c-runtime-library/link-options.md)<br/>
[main – spuštění funkce a programu](../c-language/main-function-and-program-execution.md)
