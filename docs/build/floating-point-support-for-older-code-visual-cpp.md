---
title: "Podpora plovoucí desetinné čárky ve starším kódu (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3ddc151a2a0f74c6f77be68cd026147a318a595a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="floating-point-support-for-older-code-visual-c"></a>Podpora plovoucí desetinné čárky ve starším kódu (Visual C++)
MMX a zaregistruje se s plovoucí desetinnou čárkou zásobníku (MM0-MM7/ST0-ST7) se zachovají v souvislosti přepínače.  Neexistuje žádné explicitní konvence volání pro tyto registry.  Použití těchto registrů výhradně zakázané kódu v režimu jádra.  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)