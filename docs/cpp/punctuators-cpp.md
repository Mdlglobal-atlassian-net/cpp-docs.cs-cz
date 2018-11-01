---
title: Interpunkční znaky (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
ms.openlocfilehash: cef34a17de99a189a590ac3f13c0db9563df643c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478262"
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