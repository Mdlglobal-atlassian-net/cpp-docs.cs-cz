---
title: Chyba kompilátoru C2732
ms.date: 11/04/2016
f1_keywords:
- C2732
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
ms.openlocfilehash: 61bac8c1b5c9e029cc5833f458669b490fed8c91
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755795"
---
# <a name="compiler-error-c2732"></a>Chyba kompilátoru C2732

specifikace propojení je v konfliktu s předchozí specifikací pro Function.

Funkce je již deklarována s jiným specifikátorem propojení.

Tato chyba může být způsobena zahrnutím souborů s různými specifikátory propojení.

Chcete-li tuto chybu opravit, změňte příkazy `extern` tak, aby se vazby souhlasily. Konkrétně nezalomí direktivy `#include` do bloků `extern "C"`.

## <a name="example"></a>Příklad

Následující ukázka generuje C2732:

```cpp
// C2732.cpp
extern void func( void );   // implicit C++ linkage
extern "C" void func( void );   // C2732
```
