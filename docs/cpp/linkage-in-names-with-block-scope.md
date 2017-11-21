---
title: "Propojení v názvech s rozsahem bloku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- scope [C++], linkage rules
- linkage [C++], scope linkage rules
- names [C++], scope linkage rules
- block scope [C++]
- external linkage, scope linkage rules
ms.assetid: 73efa91a-f761-47f7-bbd9-9f9e3508e218
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0549538ba2af256d3a98b83dcb691327e387de9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linkage-in-names-with-block-scope"></a>Propojení v názvech s oborem bloku
Následující pravidla propojení platí pro názvy s rozsahem bloku (místní názvy):  
  
-   Názvy deklarován jako `extern` mít externí propojení, pokud bylo dříve deklarované jako **statické**.  
  
-   Všechny ostatní názvy s rozsahem bloku nemají žádné propojení.  
  
## <a name="see-also"></a>Viz také  
 [Program a propojení](../cpp/program-and-linkage-cpp.md)