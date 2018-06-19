---
title: Kompilátoru (úroveň 4) upozornění C4234 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4234
dev_langs:
- C++
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8d5b7a2999b77c0b34ee925f5dd85a0a27c63f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293514"
---
# <a name="compiler-warning-level-4-c4234"></a>C4234 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: vyhrazeno pro budoucí použití – klíčové slovo '– klíčové slovo'  
  
 Kompilátor ještě neimplementuje klíčové slovo, které jste použili.  
  
 Toto upozornění je automaticky povýšen na chybu. Pokud chcete-li toto chování změnit, použijte [#pragma – upozornění](../../preprocessor/warning.md). Třeba, aby C4234 do problémem upozornění úroveň 4  
  
```  
#pragma warning(2:4234)  
```  
  
 ve zdrojovém kódu souboru.