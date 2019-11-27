---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c3a04f68b7fd17b2b6459c219a98fd99ec2d62d4
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397245"
---
# <a name="local-masm"></a>LOCAL (MASM)

V první direktivě v rámci makra **místní** definuje popisky, které jsou jedinečné pro jednotlivé instance makra.

## <a name="syntax"></a>Syntaxe

> **Místní** *LocalName* ⟦, *LocalName* ... ⟧
>
> **Local** *Label* ⟦ __\[__ *Count* __]__ ⟧ ⟦ __:__ *Type*⟧ ⟦ __,__ *Label* ⟦ __\[__ *Count* __]__ ⟧ ⟦*Type*⟧... ⟧

## <a name="remarks"></a>Poznámky

V druhé direktivě v rámci definice procedury (**proc**) vytvoří **místní** proměnné založené na zásobníku, které existují po dobu trvání procedury. *Popisek* může být jednoduchá proměnná nebo pole obsahující *počet* prvků.

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
