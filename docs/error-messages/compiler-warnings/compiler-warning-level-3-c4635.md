---
title: Upozornění kompilátoru (úroveň 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: fd3bf6c1b14c6dae8e2fa95a54e2d4fbc4f295c5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991848"
---
# <a name="compiler-warning-level-3-c4635"></a>Upozornění kompilátoru (úroveň 3) C4635

Cíl komentáře k dokumentu XML: chybně vytvořený kód XML: důvod

Kompilátor zjistil některé problémy s značkami XML.  Opravit problém a znovu kompilovat

Následující ukázka generuje C4635:

```cpp
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

Všimněte si, že výstup pro tuto ukázku říká: **koncová značka ' member ' neodpovídá počáteční značce ' Summary '.**

Problém s touto ukázkou je, že koncová značka pro \<Summary > je špatně vytvořená a kompilátor je nerozpozná jako \<souhrn > koncová značka.  V souboru. xdc kompilátorem v každé kompilaci/doc je vložená značka členu \<>.  Problém je tedy v tom, že koncová značka \<pollad >, se neshoduje s předchozí počáteční značkou, která byla zpracována kompilátorem (\<souhrn >.
