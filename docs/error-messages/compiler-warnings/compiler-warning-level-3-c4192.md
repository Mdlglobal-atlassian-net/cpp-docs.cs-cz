---
title: Kompilátoru (úroveň 3) upozornění C4192 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4192
dev_langs:
- C++
helpviewer_keywords:
- C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3bae9b7af95de94b8f667cb09710af21044f8b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4192"></a>C4192 kompilátoru upozornění (úroveň 3)
automaticky vyloučení "název" při Import knihovny typů, knihovny.  
  
 A `#import` knihovna obsahuje položku, *název*, která je také definován v hlavičkách systému Win32. Vzhledem k omezením knihoven typů názvy jako **IUnknown** nebo identifikátor GUID jsou často definované v knihovny typů, duplikování definici z hlavičky systému. `#import` Tyto položky rozpozná a odmítnout začlenit je v hlavičce soubory .tlh a .tli.  
  
 Chcete-li toto chování potlačit, použijte `#import` atributy [no_auto_exclude –](../../preprocessor/no-auto-exclude.md) a [include()](../../preprocessor/include-parens.md).