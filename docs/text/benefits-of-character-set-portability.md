---
title: "Výhody znaku nastavit přenositelnost | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- character sets [C++], benefits
- portability [C++], character sets
ms.assetid: bd60b925-1498-4e4f-897b-4c8ce66edcf7
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 554137352c0a8f7275a051e4026020fce25edbb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="benefits-of-character-set-portability"></a>Výhody přenositelnosti znakové sady
Můžete využít i v případě, že jste neměli v úmyslu aktuálně internationalizi vaší aplikace pomocí přenositelnost běhové funkce MFC a C:  
  
-   Kódování přenositelnosti dělá kódu základní flexibilní. Můžete později přesunout ho snadno Unicode nebo MBCS.  
  
-   Pomocí kódování Unicode mohou vaše aplikace pro systém Windows 2000 efektivnější. Protože Windows 2000 používá kódování Unicode, řetězců kódování Unicode předán do a z operačního systému, je nutné přeložit, což zahrnuje režii.  
  
-   Pomocí znakové sady MBCS umožňuje podporovat mezinárodní trhy na Win32 platformách než Windows 2000, jako je například systém Windows 95 nebo Windows 98.  
  
## <a name="see-also"></a>Viz také  
 [Kódování Unicode a MBCS](../text/unicode-and-mbcs.md)   
 [Podpora pro Unicode](../text/support-for-unicode.md)