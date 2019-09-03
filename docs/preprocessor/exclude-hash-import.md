---
title: vyloučit import atributu
ms.date: 08/29/2019
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: 6a3625ee0dd44f3e2731e1240fea5f3dd4ed109e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218715"
---
# <a name="exclude-import-attribute"></a>vyloučit import atributu

**C++Konkrétní**

Vyloučí položky z generovaných souborů hlaviček knihoven typů.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **exclude (** "*název1*" [ **,** "*název2*"...] **)**

### <a name="parameters"></a>Parametry

*Name1*\
První položka, která má být vyloučena.

*Soubor2*\
Volitelné Druhá a pozdější položky, které se mají vyloučit (v případě potřeby)

## <a name="remarks"></a>Poznámky

Knihovny typů mohou obsahovat definice položek definovaných v systémových hlavičkách nebo jiných knihovnách typů. Tento atribut může obsahovat libovolný počet argumentů, kde každá je položka knihovny typů nejvyšší úrovně, která má být vyloučena.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
