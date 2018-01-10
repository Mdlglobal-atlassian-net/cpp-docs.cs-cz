---
title: "Postupy: Zařazování polí pomocí služby PInvoke | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3694d6628005c49cc824e52d710e64e060822f96
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>Postupy: Zařazení polí pomocí služby PInvoke
Toto téma vysvětluje, jak nativních funkcí, které přijímají řetězce stylu jazyka C je možné volat pomocí řetězce typu CLR <xref:System.String> pomocí podpory volání nespravovaného kódu rozhraní .NET Framework. Programátoři jazyka Visual C++ se místo toho používají funkce interoperability C++ (Pokud je to možné), protože P/Invoke poskytuje malé kompilaci zpráv o chybách, není bezpečný a může být zdlouhavé pro implementaci. Pokud je jako knihovny DLL zabalené nespravovaného rozhraní API a zdrojový kód není k dispozici, P/Invoke je jedinou možností (jinak, najdete v části [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)).  
  
## <a name="example"></a>Příklad  
 Protože nativní a spravovaná pole jsou rozloženy odlišně v paměti, předávání úspěšně přes spravované nebo nespravované hranice vyžaduje převod nebo zařazování. Toto téma ukazuje, jak pole položek jednoduchých (blitable) lze předat nativních funkcí ze spravovaného kódu.  
  
 Jako spravovaných nebo nespravovaných dat zařazování obecně platí <xref:System.Runtime.InteropServices.DllImportAttribute> atribut se používá k vytvoření spravovaného vstupní bod pro každou nativní funkci, která bude použita. V případě funkcí, které přijímají polí jako argumentů <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut musíte použít také k určení pro kompilátor, jak budou data zařazována. V následujícím příkladu <xref:System.Runtime.InteropServices.UnmanagedType> výčtu slouží k označení, že spravované pole zařazeno jako pole ve stylu jazyka C.  
  
 Následující kód se skládá z nespravovaného a spravovaný modul. Nespravovaný modul je knihovna DLL, která definuje funkci, která přijímá pole celých čísel. Druhý modul je spravovaná aplikace příkazového řádku, která importuje tuto funkci, ale definuje z hlediska spravovaného pole a používá <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut k určení, zda mají být převedeny pole při volání nativní pole.  
  
 Spravovaný modul je kompilovat s/CLR, ale/CLR: pure pracuje stejně dobře. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
```cpp  
// TraditionalDll4.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);  
}  
  
void TakesAnArray(int len, int a[]) {  
   printf_s("[unmanaged]\n");  
   for (int i=0; i<len; i++)  
      printf("%d = %d\n", i, a[i]);  
}  
```  
  
```cpp  
// MarshalBlitArray.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value struct TraditionalDLL {  
   [DllImport("TraditionalDLL4.dll")]  
   static public void TakesAnArray(  
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);  
};  
  
int main() {  
   array<int>^ b = gcnew array<int>(3);  
   b[0] = 11;  
   b[1] = 33;  
   b[2] = 55;  
   TraditionalDLL::TakesAnArray(3, b);  
  
   Console::WriteLine("[managed]");  
   for (int i=0; i<3; i++)  
      Console::WriteLine("{0} = {1}", i, b[i]);  
}  
```  
  
 Všimněte si, že žádná část knihovny DLL je vystaven do spravovaného kódu přes tradiční #include – direktiva. Ve skutečnosti, protože knihovna DLL je přístup pouze za běhu, problémy s funkcemi, které se importovat s <xref:System.Runtime.InteropServices.DllImportAttribute> nebudou zjištěna v době kompilace.  
  
## <a name="see-also"></a>Viz také  
 [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)