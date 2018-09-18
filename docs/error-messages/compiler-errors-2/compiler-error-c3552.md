---
title: Chyba kompilátoru C3552 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd9f7ae37500e115fa33fa61298cab800c88f9c7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081257"
---
# <a name="compiler-error-c3552"></a>Chyba kompilátoru C3552

'typename': pozdně zadaný návratový typ nemůže obsahovat 'auto'

Pokud používáte `auto` – klíčové slovo jako zástupný symbol pro návratový typ funkce, je nutné zadat pozdně zadaný návratový typ. Však nelze použít jiné `auto` – klíčové slovo k určení pozdně zadaný návratový typ. Například následující fragment kódu vrátí chyba C3552.

`auto myFunction->auto; // C3552`