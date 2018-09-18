---
title: Chyba kompilátoru C3393 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3393
dev_langs:
- C++
helpviewer_keywords:
- C3393
ms.assetid: d57f7c69-0a02-4fe3-9e45-bc62644fd77c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ceb6875484a3afe1d13f13990334434a6c1b086
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022653"
---
# <a name="compiler-error-c3393"></a>Chyba kompilátoru C3393

Chyba syntaxe v klauzuli omezení: 'identifier' není typ

Identifikátor předán omezení, který musí být typu, nebyl typu.  Další informace najdete v tématu [omezení parametrů obecných typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

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