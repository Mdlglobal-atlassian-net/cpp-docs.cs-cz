---
title: Závažná chyba C1091 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1091
dev_langs:
- C++
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e93c2e6c26f8704e700465fb706867129847a460
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104235"
---
# <a name="fatal-error-c1091"></a>Závažná chyba C1091

limit kompilátoru: řetězec přesahuje délku bajtů 'délka.

Řetězcová konstanta překročil aktuální limit délky řetězce.

Můžete chtít statický řetězec rozdělit do dvou (nebo více) proměnné a používat [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) k připojení výsledku jako součást deklarace nebo za běhu.