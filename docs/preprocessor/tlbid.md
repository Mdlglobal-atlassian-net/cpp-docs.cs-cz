---
title: TLBID | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6324ec9a64a0d1c47dab8d1beee021f6c8752a96
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807975"
---
# <a name="tlbid"></a>tlbid

**Specifické pro C++**

Umožňuje načítání knihoven jiné než primární typ knihovny.

## <a name="syntax"></a>Syntaxe

```
tlbid(number)
```

### <a name="parameters"></a>Parametry

*Číslo*<br/>
Počet knihovnu typů v `filename`.

## <a name="remarks"></a>Poznámky

Pokud více knihoven typů jsou součástí jedné knihovny DLL, je možné načítat knihovny jiné než primární typ knihovny pomocí **tlbid**.

Příklad:

```cpp
#import <MyResource.dll> tlbid(2)
```

je ekvivalentní:

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**Specifické pro END C++**

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)