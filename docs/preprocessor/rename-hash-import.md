---
title: rename (#import)
ms.date: 10/18/2018
f1_keywords:
- Rename
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: 0fbed04f040a47b5b389f40eeb15254da4a7940b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179727"
---
# <a name="rename-import"></a>Přejmenovat (\#import)

**Specifické pro C++**

Funguje kolem problémy kolizí název.

## <a name="syntax"></a>Syntaxe

```
rename("OldName","NewName")
```

### <a name="parameters"></a>Parametry

*OldName*<br/>
Starý název v knihovně typů.

*NewName*<br/>
Název se použije namísto starý název.

## <a name="remarks"></a>Poznámky

Pokud tento atribut není zadán, kompilátor nahradí všechny výskyty *OldName* v knihovně typů s uživatelem zadané *NewName* ve výsledné soubory hlaviček.

Tento atribut lze použít, když název v knihovně typů se shoduje s definici makra v systémových souborech hlaviček. Pokud tato situace není vyřešen, různé chyby syntaxe se vygeneruje, jako například [Chyba kompilátoru C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) a [Chyba kompilátoru C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).

> [!NOTE]
> Nahrazení je určen pro název použitý v knihovně typů není pro název použitý ve výsledném souboru záhlaví.

Předpokládejme například, že vlastnost s názvem `MyParent` existuje v knihovně typů a makra `GetMyParent` je definována v hlavičkovém souboru a nepoužili `#import`. Protože `GetMyParent` je název výchozí funkce obálky pro zpracování chyb `get` vlastnosti, dojde ke kolizi názvů. Pokud chcete tento problém obejít, použijte následující atribut `#import` – příkaz:

```cpp
rename("MyParent","MyParentX")
```

které přejmenuje název `MyParent` v knihovně typů. Pokus o přejmenování `GetMyParent` název obálky se nezdaří:

```cpp
rename("GetMyParent","GetMyParentX")
```

Důvodem je, že název `GetMyParent` dochází pouze v výsledný hlavičkový soubor knihovny typů.

**Specifické pro END C++**

## <a name="see-also"></a>Viz také:

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)