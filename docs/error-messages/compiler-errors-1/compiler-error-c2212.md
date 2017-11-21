---
title: "C2212 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2212
dev_langs: C++
helpviewer_keywords: C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d8515302c7b794a92fe16f3c0baf9c82665aa4d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2212"></a>C2212 chyby kompilátoru
"identifikátor": __based není k dispozici pro ukazatelé na funkce  
  
 Ukazatelé na funkce nelze deklarovat `__based`. Pokud potřebujete založené na kódu data, použijte `__declspec` – klíčové slovo nebo `data_seg` – Direktiva pragma.