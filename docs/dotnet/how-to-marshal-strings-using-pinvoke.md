---
title: "Postupy: Zařazování řetězců pomocí služby PInvoke | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0047c76000d336ce18d2bbbab741dc965c1fbc59
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Postupy: Zařazení řetězců pomocí služby PInvoke
Toto téma vysvětluje, jak nativních funkcí, které přijímají řetězce stylu jazyka C nelze volat pomocí řetězce typu System::String pomocí podpory volání nespravovaného kódu rozhraní .NET Framework. Programátoři jazyka Visual C++ se místo toho používají funkce interoperability C++ (Pokud je to možné), protože P/Invoke poskytuje malé kompilaci zpráv o chybách, není bezpečný a může být zdlouhavé pro implementaci. Pokud je jako knihovny DLL zabalené nespravovaného rozhraní API a zdrojový kód není k dispozici, pak P/Invoke je jedinou možností, ale jinak zobrazit [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
 Spravovanými a nespravovanými řetězce jsou rozloženy odlišně v paměti, takže předají řetězce ze spravovaných do nespravovaných funkcí vyžaduje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut kompilátoru vložit vyžaduje převod mechanismy pro zařazování řetězcových dat. správně a bezpečně.  
  
 Stejně jako u funkce, které používají pouze vnitřní datové typy, <xref:System.Runtime.InteropServices.DllImportAttribute> deklarovat spravované vstupní body do nativních funkcí, ale--pro předávání řetězců--místo jako trvá stylu jazyka C řetězce, popisovač pro definování těchto vstupních bodů <xref:System.String> typu můžete místo toho použít. Tento parametr vyzve kompilátoru pro vložení kódu, který provede požadované převod. Pro každý argument funkce v nespravované funkci, která přebírá řetězec <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut slouží k označení, že objekt řetězec by měl být zařazen do nativní funkce jako řetězec stylu jazyka C.  
  
## <a name="example"></a>Příklad  
 Následující kód se skládá z nespravovaného a spravovaný modul. Nespravovaný modul je knihovna DLL, která definuje funkci nazvanou TakesAString, přijímající řetězec ANSI C-style ve formě char *. Spravovaný modul je aplikace příkazového řádku, která importuje funkci TakesAString, ale definuje jako přijetí spravovaného System.String místo char\*. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut slouží k označení jak spravovaný řetězec by měl být zařazen při volání TakesAString.  
  
 Spravovaný modul je kompilovat s/CLR, ale/CLR: pure pracuje stejně dobře.  
  
```  
// TraditionalDll2.cpp  
// compile with: /LD /EHsc  
#include <windows.h>  
#include <stdio.h>  
#include <iostream>  
  
using namespace std;  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
#define TRADITIONALDLL_API __declspec(dllexport)  
#else  
#define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
extern "C" {  
   TRADITIONALDLL_API void TakesAString(char*);  
}  
  
void TakesAString(char* p) {  
   printf_s("[unmanaged] %s\n", p);  
}  
```  
  
```  
// MarshalString.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value struct TraditionalDLL  
{  
   [DllImport("TraditionalDLL2.dll")]  
      static public void   
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);  
};  
  
int main() {  
   String^ s = gcnew String("sample string");  
    Console::WriteLine("[managed] passing managed string to unmanaged function...");  
   TraditionalDLL::TakesAString(s);  
   Console::WriteLine("[managed] {0}", s);  
}  
```  
  
 Tento postup způsobí, že kopii řetězec, který má být sestavený na nespravované haldě, změny provedené na řetězec pomocí nativní funkce se neprojeví v spravované kopie řetězce.  
  
 Všimněte si, že žádná část knihovny DLL je vystaven do spravovaného kódu přes tradiční #include – direktiva. Ve skutečnosti knihovnu DLL přístupná pouze za běhu, takže problémy s funkcí importovány s `DllImport` nebudou zjištěna v době kompilace.  
  
## <a name="see-also"></a>Viz také  
 [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)