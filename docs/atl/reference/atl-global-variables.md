---
title: Globální proměnné ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/06/2017
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATLBASE/_pAtlModule
dev_langs:
- C++
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d33c2a3de5b94f522833db67dfb190ede3a8a63
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054953"
---
# <a name="atl-global-variables"></a>Globální proměnné ATL

## <a name="patlmodule"></a>_pAtlModule

Globální proměnné ukládání ukazatel na aktuální modul.

```cpp
__declspec(selectany) CAtlModule * _pAtlModule
```

### <a name="remarks"></a>Poznámky

Metody v této globální proměnné lze použít k zajištění funkcí (teď zastaralé) třídy ccommodule – k dispozici v aplikaci Visual C++ 6.0.

### <a name="example"></a>Příklad

```cpp
LONG lLocks = _pAtlModule->GetLockCount();
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h
