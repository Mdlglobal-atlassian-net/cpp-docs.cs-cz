---
title: Upozornění (úroveň 1) C4420 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4420
dev_langs:
- C++
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1ba4ef4c4fc006e1a5950d0d16dc530ccc06a1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049745"
---
# <a name="compiler-warning-level-1-c4420"></a>Kompilátor upozornění (úroveň 1) C4420

'operator': operátor není k dispozici, místo toho; pomocí 'operator' kontrolu za běhu může dojít k ohrožení

Toto upozornění je generováno, když použijete [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector kontroluje nových/delete) a když nenajde žádný formulář vektoru. V takovém případě se používá bez vektoru formuláře.

Aby /RTCv fungovala správně, musí kompilátor vždy volat vektoru formu [nové](../../cpp/new-operator-cpp.md)/[odstranit](../../cpp/delete-operator-cpp.md) Pokud byla použita syntaxe vektoru.