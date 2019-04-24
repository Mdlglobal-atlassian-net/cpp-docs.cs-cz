---
title: Používání příkazu abort
ms.date: 11/04/2016
f1_keywords:
- Abort
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
ms.openlocfilehash: 0961f6f88f5de4d435fa65e50b9dbdbc478e7608
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244205"
---
# <a name="using-abort"></a>Používání příkazu abort

Volání [přerušit](../c-runtime-library/reference/abort.md) funkce dojde k okamžitému ukončení. Funkce obchází běžný proces ničení inicializovaných globálních statických objektů. Také obchází všechna speciální zpracování zadaná pomocí funkce `atexit`.

## <a name="see-also"></a>Viz také:

[Další důležité informace o ukončení](../cpp/additional-termination-considerations.md)