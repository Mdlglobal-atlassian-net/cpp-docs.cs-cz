---
title: 'Postupy: Volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
ms.openlocfilehash: 1eb5d5669c49dd49a411c275f8845dbbab989df3
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988285"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>Postupy: Volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke

Funkce, které jsou implementované v nespravovaných knihovnách DLL, mohou být volány ze spravovaného kódu pomocí funkce vyvolání (volání nespravovaného kódu) platformy. Pokud zdrojový kód pro knihovnu DLL není k dispozici, je P/Invoke jedinou možností pro spolupráci. Na rozdíl od jiných jazyků .NET ale vizuál C++ nabízí alternativu ke volání nespravovaného volání. Další informace najdete v tématu [použití C++ zprostředkovatele komunikace (implicitní PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="example"></a>Příklad

Následující příklad kódu používá funkci Win32 [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) k načtení aktuálního rozlišení obrazovky v pixelech.

Pro funkce, které používají pouze vnitřní typy jako argumenty a návratové hodnoty, není vyžadována žádná další práce. Jiné datové typy, například ukazatele na funkce, pole a struktury, vyžadují další atributy, aby bylo zajištěno správné zařazování dat.

I když není vyžadováno, je vhodné, aby deklarace volání neexistují statické členy třídy hodnot, aby neexistovaly v globálním oboru názvů, jak je znázorněno v tomto příkladu.

```cpp
// pinvoke_basic.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value class Win32 {
public:
   [DllImport("User32.dll")]
   static int GetSystemMetrics(int);

   enum class SystemMetricIndex {
      // Same values as those defined in winuser.h.
      SM_CXSCREEN = 0,
      SM_CYSCREEN = 1
   };
};

int main() {
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);
}
```

## <a name="see-also"></a>Viz také:

[Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
