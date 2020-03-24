---
title: Chyba kompilátoru C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: 567c92ddabbe2517700e4c67ef2c1ba899baada8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200665"
---
# <a name="compiler-error-c3552"></a>Chyba kompilátoru C3552

typeName: pozdní zadaný návratový typ nemůže obsahovat auto.

Použijete-li klíčové slovo `auto` jako zástupný symbol pro návratový typ funkce, je nutné zadat návratový typ s pozdním zadáním. Nemůžete však použít jiné klíčové slovo `auto` k určení zpožděného návratového typu. Například následující fragment kódu má za důsledek chybu C3552.

`auto myFunction->auto; // C3552`
