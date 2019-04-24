---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: ae79ce9245bb1c0425c3e9b92dd27b52fa443dba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179604"
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

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)