---
title: "C2410 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2410
dev_langs:
- C++
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3cd5dfa7b33f5af5c57f6479170a7a56df39a0e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2410"></a>C2410 chyby kompilátoru
"identifikátor": název nejednoznačný člena v 'kontextu.  
  
 Identifikátor je členem více než jeden struktury nebo sjednocení v tomto kontextu.  
  
 Použijte struktury nebo sjednocení specifikátor u operandu, který chybu způsobil. Struktura nebo sjednocení specifikátor je identifikátor typu `struct` nebo `union` ( `typedef` název nebo proměnnou stejného typu jako struktury nebo sjednocení odkazováno). Levý operand operátoru první výběru členů (.) používat operand musí být specifikátor.