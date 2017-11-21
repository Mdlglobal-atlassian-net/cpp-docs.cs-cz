---
title: "C2410 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2410
dev_langs: C++
helpviewer_keywords: C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3d2f8f9b21d44c2fce92c526de0f6d53b99930b8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2410"></a>C2410 chyby kompilátoru
"identifikátor": název nejednoznačný člena v 'kontextu.  
  
 Identifikátor je členem více než jeden struktury nebo sjednocení v tomto kontextu.  
  
 Použijte struktury nebo sjednocení specifikátor u operandu, který chybu způsobil. Struktura nebo sjednocení specifikátor je identifikátor typu `struct` nebo `union` ( `typedef` název nebo proměnnou stejného typu jako struktury nebo sjednocení odkazováno). Levý operand operátoru první výběru členů (.) používat operand musí být specifikátor.