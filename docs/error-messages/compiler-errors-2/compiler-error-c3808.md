---
title: Chyba kompilátoru C3808
ms.date: 11/04/2016
f1_keywords:
- C3808
helpviewer_keywords:
- C3808
ms.assetid: 2ee8ac97-3ea4-417a-8710-be73a7f98cf4
ms.openlocfilehash: e854764dc3f8d3ede79965302b62055b91df0a4c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165623"
---
# <a name="compiler-error-c3808"></a>Chyba kompilátoru C3808

> '*Type*': třída s atributem atributem ComImport nemůže definovat člen '*Member*', jsou povoleny pouze funkce abstract nebo dllimport

## <a name="remarks"></a>Poznámky

Typ, který je odvozen z <xref:System.Runtime.InteropServices.ComImportAttribute> nemůže definovat *člen*.

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

## <a name="example"></a>Příklad

Následující ukázka generuje C3808.

```cpp
// C3808.cpp
// compile with: /c /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 {
   int f() {}   // C3808
   virtual int g() abstract;   // OK

   [DllImport("msvcrt.dll")]
   int printf(System::String ^, int i);   // OK
};
```
