---
title: "Kompilátoru (úroveň 1) upozornění C4420 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4420
dev_langs: C++
helpviewer_keywords: C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 646e87243e6901827fb2d36076a95e6bcb63c3ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4420"></a>C4420 kompilátoru upozornění (úroveň 1)
'operátor': není k dispozici, operátor pomocí 'operátor' místo; Kontrola běhu může dojít k ohrožení  
  
 Toto upozornění je generováno při použití [/RTCv](../../build/reference/rtc-run-time-error-checks.md) (vector kontrola nové nebo odstranění) a pokud je nalezen žádný formulář vektoru. V takovém případě se používá jiný vektoru formuláře.  
  
 Aby /RTCv fungovala správně, by měly volat kompilátor vždy vektoru formu [nové](../../cpp/new-operator-cpp.md)/[odstranit](../../cpp/delete-operator-cpp.md) Pokud byla použita syntaxe vektoru.