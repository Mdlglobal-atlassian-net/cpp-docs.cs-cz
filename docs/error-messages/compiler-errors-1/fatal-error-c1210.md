---
title: Závažná chyba C1210 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1210
dev_langs:
- C++
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d22a34f44fb2c97fe341cb313d7917a35506cdd
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704981"
---
# <a name="fatal-error-c1210"></a>Závažná chyba C1210

> / CLR: pure a verze modulu runtime nainstalován nepodporuje/CLR: safe

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

C1210 nastane, když máte kompilátoru pro aktuální verzi, ale CLR z předchozí verze.

Některé funkce kompilátoru nemusí fungovat na předchozí verzi čas spuštění.

Chcete-li vyřešit nainstalovat C1210 běžné verzi modulu runtime jazyka, která je určena pro použití s vaší kompilátoru.