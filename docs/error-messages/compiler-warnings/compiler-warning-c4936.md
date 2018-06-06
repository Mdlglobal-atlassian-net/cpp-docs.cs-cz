---
title: C4936 upozornění kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4936
dev_langs:
- C++
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0be4a565dd251da77174c401c23b8ed8bfc531b0
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703936"
---
# <a name="compiler-warning-c4936"></a>C4936 upozornění kompilátoru

> Tato __declspec je podporována pouze, když kompilujete s/CLR nebo/CLR: pure

## <a name="remarks"></a>Poznámky

**/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

A `__declspec` ale který byl použit modifikátor `__declspec` modifikátor platí, pouze když kompilujete s jedním z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) možnosti.

Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [proces](../../cpp/process.md).

C4936 je vždy vydané jako chyba.  Můžete zakázat C4936 s [upozornění](../../preprocessor/warning.md) – Direktiva pragma.

## <a name="example"></a>Příklad

Následující ukázka generuje C4936:

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```