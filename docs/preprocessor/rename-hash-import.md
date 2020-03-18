---
title: Přejmenovat atribut import
ms.date: 08/29/2019
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: 520369f0308078fead2947e27a512f25a3ad3fab
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447493"
---
# <a name="rename-import-attribute"></a>Přejmenovat atribut import

**C++Konkrétní**

Funguje kolem problémů kolize názvů.

## <a name="syntax"></a>Syntaxe

> **#import** přejmenování *knihovny typů* **(** "*oldname*" **,** "*Nový_název*" **)**

### <a name="parameters"></a>Parametry

*OldName*\
Starý název v knihovně typů.

*Nový_název*\
Název, který se má použít místo starého názvu

## <a name="remarks"></a>Poznámky

Pokud je zadán atribut **Přejmenovat** , kompilátor nahradí všechny výskyty *oldname* v *knihovně typů* pomocí parametru *Nový_název* uživatelem zadaného v výsledných hlavičkových souborech.

Atribut **přejmenování** lze použít, pokud se název v knihovně typů shoduje s definicí makra v systémových hlavičkových souborech. Pokud tato situace není vyřešena, kompilátor může vydávat různé syntaktické chyby, jako je například [Chyba kompilátoru C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) a [Chyba kompilátoru C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).

> [!NOTE]
> Náhrada je určena pro název, který se používá v knihovně typů, nikoli pro název, který se používá ve výsledném hlavičkovém souboru.

Předpokládejme například, že vlastnost s názvem `MyParent` existuje v knihovně typů a makro `GetMyParent` je definováno v souboru hlaviček a použito před `#import`. Vzhledem k tomu, že `GetMyParent` je výchozím názvem funkce obálky pro vlastnost `get` zpracování chyb, dojde k kolizi názvů. Chcete-li tento problém obejít, použijte následující atribut v příkazu `#import`:

```cpp
#import MyTypeLib.tlb rename("MyParent","MyParentX")
```

Přejmenuje název `MyParent` v knihovně typů. Pokus o přejmenování názvu obálky `GetMyParent` se nezdařil:

```cpp
#import MyTypeLib.tlb rename("GetMyParent","GetMyParentX")
```

Je to proto, že název `GetMyParent` pouze v souboru hlaviček výsledné knihovny typů.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také

[atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
