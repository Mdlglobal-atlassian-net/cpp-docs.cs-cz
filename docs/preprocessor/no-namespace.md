---
title: importovat atribut no_namespace
ms.date: 08/29/2019
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: ba52aed69cdbb46c135e6de5078d718e93f99c87
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220735"
---
# <a name="no_namespace-import-attribute"></a>importovat atribut no_namespace

**C++Konkrétní**

Určuje, že kompilátor negeneruje název oboru názvů.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **no_namespace**

## <a name="remarks"></a>Poznámky

Obsah knihovny typů v `#import` hlavičkovém souboru je obvykle definován v oboru názvů. Název oboru názvů je uveden v `library` příkazu původního souboru IDL. Pokud je zadán atribut **no_namespace** , pak tento obor názvů není generován kompilátorem.

Pokud chcete použít jiný název oboru názvů, použijte raději atribut [rename_namespace](../preprocessor/rename-namespace.md) .

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
