---
title: 2.7.2.7 copyin | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94b4c529b7ad6fd717be1e1dee0edd3ff9ac3ff5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426884"
---
# <a name="2727-copyin"></a>2.7.2.7 copyin

**Copyin** klauzule poskytuje mechanismus pro stejnou hodnotu přiřadit **threadprivate** proměnné pro každé vlákno v týmu provádí paralelní oblasti. Pro každou proměnnou podle **copyin** klauzule, hodnotu proměnné v hlavním vlákně tým zkopírován jako při přiřazení kopie privátní vlákno na začátku paralelní oblasti. Syntaxe **copyin** klauzule vypadá takto:

```

copyin(
variable-list
)

```

Omezení týkající **copyin** klauzule jsou následující:

- Proměnná, která je zadána v **copyin** klauzule musí mít operátor přiřazení kopie přístupná a jednoznačná.

- Proměnná, která je zadána v **copyin** klauzule musí být **threadprivate** proměnné.