---
title: C3532 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3532
dev_langs:
- C++
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1efce6659f8d848b47f0c4194b6420177ffad194
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254970"
---
# <a name="compiler-error-c3532"></a>C3532 chyby kompilátoru
'type': nesprávné použití 'auto'  
  
 Zadaný typ nelze deklarovat s `auto` – klíčové slovo. Například nemůžete použít `auto` – klíčové slovo deklarace pole nebo metoda návratovým typem.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že výraz inicializace vypočítá platného typu.  
  
2.  Ujistěte se, že jste nedeklarujte pole nebo návratový typ. metoda.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3532, protože `auto` – klíčové slovo nesmí deklarovat návratový typ. metoda.  
  
```  
// C3532a.cpp  
// Compile with /Zc:auto  
auto f(){}   // C3532  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá C3532, protože `auto` – klíčové slovo nelze deklarovat pole.  
  
```  
// C3532b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int x[5];  
   auto a[5];            // C3532  
   auto b[1][2];         // C3532  
   auto y[5] = x;        // C3532  
   auto z[] = {1, 2, 3}; // C3532  
   auto w[] = x;         // C3532  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Auto – klíčové slovo](../../cpp/auto-keyword.md)