---
title: Méně závažná chyba nástroje ML A2066 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2066
dev_langs:
- C++
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92cc0daf183f617767ff5ff119c5e95b8f34cd51
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2066"></a>Méně závažná chyba nástroje ML A2066
**nekompatibilní velikost režim a segment procesoru**  
  
 Byl proveden pokus o otevření segment se **USE16**, **USE32**, nebo **ploché** atribut, který nebyl kompatibilní se zadanou procesoru nebo ke změně 16bitové procesoru v 32bitové Segment.  
  
 **USE32** a **ploché** atributy musí předcházet.386 nebo větší – direktiva procesoru.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)