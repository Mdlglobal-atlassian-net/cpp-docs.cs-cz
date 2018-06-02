---
title: C3862 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3862
dev_langs:
- C++
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b21e457feb6d090e4abaf531293987eb3504457
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704968"
---
# <a name="compiler-error-c3862"></a>C3862 chyby kompilátoru

> '*funkce*': Nelze kompilovat nespravované funkce s volbou/CLR: pure nebo/CLR: safe

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Kompilace pomocí **/CLR: pure** nebo **/CLR: safe** vytvoří MSIL jedinou bitovou kopii, bitovou kopii s žádné nativního kódu (nespravovaný).  Proto nelze použít `unmanaged` – Direktiva pragma v **/CLR: pure** nebo **/CLR: safe** kompilace.

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [spravované, nespravované](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```