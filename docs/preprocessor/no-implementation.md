---
title: importovat atribut no_implementation
ms.date: 08/29/2019
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 8f0a7454fdbedc1959b665ccb2a23748d21c342d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220767"
---
# <a name="no_implementation-import-attribute"></a>importovat atribut no_implementation

**C++Konkrétní**

Potlačí generování `.tli` záhlaví, které obsahuje implementace členských funkcí obálky.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **no_implementation**

## <a name="remarks"></a>Poznámky

Je-li tento atribut zadán, `.tlh` bude hlavička s deklaracemi, které budou vystavovat položky knihovny typů, generována `#include` bez příkazu pro zahrnutí `.tli` hlavičkového souboru.

Tento atribut se používá ve spojení s [implementation_only](../preprocessor/implementation-only.md).

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
