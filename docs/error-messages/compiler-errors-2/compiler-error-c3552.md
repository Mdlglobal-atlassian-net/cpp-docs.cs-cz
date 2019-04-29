---
title: Chyba kompilátoru C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: 27c4707097f43266a3be57ad6dc9591ab6f34e97
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375935"
---
# <a name="compiler-error-c3552"></a>Chyba kompilátoru C3552

'typename': pozdně zadaný návratový typ nemůže obsahovat 'auto'

Pokud používáte `auto` – klíčové slovo jako zástupný symbol pro návratový typ funkce, je nutné zadat pozdně zadaný návratový typ. Však nelze použít jiné `auto` – klíčové slovo k určení pozdně zadaný návratový typ. Například následující fragment kódu vrátí chyba C3552.

`auto myFunction->auto; // C3552`