---
title: Hodnoty | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13f497358ae320263fd7043787abb943f760809b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="values"></a>Hodnoty
**ANSI 3.1.2.5** reprezentace a nastaví hodnoty různých typů s plovoucí desetinnou čárkou  
  
 **Float** typ obsahuje 32 bity: 1 pro přihlášení, 8 pro exponent a 23 pro mantisa. Její rozsah je +/-3.4E38 s alespoň 7 platných číslic.  
  
 **Dvojité** typ obsahuje 64 bitů: 1 pro přihlášení, 11 pro exponent a 52 pro mantisa. Její rozsah je +/-1.7E308 s alespoň 15 číslic.  
  
 **Long double** typ obsahuje 80 bity: 1 pro přihlášení, 15 pro exponent a 64 pro mantisa. Její rozsah je +/-1.2E4932 s alespoň 19 platných číslic. Všimněte si, že se s překladačem Microsoft C reprezentaci typu **long double** je stejný jako typ **dvojité**.  
  
## <a name="see-also"></a>Viz také  
 [Matematické s plovoucí desetinnou čárkou](../c-language/floating-point-math.md)