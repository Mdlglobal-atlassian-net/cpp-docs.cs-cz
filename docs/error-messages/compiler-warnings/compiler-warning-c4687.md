---
title: "C4687 upozornění kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4687
dev_langs: C++
helpviewer_keywords: C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 266213deba94bdc925747d57dee184aca5f5f605
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-c4687"></a>C4687 upozornění kompilátoru
'class': zapečetěné abstraktní třídy nelze implementovat rozhraní 'rozhraní.  
  
 Zapečetěné, abstraktní typ je obvykle užitečné pouze pro uložení statické členské funkce.  
  
 Další informace najdete v tématu [abstraktní](../../windows/abstract-cpp-component-extensions.md)a [zapečetěné](../../windows/sealed-cpp-component-extensions.md).  
  
 C4687 je vydána jako chybu ve výchozím nastavení. Můžete potlačit C4687 s [upozornění](../../preprocessor/warning.md) – Direktiva pragma. Pokud jste si jisti, že chcete implementovat rozhraní v zapečetěné, abstraktní typ, můžete potlačit C4687.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4687.  
  
```  
// C4687.cpp  
// compile with: /clr /c  
interface class A {};  
  
ref struct B sealed abstract : A {};   // C4687  
ref struct C sealed : A {};   // OK  
ref struct D abstract : A {};   // OK  
```