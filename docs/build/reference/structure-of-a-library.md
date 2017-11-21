---
title: Struktura knihovny | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: libraries, structure
ms.assetid: a5fda8e8-4a1b-4499-9095-0df935262ce4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 875dddb961b18378029de08582e728ad626be948
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="structure-of-a-library"></a>Struktura knihovny
Knihovnu obsahuje COFF objekty. Objekty v knihovně obsahují funkce a data, která může externě odkazují jiné objekty v programu. Objekt v knihovně se někdy označuje jako člena knihovny.  
  
 Další informace o obsahu knihovny můžete získat spuštěním nástroje DUMPBIN s parametrem /LINKERMEMBER. Další informace o této možnosti najdete v tématu [DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled LIB](../../build/reference/overview-of-lib.md)