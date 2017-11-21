---
title: "Kompilátoru (úroveň 3) upozornění C4192 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4192
dev_langs: C++
helpviewer_keywords: C4192
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ff07a7fd5af7c9e4d73d9a4ce679edc7ab5e6b43
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4192"></a>C4192 kompilátoru upozornění (úroveň 3)
automaticky vyloučení "název" při Import knihovny typů, knihovny.  
  
 A `#import` knihovna obsahuje položku, *název*, která je také definován v hlavičkách systému Win32. Vzhledem k omezením knihoven typů názvy jako **IUnknown** nebo identifikátor GUID jsou často definované v knihovny typů, duplikování definici z hlavičky systému. `#import`Tyto položky rozpozná a odmítnout začlenit je v hlavičce soubory .tlh a .tli.  
  
 Chcete-li toto chování potlačit, použijte `#import` atributy [no_auto_exclude –](../../preprocessor/no-auto-exclude.md) a [include()](../../preprocessor/include-parens.md).