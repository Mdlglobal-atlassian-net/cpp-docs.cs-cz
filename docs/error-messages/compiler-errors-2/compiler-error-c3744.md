---
title: "C3744 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fd5c11e88960f2b4332a586d2fe982a8ea94fdbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3744"></a>C3744 chyby kompilátoru
__unhook musí mít aspoň 3 argumenty pro spravované události  
  
 [__Unhook](../../cpp/unhook.md) funkce vyžaduje tři parametry při použití v programu, který je zkompilovaném pro spravovaných rozšíření jazyka C++.  
  
 `__hook`a `__unhook` nejsou kompatibilní s programováním/CLR. Místo toho použijte += a-= operátory.  
  
 C3744 je dostupný, pomocí možnosti zastaralé kompilátoru pouze **/clr:oldSyntax**.  
