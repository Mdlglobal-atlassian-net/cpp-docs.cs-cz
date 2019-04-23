---
title: Chyba kompilátoru C3393
ms.date: 11/04/2016
f1_keywords:
- C3393
helpviewer_keywords:
- C3393
ms.assetid: d57f7c69-0a02-4fe3-9e45-bc62644fd77c
ms.openlocfilehash: 5147e3e406fde73a05b7069e2a9336f27b3db622
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776259"
---
# <a name="compiler-error-c3393"></a>Chyba kompilátoru C3393

Chyba syntaxe v klauzuli omezení: 'identifier' není typ

Identifikátor předán omezení, který musí být typu, nebyl typu.  Další informace najdete v tématu [omezení parametrů obecných typů (C++vyhodnocovací)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3393:

```
// C3393.cpp
// compile with: /clr /c
void MyInterface() {}
interface class MyInterface2 {};

generic<typename T>
where T : MyInterface   // C3393
// try the following line instead
// where T : MyInterface2
ref class R {};
```