---
title: 'Postupy: volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke | Dokumentace Microsoftu'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f849d2d9c3fd4a2d50d652ad159e93442b4c7ff3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404641"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>Postupy: Volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke

Funkce, které jsou implementovány v nespravovaných knihoven DLL lze volat ze spravovaného kódu pomocí vyvolání platformy (nespravovaného) funkce. Pokud není k dispozici zdrojový kód pro knihovnu DLL, P/Invoke je jedinou možností pro spolupráci. Ale na rozdíl od jiných jazyků .NET, Visual C++ poskytuje alternativu k P/Invoke. Další informace najdete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="example"></a>Příklad

Následující příklad kódu používá Win32 [GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics) funkce načtete aktuální rozlišení obrazovky v pixelech.

Pro funkce, které používají jenom vnitřní typy jako argumenty a návratové hodnoty žádná další práce je nutná. Jiné datové typy, jako je například ukazatele na funkce, polí a struktur, vyžadují další atributy, aby zařazování správná data.

I když to není potřeba, je vhodné nastavit P/Invoke deklarace statické členy třídy value class, takže neexistují v globálním oboru názvů, jak je ukázáno v tomto příkladu.

```
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

## <a name="see-also"></a>Viz také

[Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)