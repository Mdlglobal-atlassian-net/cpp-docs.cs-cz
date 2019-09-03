---
title: Přejmenovat atribut import
ms.date: 08/29/2019
f1_keywords:
- Rename
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: ef1f64e0c268f850899efe499f7b1ad3991dd570
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216661"
---
# <a name="rename-import-attribute"></a>Přejmenovat atribut import

**C++Konkrétní**

Funguje kolem problémů kolize názvů.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **Rename (** "*oldname*" **;** "*newname*" **)**

### <a name="parameters"></a>Parametry

*OldName*\
Starý název v knihovně typů.

*Nového*\
Název, který se má použít místo starého názvu

## <a name="remarks"></a>Poznámky

Pokud je zadán atribut **Přejmenovat** , kompilátor nahradí všechny výskyty *oldname* v *knihovně typů* pomocí parametru *Nový_název* uživatelem zadaného v výsledných hlavičkových souborech.

Atribut **přejmenování** lze použít, pokud se název v knihovně typů shoduje s definicí makra v systémových hlavičkových souborech. Pokud tato situace není vyřešena, kompilátor může vydávat různé syntaktické chyby, jako je například [Chyba kompilátoru C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) a [Chyba kompilátoru C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).

> [!NOTE]
> Náhrada je určena pro název, který se používá v knihovně typů, nikoli pro název, který se používá ve výsledném hlavičkovém souboru.

Předpokládejme například, že vlastnost s názvem `MyParent` existuje v knihovně typů a makro `GetMyParent` je definováno v souboru hlaviček a použito před `#import`. Vzhledem `GetMyParent` k tomu, že je výchozím názvem funkce obálky pro vlastnost zpracování `get` chyb, dojde ke kolizi názvů. Chcete-li tento problém obejít, použijte následující atribut v `#import` příkazu:

```cpp
#import MyTypeLib.tlb rename("MyParent","MyParentX")
```

který přejmenuje název `MyParent` v knihovně typů. Pokus o přejmenování `GetMyParent` názvu obálky se nezdařil:

```cpp
#import MyTypeLib.tlb rename("GetMyParent","GetMyParentX")
```

Je to proto, že `GetMyParent` název se vyskytuje pouze ve výsledném hlavičkovém souboru knihovny typů.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
