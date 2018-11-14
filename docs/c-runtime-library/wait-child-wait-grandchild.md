---
title: _WAIT_CHILD, _WAIT_GRANDCHILD
ms.date: 11/04/2016
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
ms.openlocfilehash: 714b4e79f1c229817a12908aad0d726f74023036
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524388"
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD, _WAIT_GRANDCHILD

## <a name="syntax"></a>Syntaxe

```

#include <process.h>
```

## <a name="remarks"></a>Poznámky

`_cwait` Funkce můžete využívat jakýkoli proces čekat pro jakýkoli proces (Pokud je ID procesu je známý). Argument akce může být jeden z následujících hodnot:

|Konstanta|Význam|
|--------------|-------------|
|`_WAIT_CHILD`|Volání proces čeká na zadaný nový proces ukončí.|
|`_WAIT_GRANDCHILD`|Volání procesu počká až do zadaného nový proces a všechny procesy, které vytvořil tento nový proces, ukončete.|

## <a name="see-also"></a>Viz také

[_cwait](../c-runtime-library/reference/cwait.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)