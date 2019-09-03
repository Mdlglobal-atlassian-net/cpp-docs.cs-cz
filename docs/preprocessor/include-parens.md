---
title: include () – import atributu
ms.date: 08/29/2019
f1_keywords:
- include()
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
ms.openlocfilehash: 39ab63525b2b83781cbcaf86a61742c5fb767b72
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218877"
---
# <a name="include-import-attribute"></a>include () – import atributu

**C++Konkrétní**

Zakáže automatické vyloučení.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **include ("** _název1_ **"** [ __, "__ *název2* __"__ ...] __)__

### <a name="parameters"></a>Parametry

*Name1*\
První položka, která má být nuceně zahrnutá

*Soubor2*\
Druhá položka, která má být vynuceně zahrnutá (v případě potřeby).

## <a name="remarks"></a>Poznámky

Knihovny typů mohou obsahovat definice položek definovaných v systémových hlavičkách nebo jiných knihovnách typů. `#import`pokusí se zabránit více chybám definice automatickým vyloučením těchto položek. Pokud by některé položky neměly být vyloučeny automaticky, může se zobrazit [Upozornění kompilátoru (úroveň 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md). Pomocí tohoto atributu lze zakázat automatické vyloučení. Tento atribut může mít libovolný počet argumentů, jeden pro každý název položky knihovny typů, která se má zahrnout.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
