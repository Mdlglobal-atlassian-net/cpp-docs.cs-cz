---
title: Chyba Linkerů LNK1223 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1223
dev_langs:
- C++
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8639919c74559829367108b36d62594e2a83a91a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067978"
---
# <a name="linker-tools-error-lnk1223"></a>Chyba linkerů LNK1223

soubor je neplatný nebo poškozený: soubor obsahuje neplatný .pdata příspěvky

Pro RISC platformy, které používají pdata tato chyba nastane, pokud kompilátor generované .pdata oddílu s seřazená položky.

Chcete-li vyřešit tento problém, pokuste se zkompilovat bez [/GL (optimalizace celého programu)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) povolena. Prázdných těl funkcí může také v některých případech způsobit k této chybě.