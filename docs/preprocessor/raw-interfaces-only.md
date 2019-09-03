---
title: importovat atribut raw_interfaces_only
ms.date: 08/29/2019
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 4b79aa4dbafa204d84f4d6ed7ec78fdec1b81fa7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216209"
---
# <a name="raw_interfaces_only-import-attribute"></a>importovat atribut raw_interfaces_only

**C++Konkrétní**

Potlačí generování obálkových funkcí zpracování chyb a deklarace [vlastností](../cpp/property-cpp.md) , které používají tyto funkce obálky.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **raw_interfaces_only**

## <a name="remarks"></a>Poznámky

Atribut **raw_interfaces_only** také způsobí odebrání výchozí předpony používané při pojmenovávání funkcí bez vlastností. Obvykle je `raw_`předpona. Je-li tento atribut zadán, jsou názvy funkcí převedené přímo z knihovny typů.

Tento atribut umožňuje zobrazit pouze obsah nízké úrovně v knihovně typů.

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
