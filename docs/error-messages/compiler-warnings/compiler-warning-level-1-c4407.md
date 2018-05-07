---
title: Kompilátoru (úroveň 1) upozornění C4407 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4407
dev_langs:
- C++
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cbc02c32463703f658cef1d5756926311d89b193
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4407"></a>C4407 kompilátoru upozornění (úroveň 1)
CAST. mezi různé ukazatel na člena reprezentace kompilátoru generovat nesprávný kód  
  
 Byl zjištěn nesprávný přetypování.  
  
 C4407 lze vygenerovat z důvodu pracovních kompilátoru shoda, které bylo provedeno v aplikaci Visual C++ 2005. Ukazatele na člena nyní vyžaduje úplný název a address-of – operátor (&).  
  
 C4407 může dojít, pokud přetypování mezi více dědičnosti ukazatel na členem, abyste mohli jedna dědičnost ukazatele na člena. V některých případech to může fungovat, ale někdy nelze protože reprezentace ukazatele na člena jedna dědičnost nebude obsahovat dost informací. Kompilování pomocí **/VMM** vám může pomoci (Další informace najdete v tématu [/VMM, / VMS, / vmv (obecná reprezentace)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). Můžete také zkusit Změna uspořádání vaše základní třídy; kompilátor je zjišťování ke ztrátě informací v převodu, protože základní třída má na posunu nenulové z odvozený.  
  
 Následující ukázka generuje C4407:  
  
```  
// C4407.cpp  
// compile with: /W1 /c  
struct C1 {};  
struct C2 {};  
struct C3 : C1, C2 {};  
  
typedef void(C3::*PMF_C3)();  
typedef void(C2::*PMF_C2)();  
  
PMF_C2 f1(PMF_C3 pmf) {  
   return (PMF_C2)pmf;   // C4407, change type of cast,  
   // or reverse base class inheritance of C3 (i.e. : C2, C1)  
}  
```