---
title: Závažná chyba nástroje NMAKE U1051 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 570c7e5d8e6e8250a67e4f032ac26b04388cfd00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1051"></a>Závažná chyba nástroje NMAKE U1051
Nedostatek paměti  
  
 NMAKE nemá dostatek paměti, včetně virtuální paměti, protože souboru pravidel byla příliš velká nebo složitá.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Uvolněte místo na disku.  
  
2.  Zvětšete velikost stránkovacího souboru systému Windows NT nebo odkládací soubor systému Windows.  
  
3.  Pokud jenom součást souboru pravidel se používá, buď souboru pravidel rozdělit na samostatné soubory, nebo použijte **! Pokud** omezit množství, které musí zpracovat NMAKE direktivy předběžného zpracování. **! Pokud** direktivy zahrnují **! Pokud**, `!IFDEF`, **! Ifndef –**, **! Pokud jiný**, **! ELSE** `IFDEF`, a **! ELSE** `IFNDEF`.