---
title: Chyba kompilátoru prostředků RC2001
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: f4755e04a744d94636b4b37aaf727e0d733008ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602108"
---
# <a name="resource-compiler-error-rc2001"></a>Chyba kompilátoru prostředků RC2001

Obsahuje znak nového řádku – konstanta

Řetězcová konstanta pokračuje na druhý řádek bez buď zpětné lomítko (**\\**) nebo zavřením a otevřením dvojitých uvozovek (**"**).

Pro přerušení konstantu řetězce, který je na dva řádky ve zdrojovém souboru, proveďte jednu z následujících akcí:

- Konec řádku prvním znakem pokračování řádku, zpětného lomítka.

- Zavřete řetězec na prvním řádku s dvojité uvozovky a otevřete řetězec na další řádek s další uvozovku.

Není dostatečná k ukončení první řádek s \n řídicí sekvence pro vkládání znak nového řádku do řetězcová konstanta.