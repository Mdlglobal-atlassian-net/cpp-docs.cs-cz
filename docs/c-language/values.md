---
title: Hodnoty | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ed5d412a5f4d00448ea9d7bc112b22541a179f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386969"
---
# <a name="values"></a>Hodnoty
**ANSI 3.1.2.5** reprezentace a nastaví hodnoty různých typů s plovoucí desetinnou čárkou  
  
 **Float** typ obsahuje 32 bity: 1 pro přihlášení, 8 pro exponent a 23 pro mantisa. Její rozsah je +/-3.4E38 s alespoň 7 platných číslic.  
  
 **Dvojité** typ obsahuje 64 bitů: 1 pro přihlášení, 11 pro exponent a 52 pro mantisa. Její rozsah je +/-1.7E308 s alespoň 15 číslic.  
  
 **Long double** typ obsahuje 80 bity: 1 pro přihlášení, 15 pro exponent a 64 pro mantisa. Její rozsah je +/-1.2E4932 s alespoň 19 platných číslic. Všimněte si, že se s překladačem Microsoft C reprezentaci typu **long double** je stejný jako typ **dvojité**.  
  
## <a name="see-also"></a>Viz také  
 [Matematika s plovoucí desetinnou čárkou](../c-language/floating-point-math.md)