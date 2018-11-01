---
title: Chyba kompilátoru C3132
ms.date: 11/04/2016
f1_keywords:
- C3132
helpviewer_keywords:
- C3132
ms.assetid: d54a3d12-336a-4ed0-ad4e-43cddac33b5e
ms.openlocfilehash: 2b8edc506b6038ddec0ca265cafabbebf0428d1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612978"
---
# <a name="compiler-error-c3132"></a>Chyba kompilátoru C3132

Funkce parametr: pole parametrů může používat jedině pro formální argument typu 'single-dimensional spravovaného pole.

[ParamArray](https://msdn.microsoft.com/library/system.paramarrayattribute.aspx) byl použit atribut parametru, která nebyla pole s jednou dimenzí.

Následující ukázka generuje C3132:

```
// C3132.cpp
// compile with: /clr /c
using namespace System;
void f( [ParamArray] Int32[,] );   // C3132
void g( [ParamArray] Int32[] );   // C3132

void h( [ParamArray] array<Char ^> ^ MyArray );   // OK

```