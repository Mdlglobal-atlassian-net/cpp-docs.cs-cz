---
title: Závažná chyba nástroje NMAKE U1001 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1001
dev_langs:
- C++
helpviewer_keywords:
- U1001
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4e465af5b4fa22c5f0ba5a9e01ebde0a7ee89e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068140"
---
# <a name="nmake-fatal-error-u1001"></a>Závažná chyba nástroje NMAKE U1001

Chyba syntaxe: neplatný znak 'znak"– makro

Daný znak se objeví v makru, ale není písmenem, číslicí nebo podtržítkem.

Tuto chybu může způsobovat chybějící dvojtečka v rozšíření makra:

```
syntax error : illegal character '=' in macro
```