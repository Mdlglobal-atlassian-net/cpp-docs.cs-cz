---
title: "Bajtové a široké proudy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Byte and Wide Streams
dev_langs: C++
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd4d90d50ecfe2514b53df6b0137caa866feeea3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="byte-and-wide-streams"></a>Bajtové a široké proudy
Tok bajtů zpracovává soubor jako pořadí bajtů. Datový proud v rámci programu, je stejné pořadí bajtů.  
  
 Naopak široké datového proudu souboru jsou považovány za posloupnost zobecněný vícebajtové znaky, což může mít širokou škálu kódování pravidla. (Textové a binární soubory jsou stále číst a zapisovat jak bylo popsáno dříve.) V rámci programu do datového proudu vypadá jako odpovídající pořadí široké znaky. Převody mezi dvěma reprezentace nastat do během standardní knihovny jazyka C. Pravidla převodu může, v zásadě změněna voláním [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) který mění kategorii `LC_CTYPE`. Každý datový proud široké určuje jeho pravidel převodu v době, stane se celý orientované a zachová, i když tyto pravidla kategorii `LC_CTYPE` následně změny.  
  
 Umístění v rámci široké datového proudu vyskytne stejná omezení jako text steams. Kromě toho indikátoru pozice souboru může mít i řešení stavu závislé kódování. Obvykle zahrnuje obě bajt posun v rámci datového proudu a objekt typu `mbstate_t`. Proto pouze spolehlivý způsob, jak získat pozice souboru v rámci široké datového proudu je voláním [fgetpos –](../c-runtime-library/reference/fgetpos.md), a pouze spolehlivý způsob, jak obnovit pozice získat tímto způsobem je voláním [fsetpos –](../c-runtime-library/reference/fsetpos.md).  
  
## <a name="see-also"></a>Viz také  
 [Soubory a proudy](../c-runtime-library/files-and-streams.md)   
 [setlocale –, _wsetlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md)