---
title: 2.2 Podmíněná kompilace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8f9c914d-736c-48cf-899d-c8029dbe1e32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25b52ce624777efe85e27b8ce5e7941bc2f5dcba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440378"
---
# <a name="22-conditional-compilation"></a>2.2 Podmíněná kompilace

_**OPENMP** – makro název je definován implementací CLS OpenMP jako desítkovou konstantu *yyyymm*, která bude roku a měsíce specifikace schválené. Toto makro nesmí být předmět **#define** nebo **#undef** direktiva předzpracování.

```
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Pokud dodavatelů definovat rozšíření pro OpenMP, určují další předdefinovaná makra.