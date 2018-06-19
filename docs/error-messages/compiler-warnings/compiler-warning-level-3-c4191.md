---
title: Kompilátoru (úroveň 3) upozornění C4191 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4191
dev_langs:
- C++
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 892bf76a8480e573a71e768fbe24778e7e66f88b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291489"
---
# <a name="compiler-warning-level-3-c4191"></a>C4191 kompilátoru upozornění (úroveň 3)
'operátor nebo operace': unsafe převod "typ výrazu" na "typ požadované"  
  
 Několik operací zahrnujících ukazatelů na funkce, považovány za nebezpečné:  
  
-   Typy funkce s různých pravidel pro volání.  
  
-   Typy funkcí jiné vrátí konvence.  
  
-   Typy argumentů nebo return s různou velikost, typ kategorie nebo klasifikace.  
  
-   Různé délky seznamu argumentů (na `__cdecl`pouze na přetypování z delší seznam kratší seznamu, i pokud kratší je vararg).  
  
-   Ukazatel na data (jiné než **void\***) alias proti ukazatel na funkci.  
  
-   Žádný typ rozdíl, který by yield chybě nebo upozornění na `reinterpret_cast`.  
  
 Tuto funkci prostřednictvím ukazatele výsledek volání může způsobit vaše programu havárií.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Následující ukázka generuje C4191:  
  
```  
// C4191.cpp  
// compile with: /W3 /clr  
#pragma warning(default: 4191)  
  
void __clrcall f1() { }  
void __cdecl   f2() { }  
  
typedef void (__clrcall * fnptr1)();  
typedef void (__cdecl   * fnptr2)();  
  
int main() {  
   fnptr1 fp1 = static_cast<fnptr1>(&f1);  
   fnptr2 fp2 = (fnptr2) &f2;  
  
   fnptr1 fp3 = (fnptr1) &f2;   // C4191  
   fnptr2 fp4 = (fnptr2) &f1;   // C4191  
};  
```