---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: c8ea49b9862159a5a56bfb3d2c3cd0c1f4cd7413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596869"
---
# <a name="local-masm"></a>LOCAL (MASM)

V první direktivě v rámci makra **místní** definuje popisky, které jsou jedinečné pro každou instanci makra.

## <a name="syntax"></a>Syntaxe

> MÍSTNÍ *localname* [[, *localname*]]...

> MÍSTNÍ *popisek* [[[*počet*]]] [[:*typ*]] [[, *popisek* [[[*počet*]]] [[ *typ*]]]]...

## <a name="remarks"></a>Poznámky

V druhém – direktiva v definici procedury (**PROC**), **místní** vytvoří proměnné založené na zásobníku, která existuje po dobu trvání procesu. *Popisek* může být jednoduchá proměnná nebo pole obsahující *počet* elementy.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>