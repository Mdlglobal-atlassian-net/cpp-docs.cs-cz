---
title: "C2692 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2692
dev_langs: C++
helpviewer_keywords: C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e65c0310dfd82f86b49193fb173bb483fbd4333
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2692"></a>C2692 chyby kompilátoru
'Název_funkce': plně deklaraci funkce vyžadované v kompilátoru jazyka C s ' / clr se možnost  
  
 Při kompilování pro .NET spravovaného kódu, vyžaduje kompilátor jazyka C deklarace funkcí ANSI. Kromě toho, pokud funkci nepřijímá žádné parametry, se musí explicitně deklarovat `void` jako typ parametru.