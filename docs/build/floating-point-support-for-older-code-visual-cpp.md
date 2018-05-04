---
title: Podpora plovoucí desetinné čárky ve starším kódu (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd7cbf955fbf795d06d9cd2448d0736dc435f3b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="floating-point-support-for-older-code-visual-c"></a>Podpora plovoucí desetinné čárky ve starším kódu (Visual C++)
MMX a zaregistruje se s plovoucí desetinnou čárkou zásobníku (MM0-MM7/ST0-ST7) se zachovají v souvislosti přepínače.  Neexistuje žádné explicitní konvence volání pro tyto registry.  Použití těchto registrů výhradně zakázané kódu v režimu jádra.  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../build/calling-convention.md)