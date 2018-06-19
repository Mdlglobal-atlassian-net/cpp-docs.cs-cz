---
title: C3398 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3398
dev_langs:
- C++
helpviewer_keywords:
- C3398
ms.assetid: 26f8c8a4-526f-415b-8047-155c5cd4f180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b870479977bfb49ff39d5a15fe19fc700ed66b8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255827"
---
# <a name="compiler-error-c3398"></a>C3398 chyby kompilátoru
'operátor': nelze převést na 'function_pointer' 'function_signature'. Zdroj výraz musí být symbol – funkce  
  
 Když [__clrcall](../../cpp/clrcall.md) konvence volání není zadán, když kompilujete s **/CLR**, kompilátor vygeneruje dva vstupní body (adresy) pro jednotlivé funkce, nativní vstupní bod a spravovaný vstupní bod.  
  
 Ve výchozím nastavení kompilátoru vrátí nativní vstupní bod, ale existují případy, kdy se vyžaduje spravovaný vstupní bod (například při přiřazování adresa `__clrcall` – ukazatel na funkci). Aby kompilátoru spolehlivě zvolte spravovaný vstupní bod v přiřazení musí být pravé straně symbol funkce.