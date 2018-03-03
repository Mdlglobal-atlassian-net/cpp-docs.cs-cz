---
title: "Závažná chyba nástroje NMAKE U1051 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93c109bf723b3c4cf08e998a715fe8f6f33be466
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1051"></a>Závažná chyba nástroje NMAKE U1051
Nedostatek paměti  
  
 NMAKE nemá dostatek paměti, včetně virtuální paměti, protože souboru pravidel byla příliš velká nebo složitá.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Uvolněte místo na disku.  
  
2.  Zvětšete velikost stránkovacího souboru systému Windows NT nebo odkládací soubor systému Windows.  
  
3.  Pokud jenom součást souboru pravidel se používá, buď souboru pravidel rozdělit na samostatné soubory, nebo použijte **! Pokud** omezit množství, které musí zpracovat NMAKE direktivy předběžného zpracování. **! Pokud** direktivy zahrnují **! Pokud**, `!IFDEF`, **! Ifndef –**, **! Pokud jiný**, **! ELSE** `IFDEF`, a **! ELSE** `IFNDEF`.