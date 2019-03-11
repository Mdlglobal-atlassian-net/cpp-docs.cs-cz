---
title: _crtDbgFlag
ms.date: 11/04/2016
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
ms.openlocfilehash: a967b436d53acab6d76fa36fdf9b13c7c24d49c3
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746979"
---
# <a name="crtdbgflag"></a>_crtDbgFlag

**_CrtDbgFlag** příznak se skládá z pěti bitová pole, které řídí způsob přidělení paměti v ladicí verzi haldy jsou sledovány, ověřit, hlásí a zálohované. Bitová pole příznaku jsou nastaveny pomocí [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) funkce. Tento příznak a jeho bitová pole jsou deklarovány v souboru Crtdbg.h. Tento příznak je k dispozici pouze pokud [_DEBUG](../c-runtime-library/debug.md) příznak je definována v aplikaci.

Další informace o použití tohoto příznaku ve spojení s jinými funkcemi ladění, naleznete v tématu [funkce vykazování stavu haldy](/visualstudio/debugger/crt-debug-heap-details).

## <a name="see-also"></a>Viz také:

[Příznaky řízení](../c-runtime-library/control-flags.md)
