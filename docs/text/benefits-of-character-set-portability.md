---
title: "Výhody znaku nastavit přenositelnost | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ce02fa834c39f629990d4f3c9785de94bd02196
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="benefits-of-character-set-portability"></a>Výhody přenositelnosti znakové sady
Můžete využít i v případě, že jste neměli v úmyslu aktuálně internationalizi vaší aplikace pomocí přenositelnost běhové funkce MFC a C:  
  
-   Kódování přenositelnosti dělá kódu základní flexibilní. Můžete později přesunout ho snadno Unicode nebo MBCS.  
  
-   Pomocí kódování Unicode mohou vaše aplikace pro Windows efektivnější. Protože Windows používá kódování Unicode, řetězců kódování Unicode předán do a z operačního systému, je nutné přeložit, což zahrnuje režii.  

  
## <a name="see-also"></a>Viz také  
 [Kódování Unicode a MBCS](../text/unicode-and-mbcs.md)   
 [Podpora pro Unicode](../text/support-for-unicode.md)