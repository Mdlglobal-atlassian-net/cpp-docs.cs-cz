---
title: "C2518 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2518
dev_langs: C++
helpviewer_keywords: C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2a76c528def49b1235460fa4d6632efd196417d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2518"></a>C2518 chyby kompilátoru
– klíčové slovo '– klíčové slovo' neplatný v seznamu základní třídy; Ignorovat  
  
 Klíčová slova `class` a `struct` neměla by se zobrazit v seznamu základní třídy.  
  
 Následující ukázka generuje C2518:  
  
```  
// C2518.cpp  
// compile with: /c  
class B {};  
class C : public class B {};   // C2518  
class D: public B {};   // OK  
```