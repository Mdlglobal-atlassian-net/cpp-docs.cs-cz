---
title: Kompilátoru (úroveň 1) upozornění C4819 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4819
dev_langs:
- C++
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 718e0783c3f7afcc9af958f7940f437ac4c944b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283377"
---
# <a name="compiler-warning-level-1-c4819"></a>C4819 kompilátoru upozornění (úroveň 1)
Tento soubor obsahuje znak, který není možné vyjádřit v aktuální znakové stránky (number). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.  
  
 C4819 nastane, když kompiluje soubor zdroj ANSI v systému pomocí znakové stránky, které nelze vyjádřit všechny znaky v souboru.  
  
 Chcete-li vyřešit C4819, uložte soubor ve formátu Unicode. V sadě Visual Studio, vyberte **soubor**, **rozšířené možnosti ukládání**. V **rozšířené možnosti ukládání** dialogovém okně vyberte kódování, které může představovat všechny znaky v souboru – například UTF-8 – a potom zvolte **OK**.