---
title: C2393 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2393
dev_langs:
- C++
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 057537c8efcf6e827d9ac9aaf36c0eace6d24156
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704027"
---
# <a name="compiler-error-c2393"></a>C2393 chyby kompilátoru

> '*symbol*': symbol na appdomain nelze přidělit do segmentu '*segment*.

## <a name="remarks"></a>Poznámky

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Použití [appdomain](../../cpp/appdomain.md) proměnné znamená, že jsou kompilujete s **/CLR: pure** nebo **/CLR: safe**, a bezpečné nebo čisté bitové kopie nemůže obsahovat segmenty data.

V tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) Další informace.

## <a name="example"></a>Příklad

Následující ukázka generuje C2393. Chcete-li tento problém vyřešit, nevytvářejte datového segmentu.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```