---
title: Struktura knihovny | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- libraries, structure
ms.assetid: a5fda8e8-4a1b-4499-9095-0df935262ce4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1630636b0de552712f67bc43b5182f991b10ef0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="structure-of-a-library"></a>Struktura knihovny
Knihovnu obsahuje COFF objekty. Objekty v knihovně obsahují funkce a data, která může externě odkazují jiné objekty v programu. Objekt v knihovně se někdy označuje jako člena knihovny.  
  
 Další informace o obsahu knihovny můžete získat spuštěním nástroje DUMPBIN s parametrem /LINKERMEMBER. Další informace o této možnosti najdete v tématu [DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled knihovny LIB](../../build/reference/overview-of-lib.md)