---
title: main – omezení funkce
ms.date: 11/04/2016
f1_keywords:
- Main
helpviewer_keywords:
- main function, restrictions on using
ms.assetid: 7b3df731-344b-44a8-850c-11cbcbfbfa83
ms.openlocfilehash: 9ccea987b05c7854e78ba1621fd6c0a065d73d5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301835"
---
# <a name="main-function-restrictions"></a>main – omezení funkce

Vztahuje několik omezení **hlavní** funkce, která se nedá použít u jiných funkcí jazyka C++. **Hlavní** funkce:

- Nemohou být přetíženy (viz [přetížení funkce](function-overloading.md)).

- Nelze deklarovat jako **vložené**.

- Nelze deklarovat jako **statické**.

- Nelze zabrat její adresu.

- Nelze ji volat.

## <a name="see-also"></a>Viz také:

[main: spuštění programu](../cpp/main-program-startup.md)