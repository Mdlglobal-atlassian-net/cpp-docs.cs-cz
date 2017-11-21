---
title: "Řízení příznaky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.flags
dev_langs: C++
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d8c6f58e345669cb1898bc2717a7e42ddc8e2539
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="control-flags"></a>Příznaky ovládacích prvků
Ladicí verze běhové knihovny Microsoft C používá následující příznaky tak, aby řízení přidělení haldy a procesu generování sestav. Další informace najdete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).  
  
|Příznak|Popis|  
|----------|-----------------|  
|[_CRTDBG_MAP_ALLOC –](../c-runtime-library/crtdbg-map-alloc.md)|Mapuje funkce základní hald svým ladicí verze|  
|[_DEBUG –](../c-runtime-library/debug.md)|Umožňuje použití ladění verzích běhové funkce|  
|[_crtdbgflag –](../c-runtime-library/crtdbgflag.md)|Určuje, jak správce haldy ladění sleduje přidělování|  
  
 Tyto příznaky se může definovat s možností příkazového řádku /D nebo s `#define` – direktiva. Když je příznak definovaná pomocí `#define`, direktivu musí být před příkaz pro běžné deklarace zahrnout soubor hlaviček.  
  
## <a name="see-also"></a>Viz také  
 [Globální proměnné a standardní typy](../c-runtime-library/global-variables-and-standard-types.md)