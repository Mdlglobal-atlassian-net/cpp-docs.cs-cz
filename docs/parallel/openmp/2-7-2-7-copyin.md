---
title: 2.7.2.7 copyin
ms.date: 11/04/2016
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
ms.openlocfilehash: 20db32530ee60967245497cdfb12a0fce103f7b7
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519526"
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