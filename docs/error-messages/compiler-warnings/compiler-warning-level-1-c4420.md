---
title: "Kompilátoru (úroveň 1) upozornění C4420 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4420
dev_langs:
- C++
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a57803cb584f5ee54ad5533366e6aadc85d1acf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4420"></a>C4420 kompilátoru upozornění (úroveň 1)
'operátor': není k dispozici, operátor pomocí 'operátor' místo; Kontrola běhu může dojít k ohrožení  
  
 Toto upozornění je generováno při použití [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector kontrola nové nebo odstranění) a pokud je nalezen žádný formulář vektoru. V takovém případě se používá jiný vektoru formuláře.  
  
 Aby /RTCv fungovala správně, by měly volat kompilátor vždy vektoru formu [nové](../../cpp/new-operator-cpp.md)/[odstranit](../../cpp/delete-operator-cpp.md) Pokud byla použita syntaxe vektoru.