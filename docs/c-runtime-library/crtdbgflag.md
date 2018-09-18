---
title: _crtDbgFlag | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d9900d42a5bae3c7a613028a7ae4ffe4bdc0333
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044909"
---
# <a name="crtdbgflag"></a>_crtDbgFlag

**_CrtDbgFlag** příznak se skládá z pěti bitová pole, které řídí způsob přidělení paměti v ladicí verzi haldy jsou sledovány, ověřit, hlásí a zálohované. Bitová pole příznaku jsou nastaveny pomocí [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md) funkce. Tento příznak a jeho bitová pole jsou deklarovány v souboru Crtdbg.h. Tento příznak je k dispozici pouze pokud [_DEBUG](../c-runtime-library/debug.md) příznak je definována v aplikaci.

Další informace o použití tohoto příznaku ve spojení s jinými funkcemi ladění, naleznete v tématu [funkce vykazování stavu haldy](/visualstudio/debugger/crt-debug-heap-details).

## <a name="see-also"></a>Viz také

[Příznaky řízení](../c-runtime-library/control-flags.md)