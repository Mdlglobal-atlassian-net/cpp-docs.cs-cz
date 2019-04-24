---
title: Interpunkční znaky (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
ms.openlocfilehash: cef34a17de99a189a590ac3f13c0db9563df643c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244230"
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