---
title: C2692 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2692
dev_langs:
- C++
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a02110750a748b5c520df7d202a87957f227a802
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230985"
---
# <a name="compiler-error-c2692"></a>C2692 chyby kompilátoru
'Název_funkce': plně deklaraci funkce vyžadované v kompilátoru jazyka C s ' / clr se možnost  
  
 Při kompilování pro .NET spravovaného kódu, vyžaduje kompilátor jazyka C deklarace funkcí ANSI. Kromě toho, pokud funkci nepřijímá žádné parametry, se musí explicitně deklarovat `void` jako typ parametru.