---
title: "C2696 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2696
dev_langs: C++
helpviewer_keywords: C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4d6efbf8dcf10d1608bb1a54b843a49d42cb22a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2696"></a>C2696 chyby kompilátoru
Nelze vytvořit dočasný objekt spravovaného typu "typ"  
  
Odkazuje na `const` v nespravované program způsobit kompilátoru volání konstruktoru a vytvořit dočasný objekt v zásobníku. V zásobníku však lze nikdy vytvořit spravovanou třídou.  
  
C2696 je dostupný, pomocí možnosti zastaralé kompilátoru pouze **/clr:oldSyntax**.  
