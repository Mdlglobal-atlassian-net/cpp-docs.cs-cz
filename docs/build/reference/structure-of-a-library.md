---
title: Struktura knihovny | Dokumentace Microsoftu
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
ms.openlocfilehash: 03c2c66d45ee415ddc4f3ba27b6a100c5e2ec1dc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702101"
---
# <a name="structure-of-a-library"></a>Struktura knihovny

Knihovny obsahuje objekty COFF. Objekty v knihovně obsahují funkce a data, která může odkazovat na externě jinými objekty v programu. Objekt v knihovně se někdy označuje jako člena knihovny.

Další informace o obsahu knihovny můžete získat spuštěním nástroj DUMPBIN s možností /LINKERMEMBER. Další informace o této možnosti najdete v tématu [DUMPBIN – odkaz](../../build/reference/dumpbin-reference.md).

## <a name="see-also"></a>Viz také

[Přehled knihovny LIB](../../build/reference/overview-of-lib.md)