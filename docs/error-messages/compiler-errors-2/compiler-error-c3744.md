---
title: "C3744 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3744
dev_langs: C++
helpviewer_keywords: C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 87df3fd92ac3fcad9b3e87f02f16b8151e678b77
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3744"></a>C3744 chyby kompilátoru
__unhook musí mít aspoň 3 argumenty pro spravované události  
  
 [__Unhook](../../cpp/unhook.md) funkce vyžaduje tři parametry při použití v programu, který je zkompilovaném pro spravovaných rozšíření jazyka C++.  
  
 `__hook`a `__unhook` nejsou kompatibilní s programováním/CLR. Místo toho použijte += a-= operátory.  
  
 C3744 je dostupný, pomocí možnosti zastaralé kompilátoru pouze **/clr:oldSyntax**.  
