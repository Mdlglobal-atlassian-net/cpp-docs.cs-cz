---
title: Interpunkční znaky (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- punctuators [C++]
ms.assetid: 1521564c-a977-488a-9490-068079897592
ms.openlocfilehash: cc4e56cd0dce3ae91183a8675eba96f174c3c31f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160968"
---
# <a name="punctuators-c"></a>Interpunkční znaky (C++)

Interpunkční znaky v jazyce C++ mají pro kompilátor syntaktický a sémantický význam, ale samy o sobě neurčují operaci vracející hodnotu. Některé interpunkční znaky, ať již samotné nebo v kombinacích, mohou být také operátory jazyka C++ nebo významné pro preprocesor.

Následující znaky jsou považovány za interpunkční:

```
! % ^ & * ( ) - + = { } | ~
[ ] \ ; ' : " < > ? , . / #
```

Interpunkční znaky **[]** , **()** a **{}** se musí objevit ve dvojicích po [fázi překladu](../preprocessor/phases-of-translation.md) 4.

## <a name="see-also"></a>Viz také

[Lexikální konvence](../cpp/lexical-conventions.md)
