---
title: Přejmenovat (#import) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Rename
dev_langs:
- C++
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b8525a321f56ab5e9bfe2f8e8cee7be9cd26788
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808183"
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

## <a name="see-also"></a>Viz také

[atributů #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)