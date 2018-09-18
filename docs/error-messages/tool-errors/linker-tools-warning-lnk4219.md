---
title: Upozornění Linkerů LNK4219 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4219
dev_langs:
- C++
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: daf097cd8715a7c523e6e8a2ea46714481ca7d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105205"
---
# <a name="linker-tools-warning-lnk4219"></a>Upozornění linkerů LNK4219

Oprava název opravou přetečení. Cílový "název symbolu cíl" je mimo rozsah. vkládá se převodní rutina

Linker vloží převodní rutina v situaci, kdy se nepodařilo přizpůsobit do uvedené instrukce, protože cílový symbol je příliš daleko od umístění instrukce adresy nebo posun.

Možná budete chtít změnit pořadí bitovou kopii (pomocí [/ORDER](../../build/reference/order-put-functions-in-order.md) volby, například), aby úroveň dereference.