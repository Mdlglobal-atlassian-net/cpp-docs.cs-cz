---
title: Upozornění nástroje NMAKE U4004 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4004
dev_langs:
- C++
helpviewer_keywords:
- U4004
ms.assetid: 5086bbcb-42d7-4677-a877-1a02202a86a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a89bb8abf212c8a0ffa9fb40fe5d3ea43307a08
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016647"
---
# <a name="nmake-warning-u4004"></a>Upozornění nástroje NMAKE U4004

příliš mnoho pravidel pro cíl targetname

Byla zadána více než jeden blok popis pro danou cílovou pomocí jednoho dvojtečky (**:**) jako oddělovače. NMAKE spouští příkazy v první blok popis a novější bloky ignorovat.

K určení stejného cíle ve více závislostí, použijte dvojité dvojtečky (`::`) jako oddělovač v každém řádku závislostí.