---
title: Interpunkční znaky (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 438b3f0469d1e8426b1e0ec2a19a63d1ae63c041
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039267"
---
# <a name="punctuators-c"></a>Interpunkční znaky (C++)

Interpunkční znaky v jazyce C++ mají pro kompilátor syntaktický a sémantický význam, ale samy o sobě neurčují operaci vracející hodnotu. Některé interpunkční znaky, ať již samotné nebo v kombinacích, mohou být také operátory jazyka C++ nebo významné pro preprocesor.

Následující znaky jsou považovány za interpunkční:

```
! % ^ & * ( ) - + = { } | ~
[ ] \ ; ' : " < > ? , . / #
```

Interpunkční znaky **[] č.**, **()**, a **{}** musí vyskytovat v párech po [fáze překladu](../preprocessor/phases-of-translation.md) 4.

## <a name="see-also"></a>Viz také:

[Lexikální konvence](../cpp/lexical-conventions.md)