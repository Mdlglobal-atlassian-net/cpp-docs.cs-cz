---
title: "Méně závažná chyba nástroje ML A2066 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2066
dev_langs: C++
helpviewer_keywords: A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b85402feccf4f85f2f1dd60902bb5759ed723911
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ml-nonfatal-error-a2066"></a>Méně závažná chyba nástroje ML A2066
**nekompatibilní velikost režim a segment procesoru**  
  
 Byl proveden pokus o otevření segment se **USE16**, **USE32**, nebo **ploché** atribut, který nebyl kompatibilní se zadanou procesoru nebo ke změně 16bitové procesoru v 32bitové Segment.  
  
 **USE32** a **ploché** atributy musí předcházet.386 nebo větší – direktiva procesoru.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)