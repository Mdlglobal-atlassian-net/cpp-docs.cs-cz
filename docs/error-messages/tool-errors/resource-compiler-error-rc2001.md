---
title: Chyba kompilátoru prostředků RC2001 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2001
dev_langs:
- C++
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d75d0f906ba0d7be75ca5177bc1f58bccd226251
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039969"
---
# <a name="resource-compiler-error-rc2001"></a>Chyba kompilátoru prostředků RC2001

Obsahuje znak nového řádku – konstanta

Řetězcová konstanta pokračuje na druhý řádek bez buď zpětné lomítko (**\\**) nebo zavřením a otevřením dvojitých uvozovek (**"**).

Pro přerušení konstantu řetězce, který je na dva řádky ve zdrojovém souboru, proveďte jednu z následujících akcí:

- Konec řádku prvním znakem pokračování řádku, zpětného lomítka.

- Zavřete řetězec na prvním řádku s dvojité uvozovky a otevřete řetězec na další řádek s další uvozovku.

Není dostatečná k ukončení první řádek s \n řídicí sekvence pro vkládání znak nového řádku do řetězcová konstanta.