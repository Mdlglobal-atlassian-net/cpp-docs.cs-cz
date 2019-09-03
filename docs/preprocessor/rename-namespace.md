---
title: importovat atribut rename_namespace
ms.date: 08/29/2019
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: d319d7390e7c7dce070a35be44aad37c7a34e1a0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216651"
---
# <a name="rename_namespace-import-attribute"></a>importovat atribut rename_namespace

**C++Konkrétní**

Přejmenuje obor názvů, který obsahuje obsah knihovny typů.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **rename_namespace (** "*newname*" **)**

### <a name="parameters"></a>Parametry

*Nového*\
Nový název oboru názvů.

## <a name="remarks"></a>Poznámky

Atribut **rename_namespace** přebírá jeden argument, *newname*, který určuje nový název oboru názvů.

Chcete-li odebrat obor názvů, použijte raději atribut [no_namespace](../preprocessor/no-namespace.md) .

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
