---
title: Upozornění (úroveň 3) C4191 kompilátoru | Dokumentace Microsoftu
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
ms.openlocfilehash: c3b0198971064bec114e4665a499e070ddb61501
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197495"
---
# <a name="compiler-warning-level-3-c4191"></a>Kompilátor upozornění (úroveň 3) C4191
' operator/operation': nebezpečný převod z 'type of expression' na 'type required'  
  
 Několik operací zahrnující ukazatele na funkce považovány za nebezpečné:  
  
-   Typy funkcí pomocí různých konvencí volání.  
  
-   Typy funkcí s různými vrácení konvence.  
  
-   Argument nebo návratových typů pomocí různých velikostí, typ kategorie a klasifikace.  
  
-   Rozdílné délky seznamu argumentů (na `__cdecl`pouze na přetypování z delší seznam do seznamu kratší, i pokud kratší je vararg).  
  
-   Ukazatel na data (jiné než **void**<strong>\*</strong>) alias na ukazatel na funkci.  
  
-   Další rozdíl typ, který povede k chybě nebo upozornění na `reinterpret_cast`.  
  
 Volání této funkce přes ukazatel výsledku může způsobit pád programu.  
  
 Toto upozornění je vypnuto ve výchozím nastavení. Zobrazit [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
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