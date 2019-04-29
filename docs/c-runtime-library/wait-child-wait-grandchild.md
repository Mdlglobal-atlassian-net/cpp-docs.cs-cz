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
ms.openlocfilehash: 98858058add6a0a11d4f9331989c6816e38130aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377819"
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

## <a name="see-also"></a>Viz také:

[_cwait](../c-runtime-library/reference/cwait.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
