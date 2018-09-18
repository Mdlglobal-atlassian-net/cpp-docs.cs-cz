---
title: _WAIT_CHILD _WAIT_GRANDCHILD | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
dev_langs:
- C++
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dd7b3fab51c382413c507831572afedd824c3f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018337"
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