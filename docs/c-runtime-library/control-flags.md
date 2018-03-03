---
title: "Řízení příznaky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.flags
dev_langs:
- C++
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71e0b1d01e291a1fa48740ccb6389a1b064433b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="control-flags"></a>Příznaky ovládacích prvků
Ladicí verze běhové knihovny Microsoft C používá následující příznaky tak, aby řízení přidělení haldy a procesu generování sestav. Další informace najdete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).  
  
|Příznak|Popis|  
|----------|-----------------|  
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|Mapuje funkce základní hald svým ladicí verze|  
|[_DEBUG](../c-runtime-library/debug.md)|Umožňuje použití ladění verzích běhové funkce|  
|[_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|Určuje, jak správce haldy ladění sleduje přidělování|  
  
 Tyto příznaky se může definovat s možností příkazového řádku /D nebo s `#define` – direktiva. Když je příznak definovaná pomocí `#define`, direktivu musí být před příkaz pro běžné deklarace zahrnout soubor hlaviček.  
  
## <a name="see-also"></a>Viz také  
 [Globální proměnné a standardní typy](../c-runtime-library/global-variables-and-standard-types.md)