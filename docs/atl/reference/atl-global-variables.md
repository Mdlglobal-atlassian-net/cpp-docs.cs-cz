---
title: Globální proměnné ATL
ms.date: 12/06/2017
f1_keywords:
- ATLBASE/_pAtlModule
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
ms.openlocfilehash: 4f98b31d2454b7c6e903e5b5b87bceb4ddcb6961
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62248157"
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
