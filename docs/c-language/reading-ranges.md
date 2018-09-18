---
title: Čtení rozsahů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76530dfdac917dfbde50bc3fb1b17a3c31178729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030236"
---
# <a name="reading-ranges"></a>Čtení rozsahů

**ANSI 4.9.6.2** interpretace znaku pomlčky (-), který není prvním ani posledním znakem v seznamu % [převodu ve `fscanf` – funkce

Následující řádek

```
fscanf( fileptr, "%[A-Z]", strptr);
```

načte libovolný počet znaků v rozsahu A – Z do řetězce ke kterému `strptr` body.

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)