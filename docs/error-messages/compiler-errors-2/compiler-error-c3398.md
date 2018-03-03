---
title: "C3398 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3398
dev_langs:
- C++
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4b332346dd8e8b7e906e961c86805ad0564f0f79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3398"></a>C3398 chyby kompilátoru
'operátor': nelze převést na 'function_pointer' 'function_signature'. Zdroj výraz musí být symbol – funkce  
  
 Když [__clrcall](../../cpp/clrcall.md) konvence volání není zadán, když kompilujete s **/CLR**, kompilátor vygeneruje dva vstupní body (adresy) pro jednotlivé funkce, nativní vstupní bod a spravovaný vstupní bod.  
  
 Ve výchozím nastavení kompilátoru vrátí nativní vstupní bod, ale existují případy, kdy se vyžaduje spravovaný vstupní bod (například při přiřazování adresa `__clrcall` – ukazatel na funkci). Aby kompilátoru spolehlivě zvolte spravovaný vstupní bod v přiřazení musí být pravé straně symbol funkce.