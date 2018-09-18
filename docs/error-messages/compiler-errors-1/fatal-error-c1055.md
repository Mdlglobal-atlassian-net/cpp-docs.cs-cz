---
title: Závažná chyba C1055 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1055
dev_langs:
- C++
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6960d8168bd818e4d1baa30e5e54940e6e4dc2e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115447"
---
# <a name="fatal-error-c1055"></a>Závažná chyba C1055

limit kompilátoru: došly klíče

Zdrojový soubor obsahuje příliš mnoho symbolů. Kompilátor nemá dostatek klíčů hash pro symbol tabulku.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Zdrojový soubor rozdělte na menší soubory.

1. Odstranění nepotřebných hlavičkové soubory.

1. Znovu použít dočasný a globální proměnné místo vytvoření nové značky.