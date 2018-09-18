---
title: Upozornění nástroje NMAKE U4010 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4010
dev_langs:
- C++
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a640245db460f4cd8cd658c097955a69a59d1fb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117490"
---
# <a name="nmake-warning-u4010"></a>Upozornění nástroje NMAKE U4010

'target': sestavení selhalo; /K zadán, pokračování...

Příkaz v bloku příkazů pro danou cílovou vrátil nenulový ukončovací kód. Možnost /K informaci NMAKE pokračovat ve zpracovávání nesouvisejících částí sestavení a vydání ukončovací kód 1 až po dokončení NMAKE relace.

Pokud je daného cíle, samotný závislé pro jiný cíl, NMAKE vydá upozornění [U4011](../../error-messages/tool-errors/nmake-warning-u4011.md) po tomto upozornění.