---
title: Upozornění kompilátoru (úroveň 1) C4397
ms.date: 11/04/2016
f1_keywords:
- C4397
helpviewer_keywords:
- C4397
ms.assetid: 6346fdc2-dbbf-4fba-803a-32b0d0a707be
ms.openlocfilehash: fc13f83f79f8c8103184b4322a77866a78d149be
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964931"
---
# <a name="compiler-warning-level-1-c4397"></a>Upozornění kompilátoru (úroveň 1) C4397

DefaultCharSetAttribute se ignoruje.

<xref:System.Runtime.InteropServices.DefaultCharSetAttribute> ignoruje kompilátor společnosti Microsoft C++ . Pro určení znakové sady pro knihovnu DLL použijte možnost CharSet. Další informace najdete v tématu [použití C++ zprostředkovatele komunikace (implicitní PInvoke)](../../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4397.

```cpp
// C4397.cpp
// compile with: /W1 /c /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[module:DefaultCharSetAttribute(CharSet::Unicode)];   // C4397

[DllImport("kernel32", EntryPoint="CloseHandle", CharSet=CharSet::Unicode)]   // OK
extern "C" bool ImportDefault(IntPtr hObject);

public ref class MySettingVC {
public:
   void method() {
      ImportDefault(IntPtr::Zero);
   }
};

[StructLayout(LayoutKind::Explicit)]
public ref struct StructDefault1{};

public ref class ClassDefault1{};
```