---
title: MÍSTNÍ (MASM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Local
dev_langs:
- C++
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8105bc8168ce28d468a1378c5cf7889907a7c9f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685060"
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