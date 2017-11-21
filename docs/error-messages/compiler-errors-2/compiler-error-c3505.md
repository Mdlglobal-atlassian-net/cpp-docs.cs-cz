---
title: "C3505 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3505
dev_langs: C++
helpviewer_keywords: C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 47ca6c4e8e8c01e97ed0098c84c8ea8c64f387a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3505"></a>C3505 chyby kompilátoru

> Nelze načíst knihovny typů,*guid*.  
  
C3505 může dojít, pokud používáte 32-bit, x86 hostované cross kompilátor pro 64bitové, x64 cílí na 64-bit počítač, protože kompilátor běží WOW64 a můžete jenom číst z podregistru 32-bit.  
  
Můžete tuto chybu vyřešit vytváření 32bitové a 64bitové verze knihovny typů, které se pokoušíte importovat a potom proveďte registraci oba.  Nebo můžete použít nativní 64bitový kompilátor, který vyžaduje, abyste změnit vaše **adresáře VC ++** vlastnost v integrovaném vývojovém prostředí tak, aby odkazoval na 64-bit kompilátoru.  
  
Další informace najdete v tématu,  
  
-   [Postupy: povolení 64bitová verze sady nástrojů Visual C++ v příkazovém řádku](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [Postupy: Konfigurace projektů Visual C++ pro 64bitové, x64 platformy](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)