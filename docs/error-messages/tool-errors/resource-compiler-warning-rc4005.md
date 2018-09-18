---
title: Upozornění kompilátoru prostředků RC4005 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 589fd008b3927887a8144b2fc63d2cbbde2af913
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028516"
---
# <a name="resource-compiler-warning-rc4005"></a>Upozornění kompilátoru prostředků RC4005

'identifier': předefinování makra

Identifikátor je definována dvakrát. Kompilátor používá druhou definici makra.

Toto upozornění může být způsobeno definování makra na příkazovém řádku a v kódu adresou `#define` směrnice. Je také může být způsobeno makra naimportované z vložených souborů.

Chcete-li upozornění odstranit, buď odeberte jednu z definic nebo použijte `#undef` direktiv před druhá definice.