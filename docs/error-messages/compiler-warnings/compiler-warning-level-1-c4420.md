---
title: Kompilátoru (úroveň 1) upozornění C4420 | Microsoft Docs
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
ms.openlocfilehash: 98336a30e7174b62df48e93a04ba9ee7ddcc919a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279107"
---
# <a name="compiler-warning-level-1-c4420"></a>C4420 kompilátoru upozornění (úroveň 1)
'operátor': není k dispozici, operátor pomocí 'operátor' místo; Kontrola běhu může dojít k ohrožení  
  
 Toto upozornění je generováno při použití [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector kontrola nové nebo odstranění) a pokud je nalezen žádný formulář vektoru. V takovém případě se používá jiný vektoru formuláře.  
  
 Aby /RTCv fungovala správně, by měly volat kompilátor vždy vektoru formu [nové](../../cpp/new-operator-cpp.md)/[odstranit](../../cpp/delete-operator-cpp.md) Pokud byla použita syntaxe vektoru.