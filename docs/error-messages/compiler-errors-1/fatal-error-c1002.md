---
title: "Závažná chyba C1002 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1002
dev_langs: C++
helpviewer_keywords: C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cab0e1db2d84fb5ba84d773f28e70341faf10ac6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1002"></a>Závažná chyba C1002
kompilátoru nemá dostatek místa na haldy při průchodu 2  
  
 Kompilátor nemá dostatek místa k dynamické paměti ve druhé fázi, pravděpodobně z důvodu programu s příliš mnoha symboly nebo složité výrazy.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Zdrojový soubor se rozdělí na několik menších souborů.  
  
2.  Rozdělte na menší podvýrazy výrazy.  
  
3.  Odeberte jiné programy nebo ovladače, které využívají paměti.