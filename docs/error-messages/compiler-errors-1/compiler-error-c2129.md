---
title: Chyba kompilátoru C2129 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2129
dev_langs:
- C++
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e86515a7d7c8954271578291c4ebcb1a52fc9863
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054282"
---
# <a name="compiler-error-c2129"></a>Chyba kompilátoru C2129

statické funkce 'function' deklarovaná, ale nedefinovaná.

Dopředný odkaz provedené `static` funkce, která se nikdy definovaný.

A `static` funkce musí být definován v oboru souboru. Pokud funkce je definována v jiném souboru, musí být deklarován `extern`.