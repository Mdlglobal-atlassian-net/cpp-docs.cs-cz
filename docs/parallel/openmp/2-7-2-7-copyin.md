---
title: 2.7.2.7 copyin
ms.date: 11/04/2016
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
ms.openlocfilehash: 65bb8faba085e5582e779fa0e9d5bf1a91a39f0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545441"
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