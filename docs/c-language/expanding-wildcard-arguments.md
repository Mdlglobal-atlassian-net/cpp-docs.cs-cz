---
title: Rozbalení argumentů zástupných znaků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d78b23f81b72d04e9299616b0273bc97bb7a4e0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078150"
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