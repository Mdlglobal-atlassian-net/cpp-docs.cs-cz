---
title: alloca | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0c73abcb52b991ee6bd4de839861aa4ef684181
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702743"
---
# <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) musí být 16 bajtů zarovnána a kromě toho budete muset použít ukazatel na rámec.

Zásobník, který je přidělen musí obsahovat prostor pod ním parametrů následně volané funkce, jak je popsáno v [přidělení zásobníku](../build/stack-allocation.md).

## <a name="see-also"></a>Viz také

[Použití zásobníku](../build/stack-usage.md)