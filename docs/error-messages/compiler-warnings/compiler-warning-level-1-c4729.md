---
title: "Kompilátoru (úroveň 1) upozornění C4729 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4729
dev_langs: C++
helpviewer_keywords: C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2d80512dd6aaecfbe1de06f69303eb3d42213856
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4729"></a>C4729 kompilátoru upozornění (úroveň 1)
Funkce, které jsou příliš dlouhé pro graf toku na základě upozornění  
  
 Toto upozornění se vygeneruje, když funkce je příliš dlouhý pro má kompilovat s spolehlivé Kontrola situace, které by vygeneroval upozornění. Toto upozornění je pouze vygeneruje, když [/Od](../../build/reference/od-disable-debug.md) – možnost kompilátoru použít.  
  
 Toto upozornění vyřešíte rozdělte na menší funkce funkce.