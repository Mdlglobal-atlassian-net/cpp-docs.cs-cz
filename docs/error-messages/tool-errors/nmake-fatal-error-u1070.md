---
title: NMAKE U1070 závažná chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1070
dev_langs:
- C++
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6eb462e5c3c7e497cde55151bf92c62ffb2afcd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087016"
---
# <a name="nmake-fatal-error-u1070"></a>Závažná chyba nástroje NMAKE U1070

zacyklení v definici makra "makro"

Definice makra dané obsažené makra, jejichž definice obsahovala danou – makro. Definice maker cyklické jsou neplatné.

## <a name="example"></a>Příklad

Následující definice – makro

```
ONE=$(TWO)
TWO=$(ONE)
```

způsobit následující chybu:

```
cycle in macro definition 'TWO'
```