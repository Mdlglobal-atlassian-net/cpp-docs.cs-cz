---
title: C2410 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2410
dev_langs:
- C++
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9c2a2df0941130c4f2416806a05ce0378373eb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226440"
---
# <a name="compiler-error-c2410"></a>C2410 chyby kompilátoru
"identifikátor": název nejednoznačný člena v 'kontextu.  
  
 Identifikátor je členem více než jeden struktury nebo sjednocení v tomto kontextu.  
  
 Použijte struktury nebo sjednocení specifikátor u operandu, který chybu způsobil. Struktura nebo sjednocení specifikátor je identifikátor typu `struct` nebo `union` ( `typedef` název nebo proměnnou stejného typu jako struktury nebo sjednocení odkazováno). Levý operand operátoru první výběru členů (.) používat operand musí být specifikátor.