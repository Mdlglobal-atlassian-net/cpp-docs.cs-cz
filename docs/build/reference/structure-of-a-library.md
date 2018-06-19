---
title: Struktura knihovny | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- libraries, structure
ms.assetid: a5fda8e8-4a1b-4499-9095-0df935262ce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6eff0000aef01790106b44b49b4855218fcf9332
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373098"
---
# <a name="structure-of-a-library"></a>Struktura knihovny
Knihovnu obsahuje COFF objekty. Objekty v knihovně obsahují funkce a data, která může externě odkazují jiné objekty v programu. Objekt v knihovně se někdy označuje jako člena knihovny.  
  
 Další informace o obsahu knihovny můžete získat spuštěním nástroje DUMPBIN s parametrem /LINKERMEMBER. Další informace o této možnosti najdete v tématu [DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled knihovny LIB](../../build/reference/overview-of-lib.md)