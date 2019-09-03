---
title: auto_inline – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: 59cda8cb73196215318c9570a5c067786284afaa
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216311"
---
# <a name="auto_inline-pragma"></a>auto_inline – direktiva pragma

Vyloučí všechny funkce definované v rozsahu, ve kterém je zapínání jako kandidát pro automatické vložené rozšíření.

## <a name="syntax"></a>Syntaxe

> **#pragma auto_inline (** [{ **on** | **off** }] **)**

## <a name="remarks"></a>Poznámky

Chcete-li použít direktivu pragma **auto_inline** , umístěte ji před a hned za, ne dovnitř, definici funkce. Direktiva pragma se projeví hned po první definici funkce po zjištění direktivy pragma.

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
