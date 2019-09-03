---
title: importovat atribut TLBID
ms.date: 08/29/2019
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 364fb224b0f2769cb0933e71d18ff70768189328
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216531"
---
# <a name="tlbid-import-attribute"></a>importovat atribut TLBID

**C++Konkrétní**

Umožňuje načíst knihovny jiné než primární typ knihovny.

## <a name="syntax"></a>Syntaxe

> **#import** *Type-Library-DLL* **TLBID (** *číslo* **)**

### <a name="parameters"></a>Parametry

*Automatické*\
Číslo knihovny typů v *knihovně typů type-library-DLL*.

## <a name="remarks"></a>Poznámky

Pokud je do jediné knihovny DLL integrováno více knihoven typů, je možné načíst knihovny jiné než primární typ knihovny pomocí **TLBID**.

Příklad:

```cpp
#import <MyResource.dll> tlbid(2)
```

je ekvivalentní:

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
