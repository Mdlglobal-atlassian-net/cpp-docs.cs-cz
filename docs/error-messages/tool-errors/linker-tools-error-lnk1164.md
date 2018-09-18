---
title: Chyba Linkerů LNK1164 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1164
dev_langs:
- C++
helpviewer_keywords:
- LNK1164
ms.assetid: da89765c-affa-4f88-b170-6d6b19a577cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b07dcf360a58b07b84abe655641b758d6137d0e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087425"
---
# <a name="linker-tools-error-lnk1164"></a>Chyba linkerů LNK1164

část zarovnání oddílu (číslo) větší než hodnota/align.

Velikost zarovnání pro danou část do souboru objektu nepřekročí hodnotu zadanou pomocí [/ALIGN](../../build/reference/align-section-alignment.md) možnost. **/ALIGN** hodnota musí být mocninou čísla 2 a musí být roven nebo překračují zarovnání oddílů v souboru objektu.

Buď zkompilujte znovu s menším zarovnání oddílů nebo zvýšení **/ALIGN** hodnotu.