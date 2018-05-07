---
title: C3744 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f96b8445c343bdd4f606157e692c4d6ce262e369
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3744"></a>C3744 chyby kompilátoru
__unhook musí mít aspoň 3 argumenty pro spravované události  
  
 [__Unhook](../../cpp/unhook.md) funkce vyžaduje tři parametry při použití v programu, který je zkompilovaném pro spravovaných rozšíření jazyka C++.  
  
 `__hook` a `__unhook` nejsou kompatibilní s programováním/CLR. Místo toho použijte += a-= operátory.  
  
 C3744 je dostupný, pomocí možnosti zastaralé kompilátoru pouze **/clr:oldSyntax**.  
