---
title: "C3715 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3715
dev_langs: C++
helpviewer_keywords: C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0fcfe83ada2c55540562fc17189d693675326c81
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3715"></a>C3715 chyby kompilátoru
'ukazatel': musí být ukazatel na 'class'.  
  
 Zadaný ukazatel v [__hook](../../cpp/hook.md) nebo [__unhook](../../cpp/unhook.md) , nesouvisí s platnou třídu. Chcete-li tuto chybu vyřešit, ověřte, zda vaše `__hook` a `__unhook` volání určovala ukazatelé na třídy platný.