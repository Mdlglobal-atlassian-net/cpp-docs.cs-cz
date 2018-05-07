---
title: 'Postupy: zařazení ukazatelů na funkce pomocí služby PInvoke | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1aa8da5e5b6931fb46ff283a5be15da5b2c7325d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>Postupy: Zařazení ukazatelů na funkce pomocí služby PInvoke
Toto téma vysvětluje, jak spravované delegáti jde použít místo ukazatelů na funkce při vzájemné spolupráci se službou nespravovaných funkcí pomocí funkcí rozhraní .NET Framework P/Invoke. Programátory v jazyce Visual C++ jsou ale místo toho používají funkce interoperability C++ (Pokud je to možné), protože P/Invoke poskytuje malé kompilaci zpráv o chybách, není bezpečný a může být zdlouhavé pro implementaci. Pokud je jako knihovny DLL zabalené nespravovaného rozhraní API a zdrojový kód není k dispozici, P/Invoke je jedinou možností. Jinak najdete v následujících tématech:  
  
-   [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [Postupy: Zařazování zpětných volání a delegátů pomocí funkcí interoperability C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)  
  
 Nespravovaná rozhraní API, která přebírají ukazatele funkce jako argumenty nelze volat ze spravovaného kódu se spravovaným delegátem místo ukazatele nativní funkce. Kompilátor automaticky zařazuje delegáta k nespravovaným funkcím jako ukazatel na funkci a vloží kód nezbytné Přechod spravované nebo nespravované.  
  
## <a name="example"></a>Příklad  
 Následující kód se skládá z nespravovaného a spravovaný modul. Nespravovaný modul je knihovna DLL, která definuje funkci nazvanou TakesCallback, který přijímá ukazatel na funkci. Tato adresa se používá ke spuštění funkce.  
  
 Spravovaný modul definuje delegáta, který je zařazen do nativního kódu jako ukazatel na funkci a používá <xref:System.Runtime.InteropServices.DllImportAttribute> atribut vystavit nativní funkce TakesCallback do spravovaného kódu. V hlavní funkce je instance delegáta, vytvořit a předaný funkci TakesCallback. Výstup programu ukazuje, že tato funkce získá provedený nativní funkce TakesCallback.  
  
 Spravovaná funkce potlačí uvolňování paměti pro spravovaného delegáta k zabránění uvolňování paměti rozhraní .NET Framework z přemístění delegáta, zatímco nativní funkce.  
  
```cpp  
// TraditionalDll5.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   /* Declare an unmanaged function type that takes two int arguments  
      Note the use of __stdcall for compatibility with managed code */  
   typedef int (__stdcall *CALLBACK)(int);  
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);  
}  
  
int TakesCallback(CALLBACK fp, int n) {  
   printf_s("[unmanaged] got callback address, calling it...\n");  
   return fp(n);  
}  
```  
  
```cpp  
// MarshalDelegate.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
public delegate int GetTheAnswerDelegate(int);  
public value struct TraditionalDLL {  
   [DllImport("TraditionalDLL5.dll")]  
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);  
};  
  
int GetNumber(int n) {  
   Console::WriteLine("[managed] callback!");  
   static int x = 0;  
   ++x;  
   return x + n;  
}  
  
int main() {  
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);  
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;  
   Console::WriteLine("[managed] sending delegate as callback...");  
  
   int answer = TraditionalDLL::TakesCallback(fp, 42);  
}  
```  
  
 Všimněte si, že žádná část knihovny DLL je vystaven spravovaného kódu pomocí tradiční #include – direktiva. Ve skutečnosti knihovnu DLL přístupná za běhu, takže problémy s funkcí importovány s <xref:System.Runtime.InteropServices.DllImportAttribute> nebudou zjištěna v době kompilace.  
  
## <a name="see-also"></a>Viz také  
 [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)