---
title: Výhody znaku nastavit přenositelnost | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1b78048baebfd89aed0ccc898c2bb9e3612525
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="benefits-of-character-set-portability"></a>Výhody přenositelnosti znakové sady
Můžete využít i v případě, že jste neměli v úmyslu aktuálně internationalizi vaší aplikace pomocí přenositelnost běhové funkce MFC a C:  
  
-   Kódování přenositelnosti dělá kódu základní flexibilní. Můžete později přesunout ho snadno Unicode nebo MBCS.  
  
-   Pomocí kódování Unicode mohou vaše aplikace pro Windows efektivnější. Protože Windows používá kódování Unicode, řetězců kódování Unicode předán do a z operačního systému, je nutné přeložit, což zahrnuje režii.  

  
## <a name="see-also"></a>Viz také  
 [Kódování Unicode a MBCS](../text/unicode-and-mbcs.md)   
 [Podpora pro Unicode](../text/support-for-unicode.md)