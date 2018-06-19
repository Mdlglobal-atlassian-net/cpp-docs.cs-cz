---
title: C2466 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2466
dev_langs:
- C++
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e55e5c130b0a0454577a7155b704a18933b86198
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224305"
---
# <a name="compiler-error-c2466"></a>C2466 chyby kompilátoru
Nelze přidělit pole konstantní velikost 0  
  
 Pole je přidělen nebo deklarovat s velikost nula. Konstantní výraz pro velikost pole musí být celé číslo větší než nula. Deklarace pole s nulovou dolní index je povoleno pouze pro třídy, struktury nebo členů sjednocení a pouze s rozšíření Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).  
  
 Následující ukázka generuje C2466:  
  
```  
// C2466.cpp  
// compile with: /c  
int i[0];   // C2466  
int j[1];   // OK  
char *p;  
```