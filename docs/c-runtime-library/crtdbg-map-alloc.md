---
title: "_CRTDBG_MAP_ALLOC – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
dev_langs: C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a2b61b315baa337675147ded1232a943e82b24ec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC
Když **_crtdbg_map_alloc –** příznak je definována v ladicí verze aplikace, základní verzi funkce hald přímo jsou namapované na jejich ladicí verze. Příznak se používá v Crtdbg.h udělat mapování. Tento příznak je k dispozici pouze při [_DEBUG –](../c-runtime-library/debug.md) příznak byla definována v aplikaci.  
  
 Další informace o použití ladicí verze versus základní verze funkce haldy najdete v tématu [pomocí ladění verze Versus základní verze](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="see-also"></a>Viz také  
 [Příznaky ovládacích prvků](../c-runtime-library/control-flags.md)