---
title: Upozornění kompilátoru prostředků RC4005
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: 571c4ac285e9477b017dbc21cf9ff733539759d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613600"
---
# <a name="resource-compiler-warning-rc4005"></a>Upozornění kompilátoru prostředků RC4005

'identifier': předefinování makra

Identifikátor je definována dvakrát. Kompilátor používá druhou definici makra.

Toto upozornění může být způsobeno definování makra na příkazovém řádku a v kódu adresou `#define` směrnice. Je také může být způsobeno makra naimportované z vložených souborů.

Chcete-li upozornění odstranit, buď odeberte jednu z definic nebo použijte `#undef` direktiv před druhá definice.