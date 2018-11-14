---
title: LOCAL (MASM)
ms.date: 08/30/2018
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 94af498865151ff5c49fac9dbc03de65c4ecb934
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327600"
---
# <a name="local-masm"></a>LOCAL (MASM)

V první direktivě v rámci makra **místní** definuje popisky, které jsou jedinečné pro každou instanci makra.

## <a name="syntax"></a>Syntaxe

> MÍSTNÍ *localname* \[, *localname*]...
>
> MÍSTNÍ *popisek* \[ __\[__ *počet*__]__ ] \[ __:__  *typ*] \[ __,__ *popisek* \[ __\[__ *počet* __]__  ] \[ *typ*]]...

## <a name="remarks"></a>Poznámky

V druhém – direktiva v definici procedury (**PROC**), **místní** vytvoří proměnné založené na zásobníku, která existuje po dobu trvání procesu. *Popisek* může být jednoduchá proměnná nebo pole obsahující *počet* elementy.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>