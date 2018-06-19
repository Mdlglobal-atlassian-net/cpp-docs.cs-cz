---
title: Závažná chyba C1002 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c63a8d399b3e8c781694d89825e7898fd1db4639
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225048"
---
# <a name="fatal-error-c1002"></a>Závažná chyba C1002
kompilátoru nemá dostatek místa na haldy při průchodu 2  
  
 Kompilátor nemá dostatek místa k dynamické paměti ve druhé fázi, pravděpodobně z důvodu programu s příliš mnoha symboly nebo složité výrazy.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Zdrojový soubor se rozdělí na několik menších souborů.  
  
2.  Rozdělte na menší podvýrazy výrazy.  
  
3.  Odeberte jiné programy nebo ovladače, které využívají paměti.