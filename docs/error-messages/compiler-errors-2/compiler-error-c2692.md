---
title: "C2692 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2692
dev_langs:
- C++
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9253bf70204bfded06189b6688405cabc43bdcf9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2692"></a>C2692 chyby kompilátoru
'Název_funkce': plně deklaraci funkce vyžadované v kompilátoru jazyka C s ' / clr se možnost  
  
 Při kompilování pro .NET spravovaného kódu, vyžaduje kompilátor jazyka C deklarace funkcí ANSI. Kromě toho, pokud funkci nepřijímá žádné parametry, se musí explicitně deklarovat `void` jako typ parametru.