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
ms.openlocfilehash: d51f960a9771c72e3f63c07b74266ed1be728a23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ml-nonfatal-error-a2066"></a>Méně závažná chyba nástroje ML A2066
**nekompatibilní velikost režim a segment procesoru**  
  
 Byl proveden pokus o otevření segment se **USE16**, **USE32**, nebo **ploché** atribut, který nebyl kompatibilní se zadanou procesoru nebo ke změně 16bitové procesoru v 32bitové Segment.  
  
 **USE32** a **ploché** atributy musí předcházet.386 nebo větší – direktiva procesoru.  
  
## <a name="see-also"></a>Viz také  
 [Chybové zprávy nástroje ML](../../assembler/masm/ml-error-messages.md)